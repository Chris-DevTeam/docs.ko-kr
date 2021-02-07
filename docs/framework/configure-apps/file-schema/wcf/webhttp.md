---
description: 다음에 대해 자세히 알아보세요. <webHttp>
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: acd8d77e00828d132d076c867ff3164ca1ba7230
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664381"
---
# \<webHttp>

이 요소는 구성을 통해 엔드포인트에서 <xref:System.ServiceModel.Description.WebHttpBehavior>를 지정합니다. 이 동작은 표준 바인딩과 함께 사용 될 경우 [\<webHttpBinding>](webhttpbinding.md) WCF (Windows Communication Foundation) 서비스용 웹 프로그래밍 모델을 사용 하도록 설정 합니다.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttp>**  
  
## <a name="syntax"></a>구문  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  

 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|attribute|설명|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|이 속성이 `true`로 설정되면 WCF 인프라가 사용할 가장 적절한 형식을 결정합니다. 기본적으로 자동 형식 선택은 이전 버전과의 호환성을 위해 사용되지 않습니다. 자동 형식 선택은 프로그래밍 방식이나 구성을 통해 사용하도록 설정할 수 있습니다.|  
|defaultBodyStyle|반환된 메시지의 기본 본문 스타일을 지정합니다. 자세한 내용은 <xref:System.ServiceModel.Web.WebMessageBodyStyle> 및 [WCF 웹 HTTP 형식 지정](../../../wcf/feature-details/wcf-web-http-formatting.md)을 참조 하세요.|  
|defaultOutgoingResponseFormat|메시지의 나가는 기본 응답 형식을 지정합니다. 자세한 내용은 [WCF 웹 HTTP 형식 지정](../../../wcf/feature-details/wcf-web-http-formatting.md)을 참조 하세요.|  
|faultExceptionEnabled|내부 서버 오류(HTTP 상태 코드: 500)가 발생할 때 FaultException이 생성되는지 여부를 지정하는 플래그를 가져오거나 설정합니다.|  
|helpEnabled|도움말 페이지를 사용할 수 있는지 여부를 결정하는 값을 가져오거나 설정합니다.|  
  
### <a name="child-elements"></a>자식 요소  

 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|엔드포인트 동작 집합을 지정합니다.|  
  
## <a name="see-also"></a>참고 항목

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [AJAX 통합 및 JSON 지원](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](webhttpbinding.md)
