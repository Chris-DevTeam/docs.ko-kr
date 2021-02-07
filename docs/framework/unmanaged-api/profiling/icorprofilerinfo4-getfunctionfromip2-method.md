---
description: '자세히 알아보기: ICorProfilerInfo4:: GetFunctionFromIP2 메서드'
title: ICorProfilerInfo4::GetFunctionFromIP2 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetFunctionFromIP2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type:
- apiref
ms.openlocfilehash: f6abda7c9e7d4abcc0f0b256d6a7785cea205d7a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686806"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a>ICorProfilerInfo4::GetFunctionFromIP2 메서드

관리 되는 코드 명령 포인터를 함수의 JIT 다시 컴파일된 버전에 매핑합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a>매개 변수  

 `ip`  
 진행 관리 코드의 명령 포인터입니다.  
  
 `pFunctionId`  
 제한이 함수 ID입니다.  
  
 `pReJitId`  
 제한이 함수의 JIT 다시 컴파일된 버전 id입니다.  
  
## <a name="remarks"></a>설명  

 `GetFunctionFromIP2` 는 지정 된 `GetFunctionFromIP` IP 주소를 포함 하는 함수의 함수 ID 대신 JIT 다시 컴파일된 ID를 가져오는 점을 제외 하 고와 비슷합니다.  
  
> [!NOTE]
> `GetFunctionFromIP2` 는 가비지 수집을 트리거할 수 있지만 `GetFunctionFromIP` 는 그렇지 않습니다.  자세한 내용은 [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md)를 참조 하세요.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorProf.idl, CorProf.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [ICorProfilerInfo 인터페이스](icorprofilerinfo-interface.md)
