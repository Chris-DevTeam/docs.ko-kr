---
title: IHostManualEvent 인터페이스
ms.date: 03/30/2017
api_name:
- IHostManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent
helpviewer_keywords:
- IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 300c2661-b7d1-4c39-b080-9ebdef0fd523
topic_type:
- apiref
ms.openlocfilehash: 50e37b770e3ee6e0a5cdfca61fc5b09749e5735f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673204"
---
# <a name="ihostmanualevent-interface"></a>IHostManualEvent 인터페이스

수동 다시 설정 이벤트 표현의 호스트 구현을 제공 합니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[Reset 메서드](ihostmanualevent-reset-method.md)|현재 인스턴스를 `IHostManualEvent` 신호를 받지 않는 상태로 다시 설정 합니다.|  
|[Set 메서드](ihostmanualevent-set-method.md)|현재 인스턴스를 `IHostManualEvent` 신호를 받은 상태로 설정 합니다.|  
|[Wait 메서드](ihostmanualevent-wait-method.md)|현재 `IHostManualEvent` 인스턴스가 소유 될 때까지 또는 지정 된 시간이 경과할 때까지 대기 하도록 합니다.|  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Mscoree.dll  
  
 **라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참조

- [ICLRSyncManager 인터페이스](iclrsyncmanager-interface.md)
- [IHostAutoEvent 인터페이스](ihostautoevent-interface.md)
- [IHostSemaphore 인터페이스](ihostsemaphore-interface.md)
- [IHostSyncManager 인터페이스](ihostsyncmanager-interface.md)
- [호스팅 인터페이스](hosting-interfaces.md)
