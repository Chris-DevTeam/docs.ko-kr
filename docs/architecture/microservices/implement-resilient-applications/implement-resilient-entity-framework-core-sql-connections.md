---
title: 복원력 있는 Entity Framework Core SQL 연결 구현
description: 복원력 있는 Entity Framework Core SQL 연결을 구현하는 방법을 알아봅니다. 이 기술은 클라우드에서 Azure SQL Database를 사용하는 경우에 특히 중요합니다.
ms.date: 10/16/2018
ms.openlocfilehash: cae3550ce301750949b042957d5d10f0167e614c
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97899563"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a>복원력 있는 Entity Framework Core SQL 연결 구현

Azure SQL DB의 경우, EF(Entity Framework) Core에서 이미 내부 데이터베이스 연결 복원력과 다시 시도 논리를 제공합니다. 그러나 [복원력 있는 EF Core 연결](/ef/core/miscellaneous/connection-resiliency)을 원할 경우 각 <xref:Microsoft.EntityFrameworkCore.DbContext> 연결에 대한 Entity Framework 실행 전략을 사용하도록 설정해야 합니다.

예를 들어, EF 코어 연결 수준의 다음 코드는 연결이 실패할 경우 다시 시도되는 복원력 있는 SQL 연결을 할 수 있습니다.

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    // Other code ...
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        // ...
        services.AddDbContext<CatalogContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
            {
                sqlOptions.EnableRetryOnFailure(
                maxRetryCount: 10,
                maxRetryDelay: TimeSpan.FromSeconds(30),
                errorNumbersToAdd: null);
            });
        });
    }
//...
}
```

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>BeginTransaction 및 여러 DbContexts를 사용한 실행 전략 및 명시적 트랜잭션

EF Core 연결에서 다시 시도를 사용하도록 설정되면 EF Core를 사용하여 수행하는 각 작업이 자체적으로 다시 시도할 수 있는 작업이 됩니다. 일시적인 오류가 발생할 경우 `SaveChanges`에 대한 각 쿼리와 각 호출이 하나의 단위로 다시 시도됩니다.

그러나 코드에서 `BeginTransaction`을 사용하여 트랜잭션을 시작하는 경우 하나의 단위로 처리해야 하는 고유한 작업 그룹이 정의됩니다. 오류가 발생할 경우 트랜잭션 내부의 모든 항목을 롤백해야 합니다.

EF 실행 전략(재시도 정책)을 사용할 때 해당 트랜잭션을 실행하려고 시도하고 다중 DbContext에서 `SaveChanges`를 호출하는 경우 다음과 같은 예외가 표시됩니다.

> System.InvalidOperationException: 구성된 실행 전략 ‘SqlServerRetryingExecutionStrategy’는 사용자가 시작한 트랜잭션을 지원하지 않습니다. 'DbContext.Database.CreateExecutionStrategy()'에서 반환된 실행 전략을 사용하여 트랜잭션을 다시 시도가 가능한 단위로 트랜잭션의 모든 작업을 실행합니다.

해결책은 실행해야 하는 모든 것을 나타내는 대리자를 사용하여 EF 실행 전략을 수동으로 호출하는 것입니다. 일시적인 오류가 발생하면, 실행 전략에서 대리자를 다시 호출합니다. 예를 들어 다음 코드는 제품을 업데이트한 이후 다른 DbContext를 사용해야 하는 ProductPriceChangedIntegrationEvent 개체를 저장할 때, 두 개의 다중 DbContext(\_catalogContext 및 IntegrationEventLogContext)를 사용하여 eShopOnContainers에서 구현하는 방법을 보여 줍니다.

```csharp
public async Task<IActionResult> UpdateProduct(
    [FromBody]CatalogItem productToUpdate)
{
    // Other code ...

    var oldPrice = catalogItem.Price;
    var raiseProductPriceChangedEvent = oldPrice != productToUpdate.Price;

    // Update current product
    catalogItem = productToUpdate;

    // Save product's data and publish integration event through the Event Bus
    // if price has changed
    if (raiseProductPriceChangedEvent)
    {
        //Create Integration Event to be published through the Event Bus
        var priceChangedEvent = new ProductPriceChangedIntegrationEvent(
          catalogItem.Id, productToUpdate.Price, oldPrice);

       // Achieving atomicity between original Catalog database operation and the
       // IntegrationEventLog thanks to a local transaction
       await _catalogIntegrationEventService.SaveEventAndCatalogContextChangesAsync(
           priceChangedEvent);

       // Publish through the Event Bus and mark the saved event as published
       await _catalogIntegrationEventService.PublishThroughEventBusAsync(
           priceChangedEvent);
    }
    // Just save the updated product because the Product's Price hasn't changed.
    else
    {
        await _catalogContext.SaveChangesAsync();
    }
}
```

첫 번째 <xref:Microsoft.EntityFrameworkCore.DbContext>는 `_catalogContext`이고, 두 번째 `DbContext`는 `_catalogIntegrationEventService` 개체 내에 있습니다. 커밋 작업은 EF 실행 전략을 사용하여 모든 `DbContext` 개체에서 수행됩니다.

이 다중 `DbContext` 커밋을 달성하기 위해 `SaveEventAndCatalogContextChangesAsync`는 다음 코드와 같이 `ResilientTransaction` 클래스를 사용합니다.

```csharp
public class CatalogIntegrationEventService : ICatalogIntegrationEventService
{
    //…
    public async Task SaveEventAndCatalogContextChangesAsync(
        IntegrationEvent evt)
    {
        // Use of an EF Core resiliency strategy when using multiple DbContexts
        // within an explicit BeginTransaction():
        // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
        await ResilientTransaction.New(_catalogContext).ExecuteAsync(async () =>
        {
            // Achieving atomicity between original catalog database
            // operation and the IntegrationEventLog thanks to a local transaction
            await _catalogContext.SaveChangesAsync();
            await _eventLogService.SaveEventAsync(evt,
                _catalogContext.Database.CurrentTransaction.GetDbTransaction());
        });
    }
}
```

`ResilientTransaction.ExecuteAsync` 메서드는 기본적으로 전달된 `DbContext`(`_catalogContext`)에서 트랜잭션을 시작하고 `EventLogService`에서 해당 트랜잭션을 사용하여 `IntegrationEventLogContext`의 변경 내용을 저장하도록 한 다음, 전체 트랜잭션을 커밋합니다.

```csharp
public class ResilientTransaction
{
    private DbContext _context;
    private ResilientTransaction(DbContext context) =>
        _context = context ?? throw new ArgumentNullException(nameof(context));

    public static ResilientTransaction New (DbContext context) =>
        new ResilientTransaction(context);

    public async Task ExecuteAsync(Func<Task> action)
    {
        // Use of an EF Core resiliency strategy when using multiple DbContexts
        // within an explicit BeginTransaction():
        // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
        var strategy = _context.Database.CreateExecutionStrategy();
        await strategy.ExecuteAsync(async () =>
        {
            await using var transaction = await _context.Database.BeginTransactionAsync();
            await action();
            await transaction.CommitAsync();
        });
    }
}
```

## <a name="additional-resources"></a>추가 자료

- **ASP.NET MVC 애플리케이션에서 EF를 사용한 연결 복원력 및 명령 인터셉션** \
  [https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application)

- **Cesar de la Torre. 복원력 있는 Entity Framework Core SQL 연결 및 트랜잭션 사용** \
  <https://devblogs.microsoft.com/cesardelatorre/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
>[이전](implement-retries-exponential-backoff.md)
>[다음](use-httpclientfactory-to-implement-resilient-http-requests.md)
