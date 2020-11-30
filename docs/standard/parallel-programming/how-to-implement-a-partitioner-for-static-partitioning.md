---
title: '방법: 정적 분할을 위한 파티셔너 구현'
ms.date: 03/30/2017
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
ms.openlocfilehash: 59a5519a8f129576c08604633cd3c411d3ca020e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734493"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a>방법: 정적 분할을 위한 파티셔너 구현

다음 예제에서는 정적 파티셔닝을 수행하는 PLINQ에 대해 단순한 사용자 지정 파티셔너를 구현하는 한 가지 방법을 보여줍니다. 파티셔너는 동적 파티션을 지원하지 않으므로 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>에서 사용할 수 없습니다. 이 특정 파티셔너는 각 요소로 인해 처리 시간이 늘어나는 데이터 소스의 기본 범위 파티셔너에 대해 가속을 제공할 수 있습니다.  
  
## <a name="example"></a>예제  

 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 이 예제의 파티션은 각 요소의 처리 시간이 선형으로 증가할 것이라는 가정을 기반으로 합니다. 실제로는 처리 시간을 이 방법으로 예측하기 어려울 수 있습니다. 특정 데이터 소스와 함께 정적 파티셔너를 사용하는 경우 소스에 대한 파티셔닝 수식을 최적화하거나 로드 밸런싱 논리를 추가하거나 [방법: 동적 파티션 구현](how-to-implement-dynamic-partitions.md)에 설명된 청크 파티셔닝 접근 방식을 사용할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목

- [PLINQ 및 TPL에 대한 사용자 지정 파티셔너](custom-partitioners-for-plinq-and-tpl.md)
