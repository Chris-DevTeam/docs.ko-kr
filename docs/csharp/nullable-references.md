---
title: nullable 참조 형식
description: 이 문서에서는 C# 8.0에 추가된 nullable 참조 형식에 대해 간략하게 설명합니다. 이 기능이 신규 및 기존의 프로젝트의 null 참조 예외에 대해 어떻게 안전성을 제공하는지 알아봅니다.
ms.technology: csharp-null-safety
ms.date: 04/21/2020
ms.openlocfilehash: b4906987ee23f458c1da9754ed7b402621169f63
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099345"
---
# <a name="nullable-reference-types"></a>nullable 참조 형식

C# 8.0에는 참조 형식 변수의 속성에 대한 중요한 설명을 할 수 있는 **nullable 참조 형식** 과 **nullable이 아닌 참조 형식** 이 도입되었습니다.

- **참조는 null이 아니어야 합니다**. 변수에 null이 허용되지 않는 경우 컴파일러는 null이 아닌지 먼저 확인하지 않고 이러한 참조를 역참조하기에 안전한지 확인하는 규칙을 적용합니다.
  - 이 변수는 null이 아닌 값으로 초기화되어야 합니다.
  - 이 변수에는 `null` 값을 절대로 할당할 수 없습니다.
- **참조에 null이 허용됩니다**. 변수에 null이 허용되는 경우 컴파일러는 null 참조 검사를 제대로 했는지 확인하는 다른 규칙을 적용합니다.
  - 컴파일러가 해당 값이 null이 아님을 보장할 수 있는 경우에만 변수를 역참조할 수 있습니다.
  - 이러한 변수는 기본 `null` 값으로 초기화할 수 있으며 다른 코드에서 `null` 값을 할당할 수 있습니다.

이 새로운 기능은 변수 선언에서 설계 의도를 파악할 수 없었던 이전 버전의 C#에 비해 참조 변수 처리에 관한 상당한 이점을 제공합니다. 기존 컴파일러는 참조 형식의 null 참조 예외에 대해 안전성을 제공하지 않았습니다.

- **참조가 null일 수 있습니다**. 참조 형식 변수가 `null`로 초기화되거나 나중에 `null`이 할당되는 경우 컴파일러는 경고를 발생하지 않습니다. 컴파일러는 이러한 변수가 null 검사 없이 역참조될 때 경고를 발생시킵니다.
- **참조가 null이 아닌 것으로 간주됩니다**. 컴파일러는 참조 형식이 역참조될 때 어떠한 경고도 발생시키지 않습니다. 변수가 null일 수 있는 식으로 설정된 경우 컴파일러에서 경고를 발생시킵니다.

이러한 경고는 컴파일 시에 내보내집니다. 컴파일러는 null 허용 컨텍스트에 null 검사 또는 다른 런타임 구성을 추가하지 않습니다. 런타임 시 null 허용 참조와 null을 허용하지 않는 참조는 동일합니다.

Nullable 참조 형식을 추가함으로써 의도를 보다 명확하게 선언할 수 있습니다. `null` 값은 변수가 값을 참조하지 않음을 나타내는 올바른 방법입니다. 코드에서 모든 `null` 값을 제거하는 데 이 기능을 사용하지 마세요. 대신, 컴파일러 및 코드를 읽는 다른 개발자에게 의도를 선언해야 합니다. 의도를 선언해 놓으면 컴파일러는 해당 의도와 일치하지 않는 코드 작성 시 이를 알려줍니다.

**nullable 참조 형식** 은 [nullable 값 형식](language-reference/builtin-types/nullable-value-types.md)과 동일한 구문을 사용하여 작성합니다. 변수 형식에 `?`가 추가됩니다. 예를 들어 다음 변수 선언은 nullable 문자열 변수 `name`을 나타냅니다.

```csharp
string? name;
```

형식 이름에 `?`가 추가되지 않은 모든 변수는 **null을 허용하지 않는 참조 형식** 입니다. 여기에는 이 기능을 설정한 기존 코드에 있는 모든 참조 형식 변수가 포함됩니다.

