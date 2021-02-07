---
description: '자세히 알아보기: IHostMemoryManager:: RegisterMemoryNotificationCallback 메서드'
title: IHostMemoryManager::RegisterMemoryNotificationCallback 메서드
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.RegisterMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback
helpviewer_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback method [.NET Framework hosting]
- RegisterMemoryNotificationCallback method [.NET Framework hosting]
ms.assetid: 65d301f6-4dbb-4b5f-8eff-82540e2b6465
topic_type:
- apiref
ms.openlocfilehash: 26a7468aba4f473eebff78a8c67eeb5b3e866e9c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707766"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a>IHostMemoryManager::RegisterMemoryNotificationCallback 메서드

컴퓨터의 현재 메모리 로드를 CLR (공용 언어 런타임)에 알리기 위해 호스트에서 호출 하는 콜백 함수에 대 한 포인터를 등록 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `pCallback`  
 진행 CLR에서 구현 하는 [ICLRMemoryNotificationCallback](iclrmemorynotificationcallback-interface.md) 인스턴스에 대 한 인터페이스 포인터입니다.  
  
## <a name="return-value"></a>Return Value  
  
|HRESULT|설명|  
|-------------|-----------------|  
|S_OK|`RegisterMemoryNotificationCallback` 성공적으로 반환 되었습니다.|  
|HOST_E_CLRNOTAVAILABLE|CLR이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.|  
|HOST_E_TIMEOUT|호출 시간이 초과 되었습니다.|  
|HOST_E_NOT_OWNER|호출자가 잠금을 소유 하지 않습니다.|  
|HOST_E_ABANDONED|차단 된 스레드나 파이버에서 대기 하는 동안 이벤트를 취소 했습니다.|  
|E_FAIL|알 수 없는 치명적인 오류가 발생 했습니다. 메서드가 E_FAIL 반환 하는 경우 해당 프로세스 내에서 더 이상 CLR을 사용할 수 없습니다. 호스팅 메서드를 이후에 호출 하면 HOST_E_CLRNOTAVAILABLE 반환 됩니다.|  
  
## <a name="remarks"></a>설명  

 인터페이스는 `ICLRMemoryNotificationCallback` 하나의 메서드 ([ICLRMemoryNotificationCallback:: OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md))만 정의 하 고, `pCallback` 가 CLR에서 제공 하는 인스턴스에 대 한 포인터 이기 때문에 `ICLRMemoryNotificationCallback` 콜백 함수 자체에 대 한 등록은 효과적입니다. 호스트는 `OnMemoryNotification` 표준 Win32 함수를 사용 하는 대신를 호출 하 여 메모리 압력 상태를 보고 `CreateMemoryResourceNotification` 합니다. 자세한 내용은 Windows 플랫폼 설명서를 참조 하세요.  
  
> [!NOTE]
> 에 대 한 호출은 `OnMemoryNotification` 차단 되지 않습니다. 항상 즉시 반환 됩니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Mscoree.dll  
  
 **라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [ICLRMemoryNotificationCallback 인터페이스](iclrmemorynotificationcallback-interface.md)
- [IHostMemoryManager 인터페이스](ihostmemorymanager-interface.md)
