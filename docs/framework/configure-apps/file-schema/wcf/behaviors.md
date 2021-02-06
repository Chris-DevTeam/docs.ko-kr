---
description: 다음에 대해 자세히 알아보세요. <behaviors>
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: 3cb8edea76f6e7af3c3b387e5b04b89e58a28305
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639512"
---
# \<behaviors>

이 요소는 이름이 `endpointBehaviors` 및 `serviceBehaviors`인 두 개의 자식 컬렉션을 정의합니다.  각 컬렉션은 엔드포인트 및 서비스가 사용하는 동작 요소를 각각 정의합니다. 각 동작 요소는 고유한 `name` 특성으로 식별됩니다. .NET Framework 4부터 바인딩과 동작은 이름을 가질 필요가 없습니다. 기본 구성 및 이름이 없는 바인딩 및 동작에 대 한 자세한 내용은 [WCF 서비스에 대 한](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [간소화 된 구성](../../../wcf/simplified-configuration.md) 및 단순화 된 구성을 참조 하세요.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a>구문  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  

 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  

 None  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|이 구성 섹션은 특정 엔드포인트에 정의된 모든 동작을 나타냅니다.|  
|[\<serviceBehaviors>](servicebehaviors.md)|이 구성 섹션은 특정 서비스에 정의된 모든 동작을 나타냅니다.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|모든 WCF(Windows Communication Foundation) 구성 요소의 루트 요소입니다.|  
  
## <a name="remarks"></a>설명  

 `<remove>` 요소를 사용하여 컬렉션에서 특정 동작을 제거할 수 있습니다. 이렇게 하려면 제거할 동작의 이름을 `name` 요소의 `<remove>` 특성에 제공합니다.  `<clear>` 요소를 사용하여 컬렉션의 모든 내용을 지워 동작 컬렉션이 비어 있는 상태로 시작되도록 할 수도 있습니다.  
  
## <a name="see-also"></a>참고 항목

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [동작을 사용하여 런타임 구성 및 확장](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [클라이언트 동작 구성](../../../wcf/configuring-client-behaviors.md)
- [클라이언트 런타임 동작 지정](../../../wcf/specifying-client-run-time-behavior.md)
- [서비스 런타임 동작 지정](../../../wcf/specifying-service-run-time-behavior.md)
- [보안 동작](../../../wcf/feature-details/security-behaviors-in-wcf.md)
