---
description: '자세히 알아보기: ICorDebugProcess5:: EnumerateHeap 메서드'
title: ICorDebugProcess5::EnumerateHeap 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type:
- apiref
ms.openlocfilehash: b43e7993b114ed64d009f91746ea987198edde74
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722037"
---
# <a name="icordebugprocess5enumerateheap-method"></a>ICorDebugProcess5::EnumerateHeap 메서드

관리 되는 힙의 개체에 대 한 열거자를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `ppObject`  
 제한이 관리 되는 힙에 있는 개체의 열거자 인 [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface 개체의 주소에 대 한 포인터입니다.  
  
## <a name="remarks"></a>설명  

 메서드를 호출 하기 전에 `ICorDebugProcess5::EnumerateHeap` [ICorDebugProcess5:: GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) 메서드를 호출 하 고 `areGCStructuresValid` 반환 된 [COR_HEAPINFO](cor-heapinfo-structure.md) 개체의 필드 값을 검사 하 여 현재 상태에서 가비지 컬렉션 힙을 열거 가능 하 게 해야 합니다. 또한은 `ICorDebugProcess5::EnumerateHeap` `E_FAIL` 프로세스 수명 중 너무 일찍 연결 하는 경우에는 관리 되는 힙의 메모리를 할당 하기 전에를 반환 합니다.  
  
 [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface 개체는 개체 [COR_HEAPOBJECT](cor-heapobject-structure.md) 열거할 수 있도록 하는 ICorDebugEnum 인터페이스에서 파생 된 표준 열거자입니다. 이 메서드는 모든 개체에 대 한 정보를 제공 하는 [COR_HEAPOBJECT](cor-heapobject-structure.md) 인스턴스로 [ICorDebugHeapEnum](icordebugheapenum-interface.md) collection 개체를 채웁니다. 컬렉션에는 개체에 포함 되어 있지 않지만 가비지 수집기에서 아직 수집 되지 않은 개체에 대 한 정보를 제공 하는 [COR_HEAPOBJECT](cor-heapobject-structure.md) 인스턴스가 포함 될 수도 있습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [ICorDebugProcess5 인터페이스](icordebugprocess5-interface.md)
- [디버깅 인터페이스](debugging-interfaces.md)
