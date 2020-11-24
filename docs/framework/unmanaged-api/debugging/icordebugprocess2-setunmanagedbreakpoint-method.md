---
title: ICorDebugProcess2::SetUnmanagedBreakpoint 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint
helpviewer_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint method [.NET Framework debugging]
- SetUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 93829d15-d942-4e2d-b7a4-dfc9d7fb96be
topic_type:
- apiref
ms.openlocfilehash: 1a883878107569145b97d5793f0628efefb13545
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675245"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a>ICorDebugProcess2::SetUnmanagedBreakpoint 메서드

지정 된 네이티브 이미지 오프셋에서 관리 되지 않는 중단점을 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `address`  
 진행 `CORDB_ADDRESS` 네이티브 이미지 오프셋을 지정 하는 개체입니다.  
  
 `bufsize`  
 진행 배열의 크기 (바이트) `buffer` 입니다.  
  
 `buffer`  
 제한이 중단점으로 대체 되는 opcode를 포함 하는 배열입니다.  
  
 `bufLen`  
 제한이 배열에서 반환 된 바이트 수에 대 한 포인터 `buffer` 입니다.  
  
## <a name="remarks"></a>설명  

 네이티브 이미지 오프셋이 CLR (공용 언어 런타임) 내에 있는 경우 중단점은 무시 됩니다. 이렇게 하면 디버거에서 중단점이 설정 된 경우 CLR에서 대역 외 중단점 디스패치를 방지할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
