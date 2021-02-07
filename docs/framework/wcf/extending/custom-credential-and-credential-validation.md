---
description: '자세한 정보: 사용자 지정 자격 증명 및 자격 증명 유효성 검사'
title: 사용자 지정 자격 증명 및 자격 증명 유효성 검사
ms.date: 03/30/2017
helpviewer_keywords:
- credentials [WCF], custom
- credentials [WCF]
- custom credentials [WCF]
- credential validation [WCF]
- credentials [WCF], validation
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
ms.openlocfilehash: f1ceb8cf46cca01ac31faeb9485cbeb6c8663d31
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735311"
---
# <a name="custom-credential-and-credential-validation"></a>사용자 지정 자격 증명 및 자격 증명 유효성 검사

WCF (Windows Communication Foundation)의 보안은 서비스와 클라이언트 간의 자격 증명 교환을 기반으로 합니다. Windows(Kerberos), 사용자 이름 및 암호, 인증서 등의 일반 자격 증명 형식을 사용하여 대부분의 보안 시나리오를 만족시킬 수 있습니다. 그러나 새 자격 증명 형식이 필요한 경우 이 단원의 항목에서 새 형식을 처리하고 유효성을 검사하는 방법에 대해 설명합니다.  
  
## <a name="in-this-section"></a>섹션 내용  

 [방법: 사용자 지정 인증서 유효성 검사기를 사용하는 서비스 만들기](how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 클래스에서 상속 하 여 WCF 유효성 검사를 사용자 지정 하는 방법을 설명 합니다 <xref:System.IdentityModel.Selectors.X509CertificateValidator> .  
  
 [연습: 사용자 지정 클라이언트 및 서비스 자격 증명 만들기](walkthrough-creating-custom-client-and-service-credentials.md)  
 <xref:System.ServiceModel.Description.ClientCredentials> <xref:System.ServiceModel.Description.ServiceCredentials> 새 자격 증명 형식을 수용 하기 위해 및 클래스를 확장 하는 방법을 보여 줍니다. 이 항목은 사용자 지정 자격 증명 형식을 만들 수 있도록 하는 일련의 항목 중 첫 번째입니다.  
  
 [방법: 사용자 지정 보안 토큰 공급 기업 만들기](how-to-create-a-custom-security-token-provider.md)  
 보안 토큰 공급자를 만들어 새 자격 증명 형식을 처리하고 자격 증명에 대한 새 토큰을 반환하는 방법에 대해 설명합니다. 이 항목은 일련의 항목 중 두 번째입니다.  
  
 [방법: 사용자 지정 보안 토큰 인증자 만들기](how-to-create-a-custom-security-token-authenticator.md)  
 사용자 지정 인증자를 만들어 새 자격 증명 형식을 인증하는 방법에 대해 설명합니다. 이 항목은 일련의 항목 중 세 번째입니다.  
  
## <a name="reference"></a>참고  

 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a>관련 단원  

 [인증](../feature-details/authentication-in-wcf.md)  
  
 [페더레이션 및 발급된 토큰](../feature-details/federation-and-issued-tokens.md)  
  
 [권한 부여](../feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a>참조

- [보안](../feature-details/security.md)
