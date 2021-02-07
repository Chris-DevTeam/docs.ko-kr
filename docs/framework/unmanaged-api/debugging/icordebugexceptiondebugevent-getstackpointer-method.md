---
description: '자세히 알아보기: ICorDebugExceptionDebugEvent:: GetStackPointer 메서드'
title: ICorDebugExceptionDebugEvent::GetStackPointer 메서드
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
ms.openlocfilehash: 5a62a5eb54fff1e94beebc222e3f18cc4655040f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693449"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a>ICorDebugExceptionDebugEvent::GetStackPointer 메서드

이 예외 디버그 이벤트에 대한 스택 포인터를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `pStackPointer`  
 [out] 이 예외 디버그 이벤트의 스택 포인터에 대한 포인터입니다. 자세한 내용은 설명 부분을 참조하세요.  
  
## <a name="remarks"></a>설명  

 이 스택 포인터의 의미는 다음 표와 같이 이벤트 유형에 따라 달라집니다.  
  
|이벤트 유형|`pStackPointer` 값의 의미|  
|----------------|--------------------------------------|  
|[MANAGED_EXCEPTION_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|예외를 throw한 프레임에 대한 스택 포인터입니다.|  
|[MANAGED_EXCEPTION_USER_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|예외가 throw된 지점과 가장 가까운 사용자 코드 프레임에 대한 스택 포인터입니다.|  
|[MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](cordebugrecordformat-enumeration.md)|catch 처리기가 포함된 프레임에 대한 스택 포인터입니다.|  
|[MANAGED_EXCEPTION_UNHANDLED](cordebugrecordformat-enumeration.md)|`pStackPointer`가 **null** 인 경우|  
  
> [!NOTE]
> 이 메서드는 .NET 네이티브에서만 사용할 수 있습니다.  
  
 이벤트 유형은 [ICorDebugDebugEvent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) 메서드에서 사용할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [ICorDebugExceptionDebugEvent 인터페이스](icordebugexceptiondebugevent-interface.md)
- [디버깅 인터페이스](debugging-interfaces.md)
