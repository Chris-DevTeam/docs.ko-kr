---
title: CorGCReferenceType 열거형
ms.date: 03/30/2017
api_name:
- CorGCReferenceType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorGCReferenceType
helpviewer_keywords:
- CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type:
- apiref
ms.openlocfilehash: e2903637faa11a3c0a62080cc6fafcf1fc668a56
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704996"
---
# <a name="corgcreferencetype-enumeration"></a>CorGCReferenceType 열거형

가비지가 수집될 개체의 소스를 식별합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef enum {  
    CorHandleStrong = 1,  
    CorHandleStrongPinning = 2,  
    CorHandleWeakShort = 4,  
    CorHandleWeakRefCount = 8,  
    CorHandleStrongRefCount = 32,  
    CorHandleStrongDependent = 64,  
    CorHandleStrongAsyncPinned = 128,  
    CorHandleStrongSizedByref = 256,  
  
    CorReferenceStack = 0x80000001,  
    CorReferenceFinalizer = 0x80000002,  
  
    CorHandleStrongOnly = 0x1E3,  
    CorHandleWeakOnly = 0xC,  
    CorHandleAll = 0x7FFFFFFF  
} CorGCReferenceType  
```  
  
## <a name="members"></a>멤버  
  
|멤버 이름|설명|  
|-----------------|-----------------|  
|`CorHandleStrong`|개체 참조 테이블의 강력한 참조에 대한 핸들입니다.|  
|`CorHandleStrongPinning`|개체 핸들 테이블에서 고정 된 강한 참조에 대 한 핸들입니다.|  
|`CorHandleWeakShort`|개체 핸들 테이블에서 weak reference에 대 한 핸들입니다.|  
|`CorHandleWeakRefCount`|개체 핸들 테이블에서 weak reference 계산 된 개체에 대 한 핸들입니다.|  
|`CorHandleStrongRefCount`|개체 핸들 테이블에서 참조 횟수가 계산 되는 개체에 대 한 핸들입니다.|  
|`CorHandleStrongDependent`|개체 핸들 테이블의 종속 개체에 대 한 핸들입니다.|  
|`CorHandleStrongAsyncPinned`|개체 핸들 테이블의 비동기 고정된 개체입니다.|  
|`CorHandleStrongSizedByref`|가비지 컬렉션 시 모든 개체 및 개체 루트의 집합 클로저의 대략적인 크기를 유지하는 강력한 핸들입니다.|  
|`CorReferenceStack`|관리 되는 스택의 참조입니다.|  
|`CorReferenceFinalizer`|종료자 큐의 참조입니다.|  
|CorHandleStrongOnly|핸들 테이블에서 강력한 참조만 반환 합니다. 이 값은 [ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) 메서드에만 사용 됩니다.|  
|`CorHandleWeakOnly`|핸들 테이블에서 약한 참조만 반환 합니다. 이 값은 [ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) 메서드에만 사용 됩니다.|  
|`CorHandleAll`|핸들 테이블의 모든 참조를 반환 합니다. 이 값은 [ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) 메서드에만 사용 됩니다.|  
  
## <a name="remarks"></a>설명  

 열거형은 다음과 `CorGCReferenceType` 같이 사용 됩니다.  
  
- `type` [COR_GC_REFERENCE](cor-gc-reference-structure.md) 구조체의 필드 값으로 참조 또는 핸들의 원본을 나타냅니다.  
  
- `types` [ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) 메서드에 대 한 인수로, 열거형에 포함할 핸들의 형식을 지정 합니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>참조

- [디버깅 열거형](debugging-enumerations.md)
