---
title: 리소스 사용 제어 및 성능 향상
ms.date: 03/30/2017
ms.assetid: 9a829669-5f76-4c88-80ec-92d0c62c0660
ms.openlocfilehash: f06dd0b7e66ae783b2f268551f15c5e6e8369b7f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255067"
---
# <a name="controlling-resource-consumption-and-improving-performance"></a>리소스 사용 제어 및 성능 향상

이 항목에서는 리소스 사용을 제어 하 고 성능 메트릭에 영향을 주는 WCF (Windows Communication Foundation) 아키텍처의 여러 영역에 있는 다양 한 속성에 대해 설명 합니다.

## <a name="properties-that-constrain-resource-consumption-in-wcf"></a>WCF에서 리소스 사용을 제한하는 속성

 WCF (Windows Communication Foundation)는 보안 또는 성능을 위해 특정 유형의 프로세스에 대 한 제약 조건을 적용 합니다. 이러한 제약 조건은 할당량이나 스로틀 같은 두 가지 기본 형태로 나타납니다. *할당량* 은 도달 하거나 초과 하는 경우 시스템의 특정 지점에서 즉각적인 예외가 발생 하는 제한입니다. *제한* 는 예외를 즉시 throw 하지 않는 제한입니다. 대신 스로틀 한계에 도달하면 프로세스는 해당 스로틀 값으로 설정된 한계 내에서만 계속 수행됩니다. 이러한 제한된 처리로 다른 위치에 예외가 트리거될 수 있지만, 애플리케이션에 따라 다릅니다.

 할당량과 스로틀 간의 차이 외에도 제약 속성 중 일부는 serialization 수준에, 일부는 전송 수준에, 일부는 애플리케이션 수준에 있는 등 차이가 있습니다. 예를 들어, 모든 시스템 제공 전송 바인딩 요소에 의해 구현되는 할당량인 <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType>는 악의적인 클라이언트가 메모리를 과도하게 사용하여 서비스에 대한 서비스 거부 공격을 하지 못하도록 기본적으로 65,536바이트로 설정됩니다. 일반적으로 이 값을 낮추면 성능이 향상됩니다.

 serialization 할당량의 예로는 <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> 속성이 있으며, 이 속성은 직렬 변환기가 단일 <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> 메서드 호출에서 직렬화하거나 역직렬화하는 최대 개체 수를 지정합니다. 애플리케이션 수준 스로틀의 예로는 <xref:System.ServiceModel.Dispatcher.ServiceThrottle.MaxConcurrentSessions%2A?displayProperty=nameWithType> 속성이 있으며, 기본적으로 이 속성은 동시 세션 채널 연결의 수를 10으로 제한합니다. 할당량과 달리 스로틀 값에 도달하면 애플리케이션에서는 처리를 계속 수행하지만 새 세션 채널을 허용하지는 않습니다. 따라서 다른 세션 채널 중 하나가 종료될 때까지 새 클라이언트에 연결되지 않습니다.

 이러한 제어는 특정 유형의 공격에 대해 즉각적인 완화를 제공하거나 메모리 사용 공간, 시작 시간 등과 같은 성능 메트릭을 향상하기 위해 디자인되었습니다. 그러나 애플리케이션에 따라 이러한 제어로 인해 서비스 애플리케이션 성능이 저하되거나 애플리케이션이 전혀 작동하지 않을 수 있습니다. 예를 들어, 비디오 스트리밍을 위해 개발된 애플리케이션은 기본 <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType> 속성을 쉽게 초과할 수 있습니다. 이 항목에서는 모든 수준의 WCF에서 응용 프로그램에 적용 되는 다양 한 컨트롤에 대 한 개요를 제공 하 고, 설정이 응용 프로그램에 hindering 여부에 대 한 자세한 정보를 얻을 수 있는 다양 한 방법을 설명 하며, 다양 한 문제를 해결 하는 방법을 설명 기본 속성이 serialization이나 전송 제약 조건이더라도 애플리케이션 수준에서 대부분의 스로틀 및 일부 할당량을 사용할 수 있습니다. 예를 들어, 서비스 클래스의 <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> 속성을 사용하여 <xref:System.ServiceModel.ServiceBehaviorAttribute.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> 속성을 설정할 수 있습니다.

> [!NOTE]
> 특정 문제가 있는 경우 먼저 [WCF 문제 해결 퀵 스타트](wcf-troubleshooting-quickstart.md) 를 읽고 문제 (및 해결 방법)가 나열 되어 있는지 확인 해야 합니다.

 Serialization 프로세스를 제한 하는 속성은 [데이터에 대 한 보안 고려 사항](./feature-details/security-considerations-for-data.md)에 나열 됩니다. 전송에 관련 된 리소스의 소비를 제한 하는 속성은 [전송 할당량](./feature-details/transport-quotas.md)에 나열 됩니다. 애플리케이션 계층에서 리소스 사용을 제한하는 속성은 <xref:System.ServiceModel.Dispatcher.ServiceThrottle> 클래스의 멤버입니다.

