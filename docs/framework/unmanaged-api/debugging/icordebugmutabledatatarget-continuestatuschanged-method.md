---
title: ICorDebugMutableDataTarget::ContinueStatusChanged 메서드
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
ms.openlocfilehash: 4910b125c2344505128a6979dfe4c9fad2b72c19
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695792"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a>ICorDebugMutableDataTarget::ContinueStatusChanged 메서드

지정된 스레드에서 해결되지 않은 디버그 이벤트의 연속 상태를 변경합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
## <a name="parameters"></a>매개 변수  

 `dwThreadId`  
 운영 체제에서 정의된 스레드 식별자입니다.  
  
 `continueStatus`  
 요청된 새 연속 상태를 나타내는 [COREDB_CONTINUE_STATUS](../common-data-types-unmanaged-api-reference.md) 값입니다.  
  
## <a name="remarks"></a>설명  

 디버거는 정상적일 경우 처리되는 방식과 다른 방식으로 현재 디버그 이벤트가 처리되도록 요구하는 ICorDebug 메서드를 호출할 때 `ContinueStatusChanged` 메서드를 호출합니다. 예를 들어 해결되지 않은 예외가 있고 디버거가 예외를 취소하는 작업(예: [ICorDebugILFrame::SetIP`FuncEval` 또는 ](icordebugilframe-setip-method.md))을 요청하는 경우 이 API는 예외가 취소되도록 요청하는 데 사용됩니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>참조

- [ICorDebugMutableDataTarget 인터페이스](icordebugmutabledatatarget-interface.md)
- [디버깅 인터페이스](debugging-interfaces.md)
