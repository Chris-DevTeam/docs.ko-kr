---
description: '자세히 알아보기: ICorDebugFrame:: GetFunction 메서드'
title: ICorDebugFrame::GetFunction 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetFunction method [.NET Framework debugging]
ms.assetid: 879d2311-0ff1-4616-a8b3-959ea5868b2e
topic_type:
- apiref
ms.openlocfilehash: 0309a066f686e55d086de1cbb040eea58e031df3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692994"
---
# <a name="icordebugframegetfunction-method"></a>ICorDebugFrame::GetFunction 메서드

이 스택 프레임과 연결 된 코드를 포함 하는 함수를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `ppFunction`  
 제한이 이 스택 프레임과 연결 된 코드를 포함 하는 함수를 나타내는 ICorDebugFunction 개체의 주소에 대 한 포인터입니다.  
  
## <a name="remarks"></a>설명  

 `GetFunction`프레임이 특정 함수와 연결 되어 있지 않으면 메서드가 실패할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
