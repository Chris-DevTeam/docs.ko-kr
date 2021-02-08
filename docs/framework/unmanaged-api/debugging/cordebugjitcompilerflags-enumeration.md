---
description: '자세히 알아보기: CorDebugJITCompilerFlags 열거형'
title: CorDebugJITCompilerFlags 열거형
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlags
helpviewer_keywords:
- CorDebugJITCompilerFlags enumeration [.NET Framework debugging]
ms.assetid: c0774f70-5bed-45e8-9922-fdad778c4c33
topic_type:
- apiref
ms.openlocfilehash: 7e5337293aa4fe446deb12653acd22864eb7679a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801607"
---
# <a name="cordebugjitcompilerflags-enumeration"></a>CorDebugJITCompilerFlags 열거형

관리되는 JIT(Just-In-Time) 컴파일러의 동작에 영향을 주는 값을 포함합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a>구성원  
  
|멤버|설명|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|컴파일러가 컴파일 데이터를 추적 하 고 최적화를 허용 하도록 지정 합니다.|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|컴파일러가 컴파일 데이터를 추적 하지만 최적화를 사용 하지 않도록 지정 합니다.|  
|`CORDEBUG_JIT_ENABLE_ENC`|컴파일러가 컴파일 데이터를 추적 하 고, 최적화를 사용 하지 않도록 설정 하 고, 편집 하며 계속 하기 기술을 사용 하도록 지정 합니다.|  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [디버깅 열거형](debugging-enumerations.md)
