---
description: '자세히 알아보기: ICorProfilerThreadEnum:: Next 메서드'
title: ICorProfilerThreadEnum::Next 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Next
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Next
helpviewer_keywords:
- ICorProfilerThreadEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: f3535279-3c63-41a2-ab0e-a129dc5a01e8
topic_type:
- apiref
ms.openlocfilehash: 74567624cbe5042b8ab63a28e7fb07e9f708a959
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636341"
---
# <a name="icorprofilerthreadenumnext-method"></a>ICorProfilerThreadEnum::Next 메서드

시퀀스에서 열거자의 현재 위치부터 시작하여 순차적 스레드 컬렉션에서 지정된 개수의 연속 스레드를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT Next (    [in]  ULONG      celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                    ThreadID ids[],  
    [out] ULONG *   pceltFetched  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `celt`  
 [in] 검색할 스레드 개수입니다.  
  
 `ids`  
 [out] 각각 검색된 스레드를 나타내는 `ThreadID` 값의 배열입니다.  
  
 `pceltFetched`  
 [out] `ids` 배열에 실제로 반환된 스레드 개수에 대한 포인터입니다.  
  
## <a name="return-value"></a>Return Value  

 이 메서드는 다음과 같은 특정 HRESULT뿐만 아니라 메서드 오류를 나타내는 HRESULT 오류도 반환합니다.  
  
|HRESULT|설명|  
|-------------|-----------------|  
|S_OK|`celt` 요소가 반환되었습니다.|  
|S_FALSE|`celt`개 미만의 요소가 반환되었으며 이는 열거형이 완료되었음을 나타냅니다.|  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorProf.idl, CorProf.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [ICorProfilerThreadEnum 인터페이스](icorprofilerthreadenum-interface.md)
- [프로파일링 인터페이스](profiling-interfaces.md)
