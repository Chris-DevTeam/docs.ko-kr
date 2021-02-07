---
description: ISymUnmanagedWriter::D efineLocalVariable 메서드에 대해 자세히 알아보세요.
title: ISymUnmanagedWriter::DefineLocalVariable 메서드
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineLocalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type:
- apiref
ms.openlocfilehash: cd817e3002c2a55fd8bbd7e565283752926f746b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762372"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a>ISymUnmanagedWriter::DefineLocalVariable 메서드

현재 어휘 범위에 단일 변수를 정의합니다. 이 메서드는 범위 전체의 여러 홈이 있는 동일한 이름의 변수에 대해 여러 번 호출할 수 있습니다. 그러나이 경우 `startOffset` 및 `endOffset` 매개 변수의 값이 겹치지 않아야 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT DefineLocalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a>매개 변수  

 `name`  
 진행 지역 변수 이름을 정의 하는에 대 한 포인터입니다 `WCHAR` .  
  
 `attributes`  
 진행 지역 변수 특성입니다.  
  
 `cSig`  
 진행 `ULONG32` 버퍼의 크기 (바이트)를 나타내는입니다 `signature` .  
  
 `signature`  
 진행 지역 변수 서명입니다.  
  
 `addrKind`  
 진행 주소 유형입니다.  
  
 `addr1`  
 진행 매개 변수 사양의 첫 번째 주소입니다.  
  
 `addr2`  
 진행 매개 변수 사양의 두 번째 주소입니다.  
  
 `addr3`  
 진행 매개 변수 사양의 세 번째 주소입니다.  
  
 `startOffset`  
 진행 변수의 시작 오프셋입니다. 이 매개 변수는 선택적 요소입니다. 0 인 경우이 매개 변수는 무시 되 고 변수는 전체 범위에서 정의 됩니다. 0이 아닌 값인 경우 변수는 현재 범위의 오프셋 내에 속합니다.  
  
 `endOffset`  
 진행 변수의 끝 오프셋입니다. 이 매개 변수는 선택적 요소입니다. 0 인 경우이 매개 변수는 무시 되 고 변수는 전체 범위에서 정의 됩니다. 0이 아닌 값인 경우 변수는 현재 범위의 오프셋 내에 속합니다.  
  
## <a name="return-value"></a>Return Value  

 메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 또는 일부 다른 오류 코드입니다.  
  
## <a name="requirements"></a>요구 사항  

 **헤더:** CorSym, CorSym  
  
## <a name="see-also"></a>참고 항목

- [ISymUnmanagedWriter 인터페이스](isymunmanagedwriter-interface.md)
- [DefineGlobalVariable 메서드](isymunmanagedwriter-defineglobalvariable-method.md)
- [DefineLocalVariable2 메서드](isymunmanagedwriter2-definelocalvariable2-method.md)
