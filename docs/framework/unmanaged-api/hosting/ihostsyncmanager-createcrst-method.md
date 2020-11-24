---
title: IHostSyncManager::CreateCrst 메서드
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrst
helpviewer_keywords:
- CreateCrst method [.NET Framework hosting]
- IHostSyncManager::CreateCrst method [.NET Framework hosting]
ms.assetid: ac278cc8-2540-4a6c-b5c6-b90c3970b4f4
topic_type:
- apiref
ms.openlocfilehash: 27861a9258916f4c188d981c44833e5be4c507f2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682883"
---
# <a name="ihostsyncmanagercreatecrst-method"></a>IHostSyncManager::CreateCrst 메서드

동기화에 대 한 임계 영역 개체를 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `ppCrst`  
 제한이 호스트에서 구현 하는 [IHostCrst](ihostcrst-interface.md) 인스턴스의 주소에 대 한 포인터 이거나, 임계 영역을 만들 수 없는 경우 null입니다.  
  
## <a name="return-value"></a>반환 값  
  
|HRESULT|설명|  
|-------------|-----------------|  
|S_OK|`CreateCrst` 성공적으로 반환 되었습니다.|  
|HOST_E_CLRNOTAVAILABLE|CLR (공용 언어 런타임)이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.|  
|HOST_E_TIMEOUT|호출 시간이 초과 되었습니다.|  
|HOST_E_NOT_OWNER|호출자가 잠금을 소유 하지 않습니다.|  
|HOST_E_ABANDONED|차단 된 스레드나 파이버에서 대기 하는 동안 이벤트를 취소 했습니다.|  
|E_FAIL|알 수 없는 치명적인 오류가 발생 했습니다. 메서드가 E_FAIL 반환 하는 경우 해당 프로세스 내에서 더 이상 CLR을 사용할 수 없습니다. 호스팅 메서드를 이후에 호출 하면 HOST_E_CLRNOTAVAILABLE 반환 됩니다.|  
|E_OUTOFMEMORY|요청한 임계 영역을 만드는 데 사용할 수 있는 메모리가 부족 합니다.|  
  
## <a name="remarks"></a>설명  

 임계 영역 개체는 단일 프로세스의 스레드에서만 임계 영역을 사용할 수 있다는 점을 제외 하 고 뮤텍스 개체에서 제공 하는 것과 유사한 동기화를 제공 합니다. `CreateCrst` Win32 함수를 미러링합니다 `InitializeCriticalSection` .  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Mscoree.dll  
  
 **라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참조

- [ICLRSyncManager 인터페이스](iclrsyncmanager-interface.md)
- [IHostCrst 인터페이스](ihostcrst-interface.md)
- [IHostSyncManager 인터페이스](ihostsyncmanager-interface.md)
- [IHostSemaphore 인터페이스](ihostsemaphore-interface.md)
- [뮤텍스](../../../standard/threading/mutexes.md)
- [세마포 및 SemaphoreSlim](../../../standard/threading/semaphore-and-semaphoreslim.md)
