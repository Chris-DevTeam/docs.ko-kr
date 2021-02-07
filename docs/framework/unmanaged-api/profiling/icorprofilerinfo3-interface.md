---
description: '자세히 알아보기: ICorProfilerInfo3 인터페이스'
title: ICorProfilerInfo3 인터페이스
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3
helpviewer_keywords:
- ICorProfilerInfo3 interface [.NET Framework profiling]
ms.assetid: 044a262f-0fa7-485d-b0c1-64cdc359c654
topic_type:
- apiref
ms.openlocfilehash: 52b4c699a122c302e47cffb11d01e7829009e219
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687183"
---
# <a name="icorprofilerinfo3-interface"></a>ICorProfilerInfo3 인터페이스

코드 프로파일러가 이벤트 모니터링을 제어하고 정보를 요청하기 위해 CLR(공용 언어 런타임)과 통신하는 데 사용하는 메서드를 제공합니다. `ICorProfilerInfo3`인터페이스는 [ICorProfilerInfo2](icorprofilerinfo2-interface.md) 인터페이스의 확장입니다. .NET Framework 4 이상 버전에서 지원 되는 새 메서드를 제공 합니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[EnumJITedFunctions 메서드](icorprofilerinfo3-enumjitedfunctions-method.md)|이전에 JIT 컴파일된 모든 함수에 대해 열거자를 반환합니다.|  
|[EnumModules 메서드](icorprofilerinfo3-enummodules-method.md)|애플리케이션에 로드되는 관리 모듈 컬렉션을 순차적으로 반복하는 메서드를 제공하는 열거자를 반환합니다.|  
|[GetAppDomainsContainingModule 메서드](icorprofilerinfo3-getappdomainscontainingmodule-method.md)|지정된 모듈이 로드된 애플리케이션 도메인의 식별자를 가져옵니다.|  
|[GetFunctionEnter3Info 메서드](icorprofilerinfo3-getfunctionenter3info-method.md)|[FunctionEnter3WithInfo](functionenter3withinfo-function.md) 함수를 통해 프로파일러에 보고 하는 함수의 스택 프레임 및 인수 정보를 제공 합니다. 콜백 하는 동안에만 호출할 수 있습니다 `FunctionEnter3WithInfo` .|  
|[GetFunctionLeave3Info 메서드](icorprofilerinfo3-getfunctionleave3info-method.md)|[FunctionLeave3WithInfo 함수](functionleave3withinfo-function.md) 함수를 통해 프로파일러에 보고 하는 함수의 스택 프레임 및 반환 값을 제공 합니다. 콜백 하는 동안에만 호출할 수 있습니다 `FunctionLeave3WithInfo` .|  
|[GetFunctionTailcall3Info 메서드](icorprofilerinfo3-getfunctiontailcall3info-method.md)|[FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) 함수를 통해 프로파일러에 보고 하는 함수의 스택 프레임을 제공 합니다. 콜백 하는 동안에만 호출할 수 있습니다 `FunctionTailcall3WithInfo` .|  
|[GetModuleInfo2 메서드](icorprofilerinfo3-getmoduleinfo2-method.md)|모듈 ID가 지정된 경우 모듈의 파일 이름, 모듈의 부모 어셈블리 ID 및 모듈 속성을 설명하는 비트 마스크를 반환합니다.|  
|[GetRuntimeInformation 메서드](icorprofilerinfo3-getruntimeinformation-method.md)|프로파일링되는 런타임에 대한 버전 정보를 제공합니다.|  
|[GetStringLayout2 메서드](icorprofilerinfo3-getstringlayout2-method.md)|문자열 개체의 레이아웃 정보를 가져옵니다.|  
|[GetThreadStaticAddress2 메서드](icorprofilerinfo3-getthreadstaticaddress2-method.md)|지정된 스레드 및 애플리케이션 도메인의 범위에 있는 지정된 Thread 정적 필드의 주소를 가져옵니다.|  
|[RequestProfilerDetach 메서드](icorprofilerinfo3-requestprofilerdetach-method.md)|런타임에 프로파일러를 분리하도록 지시합니다.|  
|[SetEnterLeaveFunctionHooks3 메서드](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)|[FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)및 [FunctionTailcall3](functiontailcall3-function.md) 함수에서 호출 되는 프로파일러 구현 함수를 지정 합니다.|  
|[SetEnterLeaveFunctionHooks3WithInfo 메서드](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)|관리 되는 함수의 [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)및 [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) 후크에 대해 호출 되는 프로파일러 구현 함수를 지정 합니다.|  
|[SetFunctionIDMapper2 메서드](icorprofilerinfo3-setfunctionidmapper2-method.md)|`FunctionID` 값을 대체 값에 매핑하기 위해 호출되는 프로파일러 구현 함수를 지정합니다. 대체 값은 프로파일러의 함수 진입점/종료점 후크에 전달됩니다. 이 메서드는 프로파일러가 런타임을 명확 하 게 구분 하는 데 사용할 수 있는 매개 변수를 사용 하 여 [ICorProfilerInfo:: SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) 를 확장 합니다.|  
  
## <a name="remarks"></a>설명  

 CLR은 자유 스레드 모델을 사용하여 `ICorProfilerInfo3` 인터페이스의 메서드를 구현합니다. 각 메서드가 HRESULT를 반환하여 성공 또는 실패를 나타냅니다. 가능한 반환 코드 목록은 CorError.h 파일을 참조하세요.  
  
 CLR은 `ICorProfilerInfo3` [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) 또는 [ICorProfilerCallback3:: initializeforattach](icorprofilercallback3-initializeforattach-method.md) 메서드의 프로파일러 구현을 사용 하 여 초기화 하는 동안 각 코드 프로파일러에 인터페이스를 전달 합니다. 그런 다음 코드 프로파일러가 `ICorProfilerInfo3` 메서드를 호출하여 CLR의 제어에 따라 실행되는 관리 코드에 대한 정보를 가져올 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorProf.idl, CorProf.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [프로파일링 인터페이스](profiling-interfaces.md)
- [ICorProfilerInfo 인터페이스](icorprofilerinfo-interface.md)
