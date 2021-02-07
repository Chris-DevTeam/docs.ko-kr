---
description: '자세히 알아보기: 클라이언트 보안'
title: 클라이언트에 보안 설정
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], security considerations
ms.assetid: 44c8578c-9a5b-4acd-8168-1c30a027c4c5
ms.openlocfilehash: d78ad2fba00a0707dcf1c63681d9d76e68a31c00
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99676445"
---
# <a name="securing-clients"></a>클라이언트에 보안 설정

WCF (Windows Communication Foundation)에서 서비스는 클라이언트에 대 한 보안 요구 사항을 결정 합니다. 즉, 서비스는 사용할 보안 모드 및 클라이언트가 자격 증명을 제공해야 하는지 여부를 지정합니다. 따라서 클라이언트 보안 설정 프로세스는 간단합니다. 서비스에서 가져온 메타데이터를 사용하여(게시된 경우) 클라이언트를 빌드하면 됩니다. 메타데이터는 클라이언트를 구성하는 방법을 지정합니다. 서비스에서 클라이언트가 자격 증명을 제공해야 하는 경우 요구 사항에 맞는 자격 증명을 가져와야 합니다. 이 항목에서는 이 과정을 자세히 설명합니다. 보안 서비스를 만드는 방법에 대 한 자세한 내용은 [서비스 보안](securing-services.md)설정을 참조 하세요.  
  
## <a name="the-service-specifies-security"></a>서비스에서 보안 지정  

 기본적으로 WCF 바인딩에는 보안 기능이 사용 됩니다. 예외는 <xref:System.ServiceModel.BasicHttpBinding> 입니다. 따라서 WCF를 사용 하 여 서비스를 만든 경우 인증, 기밀성 및 무결성을 보장 하기 위해 보안을 구현할 가능성이 높아집니다. 이러한 경우 서비스가 제공하는 메타데이터는 보안 통신 채널을 설정하는 데 필요한 사항을 표시합니다. 서비스 메타데이터에 보안 요구 사항이 없는 경우 서비스에 SSL(Secure Sockets Layer) over HTTP와 같은 보안 스키마를 적용할 수 없습니다. 그러나 서비스에서 클라이언트가 자격 증명을 제공해야 하는 경우 클라이언트 개발자, 배포자 또는 관리자는 클라이언트가 서비스에게 자신을 인증하는 데 사용할 실제 자격 증명을 제공해야 합니다.  
  
