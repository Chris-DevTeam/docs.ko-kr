---
description: '자세히 알아보기: ICorDebugInstanceFieldSymbol:: GetName 메서드'
title: ICorDebugInstanceFieldSymbol::GetName 메서드
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
ms.openlocfilehash: 9cc2106d1527aa0b4d9e5c52115b703ffe55037f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791194"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a>ICorDebugInstanceFieldSymbol::GetName 메서드

인스턴스 필드의 이름을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `cchName`  
 [in] `szName` 버퍼의 문자 수입니다.  
  
 `pcchName`  
 [out] `szName` 버퍼에 실제로 기록된 문자 수에 대한 포인터입니다.  
  
 `szName`  
 [out] 반환된 이름을 저장하는 문자 배열입니다.  
  
## <a name="remarks"></a>설명  
  
> [!NOTE]
> 이 메서드는 .NET 네이티브에서만 사용할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [ICorDebugInstanceFieldSymbol 인터페이스](icordebuginstancefieldsymbol-interface.md)
- [디버깅 인터페이스](debugging-interfaces.md)