컴파일러는 정적 분석을 사용하여 nullable 참조가 null이 아닌 것으로 알려져 있는지 확인합니다. 컴파일러는 null일 수 있는 nullable 참조를 역참조하는 경우 경고를 표시합니다. 변수 이름 뒤에 [null 허용 연산자](language-reference/operators/null-forgiving.md) `!`를 사용하여 이 동작을 재정의할 수 있습니다. 예를 들어 `name` 변수가 null이 아닌 것으로 알고 있는데 컴파일러 경고가 발생하는 경우 다음 코드를 작성하여 컴파일러 분석을 재정의할 수 있습니다.

```csharp
name!.Length;
```

## <a name="nullability-of-types"></a>형식의 Null 허용 여부

모든 참조 형식은 경고가 생성되는 경우를 설명하는 4가지 *nullabilities(Null 허용 여부)* 중 하나일 수 있습니다.

- *Nonnullable(Null 허용 안 함)* : 이 형식의 변수에는 null을 할당할 수 없습니다. 이 형식의 변수는 역참조되기 전에 null 검사가 필요하지 않습니다.
- *Nullable(Null 허용)* : 이 형식의 변수에는 null을 할당할 수 있습니다. `null`에 대한 사전 검사 없이 이 형식의 변수를 역참조하면 경고가 발생합니다.
- *Oblivious(모호한)* : C# 8.0 이전 상태는 명확하지 않습니다. 이 형식의 변수는 경고 없이 역참조되거나 할당될 수 있습니다.
- *Unknown(알 수 없음)* : Unknown(알 수 없음)은 형식이 *nullable* 또는 *nonnullable* 이어야 하는지 제약 조건으로 컴파일러에 명시하지 않은 형식 매개 변수에 일반적입니다.

변수 선언에서 형식의 null 허용 여부는 변수가 선언된 *nullable 컨텍스트* 로 제어됩니다.

## <a name="nullable-contexts"></a>Nullable 컨텍스트

Nullable 컨텍스트를 통해 컴파일러가 참조 형식 변수를 해석하는 방식을 미세하게 제어할 수 있습니다. 지정된 소스 줄의 **nullable 주석 컨텍스트** 는 enabled 또는 disabled입니다. C# 8.0 이전 컴파일러는 사용할 수 없는 nullable 컨텍스트에서 모든 코드를 컴파일하는 것으로 생각할 수 있습니다. 모든 참조 형식은 null일 수 있습니다. **nullable 경고 컨텍스트** 도 enabled 또는 disabled일 수 있습니다. nullable 경고 컨텍스트는 컴파일러가 해당 흐름 분석을 사용하여 생성한 경고를 지정합니다.

*.csproj* 파일에 `Nullable` 요소를 사용하여 프로젝트에 대한 nullable 주석 컨텍스트 및 nullable 경고 컨텍스트를 설정할 수 있습니다. 이 요소는 컴파일러가 형식의 null 허용 여부를 해석하는 방법 및 생성되는 경고를 구성합니다. 유효한 설정은 다음과 같습니다.

- `enable`: nullable 주석 컨텍스트가 **enabled** 입니다. nullable 경고 컨텍스트가 **enabled** 입니다.
  - 예를 들어 참조 형식 변수 `string`은 null이 아닙니다.  모든 null 허용 여부 경고가 enabled입니다.
- `warnings`: nullable 주석 컨텍스트가 **disabled** 입니다. nullable 경고 컨텍스트가 **enabled** 입니다.
  - 참조 형식의 변수가 모호합니다. 모든 null 허용 여부 경고가 enabled입니다.
- `annotations`: nullable 주석 컨텍스트가 **enabled** 입니다. nullable 경고 컨텍스트가 **disabled** 입니다.
  - 참조 형식의 변수(예: 문자열)는 null을 허용하지 않습니다. 모든 null 허용 여부 경고가 disabled입니다.
- `disable`: nullable 주석 컨텍스트가 **disabled** 입니다. nullable 경고 컨텍스트가 **disabled** 입니다.
  - 참조 형식의 변수는 이전 버전의 C#과 마찬가지로 모호할 수 있습니다. 모든 null 허용 여부 경고가 disabled입니다.

**예제**:

```xml
<Nullable>enable</Nullable>
```

또한 지시문을 사용하여 프로젝트의 아무 곳에나 이러한 동일한 컨텍스트를 설정할 수도 있습니다.

