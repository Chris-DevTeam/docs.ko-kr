---
title: '방법: 이중 계약 만들기'
description: WCF 클라이언트와 서버가 서로 독립적으로 통신할 수 있도록 이중 계약을 만드는 방법에 대해 알아봅니다. 다른에 대 한 호출을 시작할 수 있습니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
ms.openlocfilehash: cce1784865a1599e69c3f604c288ef62c9c43652
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243718"
---
# <a name="how-to-create-a-duplex-contract"></a>방법: 이중 계약 만들기

이 항목에서는 이중(양방향) 계약을 사용하는 메서드를 만드는 기본 단계를 보여 줍니다. 이중 계약을 사용하면 클라이언트와 서버가 각각 독립적으로 통신하므로 서로 호출을 시작할 수 있습니다. 이중 계약은 WCF (Windows Communication Foundation) 서비스에서 사용할 수 있는 세 가지 메시지 패턴 중 하나입니다. 다른 두 메시지 패턴은 단방향 및 요청-회신입니다. 이중 계약은 클라이언트와 서버 간 두 개의 단방향 계약으로 구성되며, 메서드 호출을 상호 관련시키지 않아도 됩니다. 서비스가 클라이언트에 세부 정보를 쿼리하거나 클라이언트에서 이벤트를 명시적으로 발생시킬 때 이러한 종류의 계약을 사용합니다. 이중 계약에 대 한 클라이언트 응용 프로그램을 만드는 방법에 대 한 자세한 내용은 [방법: 이중 계약을 사용 하 여 서비스 액세스](how-to-access-services-with-a-duplex-contract.md)를 참조 하세요. 작업 샘플은 [이중](../samples/duplex.md) 샘플을 참조 하세요.  
  
### <a name="to-create-a-duplex-contract"></a>이중 계약을 만들려면  
  
1. 이중 계약의 서버 측을 구성하는 인터페이스를 만듭니다.  
  
2. 인터페이스에 <xref:System.ServiceModel.ServiceContractAttribute> 클래스를 적용합니다.  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3. 인터페이스에 메서드 서명을 선언합니다.  
  
4. 공용 계약의 일부여야 하는 각 메서드 서명에 <xref:System.ServiceModel.OperationContractAttribute> 클래스를 적용합니다.  
  
5. 서비스가 클라이언트에서 호출할 수 있는 작업 집합을 정의하는 콜백 인터페이스를 만듭니다.  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6. 콜백 인터페이스에 메서드 서명을 선언합니다.  
  
7. 공용 계약의 일부여야 하는 각 메서드 서명에 <xref:System.ServiceModel.OperationContractAttribute> 클래스를 적용합니다.  
  
8. 기본 인터페이스의 <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> 속성을 콜백 인터페이스의 형식으로 설정하여 이중 계약에 두 개의 인터페이스를 연결합니다.  
  
### <a name="to-call-methods-on-the-client"></a>클라이언트에서 메서드를 호출하려면  
  
1. 기본 계약의 서비스 구현에서 콜백 인터페이스에 대한 변수를 선언합니다.  
  
2. 변수를 <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> 클래스의 <xref:System.ServiceModel.OperationContext> 메서드에서 반환한 개체 참조로 설정합니다.  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3. 콜백 인터페이스에서 정의한 메서드를 호출합니다.  
  
## <a name="example"></a>예제  

 다음 코드 예제에서는 이중 통신을 수행하는 방법을 보여 줍니다. 서비스의 계약에는 앞뒤로 이동하기 위한 서비스 작업이 포함됩니다. 클라이언트의 계약에는 해당 위치를 보고하는 서비스 작업이 포함됩니다.  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
- <xref:System.ServiceModel.ServiceContractAttribute> 및 <xref:System.ServiceModel.OperationContractAttribute> 특성을 적용하면 WSDL(웹 서비스 기술 언어)에서 서비스 계약 정의를 자동으로 생성할 수 있습니다.  
  
- [ServiceModel Metadata 유틸리티 도구 (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) 를 사용 하 여 WSDL 문서를 검색 하 고 클라이언트에 대 한 코드 및 구성 (선택 사항)을 검색 합니다.  
  
- 이중 서비스를 노출하는 엔드포인트를 보호해야 합니다. 서비스가 이중 메시지를 받으면 들어오는 해당 메시지에서 ReplyTo를 확인하여 회신을 보낼 위치를 결정합니다. 채널이 보안되지 않으면 신뢰할 수 없는 클라이언트가 대상 컴퓨터의 ReplyTo를 사용하여 악의적인 메시지를 보낼 수 있으므로 해당 대상 컴퓨터의 서비스 거부가 발생할 수 있습니다. 정규 요청-회신 메시지를 사용하는 경우에는 ReplyTo가 무시되고 원래 메시지가 들어온 채널에서 응답이 보내지므로 이러한 문제가 생기지 않습니다.  
  
## <a name="see-also"></a>참고 항목

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [방법: 이중 계약을 사용하여 서비스 액세스](how-to-access-services-with-a-duplex-contract.md)
- [이중](../samples/duplex.md)
- [서비스 디자인 및 구현](../designing-and-implementing-services.md)
- [방법: 서비스 계약 정의](../how-to-define-a-wcf-service-contract.md)
- [세션](../samples/session.md)
