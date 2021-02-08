---
description: '자세한 정보: 방법: 페더레이션 서비스 자격 증명 구성'
title: '방법: 페더레이션 서비스에서 자격 증명 구성'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 149ab165-0ef3-490a-83a9-4322a07bd98a
ms.openlocfilehash: 100012312b9b900f35753e1fa0761ba132fe0c06
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780078"
---
# <a name="how-to-configure-credentials-on-a-federation-service"></a>방법: 페더레이션 서비스에서 자격 증명 구성

WCF (Windows Communication Foundation)에서 페더레이션된 서비스 만들기는 다음과 같은 주요 절차로 구성 됩니다.  
  
1. <xref:System.ServiceModel.WSFederationHttpBinding> 또는 유사한 사용자 지정 바인딩을 구성합니다. 적절 한 바인딩을 만드는 방법에 대 한 자세한 내용은 [방법: WSFederationHttpBinding 만들기](how-to-create-a-wsfederationhttpbinding.md)를 참조 하세요.  
  
2. 서비스에 제공되는 발급된 토큰에 대한 인증 방법을 제어하는 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>을 구성합니다.  
  
 이 항목에서는 두 번째 단계에 대해 자세히 설명합니다. 페더레이션된 서비스의 작동 방식에 대 한 자세한 내용은 [페더레이션](federation.md)을 참조 하세요.  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-code"></a>IssuedTokenServiceCredential의 속성을 코드로 설정하려면  
  
1. <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A> 클래스의 <xref:System.ServiceModel.Description.ServiceCredentials> 속성을 사용하여 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> 인스턴스에 대한 참조를 반환합니다. <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> 클래스의 <xref:System.ServiceModel.ServiceHostBase> 속성에서 이 속성에 액세스합니다.  
  
2. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> `true` CardSpace 카드와 같은 자체 발급 토큰을 인증할 경우 속성을로 설정 합니다. 기본값은 `false`입니다.  
  
3. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> 속성에 의해 반환된 컬렉션을 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 클래스의 인스턴스로 채웁니다. 각 인스턴스는 서비스에서 인증되는 토큰 발급자를 나타냅니다.  
  
    > [!NOTE]
    > <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> 속성에 의해 반환된 클라이언트 측 컬렉션과는 달리, 알려진 인증서 컬렉션은 키 컬렉션이 아닙니다. 발급된 토큰이 포함된 메시지를 보낸 클라이언트 주소와 상관없이, 서비스에서는 지정된 인증서에서 발급한 토큰을 적용합니다.  
  
4. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> 속성을 <xref:System.ServiceModel.Security.X509CertificateValidationMode> 열거형 값 중 하나로 설정합니다. 이 작업은 코드로만 수행할 수 있습니다. 기본값은 <xref:System.IdentityModel.Selectors.X509CertificateValidator.ChainTrust%2A>입니다.  
  
5. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> 속성이 <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>으로 설정된 경우 사용자 지정 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 클래스의 인스턴스를 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> 속성에 할당합니다.  
  
6. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A>가 `ChainTrust` 또는 `PeerOrChainTrust`로 설정된 경우에는 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.RevocationMode%2A> 속성을 적절한 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 열거형 값으로 설정합니다. 해지 모드는`PeerTrust` 또는 `Custom` 유효성 검사 모드에서 사용되지 않습니다.  
  
7. 필요에 따라 사용자 지정 <xref:System.IdentityModel.Tokens.SamlSerializer> 클래스의 인스턴스를 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.SamlSerializer%2A> 속성에 할당합니다. 예를 들어 사용자 지정 SAML(Security Assertions Markup Language) 어설션을 구문 분석하기 위해 사용자 지정 SAML serializer가 필요합니다.  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-configuration"></a>IssuedTokenServiceCredential의 속성을 구성에서 설정하려면  
  
1. 요소를 `<issuedTokenAuthentication>` <> 요소의 자식으로 만듭니다 `serviceCredentials` .  
  
