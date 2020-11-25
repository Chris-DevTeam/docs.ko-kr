---
title: ICorDebugBreakpoint 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint
helpviewer_keywords:
- ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type:
- apiref
ms.openlocfilehash: 0c84a91c7da553d0c84a4995b4744576d861dcb9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730203"
---
# <a name="icordebugbreakpoint-interface"></a>ICorDebugBreakpoint 인터페이스

함수의 중단점 또는 값에 대 한 조사식을 나타냅니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[Activate 메서드](icordebugbreakpoint-activate-method.md)|이의 활성 상태를 설정 합니다 `ICorDebugBreakpoint` .|  
|[IsActive 메서드](icordebugbreakpoint-isactive-method.md)|이가 활성 상태 인지 여부를 나타내는 값을 가져옵니다 `ICorDebugBreakpoint` .|  
  
## <a name="remarks"></a>설명  

 중단점은 조건식을 직접 지원 하지 않습니다. 이러한 기능이 필요한 경우 디버거는 위에서이 기능을 구현 해야 합니다 `ICorDebugBreakpoint` .  
  
 ICorDebugFunctionBreakpoint 인터페이스는 `ICorDebugBreakpoint` 함수 내에서 중단점을 지원 하도록 확장 됩니다.  
  
> [!NOTE]
> 이 인터페이스는 크로스 시스템 또는 크로스 프로세스 원격 호출을 지원하지 않습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참조

- [디버깅 인터페이스](debugging-interfaces.md)
