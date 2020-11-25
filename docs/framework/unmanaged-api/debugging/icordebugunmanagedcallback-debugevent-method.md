---
title: ICorDebugUnmanagedCallback::DebugEvent 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback.DebugEvent
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type:
- apiref
ms.openlocfilehash: 75341b1af034972c861b75f29a06eaa2c4e33c3a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703039"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a>ICorDebugUnmanagedCallback::DebugEvent 메서드

네이티브 이벤트가 발생 했음을 디버거에 알립니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `pDebugEvent`  
 진행 네이티브 이벤트에 대 한 포인터입니다.  
  
 `fOutOfBand`  
 [in] `true` 디버거가 [ICorDebugController:: Continue](icordebugcontroller-continue-method.md)를 호출할 때까지 관리 되는 프로세스 상태와의 상호 작용을 할 수 없는 경우이 고, 그렇지 않으면 `false` 입니다.  
  
## <a name="remarks"></a>설명  

 디버깅 중인 스레드가 Win32 스레드 이면 Win32 디버깅 인터페이스의 멤버를 사용 하지 마십시오. `ICorDebugController::Continue`대역 외 이벤트를 계속 진행 하는 경우에만 Win32 스레드에서만를 호출할 수 있습니다.  
  
 콜백은 `DebugEvent` 콜백에 대 한 표준 규칙을 따르지 않습니다. 를 호출 하면 `DebugEvent` 프로세스가 RAW OS-debug 중지 됨 상태가 됩니다. 프로세스는 동기화 되지 않습니다. 관리 코드에 대 한 정보 요청을 충족 하기 위해 필요한 경우 자동으로 동기화 된 상태가 자동으로 입력 되므로 다른 중첩 된 콜백이 발생할 수 있습니다 `DebugEvent` .  
  
 프로세스를 계속 하기 전에 예외 이벤트를 무시 하려면 프로세스에서 [ICorDebugProcess:: ClearCurrentException](icordebugprocess-clearcurrentexception-method.md) 을 호출 합니다. 이 메서드를 호출 하면 CONTINUE 요청에서 DBG_EXCEPTION_NOT_HANDLED 대신 DBG_CONTINUE를 보내고, 대역 외 중단점과 단일 단계 예외를 자동으로 지웁니다. Out-of-band 이벤트는 디버깅 중인 응용 프로그램이 중지 되 고 처리 중인 대역 내 이벤트가 이미 있는 경우에도 언제 든 지 제공 될 수 있습니다.  
  
 .NET Framework 버전 2.0에서 디버거는 대역 외 중단점 이벤트를 즉시 실행 해야 합니다. 디버거는 [ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) 및 [ICorDebugProcess2:: ClearUnmanagedBreakpoint](icordebugprocess2-clearunmanagedbreakpoint-method.md) 메서드를 사용 하 여 중단점을 추가 하 고 제거 해야 합니다. 이러한 메서드는 대역 외 중단점을 자동으로 건너뜁니다. 따라서 디스패치되는 대역 외 중단점은 Win32 함수에 대 한 호출과 같이 명령 스트림에 이미 있는 원시 중단점 이어야 합니다 `DebugBreak` . `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess:: getthreadcontext](icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess:: setthreadcontext](icordebugprocess-setthreadcontext-method.md)또는 [디버깅 API](index.md)의 다른 멤버를 사용 하지 마십시오.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참조

- [ICorDebugUnmanagedCallback 인터페이스](icordebugunmanagedcallback-interface.md)
