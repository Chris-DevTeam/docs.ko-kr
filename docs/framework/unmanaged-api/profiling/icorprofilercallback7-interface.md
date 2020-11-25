---
title: ICorProfilerCallback7 인터페이스
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: a0be019e-aaa1-4036-990f-565f114d4b5c
ms.openlocfilehash: e9c7186b3217c29805327e6c1d6b10f580c3a9e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725458"
---
# <a name="icorprofilercallback7-interface"></a>ICorProfilerCallback7 인터페이스

[.NET Framework 4.6.1 이상 버전에서 지원됨]  
  
 공용 언어 런타임이 메모리 내 모듈과 연관된 기호 스트림이 업데이트되었음을 프로파일러에 알리기 위해 사용하는 콜백 메서드를 제공하는 [ICorProfilerCallback6](icorprofilercallback6-interface.md) 의 서브클래스입니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[ModuleInMemorySymbolsUpdated 메서드](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|메모리 내 모듈과 연관된 기호 스트림이 업데이트되었음을 프로파일러에 알립니다.|  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorProf.idl, CorProf.h  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>참조

- [프로파일링 인터페이스](profiling-interfaces.md)
