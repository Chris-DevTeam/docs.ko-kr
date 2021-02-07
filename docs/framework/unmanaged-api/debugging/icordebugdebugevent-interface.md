---
description: '자세히 알아보기: ICorDebugDebugEvent 인터페이스'
title: ICorDebugDebugEvent 인터페이스
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
ms.openlocfilehash: 5735be22b76e9f74847bb5138c00130f28dbfc96
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764309"
---
# <a name="icordebugdebugevent-interface"></a>ICorDebugDebugEvent 인터페이스

모든 `ICorDebug` 디버그 이벤트가 파생되는 기본 인터페이스를 정의합니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[GetEventKind 메서드](icordebugdebugevent-geteventkind-method.md)|이 `ICorDebugDebugEvent` 개체가 나타내는 이벤트의 종류를 나타냅니다.|  
|[GetThread 메서드](icordebugdebugevent-getthread-method.md)|이벤트가 발생한 스레드를 가져옵니다.|  
  
## <a name="remarks"></a>설명  

 다음 인터페이스는 `ICorDebugDebugEvent` 인터페이스에서 파생됩니다.  
  
- [ICorDebugExceptionDebugEvent](icordebugexceptiondebugevent-interface.md)  
  
- [ICorDebugModuleDebugEvent](icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> 이 인터페이스는 .NET 네이티브에서만 사용할 수 있습니다. .NET 네이티브 외부의 ICorDebug 시나리오에 대해 `QueryInterface`를 호출하여 인터페이스 포인터를 검색하려고 하면 `E_NOINTERFACE`가 반환됩니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [디버깅 인터페이스](debugging-interfaces.md)
- [디버깅](index.md)
