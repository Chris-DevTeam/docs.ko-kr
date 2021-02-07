---
description: '자세한 정보: 시퀀스의 첫 번째 요소 반환'
title: 시퀀스의 첫 번째 요소 반환
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: 004e9a1f03677f6ba49916404b1c44408df40dfa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663016"
---
# <a name="return-the-first-element-in-a-sequence"></a>시퀀스의 첫 번째 요소 반환

<xref:System.Linq.Enumerable.First%2A> 연산자를 사용하여 시퀀스의 첫 번째 요소를 반환합니다. <xref:System.Linq.Enumerable.First%2A>를 사용한 쿼리는 즉시 실행됩니다.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]에서는 <xref:System.Linq.Enumerable.Last%2A> 연산자를 지원하지 않습니다.  
  
## <a name="example"></a>예제  

 다음 코드에서는 테이블에서 첫 번째 `Shipper`를 찾습니다.  
  
 Northwind 샘플 데이터베이스에 대한 쿼리를 실행하면 결과는 다음과 같습니다.  
  
 `ID = 1, Company = Speedy Express`.  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a>예제  

 다음 코드에서는 `Customer` BONAP이 있는 단일 `CustomerID`를 찾습니다.  
  
 Northwind 샘플 데이터베이스에 대해 이 쿼리를 실행하면 결과는 `ID = BONAP, Contact = Laurence Lebihan`입니다.  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a>참고 항목

- [쿼리 예제](query-examples.md)
- [샘플 데이터베이스 다운로드](downloading-sample-databases.md)
