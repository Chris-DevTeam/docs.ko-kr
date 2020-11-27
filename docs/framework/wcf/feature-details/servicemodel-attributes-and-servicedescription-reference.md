---
title: ServiceModel 특성 및 ServiceDescription 참조
ms.date: 03/30/2017
ms.assetid: 4ab86b17-eab9-4846-a881-0099f9a7cc64
ms.openlocfilehash: db2824d7452f1ec4c675782e18ad25bd4be6a483
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253871"
---
# <a name="servicemodel-attributes-and-servicedescription-reference"></a>ServiceModel 특성 및 ServiceDescription 참조

*설명 트리* 는 <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> 서비스의 모든 측면을 함께 설명 하는 형식 (클래스부터 시작)의 계층 구조입니다. WCF (Windows Communication Foundation)는 설명 트리를 사용 하 여 유효한 서비스 런타임을 빌드하고, WSDL (Web Services Description Language), XSD (XML 스키마 정의 언어) 및 클라이언트가 서비스에 연결 하 고 사용 하는 데 사용할 수 있는 서비스에 대 한 정책 어설션 (메타 데이터)을 게시 하 고, 설명 트리 값의 다양 한 코드 및 구성 파일 표현을 생성 합니다.  
  
 이 항목에서는 계약 관련 속성을 서비스 계약에서 가져오는 방법 및 이러한 속성이 구현되고 해당 설명 트리에 추가되는 방법에 대해 설명합니다. 일부 경우 특성 값이 동작 속성으로 변환된 다음 동작이 설명 트리에 삽입됩니다. 설명 트리 값이 메타 데이터로 변환 되는 방법에 대 한 자세한 내용은 [ServiceDescription 및 WSDL 참조](servicedescription-and-wsdl-reference.md)를 참조 하세요.  
  
## <a name="mapping-operations-to-the-description-tree"></a>작업을 설명 트리에 매핑  

 WCF 응용 프로그램에서 서비스 계약은 인터페이스 또는 클래스와 해당 메서드를 작업 그룹으로 표시 하는 특성을 사용 하는 인터페이스 (또는 클래스)에 의해 모델링 됩니다. <xref:System.ServiceModel.ServiceHost> 클래스가 열리면 서비스 계약 및 구현이 반영되고 구성 정보와 함께 설명 트리에 병합됩니다.  
  
 작업 모델에는 *매개 변수* 모델과 *메시지 계약* 모델 이라는 두 가지 유형이 있습니다. 매개 변수 모델은 매개 변수가 없거나 <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType> 클래스에 의해 표시된 값 형식을 반환하는 관리된 메서드를 사용합니다. 이 모델에서 개발자는 매개 변수 및 반환 값의 serialization을 제어 하지만 WCF는 서비스 및 해당 계약에 대 한 설명 트리를 채우는 데 사용 되는 값을 생성 합니다.  
  
 구성 파일에서 지정된 바인딩이 직접 <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A?displayProperty=nameWithType> 속성으로 로드됩니다.  
  
|ServiceBehaviorAttribute 속성|영향을 받은 설명 트리 값|  
|---------------------------------------|-------------------------------------|  
|Name|<xref:System.ServiceModel.Description.ServiceDescription.Name%2A>|  
|네임스페이스|<xref:System.ServiceModel.Description.ServiceDescription.Namespace%2A>|  
|ConfigurationName|<xref:System.ServiceModel.Description.ServiceDescription.ConfigurationName%2A>|  
|IgnoreExtensionDataObject|모든 작업에 대해 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.IgnoreExtensionDataObject%2A> 속성을 설정합니다.|  
|MaxItemsInObjectGraph|모든 작업에 대해 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> 속성을 설정합니다.|  
  
|ServiceContractAttribute 속성|영향을 받은 설명 트리 값|  
|---------------------------------------|-------------------------------------|  
|CallbackContract|모든 작업 <xref:System.ServiceModel.Description.ContractDescription.CallbackContractType%2A>에 추가된 <xref:System.ServiceModel.Description.MessageDescription>, <xref:System.ServiceModel.Description.OperationDescription.Messages%2A>입니다.|  
|ConfigurationName|<xref:System.ServiceModel.Description.ContractDescription.ConfigurationName%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.ContractDescription.ProtectionLevel%2A> 및 가능한 자식 보호 수준입니다. 보호 수준 계층 구조에 대 한 자세한 내용은 [보호 수준 이해](../understanding-protection-level.md)를 참조 하세요.|  
|SessionMode|<xref:System.ServiceModel.Description.ContractDescription.SessionMode%2A>|  
  
|ServiceKnownTypesAttribute 값|영향을 받은 설명 트리 값|  
|--------------------------------------|-------------------------------------|  
|MethodName|<xref:System.ServiceModel.Description.OperationDescription.KnownTypes%2A>|  
  
