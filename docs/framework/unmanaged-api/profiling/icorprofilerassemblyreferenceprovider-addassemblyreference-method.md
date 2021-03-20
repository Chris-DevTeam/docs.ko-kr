---
description: '자세히 알아보기: ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference 메서드'
title: ICorProfilerAssemblyReferenceProvider::AddAssemblyReference 메서드
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type:
- apiref
ms.openlocfilehash: e73a6d59b76744dcf9f4991be2589220669e154d
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760746"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a>ICorProfilerAssemblyReferenceProvider::AddAssemblyReference 메서드

[.NET Framework 4.5.2 이상 버전에서 지원됨]  
  
 프로파일러가 [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) 콜백에서 추가할 어셈블리 참조의 CLR (공용 언어 런타임)에 대해 알립니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a>매개 변수

`pAssemblyRefInfo` 어셈블리 참조 클로저를 수행할 때 고려해 야 하는 어셈블리 참조에 대 한 정보를 CLR에 제공 하는 [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) 구조체에 대 한 포인터입니다.
  
## <a name="remarks"></a>설명  

 프로파일러는 `wszAssemblyPath` [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) 콜백의 인수에 지정 된 어셈블리에서 참조 하려는 각 대상 어셈블리에 대해이 메서드를 호출 합니다. [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface 개체는 인수의 어셈블리 경로 및 이름과 함께 프로파일러의 [ICorProfilerCallback6:: getassemblyreferences](icorprofilercallback6-getassemblyreferences-method.md) 콜백으로 전달 됩니다 `wszAssemblyPath` .  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorProf.idl, CorProf.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>참조

- [ICorProfilerAssemblyReferenceProvider 인터페이스](icorprofilerassemblyreferenceprovider-interface.md)
- [GetAssemblyReferences 메서드](icorprofilercallback6-getassemblyreferences-method.md)
- [ModuleLoadFinished 메서드](icorprofilercallback-moduleloadfinished-method.md)
