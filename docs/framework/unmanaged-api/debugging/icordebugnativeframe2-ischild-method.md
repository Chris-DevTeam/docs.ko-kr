---
description: '자세히 알아보기: ICorDebugNativeFrame2:: IsChild 메서드'
title: ICorDebugNativeFrame2::IsChild 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsChild Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsChild
helpviewer_keywords:
- IsChild method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsChild method [.NET Framework debugging]
ms.assetid: 9e2aae09-49cb-4fbd-81e5-e29cd864a88b
topic_type:
- apiref
ms.openlocfilehash: 7c698c5a49ee445b4ba9c591c96f700f86a86c32
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722297"
---
# <a name="icordebugnativeframe2ischild-method"></a>ICorDebugNativeFrame2::IsChild 메서드

현재 프레임이 자식 프레임 인지 여부를 확인 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a>매개 변수  

 `pIsChild`  
 제한이 현재 프레임이 자식 프레임 인지 여부를 지정 하는 부울 값입니다.  
  
## <a name="return-value"></a>Return Value  

 이 메서드는 다음과 같은 특정 HRESULT뿐만 아니라 메서드 오류를 나타내는 HRESULT 오류도 반환합니다.  
  
|HRESULT|설명|  
|-------------|-----------------|  
|S_OK|자식 상태가 성공적으로 반환 되었습니다.|  
|E_FAIL|자식 상태를 반환할 수 없습니다.|  
|E_INVALIDARG|`pIsChild`가 null입니다.|  
  
## <a name="exceptions"></a>예외  
  
## <a name="remarks"></a>설명  

 메서드는 `IsChild` `true` 메서드를 호출 하는 프레임 개체가 다른 프레임의 자식인 경우를 반환 합니다. 이 경우 [IsMatchingParentFrame](icordebugnativeframe2-ismatchingparentframe-method.md) 메서드를 사용 하 여 프레임이 부모 인지 여부를 확인 합니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [ICorDebugNativeFrame2 인터페이스](icordebugnativeframe2-interface.md)
- [디버깅 인터페이스](debugging-interfaces.md)
- [디버깅](index.md)
