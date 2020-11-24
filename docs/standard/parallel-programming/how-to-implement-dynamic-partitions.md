---
title: '방법: 동적 파티션 구현'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
ms.openlocfilehash: 1120d846743ac3b89d2d110b4d1abdd0083f9eab
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825743"
---
# <a name="how-to-implement-dynamic-partitions"></a>방법: 동적 파티션 구현

다음 예제는 동적 파티셔닝을 구현하고 특정 오버로드 <xref:System.Threading.Tasks.Parallel.ForEach%2A> 및 PLINQ에서 사용할 수 있는 사용자 지정 <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType>를 구현하는 방법을 보여줍니다.  
  
## <a name="example"></a>예제

파티션이 열거자에 대해 <xref:System.Collections.IEnumerator.MoveNext%2A>를 호출할 때마다 열거자는 하나의 목록 요소가 있는 파티션을 제공합니다. PLINQ 및 <xref:System.Threading.Tasks.Parallel.ForEach%2A>의 경우 파티션은 <xref:System.Threading.Tasks.Task> 인스턴스입니다. 요청이 여러 스레드에서 동시에 발생하므로 현재 인덱스에 대한 액세스가 동기화됩니다.  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

이는 청크 파티셔닝에 대한 예제이며, 각 청크는 하나의 요소로 구성됩니다. 많은 요소를 한 번에 제공하여 잠금에 대한 경합을 줄이고 이론적으로 성능을 빠르게 달성할 수 있습니다. 그러나 특정 지점에서는, 보다 큰 청크의 경우 모든 작업이 수행될 때까지 모든 스레드를 사용하려면 추가 로드 밸런싱 논리가 필요할 수 있습니다.  
  
## <a name="see-also"></a>참조

* [PLINQ 및 TPL에 대한 사용자 지정 파티셔너](custom-partitioners-for-plinq-and-tpl.md)
* [방법: 정적 분할을 위한 파티셔너 구현](how-to-implement-a-partitioner-for-static-partitioning.md)
