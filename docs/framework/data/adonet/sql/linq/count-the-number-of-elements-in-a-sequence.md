---
description: '자세한 정보: 시퀀스의 요소 수 계산'
title: 시퀀스의 요소 수 계산
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: 91030516098e900229a1e131ea0c9a7d8bef4034
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663081"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a>시퀀스의 요소 수 계산

<xref:System.Linq.Enumerable.Count%2A> 연산자를 사용하여 시퀀스의 요소 수를 계산합니다.  
  
 Northwind 샘플 데이터베이스에 대한 쿼리를 실행하여 `91`의 출력을 생성합니다.  
  
## <a name="example"></a>예제  

 다음 예제에서는 데이터베이스의 `Customers` 수를 계산합니다.  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a>예제  

 다음 예제에서는 데이터베이스에서 중지되지 않은 제품의 수를 계산합니다.  
  
 Northwind 샘플 데이터베이스에 대한 예제를 실행하여 `69`의 출력을 생성합니다.  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>참고 항목

- [집계 쿼리](aggregate-queries.md)
- [샘플 데이터베이스 다운로드](downloading-sample-databases.md)
