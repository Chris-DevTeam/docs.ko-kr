---
description: '자세한 정보: 재생 공격'
title: 재생 공격
ms.date: 03/30/2017
ms.assetid: 7a17e040-93cd-4432-81b9-9f62fec78c8f
ms.openlocfilehash: b367bd6238f85471871c59b393a8f28a40c4ddba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632856"
---
# <a name="replay-attacks"></a>재생 공격

공격자가 두 당사자 간에 메시지 스트림을 복사 하 고 하나 이상의 당사자에 게 스트림을 재생 하는 경우 *재생 공격이* 발생 합니다. 완화되지 않은 경우 공격을 받기 쉬운 컴퓨터는 스트림을 올바른 메시지로 처리하여 항목에 대한 중복 주문과 같은 잘못된 결과의 범위에 있게 됩니다.  
  
## <a name="bindings-may-be-subject-to-reflection-attacks"></a>바인딩이 반사 공격을 받기 쉬운 경우  

 *리플렉션 공격은* 메시지를 받는 사람에 게 회신으로 보낸 것 처럼 메시지를 다시 보낸 사람에 게 다시 재생 하는 것입니다. WCF (Windows Communication Foundation) 메커니즘에서 표준 *재생 검색* 은이를 자동으로 처리 하지 않습니다.  
  
 WCF 서비스 모델은 메시지를 요청 하 고 응답 메시지에 서명 된 헤더를 필요로 하는 서명 된 메시지 ID를 추가 하기 때문에 기본적으로 리플렉션 공격이 완화 됩니다 `relates-to` . 따라서 요청 메시지를 응답으로 재생할 수 없습니다. 보안 RM(신뢰할 수 있는 메시지) 시나리오에서 반사 공격은 다음과 같은 이유로 완화됩니다.  
  
- 시퀀스 만들기 및 시퀀스 만들기 응답 메시지 스키마는 다릅니다.  
  
- 단면 시퀀스의 경우 클라이언트가 보내는 시퀀스 메시지는 클라이언트가 그러한 메시지를 인식할 수 없으므로 재생될 수 없습니다.  
  
- 이중 시퀀스의 경우 두 시퀀스 ID는 고유해야 합니다. 따라서 나가는 시퀀스 메시지를 들어오는 시퀀스 메시지로 재생할 수 없습니다(모든 시퀀스 헤더 및 본문도 서명됨).  
  
 반사 공격을 받기 쉬운 바인딩은 WS-Addressing이 없는 바인딩 즉, WS-Addressing이 사용되지 않는 바인딩을 사용자 지정하고 대칭 키 기반 보안을 사용하는 바인딩입니다. <xref:System.ServiceModel.BasicHttpBinding>은 기본적으로 WS-Addressing을 사용하지 않지만, 이 공격에 노출될 수 있는 방식으로는 대칭 키 기반 보안을 사용하지 않습니다.  
  
 사용자 지정 바인딩을 완화하는 것은 보안 컨텍스트를 설정하지 않거나 WS-Addressing 헤더를 요청하는 것입니다.  
  
## <a name="web-farm-attacker-replays-request-to-multiple-nodes"></a>웹 팜: 공격자가 여러 노드에 요청 재생  

 클라이언트는 웹 팜에 구현된 서비스를 사용합니다. 공격자는 팜의 한 노드로 보내진 요청을 팜의 다른 노드에 재생합니다. 또한, 서비스를 다시 시작하는 경우 재생 캐시가 플러시되어 공격자가 요청을 재생할 수 있습니다. 캐시에 이전에 사용된 메시지 서명 값이 있고 캐시가 재생되지 않으므로 그러한 서명은 한 번만 사용할 수 있습니다. 재생 캐시는 웹 팜에서 공유되지 않습니다.  
  
 완화 방안은 다음과 같습니다.  
  
- 상태 저장 보안 컨텍스트 토큰(보안 대화 사용 또는 사용 안 함)과 함께 메시지 모드 보안을 사용합니다. 자세한 내용은 [방법: 보안 세션에 대 한 보안 컨텍스트 토큰 만들기](how-to-create-a-security-context-token-for-a-secure-session.md)를 참조 하세요.  
  
- 전송 수준 보안을 사용하도록 서비스를 구성합니다.  
  
## <a name="see-also"></a>참고 항목

- [Security Considerations](security-considerations-in-wcf.md)
- [정보 공개](information-disclosure.md)
- [권한 상승](elevation-of-privilege.md)
- [서비스 거부](denial-of-service.md)
- [변조](tampering.md)
- [지원 되지 않는 시나리오](unsupported-scenarios.md)
