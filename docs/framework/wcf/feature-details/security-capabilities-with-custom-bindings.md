---
title: 사용자 지정 바인딩을 사용하는 보안 기능
ms.date: 03/30/2017
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
ms.openlocfilehash: 1b12907481ccb3f3c5f4b8aaba6ede8ebfa6228a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288309"
---
# <a name="security-capabilities-with-custom-bindings"></a>사용자 지정 바인딩을 사용하는 보안 기능

시스템에서 제공되는 바인딩 중 하나를 사용하여 일반적으로 사용되는 보안 작업을 수행할 수 있습니다. 하지만 좀더 제어가 필요한 경우에는 이 항목의 설명에 따라 <xref:System.ServiceModel.Channels.SecurityBindingElement>를 사용하여 사용자 지정 바인딩을 만들 수도 있습니다. 사용자 지정 바인딩에 대 한 자세한 내용은 [사용자 지정 바인딩](../extending/custom-bindings.md)을 참조 하세요.  
  
## <a name="in-this-section"></a>섹션 내용  

 [SecurityBindingElement 인증 모드](securitybindingelement-authentication-modes.md)  
 사용자 지정 바인딩에서 가능한 인증 모드에 대해 설명합니다.  
  
 [방법: SecurityBindingElement를 사용하여 사용자 지정 바인딩 만들기](how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 보안 요소로 사용자 지정 바인딩을 만드는 기본 단계에 대해 설명합니다.  
  
 [방법: 지정된 인증 모드에 대한 SecurityBindingElement 만들기](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 지정된 인증 모드의 보안 요소를 만드는 방법에 대해 설명합니다.  
  
 [방법: WSFederationHttpBinding에서 보안 세션을 사용하지 않도록 설정](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 페더레이션 서비스를 만드는 경우 보안 세션을 비활성화하는 방법에 대해 설명합니다.  
  
 [방법: 메시지 재생 검색 사용](how-to-enable-message-replay-detection.md)  
 재생 공격이 발생한 경우를 확인하는 방법에 대해 설명합니다.  
  
 [방법: 지원하는 자격 증명 만들기](how-to-create-a-supporting-credential.md)  
 필요한 경우 서비스에 지원하는 자격 증명을 제공하는 방법에 대해 설명합니다.  
  
 [방법: 서명 확인 설정](how-to-set-up-a-signature-confirmation.md)  
 메시지에 디지털 서명을 할 때 서명을 확인하는 단계에 대해 설명합니다.  
  
 [방법: 최대 클럭 오차 설정](how-to-set-a-max-clock-skew.md)  
 서비스와 클라이언트 사이에서 최대로 허용되는 시간 차이를 설정하는 방법에 대해 설명합니다.  
  
 [방법: 디지털 서명 암호화를 사용하지 않도록 설정](how-to-disable-encryption-of-digital-signatures.md)  
 디지털 서명의 암호화를 비활성화할 경우 얻을 수 있는 성능 상의 이점에 대해 설명합니다.  
  
## <a name="reference"></a>참고  

 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a>관련 단원  

 [보호 수준 이해](../understanding-protection-level.md)  
  
 [서비스 및 클라이언트에 보안 설정](securing-services-and-clients.md)  
  
## <a name="see-also"></a>참고 항목

- [바인딩 및 보안](bindings-and-security.md)
- [보안 개요](security-overview.md)
- [시스템 제공 바인딩](../system-provided-bindings.md)
