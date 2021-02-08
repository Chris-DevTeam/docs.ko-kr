---
description: '자세한 정보: 프로 파일링 인터페이스'
title: 프로파일링 인터페이스
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
ms.openlocfilehash: d35931c0caad93116d7ea26d29020d84e48ebc29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798929"
---
# <a name="profiling-interfaces"></a>프로파일링 인터페이스

이 섹션에서는 CLR(공용 언어 런타임)에서 실행되는 프로그램을 프로파일링하는 데 사용할 수 있는 관리되지 않는 인터페이스에 대해 설명합니다.  
  
## <a name="in-this-section"></a>섹션 내용  

 [ICLRProfiling 인터페이스](iclrprofiling-interface.md)  
 프로파일러가 실행 중인 프로세스에 연결할 수 있도록 하는 [AttachProfiler](iclrprofiling-attachprofiler-method.md) 메서드를 제공 합니다.  
  
 [ICorProfilerAssemblyReferenceProvider 인터페이스](icorprofilerassemblyreferenceprovider-interface.md)  
 프로파일러가 [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback에서 추가 될 어셈블리 참조의 CLR에 알릴 수 있습니다.  
  
 [ICorProfilerCallback 인터페이스](icorprofilercallback-interface.md)  
 코드 프로파일러가 구독한 이벤트가 발생하면 CLR이 해당 프로파일러에 알림을 보내는 데 사용되는 메서드를 제공합니다.  
  
 [ICorProfilerCallback2 인터페이스](icorprofilercallback2-interface.md)  
 .NET Framework 2.0 이상 버전에서 지원되는 콜백으로 `ICorProfilerCallback` 인터페이스를 확장합니다.  
  
 [ICorProfilerCallback3 인터페이스](icorprofilercallback3-interface.md)  
 CLR이 프로파일러에 연결 및 분리 상태 정보를 전달하는 데 사용하는 콜백 메서드를 제공합니다.  
  
 [ICorProfilerCallback4 인터페이스](icorprofilercallback4-interface.md)  
 CLR이 프로파일러에 정보를 전달하는 데 사용하는 콜백 메서드를 제공합니다.  
  
 [ICorProfilerCallback5 인터페이스](icorprofilercallback5-interface.md)  
 가비지 컬렉션 루트에서 참조하는 개체의 전이적 Closure를 식별하는 메서드를 제공합니다.  
  
 [ICorProfilerCallback6 인터페이스](icorprofilercallback6-interface.md)  
 CLR이 어셈블리를 로드하는 중임을 프로파일러에 알리는 데 사용하는 콜백 메서드를 제공합니다.  
  
 [ICorProfilerCallback7 인터페이스](icorprofilercallback7-interface.md)  
 메모리 내 모듈과 연관 된 기호 스트림이 업데이트 되었음을 프로파일러에 알리기 위해 공용 언어 런타임에서 사용 하는 콜백 메서드를 제공 합니다.  

[ICorProfilerCallback8 인터페이스](icorprofilercallback8-interface.md)  
공용 언어 런타임에서 동적 메서드의 JIT 컴파일이 시작 및 완료 되었음을 프로파일러에 알리는 데 사용 하는 콜백 메서드를 제공 합니다.

[ICorProfilerCallback9 인터페이스](icorprofilercallback9-interface.md)  
공용 언어 런타임에서 동적 메서드가 가비지 수집 되 고 이후에 언로드되는 것을 프로파일러에 알리는 데 사용 하는 콜백 메서드를 제공 합니다.

 [ICorProfilerFunctionControl 인터페이스](icorprofilerfunctioncontrol-interface.md)  
 코드 프로파일러가 CLR과 통신하여 특정 메서드를 다시 컴파일할 때 JIT 컴파일러가 코드를 생성하는 방법을 제어할 수 있도록 하는 메서드를 제공합니다.  
  
 [ICorProfilerFunctionEnum 인터페이스](icorprofilerfunctionenum-interface.md)  
 CLR에서 함수 컬렉션을 순서대로 반복하는 메서드를 제공합니다.  
  
 [ICorProfilerInfo 인터페이스](icorprofilerinfo-interface.md)  
 코드 프로파일러가 CLR과 통신하여 이벤트 모니터링을 제어하고 정보를 요청하는 데 사용하는 메서드를 제공합니다.  
  
 [ICorProfilerInfo2 인터페이스](icorprofilerinfo2-interface.md)  
 .NET Framework 2.0 이상 버전에서 지원되는 메서드로 `ICorProfilerInfo` 인터페이스를 확장합니다.  
  
 [ICorProfilerInfo3 인터페이스](icorprofilerinfo3-interface.md)  
 `ICorProfilerInfo2`.NET Framework 4 이상 버전에서 지원 되는 메서드로 인터페이스를 확장 합니다.  
  
 [ICorProfilerInfo4 인터페이스](icorprofilerinfo4-interface.md)  
 코드 프로파일러가 CLR과 통신하여 이벤트 모니터링을 제어하고 정보를 요청하는 데 사용하는 메서드를 제공합니다.  
  
 [ICorProfilerInfo5 인터페이스](icorprofilerinfo5-interface.md)  
 코드 프로파일러가 CLR과 통신하여 이벤트 모니터링을 제어하는 데 사용하는 메서드를 제공합니다.  
  
 [ICorProfilerInfo6 인터페이스](icorprofilerinfo6-interface.md)  
 지정 된 NGen 모듈에 속하고 지정 된 메서드의 본문에서 인라인 된 모든 메서드에 열거자를 제공 합니다.  
  
 [ICorProfilerInfo7 인터페이스](icorprofilerinfo7-interface.md)  
 새로 정의 된 메타 데이터를 모듈에 적용 하 고 메모리 내 기호 스트림에 대 한 액세스를 제공 하는 메서드를 제공 합니다.  
  
 [ICorProfilerModuleEnum 인터페이스](icorprofilermoduleenum-interface.md)  
 애플리케이션이나 프로파일러가 로드한 모듈 컬렉션을 순서대로 반복하는 메서드를 제공합니다.  
  
 [ICorProfilerObjectEnum 인터페이스](icorprofilerobjectenum-interface.md)  
 [Ngen.exe (네이티브 이미지 생성기)](../../tools/ngen-exe-native-image-generator.md)에서 생성 되는 고정 된 개체의 컬렉션을 순차적으로 반복 하는 메서드를 제공 합니다.  
  
 [ICorProfilerThreadEnum 인터페이스](icorprofilerthreadenum-interface.md)  
 CLR에서 스레드 컬렉션을 순서대로 반복하는 메서드를 제공합니다.  
  
 [IMethodMalloc 인터페이스](imethodmalloc-interface.md)  
 새 MSIL (Microsoft 중간 언어) 함수 본문에 메모리를 할당 하는 [Alloc](imethodmalloc-alloc-method.md) 메서드를 제공 합니다.  
  
## <a name="related-sections"></a>관련 섹션  

 [프로파일링 개요](profiling-overview.md)  
  
 [프로파일링 전역 정적 함수](profiling-global-static-functions.md)  
  
 [프로파일링 열거형](profiling-enumerations.md)  
  
 [프로파일링 구조체](profiling-structures.md)
