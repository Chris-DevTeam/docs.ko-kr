---
description: '자세히 알아보기: ICorDebug:: Initialize 메서드'
title: ICorDebug::Initialize 메서드
ms.date: 03/30/2017
api_name:
- ICorDebug.Initialize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Initialize
helpviewer_keywords:
- Initialize method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Initialize method [.NET Framework debugging]
ms.assetid: 6fae3b23-5c9f-47c0-85d8-6bb75e050786
topic_type:
- apiref
ms.openlocfilehash: 6b6ddd8c1c21470477420909bcf75906b5731ee6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791597"
---
# <a name="icordebuginitialize-method"></a>ICorDebug::Initialize 메서드

초기화는 `ICorDebug` 개체입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a>설명  

 디버거는 `Initialize` 만들 때를 호출 하 여 디버깅 서비스를 초기화 해야 합니다. 이 메서드는의 다른 메서드를 호출 하기 전에 호출 해야 합니다 `ICorDebug` .  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [ICorDebug 인터페이스](icordebug-interface.md)
