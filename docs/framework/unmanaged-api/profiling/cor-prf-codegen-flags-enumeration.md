---
description: '다음에 대 한 자세한 정보: 열거형 COR_PRF_CODEGEN_FLAGS'
title: COR_PRF_CODEGEN_FLAGS 열거형
ms.date: 03/30/2017
api_name:
- COR_PRF_CODEGEN_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODEGEN_FLAGS
helpviewer_keywords:
- COR_PRF_CODEGEN_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 3e184022-0247-4824-a23d-6b29593d8d01
topic_type:
- apiref
ms.openlocfilehash: 40ddaa77047e0b1daa743b512f21ba7643127230
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649178"
---
# <a name="cor_prf_codegen_flags-enumeration"></a>COR_PRF_CODEGEN_FLAGS 열거형

[ICorProfilerFunctionControl:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) 메서드를 사용 하 여 설정할 수 있는 코드 생성 플래그를 정의 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a>구성원  
  
|멤버|설명|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|이 함수의 본문에는 함수가 인라인 되지 않습니다. 그러나 함수 자체가 해당 호출자에 게 인라인 될 수 있습니다.|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|이 함수의 본문에 대해 모든 최적화를 사용할 수 없습니다. 그러나 함수 자체는 여전히 해당 호출자에 게 인라인 될 수 있습니다.|  
  
## <a name="remarks"></a>설명  

 `COR_PRF_CODEGEN_FLAGS`열거형은 [ICorProfilerFunctionControl:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) 메서드에서 프로파일러를 사용 하 여 JIT 다시 컴파일된 함수의 코드 생성을 제어할 수 있도록 합니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorProf.idl, CorProf.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [프로파일링 열거형](profiling-enumerations.md)
