---
description: 다음에 대 한 자세한 정보:/(나누기) (Entity SQL)
title: '- 나누면 (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: 4ac487c636c460401eeb147dc7ce1a8d8ba7f7ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724637"
---
# <a name="-divide-entity-sql"></a>/ (나누기) (Entity SQL)

한 숫자를 다른 숫자로 나눕니다.  
  
## <a name="syntax"></a>구문  
  
```sql  
dividend / divisor  
```  
  
## <a name="arguments"></a>인수  

 `dividend`  
 나눌 숫자 식입니다. `dividend` 는 숫자 데이터 형식의 유효한 식입니다.  
  
 `divisor`  
 피제수를 나눌 숫자 식입니다. `divisor` 는 숫자 데이터 형식의 유효한 식입니다.  
  
## <a name="result-types"></a>결과 형식  

 두 인수에 대해 암시적 형식 승격을 수행한 결과 데이터 형식입니다. 암시적 형식 승격에 대 한 자세한 내용은 [형식 시스템](type-system-entity-sql.md)을 참조 하세요.  
  
## <a name="example"></a>예제  

 다음 Entity SQL 쿼리에서는/산술 연산자를 사용 하 여 한 숫자를 다른 숫자로 나눕니다. 쿼리는 AdventureWorks Sales 모델을 기반으로 합니다. 이 쿼리를 컴파일하고 실행하려면 다음 단계를 수행하세요.  
  
1. [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)의 절차를 따릅니다.  
  
2. 다음 쿼리를 `ExecuteStructuralTypeQuery` 메서드에 인수로 전달합니다.  
  
 [!code-sql[DP EntityServices Concepts#DIVIDE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#divide)]  
  
## <a name="see-also"></a>참고 항목

- [엔터티 SQL 참조](entity-sql-reference.md)
