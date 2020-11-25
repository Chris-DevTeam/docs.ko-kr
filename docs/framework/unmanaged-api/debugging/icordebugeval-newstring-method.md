---
title: ICorDebugEval::NewString 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type:
- apiref
ms.openlocfilehash: c2d29a0cc344539bf515793c071fe839aa441ebc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729722"
---
# <a name="icordebugevalnewstring-method"></a>ICorDebugEval::NewString 메서드

지정 된 내용을 사용 하 여 새 문자열 인스턴스를 할당 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `string`  
 진행 문자열의 내용에 대 한 포인터입니다.  
  
## <a name="remarks"></a>설명  

 문자열은 항상 스레드가 현재 실행 중인 응용 프로그램 도메인에 만들어집니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
