---
title: 스택 ETW 이벤트
description: 이벤트가 발생 한 후 스택 추적을 생성 하기 위해 다른 이벤트와 함께 사용 해야 하는 stack ETW 이벤트에 대해 읽어 보십시오.
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
ms.openlocfilehash: 3b890e587abd5cb1b7315fe41897f24638fd4604
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236210"
---
# <a name="stack-etw-event"></a>스택 ETW 이벤트

스택 이벤트는 이벤트가 발생한 후 스택 추적을 생성하기 위해 다른 이벤트와 함께 사용해야 합니다. 런타임 공급자가 사용하도록 설정된 경우에 기록됩니다. 다른 런타임 이벤트가 발생할 때마다 이벤트가 발생하기 때문에 빈도가 매우 높은 이벤트입니다. 이러한 이유로 이 이벤트를 사용할 때는 주의하는 것이 좋습니다.  
  
 다음 표에서는 키워드와 수준을 보여 줍니다. 자세한 내용은 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md)을 참조하세요.  
  
|이벤트를 발생시키기 위한 키워드|Level|  
|-----------------------------------|-----------|  
|`StackKeyword`(0x40000000)|LogAlways(0)|  
  
 다음 표에서는 이벤트 정보를 보여 줍니다.  
  
|이벤트|이벤트 ID|발생 시기|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|82|다른 이벤트와 더불어 이벤트 다음에 스택 추적을 생성합니다.|  
  
 다음 표에서는 이벤트 데이터를 보여 줍니다.  
  
|필드 이름|데이터 형식|Description|  
|----------------|---------------|-----------------|  
|ClrInstanceID|win:Uint16|고유한 런타임 식별자입니다.|  
|Reserved1|win:UInt8|예약되어 있습니다.|  
|Reserved2|win:UInt8|예약되어 있습니다.|  
|FrameCount|win:UInt32|스택 추적의 프레임 수입니다.|  
|스택|win:Pointer|명령 포인터의 열입니다.|  
  
## <a name="see-also"></a>참고 항목

- [CLR ETW 이벤트](clr-etw-events.md)
