---
title: 열거형 형식 대신 열거형 클래스 사용
description: 컨테이너화된 .NET 애플리케이션용 .NET 마이크로 서비스 아키텍처 | 후자의 몇 가지 제한 사항을 해결하는 방법으로 열거형 대신 열거형 클래스를 사용하는 방법을 배웁니다.
ms.date: 11/25/2020
ms.openlocfilehash: a45347d7cc9c3fc6378198ca1c44ba6fecfd54f5
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97899530"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a>열거형 형식 대신 열거형 클래스 사용하기

[열거형](../../../csharp/language-reference/builtin-types/enum.md)(또는 줄여서 *열거형 형식*)은 정수 형식에 대한 씬 언어 래퍼입니다. 닫힌 값 집합에서 값을 저장하는 경우 해당 사용을 제한해야 할 수도 있습니다. 크기(소규모, 중간 규모, 대규모)를 기반으로 하는 분류가 좋은 예입니다. 제어 흐름 또는 추가 추상화에 열거형을 사용하는 것은 [코드 스멜](https://deviq.com/antipatterns/code-smells)일 수 있습니다. 이 형식으로 사용하면 열거형의 값을 확인하는 여러 제어 흐름 문을 사용하여 취약한 코드가 발생합니다.

대신 개체 지향 언어의 모든 풍부한 기능을 활성화하는 열거형 클래스를 만들 수 있습니다.

그러나 중요한 항목은 아니며 대부분의 경우에 간단한 설명을 위해 기본 설정된 기본 [열거형 형식](../../../csharp/language-reference/builtin-types/enum.md)을 계속 사용할 수 있습니다. 열거형 클래스의 사용은 업무와 연관된 개념과 더 관련되어 있습니다.

## <a name="implement-an-enumeration-base-class"></a>열거형 기본 클래스 구현하기

다음 예제와 같이 eShopOnContainers의 마이크로 서비스를 정렬하면 샘플 열거형 기본 클래스 구현을 제공합니다.

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }

    public int Id { get; private set; }

    protected Enumeration(int id, string name) => (Id, Name) = (id, name);

    public override string ToString() => Name;

    public static IEnumerable<T> GetAll<T>() where T : Enumeration =>
        typeof(T).GetFields(BindingFlags.Public |
                            BindingFlags.Static |
                            BindingFlags.DeclaredOnly)
                 .Select(f => f.GetValue(null))
                 .Cast<T>();

    public override bool Equals(object obj)
    {
        if (obj is not Enumeration otherValue)
        {
            return false;
        }

        var typeMatches = GetType().Equals(obj.GetType());
        var valueMatches = Id.Equals(otherValue.Id);

        return typeMatches && valueMatches;
    }

    public int CompareTo(object other) => Id.CompareTo(((Enumeration)other).Id);

    // Other utility methods ...
}
```

다음 `CardType` : `Enumeration` 클래스와 같이 모든 엔터티 또는 값 개체의 형식으로 이 클래스를 사용할 수 있습니다.

```csharp
public class CardType
    : Enumeration
{
    public static CardType Amex = new CardType(1, nameof(Amex));
    public static CardType Visa = new CardType(2, nameof(Visa));
    public static CardType MasterCard = new CardType(3, nameof(MasterCard));

    public CardType(int id, string name)
        : base(id, name)
    {
    }
}
```

## <a name="additional-resources"></a>추가 자료

- **Jimmy Bogard. 열거형 클래스** \
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- **Steve Smith. C#의 열거형 대체 항목** \
  <https://ardalis.com/enum-alternatives-in-c>

- **Enumeration.cs.** eShopOnContainers의 기본 열거형 클래스\
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- **CardType.cs**. eShopOnContainers의 샘플 열거형 클래스 \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>

- **SmartEnum**. Ardalis-.NET에서 더 강력한 형식의 스마트한 열거형을 생성하는데 도움을 준 클래스입니다. \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
>[이전](implement-value-objects.md)
>[다음](domain-model-layer-validations.md)
