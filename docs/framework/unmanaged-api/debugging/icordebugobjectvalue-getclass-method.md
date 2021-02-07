---
description: '자세히 알아보기: ICorDebugObjectValue:: GetClass 메서드'
title: ICorDebugObjectValue::GetClass 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetClass
helpviewer_keywords:
- ICorDebugObjectValue::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 5be25292-8357-445f-a09b-f997c0de761c
topic_type:
- apiref
ms.openlocfilehash: 4ea6a47814777da934aa14bba947a047c075396c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722219"
---
# <a name="icordebugobjectvaluegetclass-method"></a>ICorDebugObjectValue::GetClass 메서드

이 개체 값의 클래스를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `ppClass`  
 제한이 이 "ICorDebugObjectValue" 개체로 표시 되는 개체 값의 클래스를 나타내는 "ICorDebugClass" 개체의 주소에 대 한 포인터입니다.  
  
## <a name="remarks"></a>설명  

 `GetClass`및 [ICorDebugValue:: GetType](icordebugvalue-gettype-method.md) 메서드는 각각 값의 형식에 대 한 정보를 반환 하며, 둘 다 제네릭 인식 [ICorDebugValue2:: GetExactType](icordebugvalue2-getexacttype-method.md)로 대체 됩니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고 항목
