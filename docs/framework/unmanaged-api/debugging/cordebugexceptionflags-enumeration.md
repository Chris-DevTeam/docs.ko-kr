---
title: CorDebugExceptionFlags 열거형
ms.date: 03/30/2017
api_name:
- CorDebugExceptionFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionFlags
helpviewer_keywords:
- CorDebugExceptionFlags enumeration [.NET Framework debugging]
ms.assetid: b22687a8-e9cf-4e65-a1b0-f92a81bc524e
topic_type:
- apiref
ms.openlocfilehash: a50272bce2e27963a1d684fef40bac30cf44e1f0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712718"
---
# <a name="cordebugexceptionflags-enumeration"></a>CorDebugExceptionFlags 열거형

예외에 대한 추가 정보를 제공합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a>멤버  
  
|멤버|설명|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|예외가 없습니다.|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|예외를 가로챌 수 있습니다.<br /><br /> 시간상 디버거가 아직 예외를 가로챌 수 없습니다. 예를 들어 현재 콜백 아래에 관리 코드가 없거나 예외 이벤트가 JIT(Just-In-Time) 연결에서 발생한 경우에는 예외를 가로챌 수 없습니다.|  
  
## <a name="remarks"></a>설명  

 이후 버전에서는 이 열거형에 대해 새 값이 추가될 수 있으므로 예기치 않은 값에 대해 `CorDebugExceptionFlags`를 사용하는 코드를 준비해야 합니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참조

- [디버깅 열거형](debugging-enumerations.md)
