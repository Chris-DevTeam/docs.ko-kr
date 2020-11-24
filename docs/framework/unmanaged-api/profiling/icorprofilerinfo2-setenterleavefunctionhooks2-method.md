---
title: ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type:
- apiref
ms.openlocfilehash: f71d0b5c77d4a514001bcbe6904ed912be388d18
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681550"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a>ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 메서드

관리 되는 함수의 "enter", "leave" 및 "tailcall" 후크에 대 한 업데이트 된 버전에 대해 호출 될 프로파일러 구현 함수를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a>매개 변수  

 `pFuncEnter`  
 진행 [FunctionEnter2](functionenter2-function.md) 콜백으로 사용할 구현에 대 한 포인터입니다.  
  
 `pFuncLeave`  
 진행 [FunctionLeave2](functionleave2-function.md) 콜백으로 사용할 구현에 대 한 포인터입니다.  
  
 `pFuncTailcall`  
 진행 [FunctionTailcall2](functiontailcall2-function.md) 콜백으로 사용할 구현에 대 한 포인터입니다.  
  
## <a name="remarks"></a>설명  

 `SetEnterLeaveFunctionHooks2`메서드는 [ICorProfilerInfo:: SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) 메서드와 유사 합니다. 이전에는 enter/leave/tailcall 콜백의 최신 버전으로 사용할 함수를 지정 하 고 후자는 enter/leave/tailcall 콜백의 이전 버전으로 사용할 함수를 지정 하는 데 사용 됩니다.  
  
 한 번에 하나의 콜백 집합만 활성 상태일 수 있습니다. 따라서 프로파일러가 및를 모두 호출 하면 `ICorProfilerInfo::SetEnterLeaveFunctionHooks` `SetEnterLeaveFunctionHooks2` `SetEnterLeaveFunctionHooks2` 이 사용 됩니다.  
  
 `SetEnterLeaveFunctionHooks2`메서드는 프로파일러의 [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) 콜백에서만 호출할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorProf.idl, CorProf.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참조

- [ICorProfilerInfo 인터페이스](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 인터페이스](icorprofilerinfo2-interface.md)
