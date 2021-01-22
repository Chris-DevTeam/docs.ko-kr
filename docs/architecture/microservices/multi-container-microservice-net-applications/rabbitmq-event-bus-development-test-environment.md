---
title: RabbitMQ를 사용하여 개발 또는 테스트 환경에 대한 이벤트 서비스 구현
description: 컨테이너화된 .NET 애플리케이션의 .NET 마이크로 서비스 아키텍처 | RabbitMQ를 사용하여 개발 또는 테스트 환경의 통합 이벤트에 대해 이벤트 버스 메시징 구현
ms.date: 01/13/2021
ms.openlocfilehash: a1e7d11e376080a03269f202fa6ae24ffeb0f4d2
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188083"
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a>RabbitMQ를 사용하여 개발 또는 테스트 환경에 대한 이벤트 서비스 구현

컨테이너에서 실행 중인 RabbitMQ에 기반하는 사용자 지정 이벤트 버스를 만들면 eShopOnContainers 애플리케이션이 수행한 대로 개발 및 테스트 환경에 대해서만 사용해야 합니다. 프로덕션 준비가 완료된 서비스 버스의 일부로 빌드하지 않는 경우 프로덕션 환경에 사용하지 않아야 합니다. 간단한 사용자 지정 이벤트 버스에는 상용 서비스 버스에 있는 프로덕션에 사용 가능한 중요한 여러 기능이 없을 수 있습니다.

eShopOnContainers에서 이벤트 버스 사용자 지정 구현 중 하나는 기본적으로 RabbitMQ API를 사용하는 라이브러리입니다. Azure Service Bus에 기반한 다른 구현이 있습니다.

RabbitMQ를 사용하는 이벤트 버스 구현을 통해 그림 6-21에 표시된 대로 마이크로 서비스가 이벤트를 구독하고, 게시하고, 수신할 수 있습니다.

![메시지 발신자와 메시지 수신자 사이의 RabbitMQ를 보여 주는 다이어그램](./media/rabbitmq-event-bus-development-test-environment/rabbitmq-implementation.png)

**그림 6-21** 이벤트 버스의 RabbitMQ 구현

RabbitMQ는 메시지 게시자와 구독자 간에 배포를 처리하는 중개자의 역할을 합니다. 코드에서 EventBusRabbitMQ 클래스는 제네릭 IEventBus 인터페이스를 구현합니다. 해당 구현은 이 개발/테스트 버전에서 프로덕션 버전으로 교체할 수 있도록 종속성 주입을 기반으로 합니다.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
}
```

샘플 개발/테스트 이벤트 버스의 RabbitMQ 구현은 상용구 코드입니다. RabbitMQ 서버에 대한 연결을 처리하고 큐에 메시지 이벤트를 게시하기 위한 코드를 제공해야 합니다. 또한 각 이벤트 유형에 대해 통합 이벤트 처리기의 컬렉션 사전을 구현해야 합니다. 이러한 이벤트 유형에는 그림 6-21에 표시된 대로 각 수신기 마이크로 서비스에 대한 다른 인스턴스화 및 구독이 있을 수 있습니다.

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a>RabbitMQ를 사용하여 단순 게시 메서드 구현

다음 코드는 전체 시나리오를 보여 주기 위해 RabbitMQ에서 이벤트 버스를 구현하는 *_간소화된_* 버전입니다. 실제로는 이러한 방식으로 연결을 처리하지 않습니다. 전체 구현을 확인하려면 [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) 리포지토리에서 실제 코드를 참조하세요.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...

    public void Publish(IntegrationEvent @event)
    {
        var eventName = @event.GetType().Name;
        var factory = new ConnectionFactory() { HostName = _connectionString };
        using (var connection = factory.CreateConnection())
        using (var channel = connection.CreateModel())
        {
            channel.ExchangeDeclare(exchange: _brokerName,
                type: "direct");
            string message = JsonConvert.SerializeObject(@event);
            var body = Encoding.UTF8.GetBytes(message);
            channel.BasicPublish(exchange: _brokerName,
                routingKey: eventName,
                basicProperties: null,
                body: body);
       }
    }
}
```

