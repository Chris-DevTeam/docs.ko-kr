---
description: '자세히 알아보기: ICorDebugController:: SetAllThreadsDebugState 메서드'
title: ICorDebugController::SetAllThreadsDebugState 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugController.SetAllThreadsDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type:
- apiref
ms.openlocfilehash: 3bce5360833ae18c68bc8d7ea24f0dec7615f7a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710740"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a>ICorDebugController::SetAllThreadsDebugState 메서드

프로세스에 있는 모든 관리 되는 스레드의 디버그 상태를 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `state`  
 진행 디버그할 스레드의 상태를 지정 하는 "CorDebugThreadState" 열거형의 값입니다.  
  
 `pExceptThisThread`  
 진행 디버그 상태 설정에서 제외할 스레드를 나타내는 "ICorDebugThread" 개체에 대 한 포인터입니다. 이 값이 null 이면 스레드가 제외 되지 않습니다.  
  
## <a name="remarks"></a>설명  

 `SetAllThreadsDebugState`메서드는 [Enumeratethreads 메서드](icordebugcontroller-enumeratethreads-method.md)를 통해 표시 되지 않는 스레드에 영향을 줄 수 있으므로 메서드로 일시 중단 된 스레드는 메서드를 사용 하 여 `SetAllThreadsDebugState` 다시 시작 해야 합니다 `SetAllThreadsDebugState` .  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고 항목
