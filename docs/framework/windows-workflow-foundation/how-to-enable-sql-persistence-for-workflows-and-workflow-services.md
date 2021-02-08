---
description: '방법: 워크플로 및 워크플로 서비스에 SQL 지 속성 사용에 대 한 자세한 정보'
title: '방법: 워크플로 및 워크플로 서비스에 SQL 지속성 사용'
ms.date: 03/30/2017
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
ms.openlocfilehash: 5c124c4ec1d75d4b3b24468c04a4fb82236aa29a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777725"
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a>방법: 워크플로 및 워크플로 서비스에 SQL 지속성 사용

이 항목에서는 프로그래밍 방식과 구성 파일을 사용하여 워크플로 및 워크플로 서비스에 지속성을 사용하도록 SQL 워크플로 인스턴스 저장소 기능을 구성하는 방법을 설명합니다.

Windows Server AppFabric은 지속성의 구성 프로세스를 단순화합니다. 자세한 내용은 [App Fabric 지 속성 구성](/previous-versions/appfabric/ee790848(v=azure.10))을 참조 하세요.

SQL 워크플로 인스턴스 저장소 기능을 사용하기 전에 이 기능에서 워크플로 인스턴스를 유지하는 데 사용할 데이터베이스를 만들어야 합니다. [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 설치 프로그램에서는 SQL 워크플로 인스턴스 저장소 기능과 관련된 SQL 스크립트 파일을 %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN 폴더에 복사합니다. SQL 워크플로 인스턴스 저장소에서 워크플로 인스턴스를 유지하는 데 사용할 SQL Server 2005 또는 SQL Server 2008 데이터베이스에 대해 이 스크립트 파일을 실행합니다. SqlWorkflowInstanceStoreSchema.sql 파일을 먼저 실행한 다음 SqlWorkflowInstanceStoreLogic.sql 파일을 실행합니다.

> [!NOTE]
> 지속성 데이터베이스를 정리하여 새 데이터베이스 상태를 만들려면 %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN의 스크립트를 다음 순서대로 실행합니다.
>
> 1. SqlWorkflowInstanceStoreSchema.sql
> 2. SqlWorkflowInstanceStoreLogic.sql

> [!IMPORTANT]
> 지속성 데이터베이스를 만들지 않으면 호스트가 워크플로를 유지하려고 시도할 때 SQL 워크플로 인스턴스 저장소 기능에서 다음과 유사한 예외가 throw됩니다.
>
> System.Data.SqlClient.SqlException: 'System.Activities.DurableInstancing.CreateLockOwner' 저장 프로시저를 찾을 수 없습니다.

다음 단원에서는 SQL 워크플로 인스턴스 저장소를 사용하여 워크플로 및 워크플로 서비스에 지속성을 사용하는 방법을 설명합니다. SQL 워크플로 인스턴스 저장소의 속성에 대 한 자세한 내용은 [Sql 워크플로 인스턴스 저장소의 속성](properties-of-sql-workflow-instance-store.md)을 참조 하세요.

## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a>WorkflowApplication을 사용하는 자체 호스팅 워크플로에 지속성 사용

<xref:System.Activities.WorkflowApplication> 개체 모델을 사용하여 프로그래밍 방식으로 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>을 사용하는 자체 호스팅 워크플로에 지속성을 사용할 수 있습니다. 다음 절차에서는 이를 수행하는 단계를 보여 줍니다.

#### <a name="to-enable-persistence-for-self-hosted-workflows"></a>자체 호스팅 워크플로에 지속성을 사용하려면

1. System.Activities.DurableInstancing.dll에 대 한 참조를 추가 합니다.

2. 소스 파일 맨 위의 기존 "using" 문 뒤에 다음 문을 추가합니다.

    ```csharp
    using System.Activities.DurableInstancing;
    ```

3. <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>를 구성하고 다음 코드 예제에서와 같이 <xref:System.Activities.WorkflowApplication.InstanceStore%2A>의 <xref:System.Activities.WorkflowApplication> 에 이를 할당합니다.

    ```csharp
    SqlWorkflowInstanceStore store =
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");

    WorkflowApplication wfApp =
        new WorkflowApplication(new Workflow1());

    wfApp.InstanceStore = store;
    ```

   > [!NOTE]
   > SQL Server 에디션에 따라 연결 문자열 서버 이름이 다를 수 있습니다.

4. <xref:System.Activities.WorkflowApplication.Persist%2A> 개체에 대해 <xref:System.Activities.WorkflowApplication> 메서드를 호출하여 워크플로를 유지하거나 <xref:System.Activities.WorkflowApplication.Unload%2A> 메서드를 호출하여 워크플로를 유지하고 언로드합니다. <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> 개체를 통해 발생한 <xref:System.Activities.WorkflowApplication> 이벤트를 처리하고 <xref:System.Activities.PersistableIdleAction.Persist>의 적절한 멤버(<xref:System.Activities.PersistableIdleAction.Unload> 또는 <xref:System.Activities.PersistableIdleAction>)를 반환할 수도 있습니다.

   ```csharp
   wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
   {
       return PersistableIdleAction.Persist;
   };
   ```

> [!NOTE]
> 단계별 지침은 방법: [시작 자습서](getting-started-tutorial.md) 의 [장기 실행 워크플로 만들기 및 실행](how-to-create-and-run-a-long-running-workflow.md) 단계를 참조 하세요.

## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a>WorkflowServiceHost를 사용하는 자체 호스팅 워크플로 서비스에 지속성 사용

<xref:System.ServiceModel.WorkflowServiceHost> 클래스 또는 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> 클래스를 사용하여 프로그래밍 방식으로 <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A>를 사용하는 자체 호스팅 워크플로 서비스에 지속성을 허용할 수 있습니다.

### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a>SqlWorkflowInstanceStoreBehavior 클래스 사용

다음 절차에서는 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> 클래스를 사용하여 자체 호스팅 워크플로 서비스에 지속성을 사용하는 방법을 설명합니다.

#### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a>SqlWorkflowInstanceStoreBehavior를 통해 지속성을 사용하려면

1. System.ServiceModel.dll에 참조를 추가합니다.

2. 소스 파일 맨 위의 기존 "using" 문 뒤에 다음 문을 추가합니다.

    ```csharp
    using System.ServiceModel.Activities.Description;
    ```

3. ph x="1" /&gt; 인스턴스를 만들고 워크플로 서비스에 대한 엔드포인트를 추가합니다.

    ```csharp
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");
    ```

4. `SqlWorkflowInstanceStoreBehavior` 개체를 구성하고 동작 개체의 속성을 설정합니다.

    ```csharp
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");
    host.Description.Behaviors.Add(instanceStoreBehavior);
    ```

5. 워크플로 서비스 호스트를 엽니다.

    ```csharp
    host.Open();
    ```

### <a name="using-the-durableinstancingoptions-property"></a>DurableInstancingOptions 속성 사용

`SqlWorkflowInstanceStoreBehavior`가 적용되면 `DurableInstancingOptions.InstanceStore`의 `WorkflowServiceHost`는 구성 값을 사용하여 만든 `SqlWorkflowInstanceStore` 개체로 설정됩니다. 다음 코드 예제에서와 같이 <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> 클래스를 사용하지 않고 프로그래밍 방식으로 `WorkflowServiceHost`의 `SqlWorkflowInstanceStoreBehavior` 속성을 설정할 수도 있습니다.

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a>구성 파일을 통해 WorkflowServiceHost를 사용하는 WAS 호스팅 워크플로 서비스에 지속성 사용

구성 파일을 통해 자체 호스팅 또는 WAS(Windows Process Activation Service) 호스팅 워크플로 서비스에 지속성을 사용할 수 있습니다. WAS 호스팅 워크플로 서비스는 자체 호스팅 워크플로 서비스와 마찬가지로 WorkflowServiceHost를 사용합니다.

`SqlWorkflowInstanceStoreBehavior`XML 구성을 통해 [SQL 워크플로 인스턴스 저장소](sql-workflow-instance-store.md) 속성을 편리 하 게 변경할 수 있도록 하는 서비스 동작입니다. WAS 호스팅 워크플로 서비스에는 Web.config 파일을 사용합니다. 다음 구성 예제에서는 구성 파일에서 `sqlWorkflowInstanceStore` 동작 요소를 사용하여 SQL 워크플로 인스턴스 저장소를 구성하는 방법을 보여 줍니다.

```xml
<serviceBehaviors>
    <behavior name="">
        <sqlWorkflowInstanceStore
                    connectionString="Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"
                    instanceEncodingOption="GZip | None"
                    instanceCompletionAction="DeleteAll | DeleteNothing"
                    instanceLockedExceptionAction="NoRetry | BasicRetry |AggressiveRetry"
                    hostLockRenewalPeriod="00:00:30"
                    runnableInstancesDetectionPeriod="00:00:05" />

    </behavior>
</serviceBehaviors>
```

`connectionString` 또는 `connectionStringName` 속성의 값을 설정하지 않으면 SQL 워크플로 인스턴스 저장소에서는 기본 명명된 연결 문자열 `DefaultSqlWorkflowInstanceStoreConnectionString`을 사용합니다.

`SqlWorkflowInstanceStoreBehavior`가 적용되면 `DurableInstancingOptions.InstanceStore`의 `WorkflowServiceHost`는 구성 값을 사용하여 만든 `SqlWorkflowInstanceStore` 개체로 설정됩니다. 서비스 동작 요소를 사용하지 않고 프로그래밍 방식으로 같은 작업을 수행하여 `SqlWorkflowInstanceStore`와 함께 `WorkflowServiceHost`를 사용할 수 있습니다.

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

> [!IMPORTANT]
> Web.config 파일에는 사용자 이름 및 암호와 같은 중요한 정보를 저장하지 않는 것이 좋습니다. Web.config 파일에 중요한 정보를 저장하는 경우 파일 시스템 ACL(액세스 제어 목록)을 사용하여 Web.config 파일에 대한 액세스를 보호해야 합니다. 또한 [보호 된 구성을 사용 하 여 구성 정보 암호화](/previous-versions/aspnet/53tyfkaw(v=vs.100))에 설명 된 대로 구성 파일 내에서 구성 값을 보호할 수도 있습니다.

### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a>SQL 워크플로 인스턴스 저장소 기능과 관련된 Machine.config 요소

[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]를 설치하면 SQL 워크플로 인스턴스 저장소 기능과 관련된 다음 요소가 Machine.config 파일에 추가됩니다.

- \<sqlWorkflowInstanceStore>구성 파일의 서비스 동작 요소를 사용 하 여 서비스에 대 한 지 속성을 구성할 수 있도록 Machine.config 파일에 다음 동작 확장 요소를 추가 합니다.

    ```xml
    <configuration>
        <system.serviceModel>
            <extensions>
                <behaviorExtensions>
                    <add name="sqlWorkflowInstanceStore" type="System.Activities.DurableInstancing.SqlWorkflowInstanceStoreElement, System.Activities.DurableInstancing, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
                </behaviorExtensions>
            </extensions>
        </system.serviceModel>
    </configuration>
    ```