eShopOnContainers 애플리케이션에서 Publish 메서드의 [실제 코드](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs)는 [Polly](https://github.com/App-vNext/Polly) 재시도 정책을 사용하여 향상됩니다. 그러면 RabbitMQ 컨테이너가 준비되지 않은 경우 작업을 몇 번 다시 시도합니다. 이 시나리오는 docker-compose가 컨테이너를 시작할 때 발생할 수 있습니다. 예를 들어 RabbitMQ 컨테이너가 다른 컨테이너보다 느리게 시작될 수도 있습니다.

앞서 언급했듯이 이 코드가 개발/테스트 환경에서만 사용되도록 RabbitMQ에 여러 가지 구성을 사용할 수 있습니다.

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a>RabbitMQ API를 사용하여 구독 코드 구현

다음 코드는 게시 코드로 RabbitMQ에 대한 이벤트 버스 구현을 간소화합니다. 일반적으로 개선하는 경우가 아니면 변경할 필요가 없습니다.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...

    public void Subscribe<T, TH>()
        where T : IntegrationEvent
        where TH : IIntegrationEventHandler<T>
    {
        var eventName = _subsManager.GetEventKey<T>();

        var containsKey = _subsManager.HasSubscriptionsForEvent(eventName);
        if (!containsKey)
        {
            if (!_persistentConnection.IsConnected)
            {
                _persistentConnection.TryConnect();
            }

            using (var channel = _persistentConnection.CreateModel())
            {
                channel.QueueBind(queue: _queueName,
                                    exchange: BROKER_NAME,
                                    routingKey: eventName);
            }
        }

        _subsManager.AddSubscription<T, TH>();
    }
}
```

각 이벤트 유형에는 RabbitMQ에서 이벤트를 가져오는 관련 채널이 있습니다. 그런 다음, 채널 및 이벤트 유형마다 필요한 만큼 많은 이벤트 처리기가 있을 수 있습니다.

구독 메서드는 IIntegrationEventHandler 개체를 허용합니다. 이는 현재 마이크로 서비스의 콜백 메서드 및 해당 관련 IntegrationEvent 개체와 같습니다. 그런 다음, 코드는 클라이언트 마이크로 서비스마다 각 통합 이벤트 유형이 가질 수 있는 이벤트 처리기의 목록에 해당 이벤트 처리기를 추가합니다. 클라이언트 코드가 이벤트를 구독하지 않은 경우 코드가 다른 서비스에서 해당 이벤트를 게시할 때 RabbitMQ의 푸시 스타일로 이벤트를 수신할 수 있도록 이벤트 유형에 대한 채널을 만듭니다.

위에서 언급한 것처럼, eShopOnContainers에서 구현된 이벤트 버스는 주 시나리오만 처리하므로 프로덕션 환경에서 사용할 수 있는 준비가 되지 않았으므로 교육 목적으로만 제공됩니다.

프로덕션 시나리오의 경우 아래 추가 리소스(RabbitMQ 관련 내용)와 [마이크로 서비스 간 이벤트 기반 통신 구현](./integration-event-based-microservice-communications.md#additional-resources) 섹션을 확인하세요.

## <a name="additional-resources"></a>추가 자료

RabbitMQ에 대한 지원을 제공하는 프로덕션 준비가 완료된 솔루션입니다.

- _ *EasyNetQ** - RabbitMQ용 오픈 소스 .NET API 클라이언트
  <https://easynetq.com/>

- **MassTransit** \
  <https://masstransit-project.com/>
  
> [!div class="step-by-step"]
> [이전](integration-event-based-microservice-communications.md)
> [다음](subscribe-events.md)
