---
description: '자세히 알아보기: 복합 형식'
title: 복합 형식
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: 06bb6f54f488e4c6038382707a2ad3e85f000bc2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663900"
---
# <a name="complex-type"></a>복합 형식

*복합 형식은* [엔터티 형식](entity-type.md) 또는 다른 복합 형식에 대 한 다양 한 구조적 속성을 정의 하기 위한 템플릿입니다. 각 템플릿에는 다음 정보가 들어 있습니다.  
  
- 고유한 이름 (필수)  
  
    > [!NOTE]
    > 복합 형식의 이름은 동일한 네임스페이스 내의 엔터티 형식 이름과 달라야 합니다.  
  
- 하나 이상의 [속성](property.md)형식으로 된 데이터입니다. 선택 사항입니다.  
  
    > [!NOTE]
    > 복합 형식의 속성은 다른 복합 형식일 수 있습니다.  
  
 복합 형식은 기본 형식 속성이나 다른 복합 형식의 형태로 데이터 페이로드를 전달할 수 있다는 점에서 엔터티 형식과 비슷합니다. 그러나 복합 형식과 엔터티 형식 사이에는 약간의 중요한 차이점이 존재합니다.  
  
- 복합 형식은 식별자를 포함하지 않으므로 독립적으로 존재할 수 없습니다. 복합 형식은 엔터티 형식 또는 다른 복합 형식의 속성으로만 존재할 수 있습니다.  
  
- 복합 형식은 [연결](association-type.md)에 참여할 수 없습니다. 연결의 끝은 복합 형식이 될 수 없으므로 복합 형식에 대해 [탐색 속성](navigation-property.md) 을 정의할 수 없습니다.  
  
## <a name="example"></a>예제  

 [ADO.NET Entity Framework](./ef/index.md) 에서는[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)(개념 스키마 정의 언어) 이라는 DSL (도메인별 언어)을 사용 하 여 개념적 모델을 정의 합니다. 다음 CSDL에서는 기본 형식 속성 `StreetAddress`, `City`, `StateOrProvince`, `Country` 및 `PostalCode`가 있는 복합 형식 Address를 정의합니다.  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 위의 `Address` 복합 형식을 엔터티 형식의 속성으로 정의하려면 엔터티 형식 정의에서 속성 형식을 선언해야 합니다. 다음 CSDL에서는 `Address` 속성을 엔터티 형식(Publisher)의 복합 형식으로 선언합니다.  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a>참고 항목

- [엔터티 데이터 모델의 주요 개념](entity-data-model-key-concepts.md)
- [엔터티 데이터 모델](entity-data-model.md)
