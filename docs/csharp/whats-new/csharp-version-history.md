---
title: C#의 역사 - C# 가이드
description: 이 언어의 초창기 버전은 어떤 모습이었으며 이후 어떻게 변했는가?
author: erikdietrich
ms.date: 04/08/2020
ms.openlocfilehash: 0f6739ba7a2dd0488c52b917c4a60a1b3f04a930
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100456421"
---
# <a name="the-history-of-c"></a>C\#의 역사

이 문서에서는 C# 언어의 각 주요 릴리스에 대한 기록을 제공합니다. C# 팀은 계속해서 새로운 기능을 혁신하고 추가하고 있습니다. 예정된 릴리스에서 고려되는 기능을 비롯한 자세한 언어 기능 상태는 GitHub의 [dotnet/roslyn 리포지토리에서](https://github.com/dotnet/roslyn/blob/master/docs/Language%20Feature%20Status.md) 확인할 수 있습니다.

> [!IMPORTANT]
> C # 언어는 C# 사양이 일부 기능에 대해 *표준 라이브러리* 로 정의하는 형식 및 메서드를 사용합니다. .NET 플랫폼은 다양한 패키지에서 이러한 유형과 메서드를 제공합니다. 한 가지 예는 예외 처리입니다. 모든 `throw` 문 또는 식은 throw된 개체가 <xref:System.Exception>에서 파생되는지 확인합니다. 마찬가지로 모든 `catch`는 발견되는 형식이 <xref:System.Exception>에서 파생되는지 확인합니다. 각 버전은 새 요구 사항을 추가할 수 있습니다. 이전 환경에서 최신 언어 기능을 사용하려면 특정 라이브러리를 설치해야 합니다. 이러한 종속성은 각 특정 버전에 대한 페이지에서 설명합니다. 이 종속성의 배경은 [언어 및 라이브러리 간 관계](relationships-between-language-and-library.md)에서 자세히 알아볼 수 있습니다.

C# 빌드 도구는 최신 주요 언어 릴리스가 기본 언어 버전으로 고려합니다. 주요 릴리스 사이에는 이 섹션의 다른 문서에서 상세히 설명한 포인트 릴리스가 있을 수 있습니다. 포인트 릴리스에서 최신 기능을 사용하려면 [컴파일러 언어 버전을 구성](../language-reference/configure-language-version.md)하고 해당 버전을 선택해야 합니다. C# 7.0 이후 세 가지 포인트 릴리스가 있습니다.

- C# 7.3:
  - C# 7.3은 [Visual Studio 2017 버전 15.7](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) 및 [.NET Core 2.1 SDK](../../core/whats-new/dotnet-core-2-1.md)부터 사용할 수 있습니다.
- C# 7.2:
  - C# 7.2는 [Visual Studio 2017 버전 15.5](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) 및 [.NET Core 2.0 SDK](../../core/whats-new/dotnet-core-2-0.md)부터 사용할 수 있습니다.
- C# 7.1:
  - C# 7.1은 [Visual Studio 2017 버전 15.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) 및 [.NET Core 2.0 SDK](../../core/whats-new/dotnet-core-2-0.md)부터 사용할 수 있습니다.

## <a name="c-version-10"></a>C# 버전 1.0

돌이켜보면 Visual Studio.Net 2002와 함께 릴리스된 C# 버전 1.0은 Java와 매우 비슷했습니다. [ECMA에 대해 명시된 설계 목표의 일부](https://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html)로 "단순하고 현대적인 범용 개체 지향 언어"를 추구했습니다.  당시에 Java와 같은 형태는 이러한 초기 설계 목표를 달성한 것을 의미했습니다.

그러나 지금 다시 C# 1.0을 돌이켜보면 조금 어지러워질 것입니다. 기본 제공 비동기 기능과 당연한 것으로 여겨지는 제네릭과 관련된 멋진 기능 중 일부가 부족했습니다. 사실, 제네릭이 아예 없었습니다.  그리고 [LINQ](../linq/index.md)는 아직 사용할 수 없습니다. 그러한 추가 사항은 나올 때까지 몇 년이 걸릴 것입니다.

