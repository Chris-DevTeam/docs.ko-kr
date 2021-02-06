---
description: '자세히 알아보기: ICorProfilerAssemblyReferenceProvider 인터페이스'
title: ICorProfilerAssemblyReferenceProvider 인터페이스
ms.date: 03/30/2017
api_name:
- ICorProfilerAssemblyReferenceProvider
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 17205116-66e1-4acc-8f01-532fb3867028
topic_type:
- apiref
ms.openlocfilehash: 0f16bad95dba46452ce5cc8ad1bbe6ca1bfeb7c8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648352"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a>ICorProfilerAssemblyReferenceProvider 인터페이스

[.NET Framework 4.5.2 이상 버전에서 지원됨]  
  
 프로파일러가 [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) 콜백에서 추가 될 어셈블리 참조의 CLR (공용 언어 런타임)에 알릴 수 있습니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[AddAssemblyReference 메서드](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|프로파일러가 [Moduleloadfinished](icorprofilercallback-moduleloadfinished-method.md) 콜백에서 추가 하려고 하는 어셈블리 참조의 CLR에 알립니다.|  
  
## <a name="remarks"></a>설명  

 CLR은 `ICorProfilerAssemblyReferenceProvider` [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) 콜백에서 인터페이스 개체를 프로파일러에 전달 합니다. 이를 통해 프로파일러에서 [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)에서 나중에 추가 하려는 어셈블리 참조의 CLR에 알릴 수 있습니다. 있습니다. 그러면 CLR 어셈블리 참조 closure 워커의 정확도 및 어셈블리 공유 가능 여부를 확인하는 알고리즘의 정확도가 높아집니다.  
  
 이 인터페이스는이 인터페이스 개체를 프로파일러에 전달 하는 [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) 콜백에서만 사용할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorProf.idl, CorProf.h  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [프로파일링 인터페이스](profiling-interfaces.md)