2. `allowUntrustedRsaIssuers` `<issuedTokenAuthentication>` `true` CardSpace 카드와 같은 자체 발급 토큰을 인증 하는 경우 요소의 특성을로 설정 합니다.  
  
3. `<knownCertificates>` 요소를 `<issuedTokenAuthentication>` 요소의 자식으로 만듭니다.  
  
4. `<add>` 요소를 `<knownCertificates>` 요소의 자식으로 0개 이상 만들고 `storeLocation`, `storeName`, `x509FindType` 및 `findValue` 특성을 사용하여 인증서를 찾는 방법을 지정합니다.  
  
5. 필요한 경우 `samlSerializer` <`issuedTokenAuthentication`> 요소의 특성을 사용자 지정 클래스의 형식 이름으로 설정 합니다 <xref:System.IdentityModel.Tokens.SamlSerializer> .  
  
## <a name="example"></a>예제  

 다음 예제에서는 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>의속성을 코드로 설정합니다.  
  
 [!code-csharp[C_FederatedService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedservice/cs/source.cs#2)]
 [!code-vb[C_FederatedService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedservice/vb/source.vb#2)]  
  
 페더레이션 서비스에서 클라이언트를 인증하려면 발급된 토큰이 다음 조건을 만족해야 합니다.  
  
- 발급된 토큰의 디지털 서명에 RSA 보안 키 식별자를 사용하는 경우, <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> 속성은 `true`여야 합니다.  
  
- 발급된 토큰의 서명에 X.509 발급자 일련 번호, X.509 주체 키 식별자 또는 X.509 지문 보안 식별자를 사용하는 경우, 발급된 토큰은 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> 클래스의 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> 속성에 의해 반환된 컬렉션의 인증서를 통해 서명해야 합니다.  
  
- 발급된 토큰을 X.509 인증서를 통해 서명하는 경우에는 해당 인증서가 신뢰하는 상대에게 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A>로 보내졌는지 또는 <xref:System.IdentityModel.Tokens.X509RawDataKeyIdentifierClause> 속성에서 가져온 것인지에 상관없이, 인증서에서는 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> 속성 값으로 지정된 의미 체계별로 유효성을 검사해야 합니다. X.509 인증서 유효성 검사에 대 한 자세한 내용은 [인증서 작업](working-with-certificates.md)을 참조 하세요.  
  
 예를 들어 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A>를 <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerTrust>로 설정하면 서명 인증서가 `TrustedPeople` 인증서 저장소에 있는 발급된 모든 토큰을 인증하게 됩니다. 이 경우 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.TrustedStoreLocation%2A> 속성을 <xref:System.Security.Cryptography.X509Certificates.StoreLocation.CurrentUser> 또는 <xref:System.Security.Cryptography.X509Certificates.StoreLocation.LocalMachine>으로 설정합니다. <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> 등의 다른 모드를 선택할 수도 있습니다. `Custom`을 선택하면 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 클래스의 인스턴스를 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CustomCertificateValidator%2A> 속성에 할당해야 합니다. 사용자 지정 유효성 검사기에서 원하는 조건을 사용하여 인증서의 유효성을 검사할 수 있습니다. 자세한 내용은 [방법: 사용자 지정 인증서 유효성 검사기를 사용 하는 서비스 만들기](../extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)합니다.  
  
## <a name="see-also"></a>참고 항목

- [페더레이션](federation.md)
- [페더레이션 및 트러스트](federation-and-trust.md)
- [Federation 샘플](../samples/federation-sample.md)
- [방법: WSFederationHttpBinding에서 보안 세션을 사용하지 않도록 설정](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [방법: WSFederationHttpBinding 만들기](how-to-create-a-wsfederationhttpbinding.md)
- [방법: 페더레이션 클라이언트 만들기](how-to-create-a-federated-client.md)
- [인증서 사용](working-with-certificates.md)
- [SecurityBindingElement 인증 모드](securitybindingelement-authentication-modes.md)