|OperationContractAttribute 값|영향을 받은 설명 트리 값|  
|--------------------------------------|-------------------------------------|  
|작업|계약/콜백 계약에 따른 출력 메시지 또는 입력 메시지에 대한 <xref:System.ServiceModel.Description.MessageDescription.Action%2A>입니다.|  
|AsyncPattern|true이면 <xref:System.ServiceModel.Description.OperationDescription.BeginMethod%2A> 및 <xref:System.ServiceModel.Description.OperationDescription.EndMethod%2A>입니다.|  
|IsOneWay|<xref:System.ServiceModel.Description.MessageDescription>에서 단일 <xref:System.ServiceModel.Description.OperationDescription.Messages%2A>으로 매핑됩니다.|  
|IsInitiating|<xref:System.ServiceModel.Description.OperationDescription.IsInitiating%2A>|  
|IsTerminating|<xref:System.ServiceModel.Description.OperationDescription.IsTerminating%2A>|  
|이름|<xref:System.ServiceModel.Description.OperationDescription.Name%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.OperationDescription.ProtectionLevel%2A> 및 가능한 자식 보호 수준입니다. 보호 수준 계층 구조에 대 한 자세한 내용은 [보호 수준 이해](../understanding-protection-level.md)를 참조 하세요.|  
|ReplyAction|계약/콜백 계약에 따른 출력 메시지 또는 입력 메시지에 대한 <xref:System.ServiceModel.Description.MessageDescription.Action%2A>입니다.|  
  
|FaultContractAttribute 값|영향을 받은 설명 트리 값|  
|----------------------------------|-------------------------------------|  
|작업|계약/콜백 계약에 따른 <xref:System.ServiceModel.Description.FaultDescription.Action%2A>입니다.|  
|DetailType|<xref:System.ServiceModel.Description.FaultDescription.DetailType%2A>|  
|Name|<xref:System.ServiceModel.Description.FaultDescription.Name%2A>|  
|네임스페이스|<xref:System.ServiceModel.Description.FaultDescription.Namespace%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.FaultDescription.ProtectionLevel%2A>|  
  
|DataContractFormatAttribute 값|영향을 받은 설명 트리 값|  
|---------------------------------------|-------------------------------------|  
|용도|<xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> 값이 작업의 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>에서 설정됩니다.|  
  
|XmlSerializerFormatAttribute 값|영향을 받은 설명 트리 값|  
|----------------------------------------|-------------------------------------|  
|스타일|이 <xref:System.ServiceModel.XmlSerializerFormatAttribute> 속성이 작업의 <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior>에서 설정됩니다.|  
|용도|<xref:System.ServiceModel.XmlSerializerFormatAttribute>가 작업의 <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior>에서 설정됩니다.|  
  
|TransactionFlowAttribute 값|영향을 받은 설명 트리 값|  
|------------------------------------|-------------------------------------|  
|TransactionFlowOption|<xref:System.ServiceModel.TransactionFlowAttribute>가 작업 동작으로 <xref:System.ServiceModel.Description.OperationDescription.Behaviors%2A> 속성에 추가됩니다.|  
  
|MessageContractAttribute 값|영향을 받은 설명 트리 값|  
|------------------------------------|-------------------------------------|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessageDescription.ProtectionLevel%2A>|  
|WrapperName|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperName%2A>|  
|WrapperNamespace|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperNamespace%2A>|  
  
|MessageHeaderAttribute 값|영향을 받은 설명 트리 값|  
|----------------------------------|-------------------------------------|  
|행위자|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A>의 해당 헤더에 대한 <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A>의 해당 헤더에 대한 <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|이름|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>의 해당 헤더에 대한 <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|네임스페이스|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>의 해당 헤더에 대한 <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>의 해당 헤더에 대한 <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|릴레이|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A>의 해당 헤더에 대한 <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
  
|MessageBodyMemberAttribute 값|영향을 받은 설명 트리 값|  
|--------------------------------------|-------------------------------------|  
|이름|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>의 해당 부분에 대한 <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|네임스페이스|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>의 해당 부분에 대한 <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|주문|<xref:System.ServiceModel.Description.MessagePartDescription.Index%2A>의 해당 부분에 대한 <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>의 해당 부분에 대한 <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
|MessageHeaderArrayAttribute 값|영향을 받은 설명 트리 값|  
|---------------------------------------|-------------------------------------|  
|행위자|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A>|  
|MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A>|  
|Name|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
|네임스페이스|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>|  
|릴레이|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A>|  
  
|MessagePropertyAttribute 값|영향을 받은 설명 트리 값|  
|------------------------------------|-------------------------------------|  
|이름|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
  
|MessageParameterAttribute 값|영향을 받은 설명 트리 값|  
|-------------------------------------|-------------------------------------|  
|이름|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>의 해당 부분에 대한 <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
 설명 트리 값이 메타 데이터로 변환 되는 방법에 대 한 자세한 내용은 [ServiceDescription 및 WSDL 참조](servicedescription-and-wsdl-reference.md)를 참조 하세요.  
  
## <a name="see-also"></a>참고 항목

- [ServiceDescription 및 WSDL 참조](servicedescription-and-wsdl-reference.md)
