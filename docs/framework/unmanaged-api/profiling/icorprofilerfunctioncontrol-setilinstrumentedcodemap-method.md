---
title: ICorProfilerFunctionControl::SetILInstrumentedCodeMap 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetIILInstrumentedCodeMap method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: ecf56646-7e5f-46c4-8340-f3a04e88920f
topic_type:
- apiref
ms.openlocfilehash: d22d789724a62cebb0136b9b01be22d6825384ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714538"
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a>ICorProfilerFunctionControl::SetILInstrumentedCodeMap 메서드

지정한 CIL(공용 중간 언어) 맵 엔트리를 사용하여 지정된 함수에 대한 코드 맵을 설정합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a>매개 변수  

 `cILMapEntries`  
 [in] 맵의 엔트리 수입니다.  
  
 `rgILMapEntries`  
 [in] 호출자가 할당한 COR_IL_MAP 엔트리 배열입니다. 이러한 항목의 해석은 [ICorProfilerInfo:: SetILInstrumentedCodeMap](icorprofilerinfo-setilinstrumentedcodemap-method.md) 메서드와 동일 합니다.  
  
## <a name="remarks"></a>설명  

 이 메서드를 호출 하 여 매핑을 설정 하면 디버거가 [ICorDebugILCode2:: GetInstrumentedILMap](../debugging/icordebugilcode2-getinstrumentedilmap-method.md)를 호출 하 여 매핑을 검색할 수 있습니다. 또한 스택 추적 및 변수 수명에 대한 IL 오프셋을 계산할 때 디버거가 내부적으로 매핑을 사용할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorProf.idl, CorProf.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>참조

- [ICorProfilerInfo 인터페이스](icorprofilerinfo-interface.md)
