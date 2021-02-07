---
description: '자세한 정보: WCF 단순화 기능'
title: WCF 단순화 기능
ms.date: 03/30/2017
ms.assetid: 4535a511-6064-4da0-b361-80262a891663
ms.openlocfilehash: cf89ff7775e2a162760c3c6c598a045ddccdf8d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703381"
---
# <a name="wcf-simplification-features"></a>WCF 단순화 기능

이 항목에서는 WCF 애플리케이션을 더 간단하게 작성할 수 있는 새로운 기능에 대해 설명합니다.

## <a name="simplified-generated-configuration-files"></a>단순화되어 생성된 구성 파일

Visual Studio에 서비스 참조를 추가하거나 SvcUtil.exe 도구를 사용하면 클라이언트 구성 파일이 생성됩니다. 이전 버전의 WCF에서는 바인딩 속성 값이 기본값인 경우를 포함하여 모든 바인딩 속성 값이 이러한 구성 파일에 포함되었습니다. WCF 4.5에서는 생성된 구성 파일에 기본값이 아닌 값으로 설정된 바인딩 속성만 포함됩니다.

다음은 WCF 3.0에서 생성된 구성 파일의 예입니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <system.serviceModel>
        <bindings>
            <basicHttpBinding>
                <binding name="BasicHttpBinding_IService1" closeTimeout="00:01:00"
                    openTimeout="00:01:00" receiveTimeout="00:10:00" sendTimeout="00:01:00"
                    allowCookies="false" bypassProxyOnLocal="false"
                    hostNameComparisonMode="StrongWildcard" maxBufferSize="65536"
                    maxBufferPoolSize="524288" maxReceivedMessageSize="65536"
                    messageEncoding="Text" textEncoding="utf-8" transferMode="Buffered"
                    useDefaultWebProxy="true">
                    <readerQuotas maxDepth="32" maxStringContentLength="8192"
                        maxArrayLength="16384" maxBytesPerRead="4096"
                        maxNameTableCharCount="16384" />
                    <security mode="None">
                        <transport clientCredentialType="None" proxyCredentialType="None"
                            realm="" />
                        <message clientCredentialType="UserName" algorithmSuite="Default" />
                    </security>
                </binding>
            </basicHttpBinding>
        </bindings>
        <client>
            <endpoint address="http://localhost:36906/Service1.svc" binding="basicHttpBinding"
                bindingConfiguration="BasicHttpBinding_IService1" contract="IService1"
                name="BasicHttpBinding_IService1" />
        </client>
    </system.serviceModel>
</configuration>
```

다음은 WCF 4.5에서 생성된 동일한 구성 파일의 예입니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <system.serviceModel>
        <bindings>
            <basicHttpBinding>
                <binding name="BasicHttpBinding_IService1" />
            </basicHttpBinding>
        </bindings>
        <client>
            <endpoint address="http://localhost:36906/Service1.svc" binding="basicHttpBinding"
                bindingConfiguration="BasicHttpBinding_IService1" contract="IService1"
                name="BasicHttpBinding_IService1" />
        </client>
    </system.serviceModel>
</configuration>
```

## <a name="contract-first-development"></a>계약 중심 개발

WCF는 이제 계약 중심 개발을 지원합니다. svcutil.exe 도구에는 WSDL 문서에서 서비스 및 데이터 계약을 생성할 수 있는/serviceContract 스위치가 있습니다.

## <a name="add-service-reference-from-a-portable-subset-project"></a>이식 가능한 하위 집합 프로젝트의 서비스 참조 추가

이식 가능한 하위 집합 프로젝트를 사용 하면 .NET 어셈블리 프로그래머는 여러 .NET 구현 (데스크톱, Silverlight, Windows Phone 및 Xbox)을 계속 지원 하면서 단일 소스 트리 및 빌드 시스템을 유지 관리할 수 있습니다. 이식 가능한 하위 집합 프로젝트는 .NET 구현에서 사용할 수 있는 어셈블리인 .NET 이식 가능한 라이브러리만 참조 합니다. 개발자 환경은 다른 WCF 클라이언트 애플리케이션에 서비스 참조를 추가하는 것과 동일합니다. 자세한 내용은 [이식 가능한 하위 집합 프로젝트의 서비스 참조 추가](add-service-reference-in-a-portable-subset-project.md)을 참조 하세요.

