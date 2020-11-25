---
title: IHostIoCompletionManager::GetHostOverlappedSize 메서드
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetHostOverlappedSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize
helpviewer_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize method [.NET Framework hosting]
- GetHostOverlappedSize method [.NET Framework hosting]
ms.assetid: 2902578b-d5e2-4f8d-a103-0c7b6dceda9e
topic_type:
- apiref
ms.openlocfilehash: 612a5f08982b1db5c940a7cca93166480b21e612
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724860"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a>IHostIoCompletionManager::GetHostOverlappedSize 메서드

호스트가 i/o 요청에 추가 하려는 사용자 지정 데이터의 크기를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `pcbSize`  
 제한이 CLR (공용 언어 런타임)에서 Win32 개체의 크기와 함께 할당 해야 하는 바이트 수에 대 한 포인터입니다 `OVERLAPPED` .  
  
## <a name="return-value"></a>반환 값  
  
|HRESULT|설명|  
|-------------|-----------------|  
|S_OK|`GetHostOverlappedSize` 성공적으로 반환 되었습니다.|  
|HOST_E_CLRNOTAVAILABLE|CLR이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.|  
|HOST_E_TIMEOUT|호출 시간이 초과 되었습니다.|  
|HOST_E_NOT_OWNER|호출자가 잠금을 소유 하지 않습니다.|  
|HOST_E_ABANDONED|차단 된 스레드나 파이버에서 대기 하는 동안 이벤트를 취소 했습니다.|  
|E_FAIL|알 수 없는 치명적인 오류가 발생 했습니다. 메서드가 E_FAIL 반환 하는 경우 해당 프로세스 내에서 더 이상 CLR을 사용할 수 없습니다. 호스팅 메서드를 이후에 호출 하면 HOST_E_CLRNOTAVAILABLE 반환 됩니다.|  
  
## <a name="remarks"></a>설명  

 Windows 플랫폼 Api에 대 한 모든 비동기 i/o 호출은 `OVERLAPPED` 파일 포인터 위치와 같은 정보를 제공 하는 Win32 개체를 사용 합니다. 상태를 유지 하기 위해 비동기 i/o 호출을 수행 하는 응용 프로그램은 일반적으로 사용자 지정 데이터를 구조체에 추가 합니다. `GetHostOverlappedSize` 및 [IHostIoCompletionManager:: InitializeHostOverlapped](ihostiocompletionmanager-initializehostoverlapped-method.md) 는 호스트에 이러한 사용자 지정 데이터를 포함할 수 있는 기회를 제공 합니다.  
  
 CLR은 메서드를 호출 `GetHostOverlappedSize` 하 여 호스트가 개체에 추가 하려는 사용자 지정 데이터의 크기를 확인 합니다 `OVERLAPPED` .  
  
> [!NOTE]
> `GetHostOverlappedSize` 는 한 번만 호출 됩니다. 호스트의 사용자 지정 데이터는 모든 i/o 요청에 대해 동일한 크기 여야 합니다.  
  
> [!IMPORTANT]
> 개체 자체의 크기는 `OVERLAPPED` 의 값에 포함 되지 않습니다 `pcbSize` .  
  
 구조에 대 한 자세한 내용은 `OVERLAPPED` Windows 플랫폼 설명서를 참조 하십시오.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Mscoree.dll  
  
 **라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참조

- <xref:System.Threading.NativeOverlapped>
- [ICLRIoCompletionManager 인터페이스](iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager 인터페이스](ihostiocompletionmanager-interface.md)
