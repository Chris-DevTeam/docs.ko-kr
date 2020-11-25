---
title: ICorDebugArrayValue 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue interface
helpviewer_keywords:
- ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type:
- apiref
ms.openlocfilehash: 90688132b98f8316a4b08988c08b2f7cc7ce0fd8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725053"
---
# <a name="icordebugarrayvalue-interface"></a>ICorDebugArrayValue 인터페이스

일차원 또는 다차원 배열을 나타내는 ICorDebugHeapValue의 서브 클래스입니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[GetBaseIndicies 메서드](icordebugarrayvalue-getbaseindicies-method.md)|배열에 있는 각 차원의 기본 인덱스를 가져옵니다.|  
|[GetCount 메서드](icordebugarrayvalue-getcount-method.md)|배열에 있는 요소의 총 수를 가져옵니다.|  
|[GetDimensions 메서드](icordebugarrayvalue-getdimensions-method.md)|배열의 크기를 가져옵니다.|  
|[GetElement 메서드](icordebugarrayvalue-getelement-method.md)|배열에서 지정 된 요소를 나타내는 값을 가져옵니다.|  
|[GetElementAtPosition 메서드](icordebugarrayvalue-getelementatposition-method.md)|배열을 0부터 시작 하는 1 차원 배열로 처리 하는 지정 된 위치에 있는 요소를 가져옵니다.|  
|[GetElementType 메서드](icordebugarrayvalue-getelementtype-method.md)|배열에 있는 요소의 단순 형식을 가져옵니다.|  
|[GetRank 메서드](icordebugarrayvalue-getrank-method.md)|배열의 차수를 가져옵니다.|  
|[HasBaseIndicies 메서드](icordebugarrayvalue-hasbaseindicies-method.md)|배열에 기본 인덱스가 있는지 여부를 확인 합니다.|  
  
## <a name="remarks"></a>설명  

 `ICorDebugArrayValue` 는 1 차원 배열 및 다차원 배열을 모두 지원 합니다.  
  
> [!NOTE]
> 이 인터페이스는 크로스 시스템 또는 크로스 프로세스 원격 호출을 지원하지 않습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참조

- [디버깅 인터페이스](debugging-interfaces.md)
