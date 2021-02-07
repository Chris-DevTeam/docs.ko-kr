---
description: '자세한 정보: Windows Vista, Windows Server 2003 및 Windows XP의 큐 기능 차이점'
title: Windows Vista, Windows Server 2003 및 Windows XP의 큐 기능 차이점
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], differences in operating systems
ms.assetid: aa809d93-d0a3-4ae6-a726-d015cca37c04
ms.openlocfilehash: 6a6206b3033454528797f3c8f4276add9c35023d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756385"
---
# <a name="differences-in-queuing-features-in-windows-vista-windows-server-2003-and-windows-xp"></a>Windows Vista, Windows Server 2003 및 Windows XP의 큐 기능 차이점

이 항목에서는 Windows Vista, Windows Server 2003 및 Windows XP 간에 WCF (Windows Communication Foundation) 큐 기능의 차이점에 대해 요약 합니다.  
  
## <a name="application-specific-dead-letter-queue"></a>애플리케이션별 배달 못한 편지 큐  

 대기 중인 메시지는 수신 애플리케이션이 적절한 시간 내에 메시지를 읽지 못하는 경우 무기한 큐에 남을 수 있습니다. 시간이 중요한 메시지인 경우에는 이 동작이 별로 좋지 않습니다. 시간이 중요한 메시지는 대기 중인 바인딩에서 `TimeToLive` 속성이 설정되어 있습니다. 이 속성은 메시지가 만료될 때까지 큐에 머물 수 있는 기간을 나타냅니다. 만료된 메시지는 배달 못한 편지 큐라는 특수 큐로 보내집니다. 또한 큐 할당량 초과 또는 인증 오류 등 다른 이유로 메시지가 배달 못한 편지 큐에 놓일 수도 있습니다.  
  
 일반적으로 큐 관리자를 공유하는 모든 대기 중인 애플리케이션에 대해 시스템 전체 수준의 배달 못한 편지 큐 하나가 존재합니다. 각 애플리케이션에 대해 배달 못한 편지 큐를 사용하면 이러한 애플리케이션에서 해당 애플리케이션별 배달 못한 편지 큐를 직접 지정하여 큐 관리자를 공유하는 대기 중인 애플리케이션을 서로 격리할 수 있습니다. 다른 애플리케이션과 배달 못한 편지 큐를 공유하는 애플리케이션에서는 큐에서 해당되는 메시지를 찾아야 합니다. 애플리케이션별 배달 못한 편지 큐를 사용하면 애플리케이션에서는 배달 못한 편지 큐에 있는 모든 메시지가 자신에 해당되는 것임을 확신할 수 있습니다.  
  
 Windows Vista는 응용 프로그램별 배달 못 한 편지 큐를 제공 합니다. 응용 프로그램별 배달 못 한 편지 큐는 Windows Server 2003 및 Windows XP에서 사용할 수 없으며 응용 프로그램은 시스템 차원의 배달 못 한 편지 큐를 사용 해야 합니다.  
  
## <a name="poison-message-handling"></a>포이즌 메시지 처리  

 포이즌 메시지는 받는 애플리케이션에 전달하는 최대 배달 시도 횟수를 초과한 메시지입니다. 이 상황은 트랜잭션 큐에서 메시지를 읽는 애플리케이션이 오류 때문에 메시지를 즉시 처리할 수 없는 경우에 발생합니다. 애플리케이션에서 대기 중인 메시지를 받은 트랜잭션이 중단되면 메시지가 큐에 반환됩니다. 그러면 애플리케이션에서 새 트랜잭션으로 메시지를 다시 검색하려고 시도합니다. 오류를 일으킨 문제가 해결되지 않은 경우 받는 애플리케이션은 최대 배달 시도 횟수를 초과할 때까지 같은 메시지를 받고 중단하는 루프에 갇힐 수 있으며, 포이즌 메시지가 발생합니다.  
  
 Windows Vista, Windows Server 2003 및 Windows XP의 MSMQ (메시지 큐)에서 포이즌 처리와 관련 된 주요 차이점은 다음과 같습니다.  
  
- Windows Vista의 MSMQ는 하위 큐를 지원 하지만 Windows Server 2003 및 Windows XP에서는 하위 큐를 지원 하지 않습니다. 하위 큐는 포이즌 메시지 처리에 사용됩니다. 재시도 큐와 포이즌 큐는 포이즌 메시지 처리 설정에 따라 만들어지는 애플리케이션 큐의 하위 큐입니다. `MaxRetryCycles`는 만들 재시도 하위 큐의 수를 지정합니다. 따라서 Windows Server 2003 또는 Windows XP에서 실행 되는 경우는 `MaxRetryCycles` 무시 되 고 `ReceiveErrorHandling.Move` 허용 되지 않습니다.  
  
- Windows Vista의 MSMQ는 부정 승인을 지원 하 고 windows Server 2003 및 Windows XP는 지원 하지 않습니다. 받는 큐 관리자에서 네거티브 승인을 사용하면 거부된 메시지가 보내는 큐 관리자의 배달 못한 편지 큐에 들어갑니다. 따라서 `ReceiveErrorHandling.Reject` Windows Server 2003 및 WINDOWS XP에서는이 허용 되지 않습니다.  
  
- Windows Vista의 MSMQ는 메시지 배달을 시도 하는 횟수를 유지 하는 메시지 속성을 지원 합니다. 이 abort count 속성은 Windows Server 2003 및 Windows XP에서 사용할 수 없습니다. WCF는 메모리에서 중단 횟수를 유지 하므로 웹 팜에 있는 둘 이상의 WCF 서비스에서 같은 메시지를 읽을 경우이 속성에 정확한 값이 포함 되지 않을 수 있습니다.  
  
## <a name="remote-transactional-read"></a>원격 트랜잭션 읽기  

 Windows Vista의 MSMQ는 원격 트랜잭션 읽기를 지원 합니다. 이를 통해 큐에서 읽기를 수행하는 애플리케이션을 큐가 호스팅된 컴퓨터와 다른 컴퓨터에 호스팅할 수 있습니다. 이 기능을 사용하면 중앙의 큐에서 읽기를 수행하는 서비스 팜을 구성하여 시스템의 전체적인 처리량을 높일 수 있습니다. 또한 메시지를 읽거나 처리하는 동안 오류가 발생하면 트랜잭션을 롤백하여 나중에 처리할 수 있도록 메시지를 큐에 남길 수 있습니다.  
  
## <a name="see-also"></a>참고 항목

- [배달 못 한 편지 큐를 사용하여 메시지 전송 오류 처리](using-dead-letter-queues-to-handle-message-transfer-failures.md)
- [포이즌 메시지 처리](poison-message-handling.md)
