---
description: '자세히 알아보기: ICorDebugCode2 인터페이스'
title: ICorDebugCode2 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebugCode2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2
helpviewer_keywords:
- ICorDebugCode2 interface [.NET Framework debugging]
ms.assetid: 9321903b-7dea-40d8-ba32-99016c00cc46
topic_type:
- apiref
ms.openlocfilehash: 29fd657ec56993d47ee57aa41c81b45e75352697
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765050"
---
# <a name="icordebugcode2-interface"></a>ICorDebugCode2 인터페이스

"ICorDebugCode"의 기능을 확장 하는 메서드를 제공 합니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[GetCodeChunks 메서드](icordebugcode2-getcodechunks-method.md)|이 코드 개체가 구성 된 코드의 청크를 가져옵니다.|  
|[GetCompilerFlags 메서드](icordebugcode2-getcompilerflags-method.md)|이 코드 개체가 네이티브 이미지 생성기 (Ngen.exe)를 사용 하 여 컴파일 또는 생성 된 JIT (just-in-time) 인 조건을 지정 하는 플래그를 가져옵니다.|  
  
## <a name="remarks"></a>설명  
  
> [!NOTE]
> 이 인터페이스는 크로스 시스템 또는 크로스 프로세스 원격 호출을 지원하지 않습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [ICorDebugCode3 인터페이스](icordebugcode3-interface.md)
- [디버깅 인터페이스](debugging-interfaces.md)
