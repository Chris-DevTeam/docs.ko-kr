---
title: ICorDebugFunction3 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebugFunction3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type:
- apiref
ms.openlocfilehash: 8c9c507f00780d5ef5c5aeb28a1b10493351f37e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546974"
---
# <a name="icordebugfunction3-interface"></a>ICorDebugFunction3 인터페이스
[.NET Framework 4.5.2 이상 버전에서 지원됨]  
  
 ReJIT 요청의 코드에 액세스할 수 있도록 ICorDebugFunction 인터페이스를 논리적으로 확장합니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|Description|  
|------------|-----------------|  
|[GetActiveReJitRequestILCode 메서드](icordebugfunction3-getactiverejitrequestilcode-method.md)|활성 ReJIT 요청에서 IL을 포함 하는 [ICorDebugILCode](icordebugilcode-interface.md) 에 대 한 인터페이스 포인터를 가져옵니다.|  
  
## <a name="remarks"></a>설명  
  
## <a name="requirements"></a>요구 사항  
 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>참조

- [디버깅 인터페이스](debugging-interfaces.md)
- [디버깅](index.md)
- [ReJIT: 방법 가이드](/archive/blogs/davbr/rejit-a-how-to-guide)
