---
description: '자세히 알아보기: ICorDebugAppDomain3:: GetCachedWinRTTypesForIIDs 메서드'
title: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type:
- apiref
ms.openlocfilehash: 76b93cdb8c465935a4aaf36090ee44f2b6253a3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754175"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs 메서드

인터페이스 식별자를 기반으로 응용 프로그램 도메인의 캐시 된 Windows 런타임 형식에 대 한 열거자를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `cReqTypes`  
 진행 필요한 형식의 수입니다.  
  
 `iidsToResolve`  
 진행 검색할 Windows 런타임 형식의 관리 되는 표현에 해당 하는 인터페이스 식별자가 포함 된 배열에 대 한 포인터입니다.  
  
 `ppTypesEnum`  
 제한이 의 인터페이스 식별자를 기반으로 검색 된 Windows 런타임 형식의 캐시 된 관리 표현을 열거할 수 있도록 하는 "ICorDebugTypeEnum" 인터페이스 개체의 주소에 대 한 포인터입니다 `iidsToResolve` .  
  
## <a name="remarks"></a>설명  

 메서드가 특정 인터페이스 식별자에 대 한 정보를 검색 하지 못할 경우, "ICorDebugTypeEnum" 컬렉션의 해당 항목에는 `ELEMENT_TYPE_END` 데이터 검색 문제로 인 한 오류의 형식이 나 `ELEMENT_TYPE_VOID` 알 수 없는 인터페이스 식별자가 포함 됩니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:** Windows 런타임  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [ICorDebugAppDomain3 인터페이스](icordebugappdomain3-interface.md)
