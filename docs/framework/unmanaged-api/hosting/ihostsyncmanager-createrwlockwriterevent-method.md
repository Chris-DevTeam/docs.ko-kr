---
description: '자세히 알아보기: IHostSyncManager:: CreateRWLockWriterEvent 메서드'
title: IHostSyncManager::CreateRWLockWriterEvent 메서드
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockWriterEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockWriterEvent
helpviewer_keywords:
- CreateRWLockWriterEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockWriterEvent method [.NET Framework hosting]
ms.assetid: 70e488c2-cf53-4dc0-ba52-74372d215c41
topic_type:
- apiref
ms.openlocfilehash: 509f18ff49966e5da3a25e39258d33caf69249a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784758"
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a>IHostSyncManager::CreateRWLockWriterEvent 메서드

작성기 잠금 구현에 대 한 자동 다시 설정 이벤트 개체를 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `cookie`  
 진행 자동 다시 설정 이벤트와 연결할 쿠키입니다.  
  
 `ppEvent`  
 제한이 [IHostAutoEvent](ihostautoevent-interface.md) 인스턴스의 주소에 대 한 포인터 이거나, 이벤트 개체를 만들 수 없는 경우 null입니다.  
  
## <a name="return-value"></a>Return Value  
  
|HRESULT|설명|  
|-------------|-----------------|  
|S_OK|`CreateRWLockWriterEvent` 성공적으로 반환 되었습니다.|  
|HOST_E_CLRNOTAVAILABLE|CLR (공용 언어 런타임)이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.|  
|HOST_E_TIMEOUT|호출 시간이 초과 되었습니다.|  
|HOST_E_NOT_OWNER|호출자가 잠금을 소유 하지 않습니다.|  
|HOST_E_ABANDONED|차단 된 스레드나 파이버에서 대기 하는 동안 이벤트를 취소 했습니다.|  
|E_FAIL|알 수 없는 치명적인 오류가 발생 했습니다. 메서드가 E_FAIL 반환 하는 경우 해당 프로세스 내에서 더 이상 CLR을 사용할 수 없습니다. 호스팅 메서드를 이후에 호출 하면 HOST_E_CLRNOTAVAILABLE 반환 됩니다.|  
|E_OUTOFMEMORY|메모리가 부족 하 여 요청한 이벤트 개체를 만들 수 없습니다.|  
  
## <a name="remarks"></a>설명  

 CLR은 메서드를 호출 `CreateRWLockWriterEvent` 하 여 `IHostAutoEvent` 작성기 잠금을 구현 하는 데 사용할 인스턴스에 대 한 참조를 가져옵니다. 호스트는 지정 된 쿠키를 사용 하 여 [ICLRSyncManager](iclrsyncmanager-interface.md) 인터페이스의 반복 메서드를 호출 하 여 잠금을 기다리는 작업을 확인할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Mscoree.dll  
  
 **라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [ICLRSyncManager 인터페이스](iclrsyncmanager-interface.md)
- [IHostAutoEvent 인터페이스](ihostautoevent-interface.md)
- [IHostManualEvent 인터페이스](ihostmanualevent-interface.md)
- [IHostSyncManager 인터페이스](ihostsyncmanager-interface.md)
