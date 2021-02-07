---
description: '자세한 정보: 워크플로 서비스 개요'
title: 워크플로 서비스 개요
ms.date: 03/30/2017
ms.assetid: e536dda3-e286-441e-99a7-49ddc004b646
ms.openlocfilehash: 688966714faedc3469f084aaa945f58350dfcd5a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704331"
---
# <a name="workflow-services-overview"></a>워크플로 서비스 개요

워크플로 서비스는 워크플로를 사용 하 여 구현 되는 WCF 기반 서비스입니다. 워크플로 서비스는 메시징 작업을 사용 하 여 WCF (Windows Communication Foundation) 메시지를 보내고 받는 워크플로입니다. .NET Framework 4.5에서는 워크플로 내에서 메시지를 보내고 받을 수 있는 다양한 메시징 작업을 제공합니다. 메시징 활동 및이를 사용 하 여 여러 메시지 교환 패턴을 구현 하는 방법에 대 한 자세한 내용은 [메시징 활동](messaging-activities.md)을 참조 하세요.

## <a name="benefits-of-using-workflow-services"></a>워크플로 서비스 사용의 이점

분산 애플리케이션이 점점 더 많아지면서 개별 서비스가 작업 로드를 줄이기 위해 다른 서비스를 호출하는 경우도 많아졌습니다. 이러한 호출을 비동기 작업으로 구현하면 코드가 더 복잡해집니다. 오류 처리는 예외 처리와 자세한 추적 정보 제공이라는 형태로 코드에 복잡성을 더합니다. 일부 서비스는 종종 오랫동안 실행되며 입력을 기다리면서 중요한 시스템 리소스를 차지할 수 있습니다. 이러한 문제 때문에 일반적으로 분산 애플리케이션은 작성하고 유지 관리하기가 매우 복잡하고 어렵습니다. 워크플로를 사용하면 외부 서비스 호출과 같은 비동기 작업의 코디네이션을 자연스럽게 표현할 수 있습니다. 또한 워크플로를 사용하면 장기 실행 비즈니스 프로세스를 효율적으로 표현할 수도 있습니다. 이러한 특성 때문에 워크플로는 분산 환경에서 서비스를 빌드하는 데 유용하게 사용됩니다.

## <a name="implementing-a-workflow-service"></a>워크플로 서비스 구현

WCF 서비스를 구현 하는 경우 서비스 및 해당 서비스를 보내고 받는 데이터를 설명 하는 다양 한 계약을 정의 합니다. 이러한 데이터는 데이터 계약과 메시지 계약으로 표현되기 때문에 WCF 및 워크플로 서비스에서는 데이터 계약 및 메시지 계약 정의를 서비스 설명의 일부로 사용합니다. 서비스 자체에서는 서비스의 작업을 설명하기 위해 메타데이터(WSDL 형식)를 노출합니다. WCF에서는 서비스 계약과 작업 계약을 사용하여 서비스와 서비스가 지원하는 작업을 정의합니다. 그러나 워크플로 서비스에서는 이러한 계약이 비즈니스 프로세스 자체의 일부이기 때문에 계약 유추라고 하는 프로세스에 의해 메타데이터로 노출됩니다. <xref:System.ServiceModel.Activities.WorkflowServiceHost>를 사용하여 워크플로 서비스가 호스트되면 워크플로 정의가 검사되고 워크플로에 있는 메시징 작업 집합을 기반으로 계약이 생성됩니다. 특히 계약을 생성하는 데는 다음 작업과 속성이 사용됩니다.

<xref:System.ServiceModel.Activities.Receive> 작업

- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>

- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>

- <xref:System.ServiceModel.Activities.Receive.Action%2A>

<xref:System.ServiceModel.Activities.SendReply> 작업

- <xref:System.ServiceModel.Activities.SendReply.Action%2A>

<xref:System.ServiceModel.Activities.TransactedReceiveScope> 작업

계약 유추의 최종 결과는 WCF 서비스 및 작업 계약과 동일한 데이터 구조를 사용 하는 서비스에 대 한 설명입니다. 이 정보는 나중에 워크플로 서비스에 대한 WSDL을 노출하는 데 사용됩니다.

