---
description: '자세한 정보: 익명 클라이언트를 사용 하는 메시지 보안'
title: 익명 클라이언트를 사용하는 메시지 보안
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
ms.openlocfilehash: 921ddd9e8e7d2a860f3516c452870bc2bb150911
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726977"
---
# <a name="message-security-with-an-anonymous-client"></a>익명 클라이언트를 사용하는 메시지 보안

다음 시나리오에서는 WCF (Windows Communication Foundation) 메시지 보안을 통해 보호 되는 클라이언트 및 서비스를 보여 줍니다. 이 디자인은 전송 보안 대신 메시지 보안을 사용하여 나중에 보다 다양한 클레임 기반 모델을 지원할 수 있도록 하는 것을 목적으로 합니다. 권한 부여에 대 한 다양 한 클레임 사용에 대 한 자세한 내용은 [Id 모델을 사용 하 여 클레임 및 권한 부여 관리](managing-claims-and-authorization-with-the-identity-model.md)를 참조 하세요.

응용 프로그램 예제는 [메시지 보안 익명](../samples/message-security-anonymous.md)을 참조 하세요.

![익명 클라이언트를 사용 하는 메시지 보안](media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")

|특성|설명|
|--------------------|-----------------|
|보안 모드|메시지|
|상호 운용성|WCF만|
|인증(서버)|초기 협상에 서버 인증이 필요하지만 클라이언트 인증은 필요하지 않습니다.|
|인증(클라이언트)|없음|
|무결성|예, 공유 보안 컨텍스트 사용|
|기밀성|예, 공유 보안 컨텍스트 사용|
|전송|HTTP|

## <a name="service"></a>서비스

다음 코드와 구성은 독립적으로 실행되어야 합니다. 다음 중 하나를 수행합니다.

- 구성 없이 코드를 사용하여 독립 실행형 서비스를 만듭니다.

- 제공된 구성을 사용하여 서비스를 만들지만 엔드포인트를 정의하지 않습니다.

### <a name="code"></a>코드

다음 코드에서는 메시지 보안을 사용하는 서비스 엔드포인트를 만드는 방법을 보여 줍니다.

[!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
[!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]

### <a name="configuration"></a>Configuration

코드 대신 다음 구성을 사용할 수 있습니다. 서비스 동작 요소를 사용하여 서비스를 클라이언트에 인증하는 데 사용되는 인증서를 지정합니다. 서비스 요소는 `behaviorConfiguration` 특성을 사용하여 동작을 지정해야 합니다. 바인딩 요소는 클라이언트 자격 증명 형식을 `None`으로 지정하여 익명 클라이언트가 서비스를 사용할 수 있게 합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="ServiceCredentialsBehavior">
          <serviceCredentials>
            <serviceCertificate findValue="contoso.com"
                                storeLocation="LocalMachine"
                                storeName="My" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <services>
      <service behaviorConfiguration="ServiceCredentialsBehavior"
               name="ServiceModel.Calculator">
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="WSHttpBinding_ICalculator"
                  name="CalculatorService"
                  contract="ServiceModel.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client />
  </system.serviceModel>
</configuration>
```

## <a name="client"></a>클라이언트

다음 코드와 구성은 독립적으로 실행되어야 합니다. 다음 중 하나를 수행합니다.

- 이 코드와 클라이언트 코드를 사용하여 독립 실행형 클라이언트를 만듭니다.

- 엔드포인트 주소를 정의하지 않는 클라이언트를 만듭니다. 대신 구성 이름을 인수로 사용하는 클라이언트 생성자를 사용합니다. 다음은 그 예입니다. 

    [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
    [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a>코드

다음 코드에서는 클라이언트 인스턴스를 만듭니다. 바인딩은 메시지 모드 보안을 사용하며 클라이언트 자격 증명 형식은 none으로 설정됩니다.

[!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
[!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]

### <a name="configuration"></a>Configuration

다음 코드에서는 클라이언트를 구성합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client>
      <endpoint address="http://machineName/Calculator"
        binding="wsHttpBinding"
        bindingConfiguration="WSHttpBinding_ICalculator"
        contract="ICalculator"
        name="WSHttpBinding_ICalculator">
        <identity>
          <dns value="contoso.com" />
        </identity>
      </endpoint>
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a>참고 항목

- [보안 개요](security-overview.md)
- [분산 애플리케이션 보안](distributed-application-security.md)
- [Message Security Anonymous](../samples/message-security-anonymous.md)
- [서비스 ID 및 인증](service-identity-and-authentication.md)
- [Windows Server AppFabric 보안 모델](/previous-versions/appfabric/ee677202(v=azure.10))
