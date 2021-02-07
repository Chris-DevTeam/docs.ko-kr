---
description: '자세한 정보: 방법: 관련 데이터 필터링'
title: '방법: 관련 데이터 필터링'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec8b8f97-5d01-4f31-9b97-d1556df6a4bc
ms.openlocfilehash: d44e0805b82c0c58f9ee19808e078f9f9b337050
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738951"
---
# <a name="how-to-filter-related-data"></a>방법: 관련 데이터 필터링

<xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> 메서드를 사용하여 검색된 데이터의 양을 제한하기 위한 하위 쿼리를 지정합니다.  
  
## <a name="example"></a>예제  

 다음 예제에서 <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> 메서드는 `Orders`를 오늘 선적되지 되지 않은 것으로 제한합니다. 이 방법을 사용하지 않을 경우 한 개의 하위 집합만 필요한 경우에도 모든 `Orders`가 검색됩니다.  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.DataLoadOptions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#1)]  
  
## <a name="see-also"></a>참고 항목

- [데이터베이스 쿼리](querying-the-database.md)