## <a name="aspnet-compatibility-mode-default-changed"></a>ASP.NET 호환 모드 기본값 변경

WCF는 개발자가 WCF 서비스를 작성할 때 ASP.NET HTTP 파이프라인 기능에 완전하게 액세스할 수 있게 해 주는 ASP.NET 호환 모드를 제공합니다. 이 모드를 사용 하려면 `aspNetCompatibilityEnabled` web.config의 섹션에서 특성을 true로 설정 해야 합니다 [\<serviceHostingEnvironment>](../configure-apps/file-schema/wcf/servicehostingenvironment.md) . 또한이 appDomain의 모든 서비스에는 `RequirementsMode` 속성이 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> 또는로 설정 되어 있어야 합니다 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required> . 기본적으로 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> 는로 설정 되 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> 고, 기본 WCF 서비스 응용 프로그램 템플릿은 특성을로 설정 합니다 `aspNetCompatibilityEnabled` `true` . 자세한 내용은 Windows Communication Foundation 4.5 및 [WCF 서비스와 ASP.NET](./feature-details/wcf-services-and-aspnet.md) [의 새로운 기능](whats-new.md) 을 참조 하세요.

## <a name="streaming-improvements"></a>스트리밍 향상

- 비동기 스트리밍 지원이 WCF에 새로 추가되었습니다. 비동기 스트리밍을 사용하려면 <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> 엔드포인트 동작을 서비스 호스트에 추가하고 <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> 속성을 `true`로 설정합니다. 따라서 서비스에서 읽는 속도가 느린 여러 클라이언트에 스트리밍된 메시지를 보낼 때 확장성이 개선될 수 있습니다. WCF는 더 이상 클라이언트당 하나의 스레드를 차단하지 않으며 다른 클라이언트에 서비스를 제공하기 위해 스레드를 개방합니다.

- 서비스가 IIS에서 호스팅되는 경우 메시지 버퍼링과 관련된 제한이 제거되었습니다. 이전 버전의 WCF에서는 스트리밍 메시지 전송을 사용한 IIS 호스팅 서비스 메시지를 수신할 때 ASP.NET에서 전체 메시지를 버퍼링한 후 WCF로 보냈습니다. 이 경우 메모리 소비가 매우 커집니다. 이 버퍼링은 .NET Framework 4.5에서 제거 되었으므로 이제 IIS에서 호스팅되는 WCF 서비스는 전체 메시지를 받기 전에 들어오는 스트림 처리를 시작할 수 있으므로 진정한 스트리밍이 가능 합니다. 이에 따라 WCF가 메시지에 즉시 응답할 수 있어 성능이 개선됩니다. 또한 들어오는 요청에 대한 ASP.NET 크기 제한인 `maxRequestLength` 값을 지정할 필요가 없습니다. 이 속성은 설정해도 무시됩니다. 에 대 한 자세한 `maxRequestLength` 내용은 [ \<httpRuntime> 구성 요소](/previous-versions/dotnet/netframework-1.1/e1f13641(v=vs.71))를 참조 하세요. MaxAllowedContentLength를 구성 해야 합니다. 자세한 내용은 [IIS 요청 제한](/previous-versions/iis/settings-schema/ms689462(v=vs.90))을 참조 하세요.

## <a name="new-transport-default-values"></a>새 전송 기본값

다음 표에는 변경된 설정과 추가 정보를 찾을 수 있는 위치가 나와 있습니다.

