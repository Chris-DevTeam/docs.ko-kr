---
description: '다음에 대 한 자세한 정보: <windows> <clientCredentials> 요소'
title: <windows> of <clientCredentials> 요소
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: d693ad914dfa02ef12a7c8520ca84be3a9595e73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682425"
---
# <a name="windows-of-clientcredentials-element"></a>\<windows> of \<clientCredentials> 요소

클라이언트를 나타내는 데 사용되는 Windows 자격 증명의 설정을 지정합니다.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windows>**  
  
## <a name="syntax"></a>구문  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  

 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|attribute|설명|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|클라이언트가 서버에 전달하는 가장 기본 설정을 지정합니다. 클라이언트에서 선택하는 가장 모드는 서버에 적용되지 않습니다. 유효한 값은 다음과 같습니다.<br /><br /> -식별: 서버는 클라이언트의 id와 권한을 가져올 수 있지만 클라이언트를 가장할 수는 없습니다.<br />-가장: 서버는 로컬 시스템에서 클라이언트의 보안 컨텍스트를 가장할 수 있습니다.<br />-위임: 서버는 원격 시스템에서 클라이언트의 보안 컨텍스트를 가장할 수 있습니다.<br />-Anonymous: 서버에서 클라이언트를 가장 하거나 식별할 수 없습니다.<br />-None: 가장 수준이 할당 되지 않습니다.<br /><br /> 기본값은 Identification입니다. 이 특성은 <xref:System.Security.Principal.TokenImpersonationLevel> 형식입니다.|  
|`allowNtlm`|이 속성을 `true`로 설정하면 Kerberos를 사용할 수 없는 경우 NTLM으로 인증을 다운그레이드할 수 있습니다.<br /><br /> 이 속성을 설정 `false` 하면 NTLM이 사용 하는 경우 예외를 throw 하는 최상의 노력을 하도록 Windows Communication Foundation (WCF). 이 속성을 `false`로 설정하면 유선을 통해 NTLM 자격 증명을 보낼 수 있습니다.|  
  
### <a name="child-elements"></a>자식 요소  

 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|클라이언트를 서비스에 인증할 때 사용되는 자격 증명을 지정합니다.|  
  
## <a name="see-also"></a>참고 항목

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [클라이언트에 보안 설정](../../../wcf/securing-clients.md)
- [인증서 사용](../../../wcf/feature-details/working-with-certificates.md)
- [서비스 및 클라이언트에 보안 설정](../../../wcf/feature-details/securing-services-and-clients.md)