C# 버전 1.0은 오늘날보다 기능이 없는 편이었습니다. 좀 더 자세한 코드를 작성해야 했습니다. 하지만 출발점이 필요했습니다. C# 버전 1.0은 Windows 플랫폼에서 Java를 대체하는 실용적인 방법이었습니다.

C# 1.0의 주요 기능에는 다음이 포함되어 있습니다.

- [클래스](../programming-guide/classes-and-structs/classes.md)
- [구조체](../language-reference/builtin-types/struct.md)
- [인터페이스](../programming-guide/interfaces/index.md)
- [이벤트](../events-overview.md)
- [속성](../properties.md)
- [대리자](../delegates-overview.md)
- [연산자 및 식](../language-reference/operators/index.md)
- [문](../programming-guide/statements-expressions-operators/statements.md)
- [특성](../programming-guide/concepts/attributes/index.md)

## <a name="c-version-12"></a>C# 버전 1.2

C# 버전 1.2는 Visual Studio .NET 2003과 함께 제공됩니다. 여기에는 언어에 대한 몇 가지 작은 개선이 포함되어 있습니다. 가장 주목할 만한 점은 이 버전부터 <xref:System.Collections.IEnumerator>가 <xref:System.IDisposable>를 구현할 때 <xref:System.Collections.IEnumerator>의 <xref:System.IDisposable.Dispose%2A>라는 `foreach` 루트에서 생성된 코드입니다.

## <a name="c-version-20"></a>C# 버전 2.0

이제 흥미로운 일이 시작됩니다. Visual Studio 2005와 함께 2005년에 릴리스된 C# 2.0의 몇 가지 주요 기능을 살펴보겠습니다.

