---
description: '자세히 알아보기: ICorDebugModule:: GetProcess 메서드'
title: ICorDebugModule::GetProcess 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetProcess method [.NET Framework debugging]
ms.assetid: 5e13446c-0271-446c-924a-9072c0e6eeae
topic_type:
- apiref
ms.openlocfilehash: eb8497ac8ec6913fe079d6f5f148d3769bf6633a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691629"
---
# <a name="icordebugmodulegetprocess-method"></a>ICorDebugModule::GetProcess 메서드

이 모듈의 프로세스를 포함 하는을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `ppProcess`  
 제한이 이 모듈을 포함 하는 프로세스를 나타내는 ICorDebugProcess 개체의 주소에 대 한 포인터입니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
