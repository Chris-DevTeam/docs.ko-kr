---
title: .NET으로 병렬 프로그래밍
description: .NET 병렬 프로그래밍에 대해 알아보세요. .NET 개발을 단순화하기 위해 .NET 런타임, 클래스 라이브러리 형식 및 진단 도구를 사용합니다.
ms.date: 09/12/2018
helpviewer_keywords:
- parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
ms.openlocfilehash: 4d141a6a8fd7b7bf1aad943f8b911c8b39267223
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820360"
---
# <a name="parallel-programming-in-net"></a>.NET으로 병렬 프로그래밍

많은 개인용 컴퓨터 및 워크스테이션에는 여러 CPU 코어가 있기 때문에 다중 스레드를 동시에 실행할 수 있습니다. 하드웨어를 활용하기 위해 코드를 병렬화하여 작업을 여러 프로세서에 분산할 수 있습니다.

이전의 병렬화에서는 스레드 및 잠금에 대한 저수준 조작이 필요했습니다. Visual Studio 및 .NET에서 런타임, 클래스 라이브러리 형식 및 진단 도구를 제공하여 병렬 프로그래밍 지원이 향상됩니다. .NET Framework 4에 도입된 이 기능은 병렬 개발을 단순화하므로, 스레드 또는 스레드 풀에 대해 직접 작업할 필요 없이 효율적이고 세분화된, 확장성 있는 병렬 코드를 자연스러운 언어로 작성할 수 있습니다.

다음 그림은 .NET의 병렬 프로그래밍 아키텍처에 대한 간략한 개요를 제공합니다.

![.NET 병렬 프로그래밍 아키텍처](./media/tpl-architecture.png)

## <a name="related-topics"></a>관련 항목

|기술|설명|
|----------------|-----------------|
|[TPL(작업 병렬 라이브러리)](task-parallel-library-tpl.md)|<xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> 및 `For` 루프의 병렬 버전을 포함하는 `ForEach` 클래스 및 비동기 작업에 대한 선호되는 표현 방식을 나타내는 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 클래스의 설명서를 제공합니다.|
|[PLINQ(병렬 LINQ)](introduction-to-plinq.md)|여러 시나리오에서 성능을 대폭 향상시키는 LINQ to Objects의 병렬 구현입니다.|
|[병렬 프로그래밍을 위한 데이터 구조](data-structures-for-parallel-programming.md)|스레드로부터 안전한 컬렉션 클래스, 간단한 동기화 형식 및 초기화 지연 관련 형식에 대한 설명서의 링크를 제공합니다.|
|[병렬 진단 도구](parallel-diagnostic-tools.md)|작업 및 병렬 스택의 Visual Studio 디버거 창에 대한 설명서와 [Concurrency 시각화](/visualstudio/profiling/concurrency-visualizer)에 대한 설명서로 연결되는 링크를 제공합니다.|
|[PLINQ 및 TPL에 대한 사용자 지정 파티셔너](custom-partitioners-for-plinq-and-tpl.md)|파티션 작동 방식 및 기본 파티션을 구성하거나 새 파티션을 만드는 방법에 대해 설명합니다.|
|[작업 스케줄러](xref:System.Threading.Tasks.TaskScheduler)|스케줄러 작동 방식 및 기본 스케줄러의 구성 방법에 대해 설명합니다.|
|[PLINQ 및 TPL의 람다 식](lambda-expressions-in-plinq-and-tpl.md)|C# 및 Visual Basic으로 작성된 람다 식의 간략한 개요를 제공하고, 람다 식이 PLINQ 및 작업 병렬 라이브러리에서 사용되는 방식을 보여 줍니다.|
|[추가 정보](for-further-reading-parallel-programming.md)|.NET의 병렬 프로그래밍과 관련된 추가 정보 및 샘플 리소스에 대한 링크를 제공합니다.|

## <a name="see-also"></a>참조

- [비동기 개요](../async.md)
- [관리되는 스레딩](../threading/index.md)