- [제네릭](../programming-guide/generics/index.md)
- [부분 형식(Partial Type)](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [무명 메서드](../language-reference/operators/delegate-operator.md)
- [Nullable 값 형식](../language-reference/builtin-types/nullable-value-types.md)
- [반복기](../programming-guide/concepts/iterators.md)
- [공변성(Covariance) 및 반공변성(Contravariance)](../programming-guide/concepts/covariance-contravariance/index.md)

기존 기능에 추가된 기타 C# 2.0 기능은 다음과 같습니다.

- getter/setter 별도의 액세스 가능
- 메서드 그룹 변환(대리자)
- 정적 클래스
- 대리자 유추

C#은 일반적인 OO(개체 지향) 언어로 시작되었지만 C# 버전 2.0을 통해 급격히 바뀌었습니다. C#이 자리를 잡은 후 개발자들은 몇 가지 심각한 고민을 겪었습니다. 이후 대대적인 문제가 발생했습니다.

제네릭을 사용하면 형식을 안전하게 유지하면서 임의의 형식에서 형식 및 메서드를 작동할 수 있습니다. 예를 들어 <xref:System.Collections.Generic.List%601>를 사용하면 `List<string>` 또는 `List<int>`를 사용하고 이를 반복하는 동안 해당 문자열이나 정수에 형식이 안전한 작업을 수행할 수 있습니다. 모든 작업에서 `ArrayList`에서 파생된 `ListInt` 형식을 만들거나 `Object`에서 캐스팅하는 것보다 제네릭을 사용하는 것이 좋습니다.

C# 버전 2.0에서는 반복기라는 기능이 도입되었습니다. 간단히 말해서, 반복기를 사용하면 `List`(또는 다른 열거 가능 형식)의 모든 항목을 `foreach` 루프로 검사할 수 있습니다. 반복기를 언어의 첫 번째 클래스 부분에 사용하면 언어의 가독성과 사용자의 코드 추론 능력이 크게 향상됩니다.

그리고 이때까지 C#은 Java를 따라잡으려는 노력을 계속했습니다. Java는 이미 제네릭 및 반복기가 포함된 버전을 출시했습니다. 하지만 언어가 계속 발전함에 따라 곧 변경될 것입니다.

## <a name="c-version-30"></a>C# 버전 3.0

C# 버전 3.0은 Visual Studio 2008과 함께 2007년말에 출시되었지만 언어 기능을 완전히 갖춘 버전은 .NET Framework 버전 3.5와 함께 제공됩니다. 이 버전은 C#의 성장에 큰 변화를 가져왔습니다. C#은 진정으로 강력한 프로그래밍 언어로 자리매김했습니다. 이 버전의 몇 가지 주요 특징을 살펴보겠습니다.

- [자동 구현 속성](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [무명 형식](../programming-guide/classes-and-structs/anonymous-types.md)
- [쿼리 식](../linq/query-expression-basics.md)
- [람다 식](../language-reference/operators/lambda-expressions.md)
- [식 트리](../expression-trees.md)
- [확장 메서드](../programming-guide/classes-and-structs/extension-methods.md)
- [암시적 형식 지역 변수](../language-reference/keywords/var.md)
- [부분 메서드](../language-reference/keywords/partial-method.md)
- [개체 및 컬렉션 이니셜라이저](../programming-guide/classes-and-structs/object-and-collection-initializers.md)

되돌아보면, 이러한 특징은 대부분 필연적이고 불가분한 것입니다. 이러한 모든 특징은 전략적으로 잘 맞습니다. 일반적으로 C# 버전의 핵심 기능은 LINQ(Language-Integrated Query)라고도 하는 쿼리 식이라 생각합니다.

더 미묘한 뷰는 LINQ가 생성되는 기반인 식 트리, 람다 식 및 익명 형식을 검사합니다. 하지만 두 경우 모두 C# 3.0은 혁신적인 개념을 제공합니다. C# 3.0은 C#을 하이브리드 개체 지향/기능 언어로 전환하기 위한 토대를 마련하기 시작했습니다.

특히, 이제 무엇보다도 컬렉션에 대한 작업을 수행할 수 있는 SQL 스타일의 선언적 쿼리를 작성할 수 있습니다. 정수 목록의 평균을 계산하는 `for` 루프를 작성하는 대신 이제 간단하게 `list.Average()`로 처리할 수 있습니다. 쿼리 식과 확장 메서드의 조합은 정수 목록을 훨씬 더 효율적으로 보이게 해줍니다.

실제로 개념을 파악하고 통합하는 데는 시간이 걸렸지만 점진적으로 그 개념이 완성되었습니다. 그리고 몇 년이 지난 지금, 코드는 훨씬 더 간결하고 간단하며 기능적입니다.

## <a name="c-version-40"></a>C# 버전 4.0

Visual Studio 2010과 함께 릴리스된 C# 버전 4.0은 버전 3.0의 혁신에 따른 기대에 부응하느라 어려움을 겪을 것으로 예상되었습니다. 버전 3.0에서 C#은 Java의 그림자를 확실히 벗어나 두각을 나타내었습니다. 금세 정교해졌습니다.

다음 버전에서는 몇 가지 흥미로운 새 기능이 도입되었습니다.

- [동적 바인딩](../language-reference/builtin-types/reference-types.md)
- [명명된/선택적 인수](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [제네릭 공변(covariant) 및 반공변(contravariant)](../../standard/generics/covariance-and-contravariance.md)
- [포함된 interop 형식](../../framework/interop/type-equivalence-and-embedded-interop-types.md)

포함된 interop 형식은 배포의 어려움을 완화합니다. 제네릭 공변성(Covariance)과 반공변성(Contravariance)은 제네릭을 사용하는 기능을 더 많이 제공하지만, 약간 학문적이며, 프레임워크와 라이브러리 작성자에게 가장 높은 평가를 받을 것입니다. 명명되고 선택적인 매개 변수를 사용하면 많은 메서드 오버로드를 제거하고 편리성을 제공할 수 있습니다. 그러나 이러한 기능 중 어느 것도 정확히 패러다임의 변화는 아닙니다.

주요 기능은 `dynamic` 키워드였습니다. `dynamic` 키워드는 C# 버전 4.0에 컴파일 시간에 컴파일러를 재정의하는 기능을 도입했습니다. 동적 키워드를 사용하면 JavaScript와 같이 동적으로 형식화된 언어와 유사한 구조를 만들 수 있습니다. `dynamic x = "a string"`을 만든 다음, 6을 추가하여 다음에 수행해야 할 작업을 런타임에 맡길 수 있습니다.

동적 바인딩은 오류를 유발할 수 있지만 언어 내에서 훌륭한 기능도 제공합니다.

## <a name="c-version-50"></a>C# 버전 5.0

Visual Studio 2012과 함께 릴리스된 C# 버전 5.0은 언어에 중점을 둔 버전이었습니다. 해당 버전에 대한 거의 모든 노력은 다른 획기적인 언어 개념인 비동기 프로그래밍을 위한 `async` 및 `await` 모델로 옮겨 갔습니다.  다음은 주요 기능 목록입니다.

- [비동기 멤버](../async.md)
- [호출자 정보 특성](../language-reference/attributes/caller-information.md)

### <a name="see-also"></a>관련 항목

- [코드 프로젝트: C# 5.0의 호출자 정보 특성](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

호출자 정보 특성을 사용하면 엄청난 양의 상용구 리플렉션 코드를 사용하지 않고도 실행 중인 컨텍스트에 대한 정보를 쉽게 검색할 수 있습니다. 진단 및 로깅 작업의 용도는 매우 다양합니다.

하지만 이 릴리스의 진정한 스타는 `async`과 `await`입니다. 이러한 기능이 2012년에 출시되었을 때 C#은 언어에 첫 번째 클래스 참여자로 비동기를 적용하여 다시 업계의 판도를 바꾸었습니다. 장기 실행 작업 및 콜백 웹 구현을 처리한 적이 있다면 이 언어 기능을 좋아할 것입니다.

## <a name="c-version-60"></a>C# 버전 6.0

버전 3.0과 5.0에서 C#은 개체 지향 언어의 주요 새 기능을 추가했습니다. Visual Studio 2015와 함께 릴리스된 버전 6.0은 주요 핵심 기능 대신 C# 프로그래밍을 보다 생산적으로 만드는 많은 작은 기능을 릴리스했습니다. 다음은 몇 가지 예입니다.

- [정적 가져오기](../language-reference/keywords/using-static.md)
- [예외 필터](../language-reference/keywords/when.md)
- [Auto 속성 이니셜라이저](../properties.md)
- [식 본문 멤버](../language-reference/operators/lambda-operator.md#expression-body-definition)
- [Null 전파자](../language-reference/operators/member-access-operators.md#null-conditional-operators--and-)
- [문자열 보간](../language-reference/tokens/interpolated.md)
- [nameof 연산자](../language-reference/operators/nameof.md)

기타 새로운 기능은 다음과 같습니다.

- 인덱스 이니셜라이저
- Catch/Finally 블록의 Await
- Getter 전용 속성의 기본값

이러한 각 기능은 그 자체로 흥미롭습니다. 그러나 전체적으로 살펴보면 흥미로운 패턴을 볼 수 있습니다. 이 버전에서 C#은 언어 상용구를 제거하여 코드를 더 간결하고 읽기 쉽게 만들었습니다. 따라서 깔끔하고 간단한 코드를 좋아하는 사람들에게 이 언어 버전은 큰 선물이었습니다.

이 버전에는 또 다른 변화가 있지만 본질적으로 기존 언어 기능은 아닙니다. [Roslyn 서비스형 컴파일러](https://github.com/dotnet/roslyn)가 릴리스되었습니다. C# 컴파일러는 이제 C#으로 작성되며, 프로그래밍 작업의 일부로 컴파일러를 사용할 수 있습니다.

## <a name="c-version-70"></a>C# 버전 7.0

C# 버전 7.0은 Visual Studio 2017과 함께 릴리스되었습니다. 이 버전에는 C# 6.0 방식의 혁신적이고 유용한 기능이 있지만 서비스형 컴파일러는 없습니다. 다음은 새 기능 중 일부입니다.

- [외부 변수](./csharp-7.md#out-variables)
- [튜플 및 분해](./csharp-7.md#tuples-and-discards)
- [패턴 일치](./csharp-7.md#pattern-matching)
- [로컬 함수](./csharp-7.md#local-functions)
- [확장된 식 본문 멤버](./csharp-7.md#more-expression-bodied-members)
- [참조 로컬 및 반환](./csharp-7.md#ref-locals-and-returns)

이러한 기능에는 다음이 포함됩니다.

- [삭제](./csharp-7.md#tuples-and-discards)
- [이진 리터럴 및 자릿수 구분 기호](./csharp-7.md#numeric-literal-syntax-improvements)
- [Throw 식](./csharp-7.md#throw-expressions)

이러한 모든 기능은 개발자에게 멋진 새 기능과 이전보다 훨씬 깔끔한 코드를 작성할 수 있는 기회를 제공합니다. 하이라이트는 `out` 키워드와 함께 사용할 변수의 선언을 압축하고 튜플을 통해 여러 개의 반환 값을 허용하는 것입니다.

그러나 C#은 더욱 광범위하게 사용되고 있습니다. .NET Core는 이제 모든 운영 체제를 대상으로 하며 클라우드와 휴대성에 확실히 집중하고 있습니다.  이는 새로운 기능을 제공하는 것 외에도 언어 디자이너가 많이 생각하고 시간을 투자하게 만듭니다.

## <a name="c-version-71"></a>C# 버전 7.1

C#은 C# 7.1과 함께 ‘포인트 릴리스’를 제공하기 시작했습니다.  이 버전은 [언어 버전 선택](../language-reference/configure-language-version.md) 구성 요소, 세 개의 새로운 언어 기능 및 새로운 컴파일러 동작을 추가했습니다.

이 릴리스의 새로운 언어 기능은 다음과 같습니다.

- [`async` `Main` 메서드](./csharp-7.md#async-main)
  - 애플리케이션에 대한 진입점은 `async` 한정자를 가질 수 있습니다.
- [`default` 리터럴 식](./csharp-7.md#default-literal-expressions)
  - 대상 형식을 유추할 수 있는 경우 기본 값 식에서 기본 리터럴 식을 사용할 수 있습니다.
- [유추된 튜플 요소 이름](./csharp-7.md#tuples-and-discards)
  - 튜플 요소의 이름은 대부분의 경우에 튜플 초기화에서 유추할 수 있습니다.
- [제네릭 형식 매개 변수의 패턴 일치](./csharp-7.md#pattern-matching)
  - 형식이 제네릭 형식 매개 변수인 변수에서 패턴 일치 식을 사용할 수 있습니다.

마지막으로 컴파일러에는 [참조 어셈블리 생성](./csharp-7.md#reference-assembly-generation)을 제어하는 두 가지 옵션 `-refout` 및 `-refonly`가 있습니다.

## <a name="c-version-72"></a>C# 버전 7.2

C# 7.2는 몇 가지 작은 언어 기능을 추가했습니다.

- [안전하고 효율적인 코드를 작성하는 방법](./csharp-7.md#enabling-more-efficient-safe-code)
  - 참조 의미 체계를 사용하는 값 유형으로 작동할 수 있는 구문 개선의 조합입니다.
- [뒤에 오지 않는 명명된 인수](./csharp-7.md#non-trailing-named-arguments)
  - 명명된 인수 뒤에는 위치 인수가 올 수 있습니다.
- [숫자 리터럴의 선행 밑줄](./csharp-7.md#numeric-literal-syntax-improvements)
  - 숫자 리터럴은 이제 인쇄된 숫자 앞에 선행 밑줄이 있을 수 있습니다.
- [`private protected` 액세스 한정자](./csharp-7.md#private-protected-access-modifier)
  - `private protected` 액세스 한정자는 동일한 어셈블리의 파생된 클래스에 대해 액세스를 사용합니다.
- [조건부 `ref` 식](./csharp-7.md#conditional-ref-expressions)
  - 이제 조건식(`?:`)의 결과가 참조일 수 있습니다.

## <a name="c-version-73"></a>C# 버전 7.3

C# 7.3 릴리스에는 두 개의 기본 테마가 있습니다. 하나의 테마는 안전한 코드의 성능을 안전하지 않은 코드만큼 향상할 수 있는 기능을 제공합니다. 두 번째 테마는 기존 기능에 대한 점진적인 개선을 제공합니다. 또한 새 컴파일러 옵션이 이 릴리스에 추가되었습니다.

다음 새로운 기능은 안전한 코드에 대해 향상된 성능의 테마를 지원합니다.

- [고정하지 않고 고정 필드에 액세스할 수 있습니다.](csharp-7.md#indexing-fixed-fields-does-not-require-pinning)
- [`ref` 지역 변수를 다시 할당할 수 있습니다.](csharp-7.md#enabling-more-efficient-safe-code)
- [`stackalloc` 배열에서 이니셜라이저를 사용할 수 있습니다.](csharp-7.md#stackalloc-arrays-support-initializers)
- [패턴을 지원하는 모든 형식과 함께 `fixed` 문을 사용할 수 있습니다.](csharp-7.md#more-types-support-the-fixed-statement)
- [추가적인 제네릭 제약 조건을 사용할 수 있습니다.](csharp-7.md#enhanced-generic-constraints)

기존 기능이 다음과 같이 개선되었습니다.

- 튜플 형식으로 `==` 및 `!=`를 테스트할 수 있습니다.
- 더 많은 위치에서 식 변수를 사용할 수 있습니다.
- 자동 구현 속성의 지원 필드에 특성을 연결할 수 있습니다.
- 인수에서 `in`만 다른 경우 메서드 해결이 향상되었습니다.
- 이제 오버로드 해결에 모호한 사례가 감소했습니다.

새 컴파일러 옵션은 다음과 같습니다.

- `-publicsign` - OSS(오픈 소스 소프트웨어) 시그니처를 사용하도록 설정합니다.
- `-pathmap` - 소스 디렉터리에 대한 매핑을 제공합니다.

## <a name="c-version-80"></a>C# 버전 8.0

C# 8.0은 특히 .NET Core C#을 대상으로 하는 첫 번째 주 릴리스입니다. 일부 기능은 새 CLR 기능을 사용하며, 다른 기능은 .NET Core에만 추가된 라이브러리 형식을 사용합니다. C#8.0은 다음 기능 및 향상된 기능을 C# 언어에 추가합니다.

- [읽기 전용 멤버](./csharp-8.md#readonly-members)
- [기본 인터페이스 메서드](./csharp-8.md#default-interface-methods)
- [패턴 일치 개선 사항](./csharp-8.md#more-patterns-in-more-places):
  - [Switch 식](./csharp-8.md#switch-expressions)
  - [속성 패턴](./csharp-8.md#property-patterns)
  - [튜플 패턴](./csharp-8.md#tuple-patterns)
  - [위치 패턴](./csharp-8.md#positional-patterns)
- [using 선언](./csharp-8.md#using-declarations)
- [정적 로컬 함수](./csharp-8.md#static-local-functions)
- [삭제 가능한 ref struct](./csharp-8.md#disposable-ref-structs)
- [nullable 참조 형식](../language-reference/builtin-types/nullable-reference-types.md)
- [비동기 스트림](./csharp-8.md#asynchronous-streams)
- [인덱스 및 범위](./csharp-8.md#indices-and-ranges)
- [null 병합 할당](./csharp-8.md#null-coalescing-assignment)
- [관리되지 않는 생성 형식](./csharp-8.md#unmanaged-constructed-types)
- [중첩 식의 stackalloc](./csharp-8.md#stackalloc-in-nested-expressions)
- [보간된 약어 문자열의 향상된 기능](./csharp-8.md#enhancement-of-interpolated-verbatim-strings)

기본 인터페이스 멤버에는 CLR의 향상된 기능이 필요합니다. 해당 기능은 .NET Core 3.0용 CLR에 추가되었습니다. 범위 및 인덱스와 비동기 스트림에는 .NET Core 3.0 라이브러리의 새 형식이 필요합니다. 인수 및 반환 값의 null 상태에 관한 의미 체계 정보를 제공하도록 라이브러리에 주석이 달린 경우 nullable 참조 형식은 컴파일러에서 구현되는 동안 훨씬 더 유용합니다. 해당 주석은 .NET Core 라이브러리에 추가됩니다.

‘이 문서는 [NDepend 블로그에 최초로 게시되었습니다.](https://blog.ndepend.com/c-versions-look-language-history/) Erik Dietrich 및 Patrick Smacchia 제공.’   