## <a name="obtaining-metadata"></a>메타데이터 가져오기  

 클라이언트를 만들 때 첫 번째 단계는 클라이언트가 통신할 서비스에 대한 메타데이터를 가져오는 것입니다. 이 작업은 다음 두 가지 방법으로 수행할 수 있습니다. 첫째, 서비스에서 MEX (metadata exchange) 끝점을 게시 하거나 HTTP 또는 HTTPS를 통해 메타 데이터를 사용할 수 있도록 설정 하는 경우 클라이언트에 대 한 코드 파일과 구성 파일을 모두 생성 하는 [ServiceModel Metadata 유틸리티 도구 (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)를 사용 하 여 메타 데이터를 다운로드할 수 있습니다. 도구를 사용 하는 방법에 대 한 자세한 내용은 [WCF 클라이언트를 사용 하 여 서비스 액세스](accessing-services-using-a-wcf-client.md)를 참조 하세요. 서비스가 MEX 끝점을 게시 하지 않고 HTTP 또는 HTTPS를 통해 메타 데이터를 사용할 수 있도록 하지 않는 경우 서비스 작성자에 게 보안 요구 사항 및 메타 데이터를 설명 하는 설명서를 문의 해야 합니다.  
  
> [!IMPORTANT]
> 메타데이터는 신뢰할 수 있는 소스에서 가져오고 변경하지 않는 것이 좋습니다. HTTP 프로토콜을 사용하여 검색한 메타데이터는 일반 텍스트로 전송되며 변경할 수 있습니다. 서비스가 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> 및 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> 속성을 사용하는 경우 서비스 작성자가 제공하는 URL을 통해 HTTPS 프로토콜을 사용하여 데이터를 다운로드합니다.  
  
## <a name="validating-security"></a>보안 유효성 검사  

 메타데이터 소스는 크게 신뢰할 수 있는 소스와 신뢰할 수 없는 소스의 두 가지 범주로 나눌 수 있습니다. 소스를 신뢰하고 소스의 보안 MEX 엔드포인트에서 클라이언트 코드 및 다른 메타데이터를 다운로드한 경우, 해당 클라이언트를 빌드하여 올바른 자격 증명을 제공하고 다른 문제 없이 실행할 수 있습니다.  
  
 그러나 잘 모르는 소스에서 클라이언트 및 메타데이터를 다운로드하려는 경우 코드가 사용하는 보안 방법의 유효성을 확인해야 합니다. 예를 들어, 서비스가 최소한의 수준에서 기밀성 및 무결성을 요구하지 않는 한 단순히 개인 정보 또는 재무 정보를 서비스에 보내는 클라이언트를 만들지 않아야 합니다. 이러한 정보는 표시 되기 때문에 이러한 정보를 공개 하려는 범위에 서비스 소유자를 신뢰 해야 합니다.  
  
 따라서 일반적으로 신뢰할 수 없는 소스에서 코드 및 메타데이터를 사용하는 경우 필요한 보안 수준을 충족하는지 코드 및 메타데이터를 확인합니다.  
  
## <a name="setting-a-client-credential"></a>클라이언트 자격 증명 설정  

 클라이언트에 대한 클라이언트 자격 증명 설정은 다음 두 단계로 구성됩니다.  
  
1. 서비스에 필요한 *클라이언트 자격 증명 형식을* 결정 합니다. 이 방법은 두 개의 메서드 중 하나에 의해 수행됩니다. 첫째로, 서비스 작성자의 설명서가 있는 경우 서비스에서 필요한 클라이언트 자격 증명 형식(있는 경우)을 지정해야 합니다. 둘째로, Svcutil.exe 도구로 생성된 구성 파일만 있는 경우 개별 바인딩을 검사하여 필요한 자격 증명 형식을 결정할 수 있습니다.  
  
2. 실제 클라이언트 자격 증명을 지정합니다. 실제 클라이언트 자격 증명을 형식과 구분 하기 위해 *클라이언트 자격 증명 값* 이라고 합니다. 예를 들어, 클라이언트 자격 증명 형식이 인증서를 지정할 경우 서비스가 신뢰하는 인증 기관에서 발급한 X.509 인증서를 제공해야 합니다.  
  
### <a name="determining-the-client-credential-type"></a>클라이언트 자격 증명 형식 결정  

 Svcutil.exe 도구가 생성 한 구성 파일이 있는 경우 섹션을 검토 하 여 [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) 필요한 클라이언트 자격 증명 형식을 확인 합니다. 이 단원에는 보안 요구 사항을 지정하는 바인딩 요소가 나와 있습니다. 특히 \<security> 각 바인딩의 요소를 검사 합니다. 해당 요소에는 `mode` 특성이 포함되어 있으며, 이 특성은 세 가지 가능한 값 즉, `Message`, `Transport` 또는 `TransportWithMessageCredential` 중 하나로 설정할 수 있습니다. 특성 값은 모드를 결정하고 모드는 자식 요소 중 중요한 요소를 결정합니다.  
  
 `<security>` 요소는 `<transport>` 또는 `<message>` 요소 중 하나, 또는 둘 다를 포함할 수 있습니다. 중요한 요소는 보안 모드와 일치하는 요소입니다. 예를 들어 다음 코드는 보안 모드를 `"Message"`, `<message>` 요소의 클라이언트 자격 증명 형식은 `"Certificate"` 지정합니다. 이런 경우 `<transport>` 요소는 무시될 수 있습니다. 그러나 `<message>` 요소는 X.509 인증서를 제공해야 하는 것으로 지정합니다.  

```xml  
<wsHttpBinding>  
    <binding name="WSHttpBinding_ICalculator">  
       <security mode="Message">  
           <transport clientCredentialType="Windows"
                      realm="" />  
           <message clientCredentialType="Certificate"
                    negotiateServiceCredential="true"  
                    algorithmSuite="Default"
                    establishSecurityContext="true" />  
       </security>  
    </binding>  
</wsHttpBinding>  
```  

 다음 예제와 같이 `clientCredentialType` 특성이 `"Windows"`로 설정된 경우 실제 자격 증명 값을 제공할 필요가 없습니다. Windows 통합 보안이 클라이언트를 실행하는 사용자의 실제 자격 증명(Kerberos 토큰)을 제공하기 때문입니다.  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows "
        realm="" />  
</security>  
```  
  
### <a name="setting-the-client-credential-value"></a>클라이언트 자격 증명 값 설정  

 클라이언트가 자격 증명을 제공해야 하는 경우 적절한 메서드를 사용하여 클라이언트를 구성합니다. 예를 들어, 클라이언트 인증서를 설정하려면 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 메서드를 사용합니다.  
  
 자격 증명의 일반 양식은 X.509 인증서입니다. 다음 두 가지 방법으로 자격 증명을 제공할 수 있습니다.  
  
- 클라이언트 코드에서 자격 증명 프로그래밍(`SetCertificate` 메서드 사용).  
  
 [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)클라이언트에 대 한 구성 파일의 섹션을 추가 하 고 요소를 사용 `clientCredentials` 합니다 (아래 참조).  
  
#### <a name="setting-a-clientcredentials-value-in-code"></a>\<clientCredentials>코드에서 값 설정  

 [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md)코드에 값을 설정 하려면 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 클래스의 속성에 액세스 해야 합니다 <xref:System.ServiceModel.ClientBase%601> . 다음 표에 설명한 것처럼 속성은 다양한 자격 증명 형식에 액세스할 수 있는 <xref:System.ServiceModel.Description.ClientCredentials> 개체를 반환합니다.  
  
|ClientCredential 속성|설명|참고|  
|-------------------------------|-----------------|-----------|  
|<xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>을 반환합니다.|서비스에게 자신을 인증하기 위해 클라이언트가 제공하는 X.509 인증서를 나타냅니다.|  
|<xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>|<xref:System.ServiceModel.Security.HttpDigestClientCredential>을 반환합니다.|HTTP digest 자격 증명을 나타냅니다. 자격 증명은 사용자 이름 및 암호에 대한 해시입니다.|  
|<xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>|<xref:System.ServiceModel.Security.IssuedTokenClientCredential>을 반환합니다.|보안 토큰 서비스에서 발급한 사용자 지정 보안 토큰을 나타내며 일반적으로 페더레이션 시나리오에서 사용됩니다.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>|<xref:System.ServiceModel.Security.PeerCredential>을 반환합니다.|Windows 도메인의 피어 메시 참가를 위해 사용할 피어 자격 증명을 나타냅니다.|  
|<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>|<xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>을 반환합니다.|out-of-band 협상에서 서비스가 제공하는 X.509 인증서를 나타냅니다.|  
|<xref:System.ServiceModel.Description.ClientCredentials.UserName%2A>|<xref:System.ServiceModel.Security.UserNamePasswordClientCredential>을 반환합니다.|사용자 이름 및 암호 쌍을 나타냅니다.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>|<xref:System.ServiceModel.Security.WindowsClientCredential>을 반환합니다.|Windows 클라이언트 자격 증명(Kerberos 자격 증명)을 나타냅니다. 클래스의 속성은 읽기 전용입니다.|  
  
#### <a name="setting-a-clientcredentials-value-in-configuration"></a>\<clientCredentials>구성의 값 설정  

 자격 증명 값은 요소의 자식 요소로 끝점 동작을 사용 하 여 지정 [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) 합니다. 사용되는 요소는 클라이언트 자격 증명 형식에 따라 다릅니다. 예를 들어 다음 예제에서는 <를 사용 하 여 x.509 인증서를 설정 하는 구성을 보여 줍니다 [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md) .  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>
        <behavior name="myEndpointBehavior">  
          <clientCredentials>  
            <clientCertificate findvalue="myMachineName"
            storeLocation="Current" X509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>
      </endpointBehaviors>
    </behaviors>
  </system.serviceModel>  
</configuration>  
```  
  
 구성에서 클라이언트 자격 증명을 설정 하려면 [\<endpointBehaviors>](../configure-apps/file-schema/wcf/endpointbehaviors.md) 구성 파일에 요소를 추가 합니다. 또한 다음 예제와 같이 추가 된 동작 요소는 `behaviorConfiguration` 요소의 특성 [ \<endpoint> \<client> ](../configure-apps/file-schema/wcf/endpoint-of-client.md) 을 사용 하 여 서비스의 끝점에 연결 되어야 합니다. `behaviorConfiguration` 특성 값은 동작 `name` 특성 값과 일치해야 합니다.  

```xml
<configuration>
  <system.serviceModel>
    <client>
      <endpoint address="http://localhost/servicemodelsamples/service.svc"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                behaviorConfiguration="myEndpointBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </client>
  </system.serviceModel>
</configuration>
```
  
> [!NOTE]
> 예를 들어 사용자 이름 및 암호 또는 Windows 사용자 및 암호 값과 같은 일부 클라이언트 자격 증명 값은 애플리케이션 구성 파일을 사용하여 설정할 수 없습니다. 이러한 자격 증명 값은 코드에서만 지정할 수 있습니다.  
  
 클라이언트 자격 증명을 설정 하는 방법에 대 한 자세한 내용은 [방법: 클라이언트 자격 증명 값 지정을](how-to-specify-client-credential-values.md)참조 하세요.  
  
> [!NOTE]
> 다음 예제 구성과 같이 `ClientCredentialType`가 `SecurityMode`로 설정된 경우 `"TransportWithMessageCredential",`은 무시됩니다.  
  
```xml  
<wsHttpBinding>  
    <binding name="PingBinding">  
        <security mode="TransportWithMessageCredential"  >  
           <message  clientCredentialType="UserName"
               establishSecurityContext="false"
               negotiateServiceCredential="false" />  
           <transport clientCredentialType="Certificate"  />  
         </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="see-also"></a>참고 항목

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [\<bindings>](../configure-apps/file-schema/wcf/bindings.md)
- [Configuration Editor 도구(SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)
- [서비스에 보안 설정](securing-services.md)
- [WCF 클라이언트를 사용하여 서비스 액세스](accessing-services-using-a-wcf-client.md)
- [방법: 클라이언트 자격 증명 값 지정](how-to-specify-client-credential-values.md)
- [ServiceModel Metadata 유틸리티 도구(Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [방법: 클라이언트 자격 증명 형식 지정](how-to-specify-the-client-credential-type.md)
