---
description: 자세한 내용은 <System.identitymodel>을 (를) 확인 하세요.
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 037a96c2620e06ef6aed85d1dbaba62aca72e9eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786553"
---
# \<system.identityModel.services>

WS-Federation 프로토콜을 사용 하는 인증에 대 한 구성 섹션입니다.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel.services>**  
  
## <a name="syntax"></a>구문  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  

 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  

 None  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(Wsfam) 및 <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP 모듈을 구성 하는 설정을 포함 합니다.|  
  
### <a name="parent-elements"></a>부모 요소  

 없음  
  
## <a name="remarks"></a>설명  

 `<system.identityModel.services>`응용 프로그램의 구성 파일에 섹션을 추가 하 여 SAM 및 WSFAM에 대 한 설정을 제공 합니다.  
  
> [!IMPORTANT]
> 또는 클래스를 사용 하 여 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> 코드에서 클레임 기반 액세스 제어를 제공 하는 경우 권한 부여를 결정 하는 데 사용 되는 클레임 권한 부여 관리자 ( <xref:System.Security.Claims.ClaimsAuthorizationManager> ) 및 정책이 `<identityConfiguration>` `<federationConfiguration>` 이 섹션의 요소에서 암시적으로 또는 명시적으로 참조 되는 요소를 통해 구성 됩니다. 자세한 내용은 요소 아래의 **설명을** 참조 하십시오 [\<federationConfiguration>](federationconfiguration.md) .  
  
 `<system.identityModel.services>`섹션은 클래스로 표현 됩니다 <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> . `<federationConfiguration>`섹션에서 구성 된 자식 요소의 컬렉션은 클래스로 표현 됩니다 <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> .  
  
## <a name="example"></a>예제  

 다음 XML에서는 `<system.identityModel.services>` 구성 파일에 섹션을 추가 하는 방법을 보여 줍니다. 섹션 및 섹션에 대 한 섹션 선언을 먼저 추가 해야 합니다 `<system.identityModel.services>` `<system.identityModel>` . 섹션을 추가할 때 `<system.identityModel.services>` `<system.identityModel>` 필요한 경우 런타임에서 기본 섹션을 만들 수 있도록 섹션에 대 한 선언을 추가 해야 `<identityConfiguration>` 합니다. 섹션 선언이 추가 된 후 요소 아래에서 페더레이션 인증 설정을 구성할 수 있습니다 `<system.identityModel.services>` .  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  <!-- Additional elements (not shown) -->  
  
  <system.identityModel.services>  
    <federationConfiguration>  
      <wsFederation passiveRedirectEnabled="true"
        issuer="http://localhost:15839/wsFederationSTS/Issue"
        realm="http://localhost:50969/" reply="http://localhost:50969/"
        requireHttps="false"
        signOutReply="http://localhost:50969/SignedOutPage.html"
        signOutQueryString="Param1=value2&Param2=value2"
        persistentCookiesOnPassiveRedirects="true" />  
      <cookieHandler requireSsl="false" />  
    </federationConfiguration>  
  </system.identityModel.services>  
  
</configuration>  
```
