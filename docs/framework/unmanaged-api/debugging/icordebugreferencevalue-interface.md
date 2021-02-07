---
description: '자세히 알아보기: ICorDebugReferenceValue 인터페이스'
title: ICorDebugReferenceValue 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue
helpviewer_keywords:
- ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type:
- apiref
ms.openlocfilehash: e516b1178b4f4268472dedd37d6443e673e16af6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690966"
---
# <a name="icordebugreferencevalue-interface"></a>ICorDebugReferenceValue 인터페이스

개체에 대 한 참조 인 값을 관리 하는 메서드를 제공 합니다. 즉,이 인터페이스는 포인터를 관리 하는 메서드를 제공 합니다. 이 인터페이스는 "ICorDebugValue"를 구현 합니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[Dereference 메서드](icordebugreferencevalue-dereference-method.md)|참조 되는 개체를 가져옵니다.|  
|[DereferenceStrong 메서드](icordebugreferencevalue-dereferencestrong-method.md)|구현되지 않았습니다. 이 메서드를 호출 하지 마십시오.|  
|[GetValue 메서드](icordebugreferencevalue-getvalue-method.md)|참조 된 개체의 현재 메모리 주소를 가져옵니다.|  
|[IsNull 메서드](icordebugreferencevalue-isnull-method.md)|가 null 값 인지 여부를 나타내는 값을 가져옵니다 .이 값이 이면이 `ICorDebugReferenceValue` `ICorDebugReferenceValue` 개체를 가리키지 않습니다.|  
|[SetValue 메서드](icordebugreferencevalue-setvalue-method.md)|현재 메모리 주소를 설정 합니다. 즉,이 메서드는 개체를 `ICorDebugReferenceValue` 가리키도록 설정 합니다.|  
  
## <a name="remarks"></a>설명  

 디버깅 된 프로세스가 계속 될 때 CLR (공용 언어 런타임)에서 개체에 대 한 가비지 수집을 수행할 수 있습니다. 가비지 컬렉션은 메모리에서 개체를 이동할 수 있습니다. 는 가비지 컬렉션과 `ICorDebugReferenceValue` 상호 작용 하 여 가비지 수집 후 정보를 업데이트 하거나 가비지 수집 전에 암시적으로 무효화 됩니다.  
  
 `ICorDebugReferenceValue`디버깅 된 프로세스가 계속 되 면 개체가 암시적으로 무효화 될 수 있습니다. 파생 된 "ICorDebugHandleValue"은 명시적으로 해제 되거나 노출 될 때까지 무효화 되지 않습니다.  
  
> [!NOTE]
> 이 인터페이스는 크로스 시스템 또는 크로스 프로세스 원격 호출을 지원하지 않습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [디버깅 인터페이스](debugging-interfaces.md)
