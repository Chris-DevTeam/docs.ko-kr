---
title: Null 허용 값 형식 - C# 참조
description: C# nullable 값 형식 및 사용 방법 알아보기
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: 3ab2dff6b7399b0458a69d4498b2ebda24f6c5cc
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471837"
---
# <a name="nullable-value-types-c-reference"></a>Nullable 값 형식(C# 참조)

*Null 허용 값 형식* `T?`는 기본 [값 형식](value-types.md) `T`의 모든 값과 추가 [null](../keywords/null.md) 값을 나타냅니다. 예를 들어 `bool?` 변수에는 다음 세 가지 값 중 하나를 할당할 수 있습니다. `true`, `false`, `null`. 기본 값 형식 `T`는 null 허용 값 형식 자체일 수 없습니다.

> [!NOTE]
> C# 8.0에서는 nullable 참조 형식 기능을 소개합니다. 자세한 내용은 [nullable 참조 형식](nullable-reference-types.md)을 참조하세요. Null 허용 값 형식은 C# 2부터 사용할 수 있습니다.

Null 허용 값 형식은 제네릭 <xref:System.Nullable%601?displayProperty=nameWithType> 구조체의 인스턴스입니다. 서로 교환 가능한 형식인 `Nullable<T>` 또는 `T?` 중 하나에서 기본 값 형식 `T`의 null 허용 값 형식을 참조할 수 있습니다.

기본 값 형식의 정의되지 않은 값을 표시해야 하는 경우 일반적으로 null 허용 값 형식을 사용합니다. 예를 들어 부울(`bool`) 변수는 `true` 또는 `false`만 가능합니다. 그러나 일부 애플리케이션에서는 변수 값이 정의되지 않았거나 누락될 수 있습니다. 예를 들어 데이터베이스 필드는 `true` 또는 `false`를 포함하거나 아무 값도 없을 수 있습니다(즉 `NULL`). 이러한 시나리오에서 `bool?` 형식을 사용할 수 있습니다.

## <a name="declaration-and-assignment"></a>선언 및 할당

값 형식이 암시적으로 해당 null 허용 값 형식으로 변환될 수 있기 때문에 기본 값 형식에서와 마찬가지로 null 허용 값 형식의 변수에 값을 할당할 수 있습니다. `null` 값을 할당할 수도 있습니다. 예를 들어:

