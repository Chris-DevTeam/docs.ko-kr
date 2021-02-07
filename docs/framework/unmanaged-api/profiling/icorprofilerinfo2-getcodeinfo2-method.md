---
description: '자세히 알아보기: ICorProfilerInfo2:: GetCodeInfo2 메서드'
title: ICorProfilerInfo2::GetCodeInfo2 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetCodeInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type:
- apiref
ms.openlocfilehash: 69b877b2dfe3bf23cd2b13417386c45d51de44d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760508"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a>ICorProfilerInfo2::GetCodeInfo2 메서드

지정된 `FunctionID`와 연결된 네이티브 코드의 범위를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a>매개 변수  

 `functionID`  
 [in] 네이티브 코드가 연결된 함수의 ID입니다.  
  
 `cCodeInfos`  
 [in] `codeInfos` 배열의 크기입니다.  
  
 `pcCodeInfos`  
 제한이 사용할 수 있는 [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 구조체의 총 수에 대 한 포인터입니다.  
  
 `codeInfos`  
 [out] 호출자가 제공한 버퍼입니다. 메서드가 반환된 후에는 각각 네이티브 코드 블록을 설명하는 `COR_PRF_CODE_INFO` 구조체의 배열을 포함합니다.  
  
## <a name="remarks"></a>설명  

 범위는 MSIL(Microsoft Intermediate Language) 오프셋의 오름차순으로 정렬됩니다.  
  
 `GetCodeInfo2`가 반환된 후 `codeInfos` 버퍼가 모든 `COR_PRF_CODE_INFO` 구조체를 포함하기에 충분히 큰지 확인해야 합니다. 이렇게 하려면 `cCodeInfos` 값을 `cchName` 매개 변수의 값과 비교합니다. `cCodeInfos`를 `COR_PRF_CODE_INFO` 구조체의 크기로 나눈 값이 `pcCodeInfos`보다 작으면 더 큰 `codeInfos` 버퍼를 할당하고 `cCodeInfos`를 더 큰 새 크기로 업데이트한 다음 `GetCodeInfo2`를 다시 호출합니다.  
  
 또는 길이가 0인 `codeInfos` 버퍼로 `GetCodeInfo2`를 먼저 호출하여 올바른 버퍼 크기를 구합니다. 그런 다음 `codeInfos` 버퍼 크기를 `pcCodeInfos`에서 반환된 값에 `COR_PRF_CODE_INFO` 구조체의 크기를 곱한 값으로 설정하고 `GetCodeInfo2`를 다시 호출합니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorProf.idl, CorProf.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [GetCodeInfo3 메서드](icorprofilerinfo4-getcodeinfo3-method.md)
- [ICorProfilerInfo2 인터페이스](icorprofilerinfo2-interface.md)
- [프로파일링 인터페이스](profiling-interfaces.md)
- [프로파일링](index.md)