## <a name="detecting-application-and-performance-issues-related-to-quota-settings"></a>할당량 설정과 관련된 애플리케이션 및 성능 문제 검색

 일반적인 보안 문제에 대해 기본 보호를 제공하면서 다양한 종류의 애플리케이션에서 기본 애플리케이션 기능을 사용할 수 있도록 이전 기본값이 선택되어 있습니다. 그러나 애플리케이션이 안전하고 개발된 대로 작동하더라도 다른 애플리케이션 디자인에서 하나 이상의 스로틀 설정을 초과할 수 있습니다. 이러한 경우 어떤 수준에서 어떤 스로틀 값이 초과되었는지 식별하여 애플리케이션 처리량을 늘리기 위해 수행할 적합한 작업을 결정해야 합니다.

 일반적으로 애플리케이션을 작성하고 이를 디버깅할 때 구성 파일에서 또는 프로그래밍 방식으로 <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> 속성을 `true`로 설정합니다. 이렇게 하면 WCF가 클라이언트 응용 프로그램에 서비스 예외 스택 추적을 반환 하도록 지시 합니다. 이 기능은 관련이 있을 수 있는 할당량 설정을 표시하는 방식으로(이 설정이 문제인 경우) 대부분의 애플리케이션 수준 예외를 보고합니다.

 일부 예외는 런타임에 애플리케이션 계층의 표시 범위 아래에서 발생하고, 이 메커니즘을 사용하여 반환되지 않으며, 사용자 지정 <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> 구현에 의해 처리될 수 없습니다. Microsoft Visual Studio와 같은 개발 환경을 사용하는 경우 이러한 예외의 대부분이 자동으로 표시됩니다. 그러나 일부 예외는 [내 코드만](/visualstudio/debugger/just-my-code) Visual Studio와 같은 개발 환경 설정에서 마스킹할 수 있습니다.

 개발 환경의 기능에 관계 없이 WCF 추적 및 메시지 로깅 기능을 사용 하 여 모든 예외를 디버그 하 고 응용 프로그램의 성능을 튜닝할 수 있습니다. 자세한 내용은 [추적을 사용 하 여 응용 프로그램 문제 해결](./diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)을 참조 하세요.

## <a name="performance-issues-and-xmlserializer"></a>성능 문제 및 XmlSerializer

 <xref:System.Xml.Serialization.XmlSerializer>를 사용하여 serialize할 수 있는 데이터 형식을 사용하는 서비스 및 클라이언트 애플리케이션은 런타임에 해당 데이터 형식에 대한 serialization 코드를 생성하고 컴파일합니다. 이로 인해 시작 시 성능이 저하될 수 있습니다.

> [!NOTE]
> 미리 생성된 serialization 코드는 서비스가 아닌 클라이언트 애플리케이션에서만 사용될 수 있습니다.

 [ServiceModel Metadata 유틸리티 도구 (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) 는 응용 프로그램에 대해 컴파일된 어셈블리에서 필요한 serialization 코드를 생성 하 여 이러한 응용 프로그램의 시작 성능을 향상 시킬 수 있습니다. 자세한 내용은 [방법: XmlSerializer를 사용 하 여 WCF 클라이언트 응용 프로그램의 시작 시간 향상](./feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)을 참조 하세요.

## <a name="performance-issues-when-hosting-wcf-services-under-aspnet"></a>WCF 서비스를 ASP.NET 호스팅할 때의 성능 문제

WCF 서비스를 IIS 및 ASP.NET에 호스팅하는 경우 IIS 및 ASP.NET의 구성 설정이 WCF 서비스의 처리량 및 메모리 사용 공간에 영향을 줄 수 있습니다.  ASP.NET 성능에 대 한 자세한 내용은 [ASP.NET 성능 향상](/previous-versions/msp-n-p/ff647787(v=pandp.10))을 참조 하세요. 예상치 않은 결과를 일으킬 수 있는 설정 중 하나는 <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A>의 속성인 <xref:System.Web.Configuration.ProcessModelSection>입니다. 애플리케이션의 클라이언트 수가 고정되어 있거나 적은 경우 <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A>를 2로 설정하면 다중 프로세서 컴퓨터에서 처리량이 크게 높아져 CPU 사용률이 100%에 가깝게 됩니다. 이러한 성능 증가는 비용을 초래합니다. 또한 메모리 사용량도 증가하여 확장성이 저하됩니다.

## <a name="see-also"></a>참고 항목

- [관리 및 진단](./diagnostics/index.md)
- [큰 데이터 및 스트리밍](./feature-details/large-data-and-streaming.md)
