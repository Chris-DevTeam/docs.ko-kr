---
description: '자세히 알아보기: ICorDebugAppDomain2:: GetArrayOrPointerType 메서드'
title: ICorDebugAppDomain2::GetArrayOrPointerType 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetArrayOrPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type:
- apiref
ms.openlocfilehash: e42d105e807bdb8c81f2d6f8ef6c2f65a4081d98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754227"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a>ICorDebugAppDomain2::GetArrayOrPointerType 메서드

지정 된 형식의 배열 또는 지정 된 형식에 대 한 포인터 또는 참조를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `elementType`  
 진행 만들 기본 네이티브 형식 (배열, 포인터 또는 참조)을 지정 하는 CorElementType 열거형의 값입니다.  
  
 `nRank`  
 진행 배열의 차수 (차원의 수)입니다. `elementType`가 포인터나 참조 형식을 지정 하는 경우이 값은 0 이어야 합니다.  
  
 `pTypeArg`  
 진행 만들 배열, 포인터 또는 참조의 형식을 나타내는 ICorDebugType 개체에 대 한 포인터입니다.  
  
 `ppType`  
 제한이 `ICorDebugType` 생성 된 배열, 포인터 형식 또는 참조 형식을 나타내는 개체의 주소에 대 한 포인터입니다.  
  
## <a name="remarks"></a>설명  

 *ElementType* 의 값은 다음 중 하나 여야 합니다.  
  
- ELEMENT_TYPE_PTR  
  
- ELEMENT_TYPE_BYREF  
  
- ELEMENT_TYPE_ARRAY 또는 ELEMENT_TYPE_SZARRAY  
  
 *ElementType* 의 값이 ELEMENT_TYPE_PTR 또는 ELEMENT_TYPE_BYREF 이면 *n rank* 는 0 이어야 합니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
