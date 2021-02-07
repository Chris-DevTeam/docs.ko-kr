---
description: '자세히 알아보기: Group By 절 (Visual Basic)'
title: Group By 절
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupByInto
- vb.QueryGroupBy
- vb.QueryGroupRef
- vb.QueryGroupInto
- vb.QueryGroup
helpviewer_keywords:
- queries [Visual Basic], Group By
- Group By statement [Visual Basic]
- Group By clause [Visual Basic]
ms.assetid: b1b5dcea-6654-473b-a2db-01f7e4c265d7
ms.openlocfilehash: f5cfb76b0f4b1d191f959ae1812140c6872e93bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700509"
---
# <a name="group-by-clause-visual-basic"></a>Group By 절 (Visual Basic)

쿼리 결과의 요소를 그룹화합니다. 각 그룹에 집계 함수를 적용하는 데 사용할 수도 있습니다. 그룹화 작업은 하나 이상의 키를 기반으로 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a>부분  
  
- `listField1`, `listField2`  
  
     선택 사항입니다. 그룹화된 결과에 포함할 필드를 명시적으로 식별하는 쿼리 변수의 하나 이상 필드입니다. 필드를 지정하지 않으면 쿼리 변수의 모든 필드가 그룹화된 결과에 포함됩니다.  
  
- `keyExp1`  
  
     필수 사항입니다. 요소 그룹을 결정하는 데 사용할 키를 식별하는 식입니다. 둘 이상의 키를 지정하여 복합 키를 지정할 수 있습니다.  
  
- `keyExp2`  
  
     선택 사항입니다. 복합 키를 만들기 위해 `keyExp1` 와 결합되는 하나 이상의 추가 키입니다.  
  
- `aggregateList`  
  
     필수 사항입니다. 그룹의 집계 방법을 식별하는 하나 이상의 식입니다. 그룹화된 결과의 멤버 이름을 식별하려면 다음 형식 중 하나일 수 있는 `Group` 키워드를 사용합니다.  
  
    ```vb  
    Into Group  
    ```  
  
     또는  
  
    ```vb  
    Into <alias> = Group  
    ```  
  
     그룹에 적용할 집계 함수를 포함할 수도 있습니다.  
  
## <a name="remarks"></a>설명  

 `Group By` 절을 사용하여 쿼리 결과를 그룹으로 나눌 수 있습니다. 그룹화는 키 또는 여러 키로 구성된 복합 키를 기반으로 합니다. 일치하는 키 값과 연결된 요소는 동일한 그룹에 포함됩니다.  
  
 `aggregateList` 절의 `Into` 매개 변수와 `Group` 키워드를 사용하여 그룹을 참조하는 데 사용되는 멤버 이름을 식별합니다. `Into` 절에 집계 함수를 포함하여 그룹화된 요소의 값을 계산할 수도 있습니다. 표준 집계 함수 목록은 [Aggregate Clause](aggregate-clause.md)을 참조하세요.  
  
## <a name="example"></a>예제  

 다음 코드 예제에서는 해당 위치 (국가/지역)를 기준으로 고객 목록을 그룹화 하 고 각 그룹의 고객 수를 제공 합니다. 결과는 국가/지역 이름별로 정렬 됩니다. 그룹화된 결과는 도시 이름별로 정렬됩니다.  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a>참고 항목

- [Visual Basic의 LINQ 소개](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [쿼리](index.md)
- [Select 절](select-clause.md)
- [From 절](from-clause.md)
- [Order By 절](order-by-clause.md)
- [Aggregate Clause](aggregate-clause.md)
- [Group Join 절](group-join-clause.md)
