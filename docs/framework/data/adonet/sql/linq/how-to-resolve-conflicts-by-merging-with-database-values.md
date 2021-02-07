---
description: '자세한 정보: 방법: 데이터베이스 값을 병합 하 여 충돌 해결'
title: '방법: 데이터베이스 값을 병합하여 충돌 해결'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
ms.openlocfilehash: 83cae4c98fdd2e51065c66d36ef04202bdc86c9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767767"
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a>방법: 데이터베이스 값을 병합하여 충돌 해결

변경 내용을 다시 제출하기 전에 예상 데이터베이스 값과 실제 데이터베이스 값의 차이점을 조정하려면 <xref:System.Data.Linq.RefreshMode.KeepChanges>를 사용하여 데이터베이스 값과 현재 클라이언트 멤버 값을 병합합니다. 자세한 내용은 [낙관적 동시성: 개요](optimistic-concurrency-overview.md)를 참조 하세요.  
  
> [!NOTE]
> 모든 경우에 데이터베이스에서 업데이트된 데이터를 검색하여 클라이언트의 레코드를 먼저 새로 고칩니다. 이렇게 하면 다음 업데이트 시도는 동일한 동시성 검사에서 실패하지 않습니다.  
  
## <a name="example"></a>예제  

 이 시나리오에서는 User1이 변경 내용을 제출하려는 경우 User2가 그 동안에 Assistant 열과 Department 열을 변경했기 때문에 <xref:System.Data.Linq.ChangeConflictException> 예외가 throw됩니다. 다음 표에서는 상황을 보여 줍니다.  
  
||Manager|Assistant|department|  
|------|-------------|---------------|----------------|  
|User1과 User2가 쿼리했을 때 원래 데이터베이스 상태|Alfreds|Maria|매출|  
|User1이 변경 내용 전송 준비|Alfred||Marketing|  
|User2가 이미 변경 내용 전송||Mary|서비스|  
  
 User1이 데이터베이스 값을 현재 클라이언트 멤버 값과 병합하여 이 충돌을 해결하기로 결정합니다. 그 결과, 현재 변경 집합 역시 해당 값을 변경할 때에만 데이터베이스 값을 덮어씁니다.  
  
 User1이 <xref:System.Data.Linq.RefreshMode.KeepChanges>를 사용하여 문제를 해결하는 경우 데이터베이스의 결과는 다음 표와 같습니다.  
  
||Manager|Assistant|department|  
|------|-------------|---------------|----------------|  
|충돌 해결 후 변경된 상태|Alfred<br /><br /> (User1이 전송한 값)|Mary<br /><br /> (User2가 전송한 값)|Marketing<br /><br /> (User1이 전송한 값)|  
  
 다음 예제에서는 클라이언트 역시 해당 값을 변경하지 않는 경우 데이터베이스 값과 현재 클라이언트 멤버 값을 병합하는 방법을 보여 줍니다. 검사 또는 개별 멤버 충돌에 대한 사용자 지정 처리 기능이 발생하지 않습니다.  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a>참고 항목

- [방법: 데이터베이스 값을 덮어써서 충돌 해결](how-to-resolve-conflicts-by-overwriting-database-values.md)
- [방법: 데이터베이스 값을 유지하여 충돌 해결](how-to-resolve-conflicts-by-retaining-database-values.md)
- [방법: 변경 충돌 관리](how-to-manage-change-conflicts.md)
