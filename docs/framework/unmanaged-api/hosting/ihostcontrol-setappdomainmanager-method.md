---
title: IHostControl::SetAppDomainManager 메서드
ms.date: 03/30/2017
api_name:
- IHostControl.SetAppDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type:
- apiref
ms.openlocfilehash: 2f4c004db39c14e7a71b0caa55a6089e8f69ca3a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680661"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a>IHostControl::SetAppDomainManager 메서드

응용 프로그램 도메인이 생성 되었음을 호스트에 알립니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `dwAppDomainID`  
 진행 선택한의 숫자 식별자입니다 <xref:System.AppDomain> .  
  
 `pUnkAppDomainManager`  
 진행 <xref:System.AppDomainManager> 호스트가 구현 하는 개체에 대 한 포인터 `IUnknown` 입니다.  
  
## <a name="return-value"></a>반환 값  
  
|HRESULT|설명|  
|-------------|-----------------|  
|S_OK|`SetAppDomainManager` 성공적으로 반환 되었습니다.|  
|HOST_E_CLRNOTAVAILABLE|CLR (공용 언어 런타임)이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.|  
|HOST_E_TIMEOUT|호출 시간이 초과 되었습니다.|  
|HOST_E_NOT_OWNER|호출자가 잠금을 소유 하지 않습니다.|  
|HOST_E_ABANDONED|차단 된 스레드나 파이버에서 대기 하는 동안 이벤트를 취소 했습니다.|  
|E_FAIL|알 수 없는 치명적인 오류가 발생 했습니다. 메서드가 E_FAIL 반환 하는 경우 해당 프로세스 내에서 더 이상 CLR을 사용할 수 없습니다. 호스팅 메서드를 이후에 호출 하면 HOST_E_CLRNOTAVAILABLE 반환 됩니다.|  
  
## <a name="remarks"></a>설명  

 는 <xref:System.AppDomainManager> 관리 코드를 부트스트랩 하 고 각각의 생성 및 설정을 제어 하는 메커니즘을 호스트에 제공 합니다 <xref:System.AppDomain> . 는 <xref:System.AppDomainManager> 만들어질 때 각각에 로드 됩니다 <xref:System.AppDomain> <xref:System.AppDomain> . 선택 하는 경우 CLR은 매개 변수 값을 설정 하 여 응용 프로그램 도메인이 생성 되었음을 호스트에 알립니다 `pUnkAppDomainManager` .  
  
 메서드를 구현 `SetAppDomainManager` 하는 경우 호스트는 응용 프로그램 도메인 관리자에 대 한 어셈블리 이름 및 유형을 설정할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Mscoree.dll  
  
 **라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참조

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [IHostControl 인터페이스](ihostcontrol-interface.md)
