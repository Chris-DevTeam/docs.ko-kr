---
title: PLINQ 및 TPL의 람다 식
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
ms.openlocfilehash: 9d884bbcb248effa41b24788d530151783280a53
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817122"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a>PLINQ 및 TPL의 람다 식

TPL(작업 병렬 라이브러리)에는 대리자의 <xref:System.Func%601?displayProperty=nameWithType> 또는 <xref:System.Action?displayProperty=nameWithType> 패밀리 중 하나를 입력 매개 변수로 사용하는 많은 메서드가 포함되어 있습니다. 이러한 대리자를 사용하여 병렬 루프, 작업 또는 쿼리에 사용자 지정 프로그램 논리를 전달합니다. TPL 및 PLINQ에 대한 코드 예제는 람다 식을 사용하여 인라인 코드 블록으로 해당 대리자의 인스턴스를 만듭니다. 이 항목에서는 Func 및 Action에 대한 간략한 소개를 제공하고 작업 병렬 라이브러리 및 PLINQ에서 람다 식을 사용하는 방법을 보여 줍니다.

> [!NOTE]
> 일반적인 대리자에 대한 자세한 내용은 [대리자](../../csharp/programming-guide/delegates/index.md) 및 [대리자](../../visual-basic/programming-guide/language-features/delegates/index.md)를 참조하세요. C# 및 Visual Basic의 람다 식에 대한 자세한 내용은 [람다 식](../../csharp/language-reference/operators/lambda-expressions.md) 및 [람다 식](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)을 참조하세요.

## <a name="func-delegate"></a>Func 대리자

`Func` 대리자는 값을 반환하는 메서드를 캡슐화합니다. `Func` 서명에서 마지막 또는 가장 오른쪽에 있는 형식 매개 변수는 항상 반환 형식을 지정합니다. 컴파일러 오류의 일반적인 원인 중 하나는 두 개의 입력 매개 변수를 <xref:System.Func%602?displayProperty=nameWithType>에 전달하려고 하기 때문입니다. 실제로 이 형식은 하나의 입력 매개 변수만 사용합니다. .NET은 <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType> 등에서 <xref:System.Func%6017?displayProperty=nameWithType>까지 17개 버전의 `Func`를 정의합니다.

## <a name="action-delegate"></a>Action 대리자

<xref:System.Action?displayProperty=nameWithType> 대리자는 값을 반환하지 않는 메서드(Visual Basic의 하위)를 캡슐화합니다. `Action` 형식 서명에서 형식 매개 변수는 입력 매개 변수만을 나타냅니다. `Func`와 마찬가지로 .NET은 형식 매개 변수가 없는 버전에서 16개 형식 매개 변수가 있는 버전까지 17개 버전의 `Action`을 정의합니다.

## <a name="example"></a>예제

<xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> 메서드의 다음 예제는 람다 식을 사용하여 Func 및 Action 대리자를 모두 표현하는 방법을 보여줍니다.

[!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
[!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]

## <a name="see-also"></a>참고 항목

- [병렬 프로그래밍](index.md)
