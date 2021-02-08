---
description: 자세한 내용은 RegisterParticipantFailure를 확인 하세요.
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: e930ee66720a9f397999d729e8d680fce9a37e29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99770627"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a>Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure

WS-AT 프로토콜 서비스가 제어 프로토콜에 대한 참가자를 등록하지 못했습니다.  
  
## <a name="description"></a>설명  

 MSDTC가 잘못된 등록 요청을 감지하는 경우 추적됩니다. 이는 여러 완료 등록 요청 및 내부 오류에 의해 발생할 수 있습니다.  
  
## <a name="troubleshooting"></a>문제 해결  

 완료를 두 번 이상 등록하지 마십시오.  또한 추적 메시지 내의 상태 문자열을 검사하여 실행 가능한 항목이 있는지 확인하십시오.  
  
## <a name="see-also"></a>참고 항목

- [추적](index.md)
- [추적을 사용하여 애플리케이션 문제 해결](using-tracing-to-troubleshoot-your-application.md)
- [관리 및 진단](../index.md)
