---
description: '다음에 대 한 자세한 정보:: <security><wsHttpBinding>'
title: <wsHttpBinding>의 <security>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: 646d49bd67b2b544ae2616f206bfdeabf7806579
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683062"
---
# <a name="security-of-wshttpbinding"></a>\<wsHttpBinding>의 \<security>

의 보안 기능을 나타냅니다 [\<wsHttpBinding>](wshttpbinding.md) .  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a>구문  
  
```xml  
<security mode="Message/None/Transport/TransportWithMessageCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="String"
             defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             defaultRealm="String" />
  <message clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           establishSecurityContext="Boolean"
           negotiateServiceCredential="Boolean" />
</security>
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  

 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|attribute|설명|  
|---------------|-----------------|  
|mode|필드. 적용되는 보안 형식을 지정합니다. 기본값은 `Message`입니다.<br />-이 특성은 형식입니다 <xref:System.ServiceModel.SecurityMode> .|  
  
## <a name="mode-attribute"></a>Mode 특성  
  
|값|설명|  
|-----------|-----------------|  
|없음|보안이 해제되어 있습니다.|  
|전송|HTTPS를 사용하여 보안이 제공됩니다. 서비스는 SSL 인증서로 구성해야 합니다. 메시지는 HTTPS를 사용하여 완전하게 보안 처리되며 서비스의 SSL 인증서를 사용하여 클라이언트에 의해 인증됩니다. 클라이언트 인증은 `ClientCredentials`의 의입니다 [\<transport>](transport-of-wshttpbinding.md) .|  
|메시지|SOAP 메시지 보안을 사용하여 보안이 제공됩니다. 기본적으로 SOAP 본문은 암호화 및 서명됩니다. 이 모드는 서비스 자격 증명을 클라이언트에서 out of band 방식으로 사용할 수 있는지 여부, 사용할 알고리즘 모음, 그리고 Security.Message 속성을 통해 메시지 본문에 적용될 보호 수준과 같은 다양한 기능을 제공합니다. 클라이언트 인증은 세션당 한 번씩 수행되며 세션 기간 동안 인증 결과가 캐시에 저장됩니다.|  
|TransportWithMessageCredential|이 모드에서 HTTPS는 무결성, 기밀성 및 서버 인증을 제공하고 SOAP 메시지 보안은 클라이언트 인증을 제공합니다. 기본적으로 클라이언트 인증은 세션당 한 번씩 수행되며 세션 기간 동안 인증 결과가 캐시에 저장됩니다.|  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<transport>](transport-of-wshttpbinding.md)|전송 보안 설정을 정의합니다. 이 요소는 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 형식에 해당합니다.|  
|[\<message>](message-of-wshttpbinding.md)|메시지에 대한 보안 설정을 정의합니다. 이 요소는 <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> 형식에 해당합니다.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<wsHttpBinding>](wshttpbinding.md)|HTTP 전송 애플리케이션에 대한 보안 바인딩입니다.|  
  
## <a name="remarks"></a>설명  

 WSHttpBinding 클래스는 WS-* 사양을 구현하는 서비스와 상호 운용하도록 디자인되었습니다. 이 바인딩의 전송 보안은 HTTP 또는 SSL(Secure Sockets Layer) over HTTP입니다.  
  
## <a name="see-also"></a>참고 항목

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [서비스 및 클라이언트에 보안 설정](../../../wcf/feature-details/securing-services-and-clients.md)
- [바인딩](../../../wcf/bindings.md)
- [시스템 제공 바인딩 구성](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [바인딩을 사용하여 서비스 및 클라이언트 구성](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