[!code-csharp[declare and assign](snippets/shared/NullableValueTypes.cs#Declaration)]

Null 허용 값 형식의 기본값은 `null`을 나타냅니다. 즉, <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> 속성이 `false`을 반환하는 인스턴스입니다.

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a>Null 허용 값 형식의 인스턴스 검사

C# 7.0부터 [`is`형식 패턴 포함 연산자](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching)를 사용하여 null 허용 값 형식의 인스턴스에서 `null` 여부를 검사하고 기본 형식의 값을 검색할 수 있습니다.

[!code-csharp-interactive[use pattern matching](snippets/shared/NullableValueTypes.cs#PatternMatching)]

항상 다음 읽기 전용 속성을 사용하여 null 허용 값 형식 변수의 값을 검사하고 가져올 수 있습니다.

- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>은 null 허용 값 형식의 인스턴스에 해당 기본 형식의 값이 있는지 여부를 나타냅니다.

- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType>은 <xref:System.Nullable%601.HasValue%2A>가 `true`인 경우 기본 형식의 값을 가져옵니다. <xref:System.Nullable%601.HasValue%2A>가 `false`인 경우 <xref:System.Nullable%601.Value%2A> 속성은 <xref:System.InvalidOperationException>을 throw합니다.

다음 예제는 `HasValue` 속성을 사용하여 표시하기 전에 변수가 값을 포함하는지 여부를 테스트합니다.

[!code-csharp-interactive[use HasValue](snippets/shared/NullableValueTypes.cs#HasValue)]

다음 예제와 같이 `HasValue` 속성을 사용하는 대신 null 허용 값 형식 변수를 `null`과 비교할 수도 있습니다.

[!code-csharp-interactive[use comparison with null](snippets/shared/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a>nullable 값 형식에서 기본 형식으로 변환

Null 허용 값 형식의 값을 null을 허용하지 않는 값 형식 변수에 할당하려는 경우 `null` 대신 할당할 값을 지정해야 할 수 있습니다. [null 병합 연산자`??`](../operators/null-coalescing-operator.md)를 사용하여 이 작업을 수행할 수 있습니다(<xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> 메서드를 동일한 용도로 사용할 수도 있음).

[!code-csharp-interactive[?? operator](snippets/shared/NullableValueTypes.cs#NullCoalescing)]

`null` 대신 기본 값 형식의 [기본값](default-values.md)을 사용하려면 <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> 메서드를 사용합니다.

다음 예제와 같이 null 허용 값 형식을 null을 허용하지 않는 형식으로 명시적으로 캐스트할 수도 있습니다.

[!code-csharp[explicit cast](snippets/shared/NullableValueTypes.cs#Cast)]

런타임 시 nullable 값 형식의 값이 `null`인 경우 명시적 캐스트는 <xref:System.InvalidOperationException>을 throw합니다.

null을 허용하지 않는 값 형식 `T`는 해당 null 허용 값 형식 `T?`로 암시적으로 변환될 수 있습니다.

## <a name="lifted-operators"></a>리프트 연산자

미리 정의된 단항 및 이항 [연산자](../operators/index.md) 또는 값 형식 `T`에서 지원하는 오버로드된 연산자는 해당 null 허용 값 형식 `T?`에서도 지원합니다. *리프트 연산자* 라고도 하는 이러한 연산자는 하나 또는 두 개의 피연산자가 `null`인 경우 `null` 값을 생성하고, 그렇지 않으면 연산자는 포함된 피연산자 값을 사용하여 결과를 계산합니다. 예를 들어:

[!code-csharp[lifted operators](snippets/shared/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> `|` 형식의 경우 미리 정의된 `bool?` 및 `&` 연산자는 이 섹션에서 설명된 규칙을 따르지 않습니다. 연산자 평가의 결과는 피연산자 중 하나가 `null`인 경우에도 Null이 아닐 수 있습니다. 자세한 내용은 [부울 논리 연산자](../operators/boolean-logical-operators.md) 문서의 [Nullable 부울 논리 연산자](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) 섹션을 참조하세요.

[비교 연산자](../operators/comparison-operators.md) `<`, `>`, `<=` 및 `>=`의 경우 피연산자 중 하나 또는 둘 모두가 `null`이면 결과는 `false`입니다. 그렇지 않으면 포함된 피연산자 값을 비교합니다. 특정 비교(예: `<=`)에서는 `false`를 반환하고 그 반대의 비교(`>`)에서는 `true`를 반환한다고 가정하지 마십시오. 다음 예제에서는 10이

- `null`보다 크지도, 같지도 않고
- `null`보다 작지도 않음을 보여줍니다.

[!code-csharp-interactive[relational and equality operators](snippets/shared/NullableValueTypes.cs#ComparisonOperators)]

[같음 연산자](../operators/equality-operators.md#equality-operator-) `==`의 경우 두 피연산자 모두 `null`이면 결과는 `true`이고 피연산자 중 하나만 `null`이면 결과는 `false`입니다. 그렇지 않으면 포함된 피연산자 값을 비교합니다.

[같지 않음 연산자](../operators/equality-operators.md#inequality-operator-) `!=`의 경우 두 피연산자 모두 `null`이면 결과는 `false`이고 피연산자 중 하나만 `null`이면 결과는 `true`입니다. 그렇지 않으면 포함된 피연산자 값을 비교합니다.

두 값 형식 사이에 [사용자 정의 변환](../operators/user-defined-conversion-operators.md)이 있는 경우 해당 null 허용 값 형식 사이에도 같은 변환을 사용할 수 있습니다.

## <a name="boxing-and-unboxing"></a>boxing 및 unboxing

Null 허용 값 형식 `T?`의 인스턴스는 다음과 같이 [box](../../programming-guide/types/boxing-and-unboxing.md)됩니다.

- <xref:System.Nullable%601.HasValue%2A>가 `false`를 반환하는 경우 Null 참조가 생성됩니다.
- <xref:System.Nullable%601.HasValue%2A>가 `true`를 반환하는 경우 <xref:System.Nullable%601>의 인스턴스가 아닌 기본 값 형식 `T`의 인스턴스가 box됩니다.

다음 예제와 같이 값 형식 `T`의 boxed 값을 해당 null 허용 값 형식 `T?`로 unbox할 수 있습니다.

[!code-csharp-interactive[boxing and unboxing](snippets/shared/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a>Null 허용 값 형식 식별 방법

다음 예제는 <xref:System.Type?displayProperty=nameWithType> 인스턴스가 구성된 null 허용 값 형식(지정된 형식 매개 변수 `T`가 포함된 <xref:System.Nullable%601?displayProperty=nameWithType> 형식)을 나타내는지 확인하는 방법을 보여 줍니다.

[!code-csharp-interactive[whether Type is nullable](snippets/shared/NullableValueTypes.cs#IsTypeNullable)]

예제에서와 같이 [typeof](../operators/type-testing-and-cast.md#typeof-operator) 연산자를 사용하여 <xref:System.Type?displayProperty=nameWithType> 인스턴스를 만듭니다.

인스턴스가 있는지 nullable 값 형식인지 여부를 확인하려는 경우 위의 코드로 테스트되도록 <xref:System.Type> 인스턴스를 가져오는 데 <xref:System.Object.GetType%2A?displayProperty=nameWithType> 메서드를 사용하지 마세요. nullable 값 형식의 인스턴스에서 <xref:System.Object.GetType%2A?displayProperty=nameWithType> 메서드를 호출하는 경우 인스턴스는 <xref:System.Object>로 [boxing](#boxing-and-unboxing)됩니다. Null 허용 값 형식의 Null이 아닌 인스턴스의 boxing은 기본 형식 값의 boxing과 동일하며, <xref:System.Object.GetType%2A>는 null 허용 값 형식의 기본 형식을 나타내는 <xref:System.Type> 인스턴스를 반환합니다.

[!code-csharp-interactive[GetType example](snippets/shared/NullableValueTypes.cs#GetType)]

그리고 인스턴스가 null 허용 값 형식인지 여부를 확인하는 데 [is](../operators/type-testing-and-cast.md#is-operator) 연산자를 사용하지 마세요. 다음 예제에서와 같이 null 허용 값 형식 인스턴스와 `is` 연산자를 사용하는 해당 형식 인스턴스를 구분할 수 없습니다.

[!code-csharp-interactive[is operator example](snippets/shared/NullableValueTypes.cs#IsOperator)]

다음 예제에서 제공된 코드를 사용하여 인스턴스가 nullable 값 형식인지 여부를 확인할 수 있습니다.

[!code-csharp-interactive[whether an instance is of a nullable type](snippets/shared/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> 이 섹션에서 설명하는 방법은 [nullable 참조 형식](nullable-reference-types.md)의 경우에는 적용되지 않습니다.

## <a name="c-language-specification"></a>C# 언어 사양

자세한 내용은 [C# 언어 사양](~/_csharplang/spec/introduction.md)의 다음 섹션을 참조하세요.

- [Nullable 형식](~/_csharplang/spec/types.md#nullable-types)
- [리프트 연산자](~/_csharplang/spec/expressions.md#lifted-operators)
- [암시적 null 허용 전환](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [명시적 null 허용 전환](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [리프트 변환 연산자](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a>참조

- [C# 참조](../index.md)
- ['리프트'란 정확히 어떤 의미입니까?](/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [nullable 참조 형식](nullable-reference-types.md)