|속성|켜기|새 기본값|추가 정보|
|--------------|--------|-----------------|----------------------|
|channelInitializationTimeout|<xref:System.ServiceModel.NetTcpBinding>|30초|이 속성은 TCP 연결이 .NET 프레이밍 프로토콜을 사용 하 여 자신을 인증 하는 데 사용할 수 있는 시간을 결정 합니다. 서버가 인증을 수행하는 데 충분한 정보를 가지려면 클라이언트가 몇 가지 초기 데이터를 보내야 합니다. 이 시간 제한은 인증되지 않은 악의적 클라이언트가 서버에 너무 오래 연결되지 않도록 ReceiveTimeout(10분)보다 일부러 작게 설정합니다. 기본값은 30초입니다. 에 대 한 자세한 내용 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.ChannelInitializationTimeout%2A>|
|listenBacklog|<xref:System.ServiceModel.NetTcpBinding>|16 * 프로세서 수|이 소켓 수준 속성은 대기될 "보류 중 승인" 요청의 수를 설명합니다. 수신 백로그 큐가 가득 차면 새 소켓 요청이 거부 됩니다. 에 대 한 자세한 내용 <xref:System.ServiceModel.NetTcpBinding.ListenBacklog%2A>|
|maxPendingAccepts|ConnectionOrientedTransportBindingElement<br /><br /> SMSvcHost.exe|2 * 전송용 프로세서 수<br /><br /> 4 \* SMSvcHost.exe 프로세서 수|이 속성은 서버가 수신기에서 대기시킬 수 있는 채널 수를 제한합니다. MaxPendingAccepts가 너무 낮으면 모든 대기 채널이 연결 서비스를 시작한 후 새 채널이 수신을 시작하기 전까지 약간의 시간 간격이 있게 됩니다. 이 간격 동안 연결이 도달할 수 있으며 이 경우 서버에서 연결 대기 중인 채널이 없기 때문에 연결이 실패합니다. 이 속성은 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A> 속성을 큰 숫자로 설정하여 구성할 수 있습니다. 자세한 내용은 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingAccepts%2A> 및 [Net.tcp 포트 공유 서비스 구성](./feature-details/configuring-the-net-tcp-port-sharing-service.md) 을 참조 하세요.|
|maxPendingConnections|ConnectionOrientedTransportBindingElement|12 * 프로세서 수|이 속성은 전송에서 승인하였지만 ServiceModel 디스패처에서 선택하지 않은 연결 수를 제어합니다. 이 값을 설정하려면 바인딩 요소의 `MaxConnections` 또는 바인딩의 `maxOutboundConnectionsPerEndpoint`를 사용합니다. 에 대 한 자세한 내용 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A>|
|receiveTimeout|SMSvcHost.exe|30초|이 속성은 TCP 프레이밍 데이터를 읽고 내부 연결에서 연결 디스패치를 수행하기 위한 시간 제한을 지정합니다. 이는 들어오는 연결에서 프리앰블 데이터를 읽기 위해 SMSvcHost.exe 서비스를 유지할 시간의 상한을 설정하기 위해 존재합니다. 자세한 내용은 [Net.tcp Port Sharing Service 구성](./feature-details/configuring-the-net-tcp-port-sharing-service.md)을 참조 하세요.|

> [!NOTE]
> 이러한 새로운 기본값은 .NET Framework 4.5가 설치된 컴퓨터에 WCF 서비스를 배포할 경우에만 사용됩니다. 동일한 서비스를 .NET Framework 4.0이 설치된 컴퓨터에 배포할 경우에는 .NET Framework 4.0 기본값이 사용됩니다. 이 경우에는 이러한 설정을 명시적으로 구성하는 것이 좋습니다.

## <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas

<xref:System.Xml.XmlDictionaryReaderQuotas>에는 메시지를 만드는 동안 인코더가 사용하는 메모리의 크기를 제한하는 XML 사전 판독기에 대한 구성 가능 할당량 값이 포함됩니다. 이러한 할당량은 구성 가능하지만, 개발자가 이를 명시적으로 설정해야 할 가능성을 줄이기 위해 기본값이 변경되었습니다. 메모리 소비를 제한해서 복잡한 `MaxReceivedMessageSize`를 처리하지 않아도 되도록 <xref:System.Xml.XmlDictionaryReaderQuotas> 할당량은 변경되지 않았습니다. 다음 표에는 할당량, 새 기본값 및 각 할당량의 용도에 대한 간략한 설명이 나와 있습니다.

