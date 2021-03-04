---
description: '자세히 알아보기: ICorProfilerInfo10:: RequestReJITWithInliners 메서드'
title: ICorProfilerInfo10::RequestReJITWithInliners
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.RequestReJITWithInliners
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 925a61bf2521950cad7fb0dce8f1484198f3f806
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106516"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a>ICorProfilerInfo10:: RequestReJITWithInliners 메서드

요청 된 메서드 뿐 아니라 요청 된 메서드의 모든 inliners ReJITs 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

## <a name="parameters"></a>매개 변수

- `dwRejitFlags`

  \[in] [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md)의 비트 마스크입니다.

- `cFunctions`

  \[in] 다시 컴파일할 함수 수입니다.

- `moduleIds`

  \[in] 다시 `moduleId` `module` `methodDef` 컴파일할 함수를 식별 하는 (,) 쌍의 부분을 지정 합니다.

- `methodIds`

  \[in] 다시 `methodId` `module` `methodDef` 컴파일할 함수를 식별 하는 (,) 쌍의 부분을 지정 합니다.

## <a name="remarks"></a>설명

[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) 는 인라인 메서드를 추적 하지 않습니다. 프로파일러에서 인라인 된 `RequestReJIT` 메서드의 모든 인스턴스가 ReJITted 하는지 확인 하기 위해 인라인 처리를 차단 하거나 인라이닝을 추적 하 고 모든 inliners에 대해를 호출 해야 합니다. 프로파일러가 인라인을 모니터링 하기 위해 제공 되지 않으므로 ReJIT on attach에 문제가 발생 합니다. 이 메서드를 호출 하 여 inliners의 전체 집합을 ReJITted 수 있습니다.

## <a name="requirements"></a>요구 사항

**플랫폼:** [.Net Core 지원 운영 체제](../../../core/install/windows.md?pivots=os-windows)를 참조 하세요.

**헤더:** CorProf.idl, CorProf.h

**라이브러리:** CorGuids.lib

**.Net 버전:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>참고 항목

- [ICorProfilerInfo10 인터페이스](icorprofilerinfo10-interface.md)
