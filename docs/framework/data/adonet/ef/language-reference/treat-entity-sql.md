---
description: '자세한 정보: TREAT (Entity SQL)'
title: TREAT(Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 3f014cac631d246b35d145cdb80c9aa6ac401524
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673429"
---
# <a name="treat-entity-sql"></a>TREAT(Entity SQL)

특정 기본 형식의 개체를 지정된 파생 형식의 개체로 처리합니다.  
  
## <a name="syntax"></a>구문  
  
```sql  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a>인수  

 `expression`  
 엔터티를 반환하는 모든 유효한 쿼리 식입니다.  
  
> [!NOTE]
> 지정된 식의 형식이 지정된 데이터 형식의 하위 형식이어야 하거나, 데이터 형식이 식 형식의 하위 형식이어야 합니다.  
  
 `type`  
 엔터티 형식입니다. 형식은 네임스페이스로 한정되어야 합니다.  
  
> [!NOTE]
> 지정된 식이 지정된 데이터 형식의 하위 형식이어야 하거나, 데이터 형식이 식의 하위 형식이어야 합니다.  
  
## <a name="return-value"></a>Return Value  

 지정된 데이터 형식의 값입니다.  
  
## <a name="remarks"></a>설명  

 TREAT는 관련 클래스 간에 업캐스팅을 수행하는 데 사용됩니다. 예를 들어, `Employee` 가 `Person` 에서 파생되고 p가 `Person`형식인 경우 `TREAT(p AS NamespaceName.Employee)` 는 일반 `Person` 인스턴스를 `Employee`로 업캐스팅합니다. 다시 말해서, p를 `Employee`로 취급할 수 있게 됩니다.  
  
 TREAT는 다음과 같이 쿼리할 수 있는 상속 시나리오에서 사용됩니다.  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)
```  
  
 이 쿼리는 `Person` 엔터티를 `Employee` 형식으로 업캐스팅합니다. p의 값이 실제로 `Employee`형식이 아닌 경우 식의 값은 `null`입니다.  
  
> [!NOTE]
> 지정 된 식이 `Employee` 지정 된 데이터 형식의 하위 형식 이어야 `Person` 하거나, 데이터 형식이 식의 하위 형식 이어야 합니다. 그렇지 않으면 식에서 컴파일 시간 오류가 발생합니다.  
  
 다음 표에서는 일반 패턴 및 비교적 특수한 패턴에 대한 TREAT의 동작을 보여 줍니다. 공급자 호출 이전에 모든 예외가 클라이언트 측에서 throw됩니다.  
  
|무늬|동작|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|`DbNull`를 반환합니다.|  
|`TREAT (null AS ComplexType)`|예외를 throw합니다.|  
|`TREAT (null AS RowType)`|예외를 throw합니다.|  
|`TREAT (EntityType AS EntityType)`|`EntityType` 또는 `null`을 반환합니다.|  
|`TREAT (ComplexType AS ComplexType)`|예외를 throw합니다.|  
|`TREAT (RowType AS RowType)`|예외를 throw합니다.|  
  
## <a name="example"></a>예제  

 다음 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 쿼리에서는 TREAT 연산자를 사용하여 Course 형식의 개체를 OnsiteCourse 형식의 개체 컬렉션으로 변환합니다. 쿼리는 [School 모델](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))을 기반으로 합니다.  
  
 [!code-sql[DP EntityServices Concepts#TREAT_ISOF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]  
  
## <a name="see-also"></a>참고 항목

- [엔터티 SQL 참조](entity-sql-reference.md)
- [nullable 구조적 형식](nullable-structured-types-entity-sql.md)
