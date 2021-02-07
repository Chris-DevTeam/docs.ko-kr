---
description: '자세히 알아보기: ICLRDataTarget2:: AllocVirtual 메서드'
title: ICLRDataTarget2::AllocVirtual 메서드
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.AllocVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::AllocVirtual
helpviewer_keywords:
- ICLRDataTarget2::AllocVirtual method [.NET Framework debugging]
- AllocVirtual method [.NET Framework debugging]
ms.assetid: e3226230-964b-47fb-9f53-d6fdbeda1e9e
topic_type:
- apiref
ms.openlocfilehash: d81474e4067599178285b6fa876919298617919d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729343"
---
# <a name="iclrdatatarget2allocvirtual-method"></a>ICLRDataTarget2::AllocVirtual 메서드

이 대상 프로세스의 주소 공간에서 메모리를 할당 하기 위해 CLR (공용 언어 런타임) 데이터 액세스 서비스에 의해 호출 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `addr`  
 진행 `CLRDATA_ADDRESS` 할당할 메모리의 요청 된 시작 주소를 지정 하는 값입니다.  
  
 `size`  
 진행 할당할 메모리의 크기 (바이트)입니다.  
  
 `typeFlags`  
 진행 메모리 할당을 제어 하는 플래그입니다. Win32 함수를 참조 하세요 `VirtualAlloc` .  
  
 `protectFlags`  
 진행 할당 된 메모리에 대 한 보호 특성입니다. Win32 함수를 참조 하세요 `VirtualAlloc` .  
  
 `virt`  
 제한이 `CLRDATA_ADDRESS` 할당 된 메모리의 실제 시작 주소를 지정 하는 값에 대 한 포인터입니다.  
  
## <a name="remarks"></a>설명  

 `AllocVirtual`메서드는 Win32 함수에 대 한 논리 래퍼로 사용 `VirtualAlloc` 됩니다.  
  
 이 메서드는 디버깅 애플리케이션의 작성자가 구현합니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** ClrData .idl, ClrData .h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [ICLRDataTarget2 인터페이스](iclrdatatarget2-interface.md)
- [FreeVirtual 메서드](iclrdatatarget2-freevirtual-method.md)
