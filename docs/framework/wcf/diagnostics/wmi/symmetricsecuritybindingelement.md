---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: c618b5b41790b04a84b4c50fe47baa2c0cb05ab2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274103"
---
# <a name="symmetricsecuritybindingelement"></a>SymmetricSecurityBindingElement

SymmetricSecurityBindingElement  
  
## <a name="syntax"></a>구문  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a>메서드  

 SymmetricSecurityBindingElement 클래스는 메서드를 정의하지 않습니다.  
  
## <a name="properties"></a>속성  

 SymmetricSecurityBindingElement 클래스에는 다음과 같은 속성이 있습니다.  
  
### <a name="messageprotectionorder"></a>MessageProtectionOrder  

 데이터 형식: 문자열  
  
 액세스 형식: 읽기 전용  
  
 이 바인딩의 메시지 암호화 및 서명 순서입니다.  
  
### <a name="requiresignatureconfirmation"></a>RequireSignatureConfirmation  

 데이터 형식: boolean  
  
 액세스 형식: 읽기 전용  
  
 바인딩에 서명 확인이 필요한지 여부입니다.  
  
## <a name="requirements"></a>요구 사항  
  
|MOF|Servicemodel.mof에 선언되어 있습니다.|  
|---------|-----------------------------------|  
|네임스페이스|root\ServiceModel에 정의되어 있습니다.|  
  
## <a name="see-also"></a>참고 항목

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