|할당량 이름|기본값|설명|
|----------------|-------------------|-----------------|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>|Int32.MaxValue|허용 되는 최대 배열 길이를 가져오거나 설정 합니다. 이 할당량은 바이트 배열을 포함하여 XML 판독기가 반환하는 기본 형식 배열의 최대 크기를 제한합니다. 이 할당량은 XML 판독기 자체의 메모리 소비량은 제한하지 않지만 판독기를 사용하는 모든 구성 요소의 메모리 소비량을 제한합니다. 예를 들어, <xref:System.Runtime.Serialization.DataContractSerializer> 가 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>로 보안이 설정된 판독기를 사용하는 경우에는 이 할당량보다 큰 바이트 배열을 역직렬화하지 않습니다.|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>|Int32.MaxValue|각 읽기에 대해 반환 되는 최대 허용 바이트를 가져오거나 설정 합니다. 이 할당량은 요소 시작 태그와 해당 특성을 읽을 때 단일 읽기 작업에서 읽는 바이트 수를 제한합니다. 비스트리밍 작업의 경우 요소 이름 자체는 할당량 계산에서 제외됩니다. XML 특성이 너무 많으면 특성 이름의 고유성을 확인해야 하기 때문에 처리 시간이 과도하게 오래 걸릴 수 있습니다. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A> 는 이 위협을 완화합니다.|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>|128 노드 수준|이 할당량은 XML 요소의 최대 중첩 깊이를 제한합니다. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> 는 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>와 상호 작용합니다. 판독기는 항상 현재 요소와 모든 상위 요소의 데이터를 메모리에 유지하기 때문에 판독기의 최대 메모리 소비량은 이 두 설정을 곱한 값에 비례합니다. 여러 층으로 중첩된 개체 그래프를 역직렬화할 때 역직렬 변환기가 전체 스택에 액세스하여 복구할 수 없는 <xref:System.StackOverflowException>이 throw될 수 있습니다. XML 중첩과 <xref:System.Runtime.Serialization.DataContractSerializer> 및 <xref:System.Xml.Serialization.XmlSerializer>모두의 개체 중첩 사이에는 직접적인 상관 관계가 있습니다. 이 위협을 완화하기 위해 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>를 사용합니다.|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>|Int32.MaxValue|이 할당량은 nametable에 허용되는 최대 문자 수를 제한합니다. nametable에는 XML 문서를 처리할 때 표시되는 특정 문자열(예: 네임스페이스 및 접두사)이 포함됩니다. 이러한 문자열은 메모리에 버퍼링되기 때문에 스트리밍이 예상되는 경우 과도한 버퍼링을 방지하기 위해 이 할당량이 사용됩니다.|
|<xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>|Int32.MaxValue|이 할당량은 XML 판독기에서 반환하는 최대 문자열 크기를 제한합니다. 이 할당량은 XML 판독기 자체에서는 메모리 소비량을 제한하지 않지만 판독기를 사용하는 구성 요소의 메모리 소비량을 제한합니다. 예를 들어, <xref:System.Runtime.Serialization.DataContractSerializer> 가 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>로 보안이 설정된 판독기를 사용하는 경우에는 이 할당량보다 큰 문자열을 역직렬화하지 않습니다.|

> [!IMPORTANT]
> 데이터 보안 유지에 대 한 자세한 내용은 [데이터의 보안 고려 사항](./feature-details/security-considerations-for-data.md) 에서 "XML을 안전 하 게 사용"을 참조 하세요.

> [!NOTE]
> 이러한 새로운 기본값은 .NET Framework 4.5가 설치된 컴퓨터에 WCF 서비스를 배포할 경우에만 사용됩니다. 동일한 서비스를 .NET Framework 4.0이 설치된 컴퓨터에 배포할 경우에는 .NET Framework 4.0 기본값이 사용됩니다. 이 경우에는 이러한 설정을 명시적으로 구성하는 것이 좋습니다.

## <a name="wcf-configuration-validation"></a>WCF 구성 유효성 검사

이제 Visual Studio 내에서 빌드 프로세스의 일부로 WCF 구성 파일의 유효성이 검사됩니다. 유효성 검사가 실패할 경우 유효성 검사 오류 또는 경고의 목록이 Visual Studio에 표시됩니다.

## <a name="xml-editor-tooltips"></a>XML 편집기 도구 설명

WCF 서비스의 기존 및 새 개발자들이 서비스를 구성하는 데 도움이 되도록 이제 Visual Studio XML 편집기에서 서비스 구성 파일에 포함된 모든 구성 요소 및 해당 속성에 대한 도구 설명을 제공합니다.

## <a name="basichttpbinding-improvements"></a>BasicHttpBinding 기능 향상

1. 단일 WCF 엔드포인트에서 서로 다른 여러 인증 모드에 응답할 수 있습니다.

2. IIS에서 WCF 서비스의 보안 설정을 제어할 수 있습니다.
