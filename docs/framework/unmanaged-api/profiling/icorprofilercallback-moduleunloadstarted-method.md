---
description: '자세히 알아보기: ICorProfilerCallback:: ModuleUnloadStarted 메서드'
title: ICorProfilerCallback::ModuleUnloadStarted 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadStarted
helpviewer_keywords:
- ModuleUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadStarted method [.NET Framework profiling]
ms.assetid: 2debcaab-6005-4245-afdb-4268bb7e74bd
topic_type:
- apiref
ms.openlocfilehash: 3d10654e23481fe6f8956129a0aef7ed4206bba9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745231"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a>ICorProfilerCallback::ModuleUnloadStarted 메서드

모듈이 언로드되고 있음을 프로파일러에 알립니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);
```  
  
## <a name="parameters"></a>매개 변수  

 `moduleId`  
 진행 언로드될 모듈의 ID입니다.  
  
## <a name="remarks"></a>설명  

 메서드가 반환 된 후의 값은 `moduleId` 정보 요청에 적합 하지 않습니다 `ModuleUnloadStarted` .이 모듈에 대 한 정보를 가져올 수 있는 프로파일러의 마지막 기회입니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorProf.idl, CorProf.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [ICorProfilerCallback 인터페이스](icorprofilercallback-interface.md)
- [ModuleUnloadFinished 메서드](icorprofilercallback-moduleunloadfinished-method.md)
