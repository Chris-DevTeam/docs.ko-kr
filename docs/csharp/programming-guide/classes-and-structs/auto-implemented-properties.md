---
title: 자동으로 구현된 속성 - C# 프로그래밍 가이드
description: C#에서 자동으로 구현된 속성의 경우 컴파일러는 속성의 get 및 set 접근자를 통해서만 액세스하는 전용 익명 지원 필드를 만듭니다.
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: ef3e2d6dd5851801ea06d65b87c2274d8e44b4f1
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190283"
---
# <a name="auto-implemented-properties-c-programming-guide"></a>자동으로 구현된 속성(C# 프로그래밍 가이드)

C# 3.0 이상에서는 속성 접근자에 추가적인 논리가 필요하지 않을 경우 자동 구현 속성을 통해 속성 선언이 더 간결해집니다. 이를 통해 클라이언트 코드에서 개체를 만들 수도 있습니다. 다음 예제와 같이 속성을 선언할 때 컴파일러는 속성의 `get` 및 `set` 접근자를 통해서만 액세스할 수 있는 전용 익명 지원 필드를 만듭니다. C# 9 이상에서는 `init` 접근자를 자동 구현 속성으로 선언할 수도 있습니다.
  
## <a name="example"></a>예제

다음 예제에서는 일부 자동 구현 속성이 있는 간단한 클래스를 보여 줍니다.  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

인터페이스에서는 자동 구현 속성을 선언할 수 없습니다. 자동 구현 속성은 private 인스턴스 지원 필드를 선언하는데, 인터페이스는 인스턴스 필드를 선언할 수 없기 때문입니다. 인터페이스에서 본문을 정의하지 않고 속성을 선언하면 해당 인터페이스를 구현하는 각 형식에 의해 구현되어야 하는 접근자와 함께 속성이 선언됩니다.

C# 6 이상 버전에서는 필드와 유사하게 자동 구현 속성을 초기화할 수 있습니다.  

```csharp  
public string FirstName { get; set; } = "Jane";  
```  

앞의 예제에 표시된 클래스는 변경할 수 있습니다. 클라이언트 코드에서는 개체가 만들어진 후에 개체의 값을 변경할 수 있습니다. 데이터 및 중요 동작(메서드)을 포함하는 복잡한 클래스에는 public 속성이 필요한 경우가 많습니다. 그러나 값 세트(데이터)만 캡슐화하고 동작이 적거나 없는 작은 클래스나 구조체의 경우 다음 옵션 중 하나를 사용하여 개체를 변경할 수 없게 해야 합니다.

* `get` 접근자만 선언합니다(생성자를 제외한 모든 위치에서 변경할 수 없음).
* `get` 접근자와 `init` 접근자를 선언합니다(개체 생성 중을 제외하고 모든 위치에서 변경할 수 없음).
* `set` 접근자를 [프라이빗](../../language-reference/keywords/private.md)으로 선언합니다(소비자가 변경할 수 없음).

자세한 내용은 [자동으로 구현된 속성을 사용하여 간단한 클래스를 구현하는 방법](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)을 참조하세요.

## <a name="see-also"></a>참조

- [속성](./properties.md)
- [한정자](../../language-reference/keywords/index.md)