> [!NOTE]
> [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]에서는 일부 추가적인 도구 지원 없이 기존 계약 정의만으로 워크플로 서비스를 작성할 수 없습니다. 워크플로 서비스 계약은 앞에서 설명한 계약 유추 프로세스를 통해 만들어지지만 메시지 계약과 데이터 계약은 완벽하게 지원됩니다.

## <a name="workflow-services-and-msmq-based-bindings"></a>워크플로 서비스 및 MSMQ 기반 바인딩

WCF에서는 두 개의 MSMQ 기반 바인딩, <xref:System.ServiceModel.NetMsmqBinding> 및 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>을 정의합니다.  워크플로 서비스의 장기 실행 특성 때문에 MSMQ 기반 바인딩은 워크플로 서비스에 자주 사용됩니다. MSMQ 기반 바인딩에는 MSMQ 메시지가 유효한 것으로 간주될 수 있는 기간을 지정하는 `ValidityDuration` 특성이 있습니다. 워크플로 서비스의 장기 실행 특성 때문에 워크플로 서비스가 MSMQ 메시지를 처리할 수 있기 전에 MSMQ 메시지의 유효 기간이 경과될 수 있습니다. 따라서 MSMQ 바인딩의 유효 기간을 적절한 값으로 설정해야 합니다. 이 값은 워크플로와 워크플로가 메시지를 처리하는 방식을 기반으로 선택해야 합니다. 예를 들어 <xref:System.ServiceModel.Activities.Receive> 작업, 실행하는 데 10분이 걸리는 사용자 지정 작업, 또 다른 <xref:System.ServiceModel.Activities.Receive> 작업이 차례로 포함된 워크플로가 있을 경우 `ValidityDuration`의 올바른 값은 10분 이상이어야 합니다.

## <a name="hosting-a-workflow-service"></a>워크플로 서비스 호스팅

WCF 서비스와 마찬가지로 워크플로 서비스는 호스팅해야 합니다. WCF 서비스는 클래스를 사용 하 여 서비스를 호스팅하고 <xref:System.ServiceModel.ServiceHost> 워크플로 서비스를 사용 하 여 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 서비스를 호스팅합니다. WCF 서비스와 마찬가지로 워크플로 서비스는 다양 한 방법으로 호스팅될 수 있습니다. 예를 들면 다음과 같습니다.

- 관리 되는 .NET Framework 응용 프로그램

- IIS(인터넷 정보 서비스)에서 호스팅

- WAS(Windows Process Activation Service)에서 호스팅

- 관리되는 Windows 서비스에서 호스팅

관리 되는 .NET Framework 응용 프로그램 또는 관리 되는 Windows 서비스에서 호스트 되는 워크플로 서비스는 클래스의 인스턴스를 만들고 <xref:System.ServiceModel.Activities.WorkflowServiceHost> <xref:System.ServiceModel.Activities.WorkflowService> 속성 내에서 워크플로 정의를 포함 하는의 인스턴스를 전달 합니다 <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> . 메시징 작업을 포함하는 워크플로 정의는 워크플로 서비스로 노출됩니다.

IIS 또는 WAS에서 워크플로 서비스를 호스트하려면 워크플로 서비스 정의를 포함하는 .xamlx 파일을 가상 디렉터리에 저장합니다. 기본 끝점 (사용 <xref:System.ServiceModel.BasicHttpBinding> )이 자동으로 생성 됩니다. 자세한 내용은 [간소화 된 구성](../simplified-configuration.md)을 참조 하세요. 또한 Web.config 파일을 가상 디렉터리에 저장하여 사용자 고유의 엔드포인트를 지정할 수도 있습니다. 워크플로 정의가 어셈블리에 있을 경우 가상 디렉터리와 App_Code 디렉터리에 각각 .svc 파일과 워크플로 어셈블리를 저장할 수 있습니다. .svc 파일에서는 서비스 호스트 팩터리를 지정하고 워크플로 서비스를 구현하는 클래스도 지정해야 합니다. 다음 예제에서는 서비스 호스트 팩터리를 지정하고 워크플로 서비스를 구현하는 클래스도 지정하는 방법을 보여 줍니다.

```aspx-csharp
<%@ServiceHost Factory="System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory"
Service="EchoService"%>
```
