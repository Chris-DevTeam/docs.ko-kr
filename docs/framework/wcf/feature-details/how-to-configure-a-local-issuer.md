---
description: '자세한 정보: 방법: 로컬 발급자 구성'
title: '방법: 로컬 발급자 구성'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
ms.openlocfilehash: 1c950c2bbbb55954fc65e35632523ea14ee3ac00
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780169"
---
# <a name="how-to-configure-a-local-issuer"></a>방법: 로컬 발급자 구성

이 항목에서는 발급된 토큰에 로컬 발급자를 사용하도록 클라이언트를 구성하는 방법에 대해 설명합니다.

흔히 클라이언트가 페더레이션 서비스와 통신하는 경우, 이 서비스에서는 클라이언트가 페더레이션 서비스에 자신을 인증하는 데 사용하는 토큰을 발급할 보안 토큰 서비스의 주소를 지정합니다. 특정 상황에서는 클라이언트가 *로컬 발급자* 를 사용 하도록 구성 될 수 있습니다.

WCF (Windows Communication Foundation)는 페더레이션된 바인딩의 발급자 주소가 또는 인 경우 로컬 발급자를 사용 `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null` 합니다. 이러한 경우 로컬 발급자와의 통신에 사용할 바인딩과 이 발급자의 주소를 사용하여 <xref:System.ServiceModel.Description.ClientCredentials>를 구성해야 합니다.

> [!NOTE]
> <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A>클래스의 속성이 `ClientCredentials` 로 설정 된 경우 `true` 로컬 발급자 주소를 지정 하지 않은 경우 [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) 또는 다른 페더레이션 바인딩에서 지정한 발급자 주소가 `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self` , 또는 인 경우 `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null` Windows CardSpace 발급자가 사용 됩니다.

## <a name="to-configure-the-local-issuer-in-code"></a>로컬 발급자를 코드로 구성하려면

1. <xref:System.ServiceModel.Security.IssuedTokenClientCredential> 형식의 변수를 만듭니다.

2. 해당 변수를 <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> 클래스의`ClientCredentials` 속성에서 반환된 인스턴스에 설정합니다. 이 인스턴스는 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>에서 상속된 클라이언트의<xref:System.ServiceModel.ClientBase%601> 속성이나 <xref:System.ServiceModel.ChannelFactory.Credentials%2A>의 <xref:System.ServiceModel.ChannelFactory> 속성에 의해 반환됩니다.

     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]

3. 로컬 발급자의 주소가 생성자의 인수인 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A>의 새 인스턴스에 <xref:System.ServiceModel.EndpointAddress> 속성을 설정합니다.

     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]

     또는 새 <xref:System.Uri> 인스턴스를 생성자의 인수로 만듭니다.

     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]

     `addressHeaders`매개 변수는 다음과 같이 인스턴스의 배열입니다 <xref:System.ServiceModel.Channels.AddressHeader> .

     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]

4. 속성을 사용 하 여 로컬 발급자에 대 한 바인딩을 설정 합니다 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> .

     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]

5. 선택 사항입니다. 로컬 발급자에 대해 구성된 엔드포인트 동작을 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> 속성에서 반환된 컬렉션에 추가하여 이러한 동작을 추가합니다.

     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]

## <a name="to-configure-the-local-issuer-in-configuration"></a>로컬 발급자를 구성에서 구성하려면

1. 요소를 [\<localIssuer>](../../configure-apps/file-schema/wcf/localissuer.md) [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) 끝점 동작에서 요소의 자식인 요소에 대 한 자식으로 만듭니다 [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) .

2. `address` 특성을 토큰 요청이 허용되는 로컬 발급자의 주소로 설정합니다.

3. ph x="1" /&gt; 및 `bindingConfiguration` 특성을 로컬 발급자 엔드포인트와 통신할 때 사용할 적합한 바인딩을 참조하는 값으로 설정합니다.

4. 선택 사항입니다. 요소를 [\<identity>](../../configure-apps/file-schema/wcf/identity.md) <> 요소의 자식으로 설정 `localIssuer` 하 고 로컬 발급자에 대 한 id 정보를 지정 합니다.

5. 선택 사항입니다. 요소를 [\<headers>](../../configure-apps/file-schema/wcf/headers.md) <> 요소의 자식으로 설정 `localIssuer` 하 고 로컬 발급자의 주소를 올바르게 지정 하기 위해 필요한 추가 헤더를 지정 합니다.

## <a name="net-framework-security"></a>.NET Framework 보안

지정된 바인딩에 발급자 주소와 바인딩을 지정하지 않으면 해당 바인딩을 사용하는 엔드포인트에는 로컬 발급자가 사용되지 않습니다. 로컬 발급자를 항상 사용해야 하는 클라이언트는 이러한 바인딩을 사용하지 않도록 해야 하며 발급자 주소가 `null`이 되도록 바인딩을 수정해야 합니다.

## <a name="see-also"></a>참고 항목

- [방법: 페더레이션 서비스에서 자격 증명 구성](how-to-configure-credentials-on-a-federation-service.md)
- [방법: 페더레이션 클라이언트 만들기](how-to-create-a-federated-client.md)
- [방법: WSFederationHttpBinding 만들기](how-to-create-a-wsfederationhttpbinding.md)
