---
description: '자세히 알아보기: CorDebugStepReason 열거형'
title: CorDebugStepReason 열거형
ms.date: 03/30/2017
api_name:
- CorDebugStepReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugStepReason
helpviewer_keywords:
- CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type:
- apiref
ms.openlocfilehash: 2a331b09709ffb6179f2e481baf4bf421d60ea99
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801542"
---
# <a name="cordebugstepreason-enumeration"></a>CorDebugStepReason 열거형

개별 단계의 결과를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef enum CorDebugStepReason {  
    STEP_NORMAL,  
    STEP_RETURN,  
    STEP_CALL,  
    STEP_EXCEPTION_FILTER,  
    STEP_EXCEPTION_HANDLER,  
    STEP_INTERCEPT,  
    STEP_EXIT  
} CorDebugStepReason;  
```  
  
## <a name="members"></a>구성원  
  
|멤버|설명|  
|------------|-----------------|  
|`STEP_NORMAL`|단계별 실행은 동일한 함수 내에서 정상적으로 완료 됩니다.|  
|`STEP_RETURN`|함수가 반환 된 후에도 정상적으로 계속 실행 됩니다.|  
|`STEP_CALL`|새로 호출 된 함수가 시작 될 때 계속 해 서 단계별로 진행 합니다.|  
|`STEP_EXCEPTION_FILTER`|예외가 생성 되었으며 컨트롤이 예외 필터로 전달 되었습니다.|  
|`STEP_EXCEPTION_HANDLER`|예외가 생성 되었으며 컨트롤이 예외 처리기에 전달 되었습니다.|  
|`STEP_INTERCEPT`|컨트롤이 인터셉터로 전달 되었습니다.|  
|`STEP_EXIT`|단계가 완료 되기 전에 스레드가 종료 되었습니다.|  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [StepComplete 메서드](icordebugmanagedcallback-stepcomplete-method.md)
- [디버깅 열거형](debugging-enumerations.md)
