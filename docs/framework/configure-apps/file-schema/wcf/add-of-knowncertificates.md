---
description: '다음에 대 한 자세한 정보:: <add><knownCertificates>'
title: <knownCertificates>의 <add>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 1669495e6119a35543e39230fc5dcc986ee2dec5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750288"
---
# <a name="add-of-knowncertificates"></a>\<knownCertificates>의 \<add>

알려진 인증서 컬렉션에 X.509 인증서를 추가합니다.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownCertificates>**](knowncertificates.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a>구문  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  

 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|attribute|설명|  
|---------------|-----------------|  
|findValue|문자열입니다. 검색할 값입니다.|  
|storeLocation|열거형입니다. 검색할 두 저장소 위치 중 하나입니다.|  
|storeName|열거형입니다. 검색할 시스템 저장소 중 하나입니다.|  
|x509FindType|열거형입니다. 검색할 인증서 필드 중 하나입니다.|  
  
## <a name="findvalue-attribute"></a>findValue 특성  
  
|값|Description|  
|-----------|-----------------|  
|String|이 값은 검색 중인 필드(X509FindType 특성으로 지정)에 따라 다릅니다. 예를 들어, 지문을 검색할 경우 이 값은 16진수 문자열이어야 합니다.|  
  
## <a name="x509findtype-attribute"></a>x509FindType 특성  
  
|값|설명|  
|-----------|-----------------|  
|열거형|값에는 FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier가 있습니다.|  
  
## <a name="storelocation-attribute"></a>storeLocation 특성  
  
|값|설명|  
|-----------|-----------------|  
|열거형|CurrentUser 또는 LocalMachine입니다.|  
  
## <a name="storename-attribute"></a>storeName 특성  
  
|값|설명|  
|-----------|-----------------|  
|열거형|값에는 AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople 및 TrustedPublisher가 포함됩니다.|  
  
### <a name="child-elements"></a>자식 요소  

 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<knownCertificates>](knowncertificates.md)|보안 토큰의 유효성을 검사하기 위해 STS(보안 토큰 서비스)에서 제공하는 X.509 인증서 컬렉션을 나타냅니다.|  
  
## <a name="remarks"></a>설명  

 발급된 토큰 시나리오에는 3단계가 있습니다. 첫 번째 단계에서는 서비스에 액세스 하려는 클라이언트를 *보안 토큰 서비스* 라고 합니다. 보안 토큰 서비스는 클라이언트를 인증한 다음 일반적으로 SAML(Security Assertions Markup Language) 토큰이라는 클라이언트 토큰을 발급합니다. 클라이언트는 토큰을 통해 서비스에 반환됩니다. 서비스는 토큰 및 해당 클라이언트를 인증할 수 있는 데이터의 토큰을 검사합니다. 토큰을 인증하려면 보안 토큰 서비스가 사용하는 인증서를 서비스가 인식해야 합니다.  
  
 [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)요소는 이러한 보안 토큰 서비스 인증서에 대 한 리포지토리입니다. 인증서를 추가 하려면를 사용 [\<knownCertificates>](knowncertificates.md) 합니다. 다음 예제와 같이 각 인증서에 대 한 [ \<add> 요소 \<knownCertificates> 요소](add-of-knowncertificates.md) 를 삽입 합니다.  
  
```xml  
<issuedTokenAuthentication>
  <knownCertificates>
    <add findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="My"
         X509FindType="FindBySubjectName" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
 기본적으로 인증서는 보안 토큰 서비스에서 가져와야 합니다. 이러한 "알려진" 인증서는 올바른 클라이언트만 서비스에 액세스할 수 있도록 합니다.  
  
 페더레이션 서비스에서 클라이언트를 인증 하는 데 필요한 조건을 검토 하 고이 구성 요소를 사용 하는 방법에 대 한 자세한 내용은 [방법: 페더레이션 서비스에서 자격 증명 구성](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)을 참조 하세요. 페더레이션된 시나리오에 대 한 자세한 내용은 [페더레이션 및 발급 된 토큰](../../../wcf/feature-details/federation-and-issued-tokens.md)을 참조 하세요.  
  
## <a name="example"></a>예제  

 다음 예제에서는 모든 STS 인증서에 대해 리포지토리에 인증서를 추가합니다.  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <serviceCredentials>
      <issuedTokenAuthentication>
        <knownCertificates>
          <add findValue="www.contoso.com"
               storeLocation="LocalMachine"
               storeName="CertificateAuthority"
               x509FindType="FindByIssuerName" />
        </knownCertificates>
      </issuedTokenAuthentication>
    </serviceCredentials>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a>참고 항목

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<knownCertificates>](knowncertificates.md)
- [인증서 사용](../../../wcf/feature-details/working-with-certificates.md)
- [페더레이션 및 발급된 토큰](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [방법: 페더레이션 서비스에서 자격 증명 구성](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [서비스 및 클라이언트에 보안 설정](../../../wcf/feature-details/securing-services-and-clients.md)
