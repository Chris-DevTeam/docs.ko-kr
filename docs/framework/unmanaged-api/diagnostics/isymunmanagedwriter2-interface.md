---
title: ISymUnmanagedWriter2 인터페이스
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2
helpviewer_keywords:
- ISymUnmanagedWriter2 interface [.NET Framework debugging]
ms.assetid: 8e78faa4-cf43-44fb-a91d-94d6df692a25
topic_type:
- apiref
ms.openlocfilehash: 6feb48b7c78dda64ba372e470b83ffb14f21f2f9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683331"
---
# <a name="isymunmanagedwriter2-interface"></a>ISymUnmanagedWriter2 인터페이스

기호 작성기를 나타내며 문서, 시퀀스 포인트, 어휘 범위 및 변수를 정의하는 메서드를 제공합니다. 이 인터페이스는 [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) 인터페이스를 확장 합니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[DefineConstant2 메서드](isymunmanagedwriter2-defineconstant2-method.md)|상수 값의 이름을 정의 합니다.|  
|[DefineGlobalVariable2 메서드](isymunmanagedwriter2-defineglobalvariable2-method.md)|단일 전역 변수를 정의합니다.|  
|[DefineLocalVariable2 메서드](isymunmanagedwriter2-definelocalvariable2-method.md)|현재 어휘 범위에 단일 변수를 정의합니다.|  
  
## <a name="requirements"></a>요구 사항  

 **헤더:** CorSym, CorSym  
  
## <a name="see-also"></a>참조

- [진단 기호 저장소 인터페이스](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter 인터페이스](isymunmanagedwriter-interface.md)
- [ISymUnmanagedWriter3 인터페이스](isymunmanagedwriter3-interface.md)
