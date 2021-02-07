---
description: '자세히 알아보기: ICorDebugGenericValue:: GetValue 메서드'
title: ICorDebugGenericValue::GetValue 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::GetValue
helpviewer_keywords:
- ICorDebugGenericValue::GetValue method [.NET Framework debugging]
- GetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: 4e95d7cb-144d-4ccf-8a69-d605f4744be2
topic_type:
- apiref
ms.openlocfilehash: 9c8459ce6a9fb59e934b1ebd355aa091a37b2d7b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661066"
---
# <a name="icordebuggenericvaluegetvalue-method"></a>ICorDebugGenericValue::GetValue 메서드

이 제네릭의 값을 지정 된 버퍼에 복사 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `pTo`  
 제한이 이 ICorDebugGenericValue 개체가 나타내는 값에 대 한 포인터입니다. 값은 단순 형식 또는 참조 형식 (즉, 포인터) 일 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
