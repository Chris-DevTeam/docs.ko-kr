---
title: ICorDebugAppDomain4::GetObjectForCCW 메서드
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: f3e64def16fb2817244ef7669ff4bb7fef0bd07c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684450"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a>ICorDebugAppDomain4::GetObjectForCCW 메서드

CCW(COM 호출 가능 래퍼) 포인터에서 관리되는 개체를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `ccwPointer`  
 [in] CCW(COM 호출 가능 래퍼) 포인터입니다.  
  
 `ppManagedObject`  
 제한이 지정 된 CCW 포인터에 해당 하는 관리 되는 개체를 나타내는 "ICorDebugValue" 개체의 주소에 대 한 포인터입니다.  
  
## <a name="remarks"></a>설명  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>참조

- [ICorDebugAppDomain4 인터페이스](icordebugappdomain4-interface.md)
- [디버깅 인터페이스](debugging-interfaces.md)
