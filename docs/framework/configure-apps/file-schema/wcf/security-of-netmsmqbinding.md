---
description: '다음에 대 한 자세한 정보:: <security><netMsmqBinding>'
title: <netMsmqBinding>의 <security>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: 1b60d9e390e371555f4c3abf4988e79bb0f04fe8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786852"
---
# <a name="security-of-netmsmqbinding"></a>\<netMsmqBinding>의 \<security>

MSMQ 바인딩에 대한 보안 설정을 정의합니다. 이 클래스는 전송 또는 SOAP 보안의 사용 여부 그리고 보안이 사용된다면 어떤 인증 모드 및 보호 수준을 사용하는지를 지정합니다.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a>구문  
  
```xml  
<security mode="None/Transport/Message/Both">
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
             clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security>
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  

 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|attribute|설명|  
|---------------|-----------------|  
|mode|무결성, 기밀성 및 인증을 제어하는 보안 형식을 지정합니다. 유효한 값은 다음과 같습니다.<br /><br /> -없음: 보안을 사용 하지 않습니다.<br />-전송: 전송에서 보호 및 인증을 제공 합니다. 이는 두 큐 관리자 간의 메시지 보안에 적용됩니다. 애플리케이션과 큐 관리자 간에는 보안이 제공되지 않습니다. 기존 Msmq 애플리케이션이 이러한 보안 모드 형식과 동일한 기능입니다.<br />-Message: 종단 간 응용 프로그램 보안을 지정 합니다. 전송 계층에는 보안이 제공되지 않습니다. 이는 다른 표준 바인딩에서 제공하는 보안과 유사합니다.<br />-Both: 전송 및 SOAP 메시징 계층 모두에서 보안을 제공 합니다. 두 수준 모두에서 동일한 자격 증명이 필요합니다.<br /><br /> 기본값은 Transport입니다. 이 특성은 <xref:System.ServiceModel.NetMsmqSecurityMode> 형식입니다.|  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<message>](message-of-netmsmqbinding.md)|SOAP 메시지 보안 설정을 정의합니다. 이 요소는 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement> 형식입니다.|  
|[\<transport>](transport-of-netmsmqbinding.md)|MSMQ 전송의 보안 설정을 정의합니다. 이 요소는 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement> 형식입니다.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|바인딩|의 바인딩 요소입니다. [\<netMsmqBinding>](netmsmqbinding.md)|  
  
## <a name="see-also"></a>참고 항목

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [서비스 및 클라이언트에 보안 설정](../../../wcf/feature-details/securing-services-and-clients.md)
- [바인딩](../../../wcf/bindings.md)
- [시스템 제공 바인딩 구성](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [바인딩을 사용하여 서비스 및 클라이언트 구성](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [WCF의 큐](../../../wcf/feature-details/queues-in-wcf.md)
