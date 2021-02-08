---
description: '자세한 정보: 방법: 검색 되는 관련 데이터의 양 제어'
title: '방법: 관련 데이터의 검색 양 제어'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: becf1282d18d5c630da3e3be27c62ebae404d940
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786045"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a>방법: 관련 데이터의 검색 양 제어

<xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> 메서드를 사용하여 동시에 검색되어야 하는 주 대상과 관련된 데이터를 지정합니다. 예를 들어 고객 주문에 대한 정보가 필요한 경우 <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>를 사용하여 주문 정보와 고객 정보가 검색되었는지 확인합니다. 이 접근 방법은 두 가지 정보에 대한 데이터베이스에서 원트립만의 결과입니다.  
  
> [!NOTE]
> 고객을 대상으로 할 경우 주문을 검색하는 것과 같이 외적을 하나의 큰 프로젝션처럼 검색하여 쿼리의 주 대상과 관련된 데이터를 검색할 수 있습니다. 그러나 이러한 방법에는 종종 단점이 있습니다. 예를 들어 결과는 엔터티가 아니라 프로젝션이기에 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]에서 변경되고 유지될 수 있습니다. 원하지 않는 많은 데이터가 검색될 수 있습니다.  
  
## <a name="example"></a>예제  

 다음 예제에서는 `Orders` `Customers` 쿼리가 실행 될 때 런던에 있는 모든에 대 한 모든가 검색 됩니다. 따라서 개체의 속성에 대 한 연속 액세스는 `Orders` `Customer` 새 데이터베이스 쿼리를 트리거하지 않습니다.  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>참고 항목

- [데이터베이스 쿼리](querying-the-database.md)
