---
title: 222 - OperationFailed
ms.date: 03/30/2017
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
ms.openlocfilehash: 64b41ee78e943ca16eaa791133454ec62ccf6ed8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263089"
---
# <a name="222---operationfailed"></a>222 - OperationFailed

## <a name="properties"></a>속성  
  
|||  
|-|-|  
|ID|222|  
|키워드|EndToEndMonitoring, HealthMonitoring, 문제 해결, ServiceModel|  
|Level|경고|  
|채널|Microsoft-Windows-애플리케이션 서버-애플리케이션/분석|  
  
## <a name="description"></a>Description  

 이 이벤트는 서비스 모델의 기본 `OperationInvoker`에서 해당 메서드를 호출하는 동안 예외가 발생하면 내보내집니다. `FaultException`에서 파생되는 예외가 발생할 경우에는 이 이벤트가 내보내지지 않습니다.  
  
## <a name="message"></a>메시지  

 OperationInvoker의 호출을 받은 '%1' 메서드에서 처리되지 않은 예외가 발생했습니다. 메서드 호출 기간은 '%2'밀리초입니다.  
  
## <a name="details"></a>세부 정보  
  
|데이터 항목 이름|데이터 항목 형식|Description|  
|--------------------|--------------------|-----------------|  
|메서드 이름|`xs:string`|`OperationInvoker`의 호출을 받은 메서드의 CLR 이름입니다.|  
|기간|`xs:long`|`OperationInvoker`가 메서드를 호출하는 데 걸린 시간(밀리초)입니다.|  
|HostReference|`xs:string`|웹 호스팅 서비스의 경우 이 필드는 웹 계층의 서비스를 고유하게 식별합니다. 해당 형식은 ' 웹 사이트 이름 응용 프로그램 가상 경로&#124;서비스 가상 경로&#124;ServiceName '으로 정의 됩니다. 예: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName에서 반환되는 문자열입니다.|
