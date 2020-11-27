---
title: invalidFunctionPointerInDelegate MDA
description: 대리자를 만들기 위해 잘못 된 함수 포인터를 전달 하는 경우 호출 되는 MDA (invalidFunctionPointerInDelegate 관리 디버깅 도우미)를 검토 합니다.
ms.date: 03/30/2017
helpviewer_keywords:
- invalidFunctionPointerInDelegate MDA
- managed debugging assistants (MDAs), invalid function pointer to delegates
- MDAs (managed debugging assistants), invalid function pointer to delegates
- function pointers, invalid
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- invalid function pointers
ms.assetid: 99ae44f1-783e-49a9-9009-24f54bbd0f09
ms.openlocfilehash: 8072d35a45cb1e0590aa5533210d0e0f86913164
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272620"
---
# <a name="invalidfunctionpointerindelegate-mda"></a>invalidFunctionPointerInDelegate MDA

`invalidFunctionPointerInDelegate` MDA(관리 디버깅 도우미)는 잘못된 함수 포인터가 네이티브 함수 포인터를 통해 대리자를 생성하도록 전달되면 활성화됩니다.  
  
## <a name="symptoms"></a>증상  

 함수 포인터를 통해 대리자를 사용할 때 액세스 위반 또는 예기치 않은 메모리 손상이 발생합니다.  
  
## <a name="cause"></a>원인  

 잘못된 함수 포인터가 지정되었습니다.  
  
## <a name="resolution"></a>해결 방법  

 유효한 함수 포인터를 지정합니다.  
  
## <a name="effect-on-the-runtime"></a>런타임에 대한 영향  

 이 MDA는 CLR에 아무런 영향을 미치지 않습니다.  
  
## <a name="output"></a>출력  

 잘못된 함수 포인터입니다.  
  
## <a name="configuration"></a>구성  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>참고 항목

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [관리 디버깅 도우미를 사용하여 오류 진단](diagnosing-errors-with-managed-debugging-assistants.md)
- [interop 마샬링](../interop/interop-marshaling.md)
