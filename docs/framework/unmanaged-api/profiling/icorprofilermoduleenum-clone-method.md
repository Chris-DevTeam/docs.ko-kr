---
description: '자세히 알아보기: ICorProfilerModuleEnum:: Clone 메서드'
title: ICorProfilerModuleEnum::Clone 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Clone method [.NET Framework profiling]
ms.assetid: 7dec7e36-8d88-416d-b437-abf98b76c1df
topic_type:
- apiref
ms.openlocfilehash: 0d2a235def6d3b16d661e51979742426ebe1942f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736939"
---
# <a name="icorprofilermoduleenumclone-method"></a>ICorProfilerModuleEnum::Clone 메서드

이 [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) 인터페이스의 복사본에 대 한 인터페이스 포인터를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
## <a name="parameters"></a>매개 변수  

 `ppEnum`  
 제한이 차례로이 [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) 인터페이스의 복사본을 가리키는 인터페이스 포인터에 대 한 포인터입니다. 열거자의 복사본은이 열거자와 별도로 고유한 열거형 상태를 유지 합니다. 그러나 복사본의 초기 커서 위치는이 열거자의 현재 커서 위치와 동일 합니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorProf.idl, CorProf.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [ICorProfilerModuleEnum 인터페이스](icorprofilermoduleenum-interface.md)
- [프로파일링 인터페이스](profiling-interfaces.md)
