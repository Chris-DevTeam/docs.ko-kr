---
title: notMarshalable MDA
description: 호출이 서비스 되지 않거나 COM 인터페이스 포인터에 대 한 잘못 된 컨텍스트에서 발생 하는 경우에 활성화할 수 있는 notMarshalable 수 있는 관리 디버깅 도우미를 검토 합니다.
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), interface pointer not marshalable
- interface pointer not marshalable MDA
- MDAs (managed debugging assistants), interface pointer not marshalable
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- marshalable interface pointers
- MDAs (managed debugging assistants), marshaling
- notMarshalable MDA
ms.assetid: 96e7b2c1-843f-4d64-b519-740c3a18b50a
ms.openlocfilehash: 344c275d8645b16de3ecb06517297df06323ced4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254560"
---
# <a name="notmarshalable-mda"></a>notMarshalable MDA

`notMarshalable` MDA(관리 디버깅 도우미)는 CLR(공용 언어 런타임)이 컨텍스트 간에 인터페이스를 마샬링하는 동안 등록된 유효한 프록시/스텁이 없는 COM 인터페이스 포인터 또는 잘못된 `IMarshal` 인터페이스 구현을 발견할 때 활성화됩니다.  
  
## <a name="symptoms"></a>증상  

 호출이 서비스되지 않거나 COM 인터페이스 포인터에 대한 잘못된 컨텍스트에서 호출이 발생합니다.  
  
## <a name="cause"></a>원인  

 컨텍스트 간에 인터페이스를 마샬링하는 동안 등록된 유효한 프록시/스텁이 없거나 잘못된 `IMarshal`이 있습니다.  
  
## <a name="resolution"></a>해결 방법  

 프록시 스텁이 등록되어 있고 `IMarshal` 구현이 유효한지 확인합니다.  
  
## <a name="effect-on-the-runtime"></a>런타임에 대한 영향  

 이 MDA는 런타임에 아무런 영향을 미치지 않습니다.  
  
## <a name="output"></a>출력  

 문제를 설명하는 메시지입니다.  
  
## <a name="configuration"></a>구성  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>참고 항목

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [관리 디버깅 도우미를 사용하여 오류 진단](diagnosing-errors-with-managed-debugging-assistants.md)
- [interop 마샬링](../interop/interop-marshaling.md)
