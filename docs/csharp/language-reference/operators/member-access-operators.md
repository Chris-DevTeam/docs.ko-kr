---
title: 멤버 액세스 연산자 및 식 - C# 참조
description: 형식 멤버에 액세스하는 데 사용하는 C# 연산자에 대해 알아봅니다.
ms.date: 11/13/2020
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
- ^_CSharpKeyword
- .._CSharpKeyword
helpviewer_keywords:
- member access operators [C#]
- member access operator [C#]
- dot operator [C#]
- . operator [C#]
- subscript operator [C#]
- square brackets [] operator [C#]
- indexer operator [C#]
- '[] operator [C#]'
- null-conditional operators [C#]
- Elvis operator [C#]
- ?. operator [C#]
- ?[] operator [C#]
- invocation operator [C#]
- method call [C#]
- method invocation [C#]
- delegate invocation [C#]
- () operator [C#]
- ^ operator [C#]
- index from end operator [C#]
- hat operator [C#]
- .. operator [C#]
- range operator [C#]
ms.openlocfilehash: 28d3d9c3261f1a852d16f2637309b21412611c10
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691242"
---
# <a name="member-access-operators-and-expressions-c-reference"></a>멤버 액세스 연산자 및 식(C# 참조)

형식 멤버에 액세스할 때 다음 연산자 및 식을 사용할 수 있습니다.

- [`.` (멤버 액세스)](#member-access-expression-): 네임스페이스 또는 형식의 멤버 액세스
- [`[]` (배열 요소 또는 인덱서 액세스)](#indexer-operator-): 배열 요소 또는 형식 인덱서 액세스
- [`?.` 및 `?[]`(null 조건부 연산자)](#null-conditional-operators--and-): 피연산자가 null이 아닌 경우에만 멤버 또는 요소 액세스 작업 수행
- [`()` (호출)](#invocation-expression-): 액세스된 메서드나 대리자 호출
- [`^`(끝부터 인덱스)](#index-from-end-operator-): 요소 위치가 시퀀스의 끝에서 시작됨을 표시
- [`..`(범위)](#range-operator-): 시퀀스 요소의 범위를 가져오는 데 사용할 수 있는 인덱스 범위를 지정

## <a name="member-access-expression-"></a>멤버 액세스 식 .

다음 예제와 같이 `.` 토큰을 사용하여 네임스페이스 또는 형식의 멤버에 액세스합니다.

- [`using` 지시문](../keywords/using-directive.md)의 다음 예제와 같이 `.`을 사용하여 네임스페이스 내에 중첩된 네임스페이스에 액세스합니다.

  [!code-csharp[nested namespaces](snippets/shared/MemberAccessOperators.cs#NestedNamespace)]

- 다음 코드와 같이 `.`을 사용하여 ‘정규화된 이름’을 만들고 네임스페이스 내의 형식에 액세스합니다.

  [!code-csharp[qualified name](snippets/shared/MemberAccessOperators.cs#QualifiedName)]

  [`using` 지시문](../keywords/using-directive.md)을 사용하여 정규화된 이름 사용을 선택 사항으로 설정합니다.

- 다음 코드와 같이 `.`을 사용하여 정적 및 비정적 [형식 멤버](../../programming-guide/classes-and-structs/index.md#members)에 액세스합니다.

  [!code-csharp-interactive[type members](snippets/shared/MemberAccessOperators.cs#TypeMemberAccess)]

`.`을 사용하여 [확장 메서드](../../programming-guide/classes-and-structs/extension-methods.md)에 액세스할 수도 있습니다.

## <a name="indexer-operator-"></a>인덱서 연산자 []

대괄호 `[]`는 일반적으로 배열, 인덱서 또는 포인터 요소 액세스에 사용됩니다.

### <a name="array-access"></a>배열 액세스

다음 예제는 배열 요소에 액세스하는 방법을 보여 줍니다.

[!code-csharp-interactive[array access](snippets/shared/MemberAccessOperators.cs#Arrays)]

배열 인덱스가 배열의 해당 차원 범위를 벗어난 경우 <xref:System.IndexOutOfRangeException>이 throw됩니다.

앞의 예제와 같이, 배열 형식을 선언하거나 배열 인스턴스를 인스턴스화할 때도 대괄호를 사용합니다.

배열에 대한 자세한 내용은 [배열](../../programming-guide/arrays/index.md)을 참조하세요.

### <a name="indexer-access"></a>인덱서 액세스

다음 예제는 .NET <xref:System.Collections.Generic.Dictionary%602> 형식을 사용하여 인덱서 액세스를 보여 줍니다.

[!code-csharp-interactive[indexer access](snippets/shared/MemberAccessOperators.cs#Indexers)]

인덱서를 사용하면 배열 인덱싱과 비슷한 방법으로 사용자 정의 형식의 인스턴스를 인덱싱할 수 있습니다. 정수여야 하는 배열 인덱스와 달리, 인덱서 매개 변수는 임의 형식으로 선언할 수 있습니다.

인덱서에 대한 자세한 내용은 [인덱서](../../programming-guide/indexers/index.md)를 참조하세요.

### <a name="other-usages-of-"></a>다른 [] 용도

포인터 요소 액세스에 대한 자세한 내용은 [포인터 관련 연산자](pointer-related-operators.md) 문서의 [포인터 요소 액세스 연산자](pointer-related-operators.md#pointer-element-access-operator-) 섹션을 참조하세요.

또한 대괄호를 사용하여 [특성](../../programming-guide/concepts/attributes/index.md)을 지정합니다.

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a>Null 조건부 연산자 ?. 및 ?[]

C# 6 이상에서 사용할 수 있는 null 조건부 연산자는 피연산자가 null이 아닌 것으로 평가되었을 때만 [멤버 액세스](#member-access-expression-), `?.` 또는 [요소 액세스](#indexer-operator-), `?[]`, 연산을 피연산자에게 적용하며, 그렇지 않으면 `null`을 반환합니다. 즉, 다음과 같습니다.

- `a`가 `null`로 평가되면 `a?.x` 또는 `a?[x]`의 결과는 `null`입니다.
- `a`가 null이 아닌 것으로 평가되면 `a?.x` 또는 `a?[x]`의 결과는 각각 `a.x` 또는 `a[x]`의 결과와 같습니다.

  > [!NOTE]
  > `a.x` 또는 `a[x]`가 예외를 throw하면 `a?.x` 또는 `a?[x]`는 null이 아닌 `a`와 동일한 예외를 throw합니다. 예를 들어 `a`가 null이 아닌 배열 인스턴스이고 `x`가 `a`의 경계 밖에 있는 경우, `a?[x]`는 <xref:System.IndexOutOfRangeException>을 throw합니다.

Null 조건부 연산자는 단락 연산자입니다. 즉 조건부 멤버나 요소 액세스 작업의 한 체인의 작업에서 `null`을 반환하면 나머지 체인은 실행되지 않습니다. 다음 예제에서 `A`가 `null`로 평가되면 `B`가 평가되지 않고, `A` 또는 `B`가 `null`로 평가되면 `C`가 평가되지 않습니다.

```csharp
A?.B?.Do(C);
A?.B?[C];
```

다음 예제에서는 `?.` 및 `?[]` 연산자의 사용법을 보여 줍니다.

[!code-csharp-interactive[null-conditional operators](snippets/shared/MemberAccessOperators.cs#NullConditional)]

또한 앞의 예제에서는 [null 병합 연산자 `??`](null-coalescing-operator.md)를 사용하여 null 조건부 연산 결과가 `null`인 경우 평가할 대체 식을 지정합니다.

`a.x` 또는 `a[x]`가 null을 허용하지 않는 값 형식인 경우 `T`, `a?.x` 또는 `a?[x]`는 해당하는 [null 허용 값 형식](../builtin-types/nullable-value-types.md) `T?`입니다. `T` 형식의 식이 필요하면 다음 예제와 같이 null 병합 연산자 `??`를 null 조건식에 적용합니다.

[!code-csharp-interactive[null-conditional with null-coalescing](snippets/shared/MemberAccessOperators.cs#NullConditionalWithNullCoalescing)]

앞의 예제에서 `??` 연산자를 사용하지 않는 경우 `numbers?.Length < 2`는 `numbers`가 `null`일 때 `false`로 평가됩니다.

Null 조건부 멤버 액세스 연산자 `?.`를 Elvis 연산자라고도 합니다.

### <a name="thread-safe-delegate-invocation"></a>스레드로부터 안전한 대리자 호출

다음 코드에서처럼 `?.` 연산자를 사용하여 대리자가 null이 아닌지 확인하고 스레드로부터 안전한 방식으로 호출합니다(예: [이벤트 발생 시](../../../standard/events/how-to-raise-and-consume-events.md)).

```csharp
PropertyChanged?.Invoke(…)
```

이 코드는 C# 5 및 그 이전에서 사용하는 다음 코드에 해당합니다.

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

이는 null이 아닌 `handler`만 호출되도록 하는 스레드로부터 안전한 방법입니다. 대리자 인스턴스는 변경할 수 없으므로 스레드는 `handler` 지역 변수가 참조하는 개체를 변경할 수 없습니다. 특히 다른 스레드가 실행한 코드가 `PropertyChanged` 이벤트에서 구독을 취소하고 `handler`를 호출하기 전에 `PropertyChanged`가 `null`이 되면 `handler`에서 참조하는 개체는 영향을 받지 않습니다. `?.` 연산자는 왼쪽 피연산자를 한 번만 계산하여 null이 아닌 것으로 확인된 후에는 `null`로 변경할 수 없도록 보장합니다.

## <a name="invocation-expression-"></a>호출 식 ()

괄호(`()`)를 사용하여 [메서드](../../programming-guide/classes-and-structs/methods.md) 또는 [대리자](../../programming-guide/delegates/index.md)를 호출합니다.

다음 예제는 인수를 사용하거나 사용하지 않고 메서드를 호출하는 방법과 대리자를 호출하는 방법을 보여 줍니다.

[!code-csharp-interactive[invocation with ()](snippets/shared/MemberAccessOperators.cs#Invocation)]

[`new`](new-operator.md) 연산자를 사용하여 [생성자](../../programming-guide/classes-and-structs/constructors.md)를 호출하는 경우에도 괄호를 사용합니다.

### <a name="other-usages-of-"></a>다른 () 용도

또한 괄호를 사용하여 식에서 연산을 계산하는 순서를 조정합니다. 자세한 내용은 [C# 연산자](index.md)를 참조하세요.

명시적 형식 변환을 수행하는 [캐스트 식](type-testing-and-cast.md#cast-expression)도 괄호를 사용합니다.

## <a name="index-from-end-operator-"></a>끝부터 인덱스 연산자 ^

C# 8.0 이상에서 사용할 수 있는 연산자 `^`는 요소 위치가 시퀀스의 끝에서 시작함을 나타냅니다. 시퀀스 길이 `length`의 경우 `^n`은 시퀀스의 시작에서 오프셋 `length - n`인 요소를 가리킵니다. 예를 들어 `^1`은 시퀀스의 마지막 요소를 가리키고, `^length`는 시퀀스의 첫 번째 요소를 가리킵니다.

[!code-csharp[index from end](snippets/shared/MemberAccessOperators.cs#IndexFromEnd)]

위 예제에서와 같이 식 `^e`는 <xref:System.Index?displayProperty=nameWithType> 형식입니다. 식 `^e`에서 `e`의 결과는 암시적으로 `int`으로 변환할 수 있어야 합니다.

`^` 연산자를 [범위 연산자](#range-operator-)와 함께 사용하여 인덱스 범위를 만들 수도 있습니다. 자세한 내용은 [인덱스와 범위](../../tutorials/ranges-indexes.md)를 참조하세요.

## <a name="range-operator-"></a>범위 연산자 .

C# 8.0 이상에서 사용 가능한 연산자 `..`은 인덱스 범위의 시작과 끝을 피연산자로 지정합니다. 왼쪽 피연산자는 범위의 시작(*포함*)입니다. 오른쪽 피연산자는 범위의 끝(*제외*)입니다. 다음 예제에서와 같이 피연산자 중 하나는 시퀀스의 시작부터 또는 끝부터 인덱스가 될 수 있습니다.

[!code-csharp[range examples](snippets/shared/MemberAccessOperators.cs#Ranges)]

위 예제에서와 같이 식 `a..b`는 <xref:System.Range?displayProperty=nameWithType> 형식입니다. 식 `a..b`에서 `a` 및 `b`의 결과는 암시적으로 `int` 또는 <xref:System.Index>로 변환할 수 있어야 합니다.

`..` 연산자의 피연산자 중 하나를 생략하여 개방형 범위를 지정할 수 있습니다.

- `a..`는 `a..^0`와 같습니다.
- `..b`는 `0..b`와 같습니다.
- `..`는 `0..^0`와 같습니다.

[!code-csharp[ranges with omitted operands](snippets/shared/MemberAccessOperators.cs#RangesOptional)]

자세한 내용은 [인덱스와 범위](../../tutorials/ranges-indexes.md)를 참조하세요.

## <a name="operator-overloadability"></a>연산자 오버로드 가능성

`.`, `()`, `^` 및 `..` 연산자는 오버로드할 수 없습니다. `[]` 연산자도 오버로드할 수 없는 연산자로 간주됩니다. [인덱서](../../programming-guide/indexers/index.md)를 사용하여 사용자 정의 형식의 인덱싱을 지원합니다.

## <a name="c-language-specification"></a>C# 언어 사양

자세한 내용은 [C# 언어 사양](~/_csharplang/spec/introduction.md)의 다음 섹션을 참조하세요.

- [멤버 액세스](~/_csharplang/spec/expressions.md#member-access)
- [요소 액세스](~/_csharplang/spec/expressions.md#element-access)
- [Null 조건부 연산자](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [호출 식](~/_csharplang/spec/expressions.md#invocation-expressions)

인덱스 및 범위에 대한 자세한 내용은 [기능 제안 노트](~/_csharplang/proposals/csharp-8.0/ranges.md)를 참조하세요.

## <a name="see-also"></a>참조

- [C# 참조](../index.md)
- [C# 연산자 및 식](index.md)
- [??(Null 병합 연산자)](null-coalescing-operator.md)
- [:: 연산자](namespace-alias-qualifier.md)
