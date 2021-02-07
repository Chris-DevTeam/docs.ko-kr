---
description: 다음에 대해 자세히 알아보세요. <dataContractSerializer>
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: 0705a40f55d76ef46a7debcd4ecfb5235c7c0d21
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754435"
---
# \<dataContractSerializer>

<xref:System.Runtime.Serialization.DataContractSerializer>에 대한 구성 데이터를 포함합니다. 이 요소는 서로 다른 두 가지 계층 구조에서 발생합니다. 하나는 다음 스키마 계층 구조 부분에 나열되고 다른 하나는 설명 부분에 나열됩니다.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a>구문  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  

 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|요소|설명|  
|-------------|-----------------|  
|ignoreExtensionDataObject|엔드포인트가 직렬화되거나 역직렬화될 때 해당 엔드포인트에서 제공하는 데이터를 무시할지 여부를 지정하는 부울 값입니다. 이 특성은 `<dataContractSerializer>` 요소의 `<behavior>`에서만 설정할 수 있습니다.|  
|maxItemsInObjectGraph|직렬화 또는 역직렬화할 항목의 최대 수를 지정하는 정수입니다. 이 특성은 65536입니다.|  
  
### <a name="child-elements"></a>자식 요소  

 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-servicebehaviors.md)|서비스의 동작에 대한 설정 컬렉션입니다.|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|<xref:System.Runtime.Serialization> 네임스페이스 섹션의 루트 요소를 나타내며 <xref:System.Runtime.Serialization.DataContractSerializer>의 옵션을 설정하기 위한 요소를 포함합니다.|  
  
## <a name="remarks"></a>설명  

 이 항목의 소개에 명시 된 대로이 항목은 요소가 발생 하는 두 번째 계층 구조입니다 \<X509Extension> .  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
  
 [\<dataContractSerializer>](datacontractserializer-element.md)  
  
 알려진 형식에 대한 자세한 내용은 <xref:System.Runtime.Serialization.DataContractSerializer>를 참조하세요.  
  
## <a name="see-also"></a>참고 항목

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [데이터 계약 알려진 형식](../../../wcf/feature-details/data-contract-known-types.md)
- [데이터 전송 및 Serialization](../../../wcf/feature-details/data-transfer-and-serialization.md)
