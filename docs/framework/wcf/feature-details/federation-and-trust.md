---
title: 페더레이션 및 트러스트
ms.date: 03/30/2017
helpviewer_keywords:
- federation [WCF], and trust
ms.assetid: 4bdec4f2-f8a2-4512-bdcf-14ef54b5877a
ms.openlocfilehash: 6baa336f96f2349315cab2ed51bfb67c4745a110
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255483"
---
# <a name="federation-and-trust"></a>페더레이션 및 트러스트

이 항목에서는 페더레이션 응용 프로그램, 트러스트 경계 및 구성, Windows Communication Foundation (WCF)에서 발급 된 토큰 사용과 관련 된 다양 한 측면에 대해 설명 합니다.  
  
## <a name="services-security-token-services-and-trust"></a>서비스, 보안 토큰 서비스 및 트러스트  

 일반적으로 페더레이션 엔드포인트를 노출하는 서비스에서는 클라이언트가 특정 발급자에 의해 제공되는 토큰을 사용하여 인증합니다. 서비스는 발급자에 대해 올바른 자격 증명으로 구성되는 것이 중요합니다. 그렇지 않을 경우 발급된 토큰을 통해 서명을 확인할 수 없고 클라이언트는 서비스와 통신할 수 없습니다. 서비스에서 발급자 자격 증명을 구성 하는 방법에 대 한 자세한 내용은 [방법: 페더레이션 서비스에서 자격 증명 구성](how-to-configure-credentials-on-a-federation-service.md)을 참조 하세요.  
  
 마찬가지로 대칭 키를 사용하는 경우 해당 키는 대상 서비스에 대해 암호화되기 때문에 대상 서비스에 대해 올바른 자격 증명으로 보안 토큰 서비스를 구성해야 합니다. 그렇지 않을 경우 대상 서비스에 대해 키를 암호화할 수 없고 클라이언트도 서비스와 통신할 수 없습니다.  
  
 WCF 서비스는 SecurityBindingElement의 속성 값을 사용 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> 하 [SecurityBindingElement](../diagnostics/wmi/securitybindingelement.md) 여 클라이언트와 서비스 간의 클록 기울이기를 허용 합니다. 페더레이션에서 `MaxClockSkew` 설정은 클라이언트가 발급된 토큰을 가져온 클라이언트 및 보안 토큰 서비스 사이에 모두 클럭 오차를 적용합니다. 따라서 보안 토큰 서비스는 발급된 토큰의 유효 시간 및 만료 시간을 설정할 때 클럭 오차를 허용할 필요가 없습니다.  
  
> [!NOTE]
> 발급된 토큰 수명이 단축될수록 클럭 오차의 중요성이 증가합니다. 대부분의 경우 토큰 수명이 30분 이상이면 클럭 오차가 중요한 문제가 되지 않습니다. 수명이 짧거나 토큰의 정확한 유효 시간이 중요한 경우 클럭 오차를 고려하도록 디자인해야 합니다.  
  
## <a name="federated-endpoints-and-time-outs"></a>페더레이션 엔드포인트 및 시간 제한  

 클라이언트가 페더레이션 엔드포인트와 통신하는 경우 먼저 보안 토큰 서비스에서 적절한 토큰을 가져와야 합니다. 보안 토큰 서비스가 페더레이션 엔드포인트를 노출하는 경우 클라이언트는 먼저 해당 엔드포인트에 대한 발급자로부터 토큰을 가져와야 합니다. 토큰을 가져올 때마다 시간이 걸리며 이 시간은 실제 메시지를 최종 엔드포인트에 보내기 위한 전체 시간 제한에 적용됩니다.  
  
 예를 들어 클라이언트측 채널에 대한 시간 제한은 30초로 설정됩니다. 두 토큰 발급자는 메시지를 최종 엔드포인트에 보내기 전에 토큰 검색을 위해 호출되어야 하며 각 발급자가 토큰을 발급하는 데 15초 걸립니다. 이 경우 시도가 실패하고 <xref:System.TimeoutException>이 throw됩니다. 따라서 클라이언트 채널의 <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> 값을 모든 발급된 토큰을 검색하는 데 걸리는 시간을 충분히 포함하도록 큰 값으로 설정해야 합니다. <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> 속성에 대해 값을 지정하지 않은 경우 <xref:System.ServiceModel.Channels.Binding.OpenTimeout%2A> 속성 또는 <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A> 속성(또는 둘 다)은 모든 발급된 토큰을 검색하는 데 걸리는 시간을 충분히 포함하도록 큰 값으로 설정해야 합니다.  
  
## <a name="token-lifetime-and-renewal"></a>토큰 수명 및 갱신  

 WCF 클라이언트는 서비스에 대 한 초기 요청을 만들 때 발급 된 토큰을 확인 하지 않습니다.  대신 WCF는 보안 토큰 서비스를 신뢰 하 여 적절 한 유효 기간 및 만료 시간으로 토큰을 발급 합니다. 토큰이 클라이언트에 의해 캐시되고 다시 사용하는 경우 토큰 수명은 후속 요청 시 검사되고 클라이언트는 필요한 경우 토큰을 자동으로 갱신합니다. 토큰 캐싱에 대 한 자세한 내용은 [방법: 페더레이션된 클라이언트 만들기](how-to-create-a-federated-client.md)를 참조 하세요.  
  
 발급 된 토큰 또는 보안 컨텍스트 토큰에 대해 30 초 이내에 짧은 수명을 지정 하면 발급 된 토큰을 요청할 때 또는 보안 컨텍스트 토큰을 협상 또는 갱신할 때 WCF 클라이언트에서 협상 시간 제한이 발생 하거나 다른 예외가 throw 될 수 있습니다.  
  
## <a name="issued-tokens-and-inclusionmode"></a>발급된 토큰 및 InclusionMode  

 발급된 토큰이 클라이언트에서 페더레이션 엔드포인트로 보낸 메시지에서 serialize되었는지 여부는 <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InclusionMode%2A> 클래스의 <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> 속성을 설정하여 제어됩니다. 이 속성은 <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode> 열거형 값 중 하나로 설정할 수 있지만 대부분의 페더레이션 시나리오에서 유용하지 않습니다. `SecurityTokenInclusionMode.Never` 및 `SecurityTokenInclusionMode.AlwaysToInitiator` 값은 클라이언트가 보안 토큰 서비스에 의해 발급된 토큰에 대한 참조를 신뢰하는 상대에게 보내도록 합니다. 신뢰하는 상대가 발급된 토큰 복사본을 가지고 있지 않은 한 토큰 참조를 확인할 수 없기 때문에 인증이 실패합니다. WCF `SecurityTokenInclusionMode.Once` 는와 동일 하 게 처리 `SecurityTokenInclusionMode.AlwaysToRecipient` 됩니다.  
  
## <a name="see-also"></a>참고 항목

- <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>
- [방법: 페더레이션 클라이언트 만들기](how-to-create-a-federated-client.md)
- [방법: 페더레이션 서비스에서 자격 증명 구성](how-to-configure-credentials-on-a-federation-service.md)
- [방법: WSFederationHttpBinding 만들기](how-to-create-a-wsfederationhttpbinding.md)
