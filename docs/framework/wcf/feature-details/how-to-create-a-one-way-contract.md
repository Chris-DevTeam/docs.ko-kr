---
description: '자세한 정보: 방법: One-Way 계약 만들기'
title: '방법: 단방향 계약 만들기'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85084cd9-31cc-4e95-b667-42ef01336622
ms.openlocfilehash: 465dc2da20288c918a70743fcbe3ed931620b33b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734726"
---
# <a name="how-to-create-a-one-way-contract"></a>방법: 단방향 계약 만들기

이 항목에서는 단방향 계약을 사용하는 메서드를 만드는 기본 단계를 보여 줍니다. 이러한 메서드는 클라이언트에서 WCF (Windows Communication Foundation) 서비스에 대 한 작업을 호출 하지만 회신이 필요 하지 않습니다. 이러한 형식의 계약은 예를 들어 여러 구독자에게 알림을 게시하는 데 사용될 수 있습니다. 또한 이중(양방향) 계약을 만들 때 단방향 계약을 사용할 수 있으며 이를 통해 클라이언트 및 서버가 각각 독립적으로 통신하므로 서로 호출을 시작할 수 있습니다. 특히 이 기능을 통해 서버는 클라이언트가 이벤트로 처리할 수 있는 클라이언트에 대한 단방향 호출을 만들 수 있습니다. 단방향 메서드 지정에 대한 자세한 내용은 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 속성 및 <xref:System.ServiceModel.OperationContractAttribute> 클래스를 참조하십시오.  
  
 이중 계약에 대 한 클라이언트 응용 프로그램을 만드는 방법에 대 한 자세한 내용은 [방법: One-Way 및 Request-Reply 계약을 사용 하 여 서비스 액세스](how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)를 참조 하세요. 작업 예제는 [단방향](../samples/one-way.md) 샘플을 참조 하세요.  
  
### <a name="to-create-a-one-way-contract"></a>단방향 계약을 만들려면  
  
1. <xref:System.ServiceModel.ServiceContractAttribute> 클래스를 서비스가 구현할 메서드를 정의하는 인터페이스에 적용하여 서비스 계약을 만듭니다.  
  
2. <xref:System.ServiceModel.OperationContractAttribute> 클래스를 클라이언트가 호출할 수 있는 인터페이스의 메서드에 적용하여 해당 메서드를 나타냅니다.  
  
3. 출력이 없는 작업(반환 값이 없고 out 또는 ref 매개 변수가 없음)은 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 속성을 `true`로 설정하여 단방향으로 지정합니다. <xref:System.ServiceModel.OperationContractAttribute> 클래스가 있는 작업은 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 속성이 기본적으로 `false`이기 때문에 기본적으로 요청-회신 계약을 충족합니다. 따라서 메서드에 대한 단방향 계약을 원하는 경우 특성 속성 값을 명시적으로 `true`로 지정해야 합니다.  
  
## <a name="example"></a>예제  

 다음 코드 예제에서는 여러 단방향 메서드를 포함하는 서비스에 대한 계약을 정의합니다. 기본값이 요청-회신이며 결과를 반환하는 `Equals`를 제외하고 모든 메서드에는 단방향 계약이 포함되어 있습니다.  
  
 [!code-csharp[S_Service_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
## <a name="see-also"></a>참고 항목

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [서비스 디자인 및 구현](../designing-and-implementing-services.md)
- [방법: 서비스 계약 정의](../how-to-define-a-wcf-service-contract.md)
- [세션](../samples/session.md)
- [방법: 이중 계약 만들기](how-to-create-a-duplex-contract.md)
