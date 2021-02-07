---
description: '다음에 대 한 자세한 정보: <behaviors> 워크플로'
title: <behaviors> 워크플로
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 5154a389aded34065cc7bdb11d1c73d71ca9f9f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698195"
---
# <a name="behaviors-of-workflow"></a>\<behaviors> 워크플로

이 요소는 **Servicebehaviors** 컬렉션을 포함 합니다.  컬렉션의 각 요소는 워크플로 서비스에서 사용하는 동작 요소를 정의합니다. 각 동작 요소는 고유한 **이름** 특성으로 식별 됩니다.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a>구문  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  

 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  

 None  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|이 구성 섹션은 특정 워크플로 서비스에 정의된 모든 동작을 나타냅니다.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<system.serviceModel>](../wcf/system-servicemodel.md)|모든 워크플로 구성 요소의 루트 요소입니다.|  
  
## <a name="see-also"></a>참고 항목

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [동작을 사용하여 런타임 구성 및 확장](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
