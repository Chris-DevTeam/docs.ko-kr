---
description: '다음에 대 한 자세한 정보: CorDebugCreateProcessFlags 열거형'
title: CorDebugCreateProcessFlags 열거형
ms.date: 03/30/2017
api_name:
- CorDebugCreateProcessFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugCreateProcessFlags
helpviewer_keywords:
- CorDebugCreateProcessFlags enumeration [.NET Framework debugging]
ms.assetid: e709acce-6a17-4346-b38a-467dba567358
topic_type:
- apiref
ms.openlocfilehash: 29363510c83873c7f367079857809c165bc55b1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801737"
---
# <a name="cordebugcreateprocessflags-enumeration"></a>CorDebugCreateProcessFlags 열거형

[ICorDebug:: CreateProcess](icordebug-createprocess-method.md) 메서드 호출에 사용할 수 있는 추가 디버깅 옵션을 제공 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a>구성원  
  
|멤버|설명|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|특별 한 옵션은 설정 되지 않습니다.|  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [디버깅 열거형](debugging-enumerations.md)
