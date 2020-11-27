---
title: '방법: 동일한 형식의 여러 보안 토큰 사용'
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
ms.openlocfilehash: 7374eebb9e42ef761b7ab8980b3eacf4d5671e6d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280704"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a>방법: 동일한 형식의 여러 보안 토큰 사용

- .NET Framework 3.0에서 클라이언트 메시지는 지정 된 형식의 토큰을 하나만 포함 합니다. 이제 클라이언트 메시지에 특정 형식의 여러 토큰을 포함할 수 있습니다. 이 항목에서는 동일한 형식의 토큰을 클라이언트 메시지에 여러 개 포함하는 방법을 보여 줍니다.  
  
- 서비스는 이러한 방식으로 구성할 수 없습니다. 서비스는 지원하는 토큰을 하나만 포함할 수 있습니다.  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a>동일한 형식의 보안 토큰을 여러 개 사용하려면  
  
1. 바인딩 요소로 채울 빈 바인딩 요소 컬렉션을 만듭니다.  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2. <xref:System.ServiceModel.Channels.SecurityBindingElement>를 호출하여 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>를 만듭니다.  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3. <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> 컬렉션을 만듭니다.  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4. 컬렉션에 SAML 토큰을 추가합니다.  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5. <xref:System.ServiceModel.Channels.SecurityBindingElement>에 컬렉션을 추가합니다.  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6. 바인딩 요소 컬렉션에 바인딩 요소를 추가합니다.  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7. 바인딩 요소 컬렉션에서 만들어진 새로운 사용자 지정 바인딩을 반환합니다.  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a>예제  

 다음은 앞의 절차에서 설명한 전체 메서드입니다.  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