- `#nullable enable`: nullable 주석 컨텍스트와 nullable 경고 컨텍스트를 **enabled** 로 설정합니다.
- `#nullable disable`: nullable 주석 컨텍스트와 nullable 경고 컨텍스트를 **disabled** 로 설정합니다.
- `#nullable restore`: nullable 주석 컨텍스트와 nullable 경고 컨텍스트를 프로젝트 설정으로 복원합니다.
- `#nullable disable warnings`: nullable 경고 컨텍스트를 **disabled** 로 설정합니다.
- `#nullable enable warnings`: nullable 경고 컨텍스트를 **enabled** 로 설정합니다.
- `#nullable restore warnings`: nullable 경고 컨텍스트를 프로젝트 설정으로 복원합니다.
- `#nullable disable annotations`: nullable 주석 컨텍스트를 **disabled** 로 설정합니다.
- `#nullable enable annotations`: nullable 주석 컨텍스트를 **enabled** 로 설정합니다.
- `#nullable restore annotations`: 주석 경고 컨텍스트를 프로젝트 설정으로 복원합니다.

> [!IMPORTANT]
> 전역 null 허용 컨텍스트는 생성된 코드 파일에 적용되지 않습니다. 두 전략에서 null 허용 컨텍스트는 생성됨으로 표시된 모든 소스 파일에 대해 *disabled* 입니다. 즉, 생성된 파일의 API가 주석 처리되지 않습니다. 다음 네 가지 방법으로 파일은 생성됨으로 표시됩니다.
>
> 1. .editorconfig에서 해당 파일에 적용되는 섹션에 `generated_code = true`를 지정합니다.
> 1. 파일의 맨 위에 있는 주석에 `<auto-generated>` 또는 `<auto-generated/>`를 배치합니다. 해당 주석의 모든 줄에 넣을 수 있지만 주석 블록은 파일의 첫 번째 요소여야 합니다.
> 1. 파일 이름을 *TemporaryGeneratedFile_* 로 시작합니다.
> 1. 파일 이름을 *.designer.cs*, *.generated.cs*, *.g.cs* 또는 *.g.i.cs* 로 종료합니다.
>
> 생성기는 [`#nullable`](language-reference/preprocessor-directives/preprocessor-nullable.md) 전처리기 지시문을 사용하여 옵트인할 수 있습니다.

기본적으로 null 허용 주석 및 경고 컨텍스트는 새 프로젝트를 포함하여 **사용 안 함** 입니다. 이는 기존 코드가 변경 없이 새로운 경고를 생성하지 않고 컴파일됨을 의미합니다.

이러한 옵션은 null 허용 참조 형식을 사용하도록 [기존 코드베이스를 업데이트](nullable-migration-strategies.md)하는 두 가지 고유한 전략을 제공합니다.

## <a name="nullable-annotation-context"></a>nullable 주석 컨텍스트

컴파일러는 disabled nullable 주석 컨텍스트에 다음 규칙을 사용합니다.

- disabled 컨텍스트에서 nullable 참조를 선언할 수 없습니다.
- 모든 참조 변수에는 null 값을 할당할 수 있습니다.
- 참조 형식의 변수가 역참조되면 경고가 생성되지 않습니다.
- disabled 컨텍스트에는 null 허용 연산자를 사용할 수 없습니다.

동작은 이전 버전의 C#과 같습니다.

컴파일러는 enabled nullable 주석 컨텍스트에 다음 규칙을 사용합니다.

- 모든 참조 형식의 변수는 **nullable이 아닌 참조** 입니다.
- nullable이 아닌 모든 참조는 안전하게 역참조될 수 있습니다.
- 모든 nullable 참조 형식(변수 선언에서 형식 뒤에 `?` 표시)은 null일 수 있습니다. 정적 분석은 값이 역참조될 때 null이 아닌 것으로 알려져 있는지 확인합니다. 아닌 경우 컴파일러가 경고를 생성합니다.
- null 허용 연산자를 사용하여 nullable 참조가 null이 아님을 선언할 수 있습니다.

enabled nullable 주석 컨텍스트에서 참조 형식에 추가된 `?` 문자는 **nullable 참조 형식** 을 선언합니다. **null 비허용 연산자** `!`를 식 뒤에 추가하여 식이 null이 아님을 선언할 수 있습니다.

## <a name="nullable-warning-context"></a>Nullable 경고 컨텍스트

