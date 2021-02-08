---
description: '자세히 알아보기: ICorDebugGCReferenceEnum 인터페이스'
title: ICorDebugGCReferenceEnum 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum
helpviewer_keywords:
- ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type:
- apiref
ms.openlocfilehash: ad4a61cdc2b30fb4c8e2be500eae878327c6b449
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801295"
---
# <a name="icordebuggcreferenceenum-interface"></a>ICorDebugGCReferenceEnum 인터페이스

가비지 수집되는 개체에 대한 열거자를 제공합니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[Next 메서드](icordebuggcreferenceenum-next-method.md)|가비지 수집 되는 개체에 대 한 정보를 포함 하는 지정 된 수의 [COR_GC_REFERENCE](cor-gc-reference-structure.md) 인스턴스를 가져옵니다.|  
  
## <a name="remarks"></a>설명  

 이 `ICorDebugGCReferenceEnum` 인터페이스는 "ICorDebugEnum" 인터페이스를 구현 합니다.  
  
 `ICorDebugGCReferenceEnum` [ICorDebugProcess5:: EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) 메서드를 호출 하 여 인스턴스가 [COR_GC_REFERENCE](cor-gc-reference-structure.md) 인스턴스로 채워집니다. [ICorDebugGCReference:: Next](icordebuggcreferenceenum-next-method.md) 메서드를 호출 하 여 [COR_GC_REFERENCE](cor-gc-reference-structure.md) 개체를 열거할 수 있습니다.  
  
 이 메서드로 채워진 컬렉션의 [COR_GC_REFERENCE](cor-gc-reference-structure.md) 개체는 다음과 같은 세 가지 개체를 나타냅니다.  
  
- 모든 관리 되는 스택의 개체 여기에는 공용 언어 런타임에서 만든 개체 뿐만 아니라 관리 코드의 라이브 참조도 포함 됩니다.  
  
- 핸들 테이블의 개체입니다. 여기에는 모듈의 강력한 참조 ( `HNDTYPE_STRONG` 및 `HNDTYPE_REFCOUNT` ) 및 정적 변수가 포함 됩니다.  
  
- 종료자 큐의 개체입니다. 종료자는 종료 자가 실행 될 때까지 개체를 큐에 대기 합니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [디버깅 인터페이스](debugging-interfaces.md)
