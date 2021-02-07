---
description: '자세히 알아보기: ICorDebugStackWalk:: Next 메서드'
title: ICorDebugStackWalk::Next 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
ms.openlocfilehash: 27a48ca40f6b43cae32511b71b73e68d88eb60c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717760"
---
# <a name="icordebugstackwalknext-method"></a>ICorDebugStackWalk::Next 메서드

[ICorDebugStackWalk](icordebugstackwalk-interface.md) 개체를 다음 프레임으로 이동 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a>Return Value  

 이 메서드는 다음과 같은 특정 HRESULT뿐만 아니라 메서드 오류를 나타내는 HRESULT 오류도 반환합니다.  
  
|HRESULT|설명|  
|-------------|-----------------|  
|S_OK|런타임이 다음 프레임으로 성공적으로 해제 되었습니다 (설명 참조).|  
|E_FAIL|`ICorDebugStackWalk`개체를 고급으로 설정할 수 없습니다.|  
|CORDBG_S_AT_END_OF_STACK|이 해제의 결과로 스택의 끝에 도달 했습니다.|  
|CORDBG_E_PAST_END_OF_STACK|프레임 포인터가 이미 스택의 끝에 있습니다. 따라서 추가 프레임에는 액세스할 수 없습니다.|  
  
## <a name="exceptions"></a>예외  
  
## <a name="remarks"></a>설명  

 `Next`메서드는 `ICorDebugStackWalk` 런타임에서 현재 프레임을 해제할 수 있는 경우에만 개체를 호출 프레임으로 이동 합니다. 그렇지 않으면 개체는 런타임에서 해제할 수 있는 다음 프레임으로 이동 합니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [ICorDebugStackWalk 인터페이스](icordebugstackwalk-interface.md)
- [디버깅 인터페이스](debugging-interfaces.md)
- [디버깅](index.md)