nullable 경고 컨텍스트는 nullable 주석 컨텍스트와 다릅니다. 새 주석이 해제(disabled)되어도 경고는 설정(enabled)할 수 있습니다. 컴파일러는 정적 흐름 분석을 사용하여 모든 참조에 대한 **null 상태** 를 확인합니다. null 상태는 *nullable 경고 컨텍스트* 가 **disabled** 가 아닌 경우 **null이 아님** 또는 **null일 수 있음** 입니다. 컴파일러가 **null일 수 있음** 으로 확인한 경우 역참조하면 경고가 발생합니다. 참조 상태는 컴파일러가 다음 두 조건 중 하나를 확인할 수 없으면 **null일 수 있음** 입니다.

1. 변수에 null이 아닌 값이 명확하게 할당되었습니다.
1. 변수 또는 식이 역참조되기 전에 null 검사되었습니다.

컴파일러는 nullable 경고 컨텍스트에서 **null일 수 있는** 변수 또는 식을 역참조할 때 경고를 생성합니다. 또한 컴파일러는 활성화된 null 허용 주석 컨텍스트에서 null을 허용하지 않는 참조 형식에 **null일 수 있음** 변수 또는 식이 할당되면 경고를 생성합니다.

## <a name="attributes-describe-apis"></a>API를 설명하는 특성

인수 또는 반환 값이 null일 수 있거나 null이 될 수 없는 경우에 대한 자세한 정보를 컴파일러에 제공하는 API에 특성을 추가합니다. [null 허용 특성](language-reference/attributes/nullable-analysis.md)을 다루는 언어 참조의 문서에서 이러한 특성에 대해 자세히 알아볼 수 있습니다. 이러한 특성은 현재 및 이후 릴리스에서 .NET 라이브러리에 추가됩니다. 가장 일반적으로 사용되는 API가 먼저 업데이트됩니다.

## <a name="known-pitfalls"></a>알려진 문제

참조 유형을 포함하는 배열 및 구조체는 nullable 참조 형식 기능의 알려진 문제입니다.

### <a name="structs"></a>구조체

null을 허용하지 않는 참조 형식을 포함하는 구조에서는 경고 없이 `default`를 할당할 수 있습니다. 다음 예제를 참조하세요.

```csharp
using System;

#nullable enable

public struct Student
{
    public string FirstName;
    public string? MiddleName;
    public string LastName;
}

public static class Program
{
    public static void PrintStudent(Student student)
    {
        Console.WriteLine($"First name: {student.FirstName.ToUpper()}");
        Console.WriteLine($"Middle name: {student.MiddleName.ToUpper()}");
        Console.WriteLine($"Last name: {student.LastName.ToUpper()}");
    }

    public static void Main() => PrintStudent(default);
}
```

앞의 예제에서 null을 허용하지 않는 참조 형식 `FirstName` 및 `LastName`이 null인 동안 `PrintStudent(default)`에는 경고가 없습니다.

또 다른 일반적인 사례는 일반 구조체를 처리하는 경우입니다. 다음 예제를 참조하세요.

```csharp
#nullable enable

public struct Foo<T>
{
    public T Bar { get; set; }
}

public static class Program
{
    public static void Main()
    {
        string s = default(Foo<string>).Bar;
    }
}
```

앞의 예제에서 `Bar` 속성은 런타임 시 `null`이 되고 경고 없이 null을 허용하지 않는 문자열에 할당됩니다.

### <a name="arrays"></a>배열

배열은 nullable 참조 형식의 알려진 문제가 되기도 합니다. 경고를 생성하지 않는 다음 예제를 고려하세요.

```csharp
using System;

#nullable enable

public static class Program
{
    public static void Main()
    {
        string[] values = new string[10];
        string s = values[0];
        Console.WriteLine(s.ToUpper());
    }
}
```

앞의 예제에서 배열 선언은 해당 요소가 모두 null로 초기화되는 동안 null을 허용하지 않는 문자열을 보유함을 나타냅니다. 그런 다음, `s` 변수에는 null 값(배열의 첫 번째 요소)이 할당됩니다. 마지막으로 `s` 변수가 역참조되어 런타임 예외가 발생합니다.

## <a name="see-also"></a>참조

- [Nullable 참조 형식 사양 초안](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md)
- [Nullable 참조 소개 자습서](tutorials/nullable-reference-types.md)
- [기존 코드베이스를 nullable 참조로 마이그레이션](tutorials/upgrade-to-nullable-references.md)
- [-nullable(C# 컴파일러 옵션)](language-reference/compiler-options/nullable-compiler-option.md)
