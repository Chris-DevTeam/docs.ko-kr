---
description: '자세한 정보: 일반적인 보안 시나리오'
title: 일반적인 보안 시나리오
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
ms.openlocfilehash: ad4e3964a4a018793653b5eb48b91ca566840abb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743514"
---
# <a name="common-security-scenarios"></a>일반적인 보안 시나리오

이 단원의 항목에서는 많은 수의 가능한 클라이언트 및 서비스 보안 구성을 카탈로그로 만듭니다. 구성은 요소 수에 따라 다릅니다. 예를 들어 서비스 또는 클라이언트가 인트라넷에 있는지, 보안이 Windows에서 제공되는지 아니면 HTTPS와 같은 전송에 의해 제공되는지에 따라 달라집니다.  
  
## <a name="in-this-section"></a>섹션 내용  

 [보안이 설정되지 않은 인터넷 클라이언트 및 서비스](internet-unsecured-client-and-service.md)  
 보안되지 않은 공용 클라이언트 및 서비스의 예입니다.  
  
 [보안이 설정되지 않은 인트라넷 클라이언트 및 서비스](intranet-unsecured-client-and-service.md)  
 WCF 응용 프로그램에 보안 개인 네트워크에 대 한 정보를 제공 하기 위해 개발 된 WCF (기본 Windows Communication Foundation) 서비스입니다.  
  
 [기본 인증을 사용하는 전송 보안](transport-security-with-basic-authentication.md)  
 클라이언트는 해당 애플리케이션을 통해 사용자 지정 인증을 사용하여 로그온할 수 있습니다.  
  
 [Windows 인증을 사용하는 전송 보안](transport-security-with-windows-authentication.md)  
 Windows 보안을 사용하여 보안하는 클라이언트 및 서비스를 보여 줍니다.  
  
 [익명 클라이언트를 사용하는 전송 보안](transport-security-with-an-anonymous-client.md)  
 이 시나리오에서는 기밀성 및 무결성 확보를 위해 전송 보안(예: HTTPS)을 사용합니다.  
  
 [인증서 인증을 사용하는 전송 보안](transport-security-with-certificate-authentication.md)  
 인증서를 사용하여 보안하는 클라이언트 및 서비스를 보여 줍니다.  
  
 [익명 클라이언트를 사용하는 메시지 보안](message-security-with-an-anonymous-client.md)  
 WCF 메시지 보안을 통해 보호 되는 클라이언트 및 서비스를 보여 줍니다.  
  
 [사용자 이름 클라이언트를 사용하는 메시지 보안](message-security-with-a-user-name-client.md)  
 클라이언트는 도메인 사용자 이름 및 암호를 사용하여 클라이언트가 로그온할 수 있도록 허용하는 Windows Forms 애플리케이션입니다.  
  
 [인증서 클라이언트를 사용하는 메시지 보안](message-security-with-a-certificate-client.md)  
 서버에는 여러 인증서가 있으며, 각 클라이언트에는 하나의 인증서가 있습니다. 보안 컨텍스트는 TLS(전송 계층 보안) 협상을 통해 설정됩니다.  
  
 [Windows 클라이언트를 사용하는 메시지 보안](message-security-with-a-windows-client.md)  
 인증서 클라이언트의 변형입니다. 서버에는 여러 인증서가 있으며, 각 클라이언트에는 하나의 인증서가 있습니다. 보안 컨텍스트는 TLS 협상을 통해 설정됩니다.  
  
 [자격 증명 협상 없이 Windows 클라이언트를 사용하는 메시지 보안](message-security-with-a-windows-client-without-credential-negotiation.md)  
 Kerberos 도메인을 사용하여 보안하는 클라이언트 및 서비스를 보여 줍니다.  
  
 [상호 인증서를 사용하는 메시지 보안](message-security-with-mutual-certificates.md)  
 서버에는 여러 인증서가 있으며, 각 클라이언트에는 하나의 인증서가 있습니다. 서버 인증서는 애플리케이션과 함께 분산되며 대역 외에서 사용할 수 있습니다.  
  
 [발급된 토큰을 사용하는 메시지 보안](message-security-with-issued-tokens.md)  
 독립 도메인 간에 신뢰를 설정할 수 있도록 해주는 페더레이션 보안입니다.  
  
 [신뢰할 수 있는 하위 시스템](trusted-subsystem.md)  
 클라이언트는 네트워크에 분산되어 있는 하나 이상의 웹 서비스에 액세스합니다. 웹 서비스는 데이터베이스 또는 기타 웹 서비스와 같은 보안이 필요한 추가 리소스에 액세스합니다.  
  
## <a name="reference"></a>참고  

 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>관련 단원  

 [권한 부여](authorization-in-wcf.md)  
  
 [보안 개요](security-overview.md)  
  
 [보안](security.md)  
  
 [바인딩 및 보안](bindings-and-security.md)  
  
 [서비스 및 클라이언트에 보안 설정](securing-services-and-clients.md)  
  
 [인증](authentication-in-wcf.md)  
  
 [권한 부여](authorization-in-wcf.md)  
  
 [페더레이션 및 발급된 토큰](federation-and-issued-tokens.md)  
  
 [감사](auditing-security-events.md)  
  
## <a name="see-also"></a>참고 항목

- [보안 지침 및 최선의 방법](security-guidance-and-best-practices.md)
- [Windows Server AppFabric 보안 모델](/previous-versions/appfabric/ee677202(v=azure.10))
