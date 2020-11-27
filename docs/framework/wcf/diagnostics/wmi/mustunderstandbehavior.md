---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 9cac7192d5c34de55fe0bd6a4921a41387e985f8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250439"
---
# <a name="mustunderstandbehavior"></a>MustUnderstandBehavior

MustUnderstandBehavior  
  
## <a name="syntax"></a>구문  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a>메서드  

 MustUnderstandBehavior 클래스는 메서드를 정의하지 않습니다.  
  
## <a name="properties"></a>속성  

 MustUnderstandBehavior 클래스에는 다음과 같은 속성이 있습니다.  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  

 데이터 형식: boolean  
  
 액세스 형식: 읽기 전용  
  
 이 속성이 `true`인 경우 처리되지 않은 `MustUnderstand` 특성이 있는 모든 SOAP 헤더로 인해 예외를 throw하는 동작이 발생합니다.  
  
## <a name="requirements"></a>요구 사항  
  
|MOF|Servicemodel.mof에 선언되어 있습니다.|  
|---------|-----------------------------------|  
|네임스페이스|root\ServiceModel에 정의되어 있습니다.|  
  
## <a name="see-also"></a>참고 항목

- <xref:System.ServiceModel.Description.MustUnderstandBehavior>
