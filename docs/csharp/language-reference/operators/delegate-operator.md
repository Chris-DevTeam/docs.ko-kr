---
title: 대리자 연산자 - C# 참조
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 1fe281776bd75d8fa869065cd24e85f04fec849d
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331832"
---
# <a name="delegate-operator-c-reference"></a><span data-ttu-id="48b9a-102">대리자 연산자(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="48b9a-102">delegate operator (C# reference)</span></span>

<span data-ttu-id="48b9a-103">`delegate` 연산자는 대리자 형식으로 변환될 수 있는 무명 메서드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="48b9a-103">The `delegate` operator creates an anonymous method that can be converted to a delegate type:</span></span>

[!code-csharp-interactive[anonymous method](~/samples/csharp/language-reference/operators/DelegateOperator.cs#AnonymousMethod)]

<span data-ttu-id="48b9a-104">C# 3으로 시작하는 [람다 식](../../programming-guide/statements-expressions-operators/lambda-expressions.md)은 익명 함수를 만드는 더 간결하고 이해하기 쉬운 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="48b9a-104">Beginning with C# 3, [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) provide a more concise and expressive way to create an anonymous function.</span></span> <span data-ttu-id="48b9a-105">[=> 연산자](lambda-operator.md)를 사용하여 람다 식을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="48b9a-105">Use the [=> operator](lambda-operator.md) to construct a lambda expression:</span></span>

[!code-csharp-interactive[lambda expression](~/samples/csharp/language-reference/operators/DelegateOperator.cs#Lambda)]

<span data-ttu-id="48b9a-106">`delegate` 연산자를 사용하는 경우 매개 변수 목록을 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48b9a-106">When you use the `delegate` operator, you might omit the parameter list.</span></span> <span data-ttu-id="48b9a-107">이렇게 하면 다음 예제와 같이 매개 변수 목록을 사용하여 생성된 무명 메서드를 대리자 형식으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48b9a-107">If you do that, the created anonymous method can be converted to a delegate type with any list of  parameters, as the following example shows:</span></span>

[!code-csharp-interactive[no parameter list](~/samples/csharp/language-reference/operators/DelegateOperator.cs#WithoutParameterList)]

<span data-ttu-id="48b9a-108">이 기능은 람다 식에서 지원되지 않는 무명 메서드의 유일한 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="48b9a-108">That's the only functionality of anonymous methods that is not supported by lambda expressions.</span></span> <span data-ttu-id="48b9a-109">다른 모든 경우 인라인 코드를 작성하는 데 람다 식이 선호됩니다.</span><span class="sxs-lookup"><span data-stu-id="48b9a-109">In all other cases, a lambda expression is a preferred way to write inline code.</span></span> <span data-ttu-id="48b9a-110">람다 식의 기능(예: 외부 변수 캡처)에 대한 자세한 내용은 [람다 식](../../programming-guide/statements-expressions-operators/lambda-expressions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="48b9a-110">For more information about features of lambda expressions, for example, capturing outer variables, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="48b9a-111">`delegate` 키워드를 사용하여 [대리자 형식](../builtin-types/reference-types.md#the-delegate-type)을 선언할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48b9a-111">You also use the `delegate` keyword to declare a [delegate type](../builtin-types/reference-types.md#the-delegate-type).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="48b9a-112">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="48b9a-112">C# language specification</span></span>

<span data-ttu-id="48b9a-113">자세한 내용은 [C# 언어 사양](~/_csharplang/spec/introduction.md)의 [익명 함수 식](~/_csharplang/spec/expressions.md#anonymous-function-expressions) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="48b9a-113">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="48b9a-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="48b9a-114">See also</span></span>

- [<span data-ttu-id="48b9a-115">C# 참조</span><span class="sxs-lookup"><span data-stu-id="48b9a-115">C# reference</span></span>](../index.md)
- [<span data-ttu-id="48b9a-116">C# 연산자</span><span class="sxs-lookup"><span data-stu-id="48b9a-116">C# operators</span></span>](index.md)