---
description: '자세히 알아보기: 방법: 정보를 Read-Only으로 검색'
title: '방법: 읽기 전용 정보 검색'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 7743e555bcc3f6371ca601d02313e30895e57961
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723454"
---
# <a name="how-to-retrieve-information-as-read-only"></a>방법: 읽기 전용 정보 검색

데이터를 변경하지 않으려면 읽기 전용 결과를 검색하여 쿼리의 성능을 향상시킬 수 있습니다.  
  
 <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A>를 `false`로 설정하여 읽기 전용 처리를 구현합니다.  
  
> [!NOTE]
> <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A>를 `false`로 설정한 경우 <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A>는 암시적으로 `false`로 설정됩니다.  
  
## <a name="example"></a>예제  

 다음 코드에서는 직원 고용 날짜의 읽기 전용 컬렉션을 검색합니다.  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>참고 항목

- [쿼리 개념](query-concepts.md)
- [데이터베이스 쿼리](querying-the-database.md)
- [지연된 로드 및 즉시 로드 비교](deferred-versus-immediate-loading.md)
