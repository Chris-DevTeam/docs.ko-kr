---
description: '자세한 정보: Structure 문'
title: Structure 문
ms.date: 05/12/2018
f1_keywords:
- vb.Structure
- Structure
helpviewer_keywords:
- user-defined types [Visual Basic], Structure statement
- compound data types [Visual Basic]
- Structure keyword [Visual Basic]
- Structure statement [Visual Basic]
- UDT (user-defined types)
- types [Visual Basic], user-defined
ms.assetid: 9bd1deea-2a89-4cdc-812c-6dcbb947c391
ms.openlocfilehash: 338abe359491f02c25bdb33d996fb639f58f8b35
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741070"
---
# <a name="structure-statement"></a>Structure 문

구조체의 이름을 선언 하 고 해당 구조체에서 구성 하는 변수, 속성, 이벤트 및 프로시저의 정의를 소개 합니다.

## <a name="syntax"></a>Syntax

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Partial ] _
Structure name [ ( Of typelist ) ]
    [ Implements interfacenames ]
    [ datamemberdeclarations ]
    [ methodmemberdeclarations ]
End Structure
```

## <a name="parts"></a>부분

|용어|정의|
|---|---|
|`attributelist`|선택 사항입니다. [특성 목록](attribute-list.md)을 참조 하십시오.|
|`accessmodifier`|선택 사항입니다. 다음 중 하나일 수 있습니다.<br /><br /> -   [공개적](../modifiers/public.md)<br />-   [보호](../modifiers/protected.md)<br />-   [Friend](../modifiers/friend.md)<br />-   [문자](../modifiers/private.md)<br />- [보호 된 Friend](../modifiers/protected-friend.md)<br/>- [개인 보호](../modifiers/private-protected.md) <br /><br /> [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)을 참조하세요.|
|`Shadows`|선택 사항입니다. [그림자](../modifiers/shadows.md)를 참조 하세요.|
|`Partial`|선택 사항입니다. 구조체의 부분 정의를 나타냅니다. [부분](../modifiers/partial.md)을 참조 하세요.|
|`name`|필수 사항입니다. 구조체의 이름입니다. [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)을 참조하세요.|
|`Of`|선택 사항입니다. 제네릭 구조체 임을 지정 합니다.|
|`typelist`|[Of](of-clause.md) 키워드를 사용 하는 경우 필수 사항입니다. 이 구조체의 형식 매개 변수 목록입니다. [형식 목록](type-list.md)을 참조 하십시오.|
|`Implements`|선택 사항입니다. 이 구조체는 하나 이상의 인터페이스의 멤버를 구현 함을 나타냅니다. [Implements 문](implements-statement.md)을 참조 하세요.|
|`interfacenames`|문을 사용 하는 경우 필요 `Implements` 합니다. 이 구조체에서 구현 하는 인터페이스의 이름입니다.|
|`datamemberdeclarations`|필수 사항입니다. `Const`구조체의 데이터 멤버를 선언 하는 0 개 이상의,, `Dim` `Enum` 또는 `Event` 문입니다. |
|`methodmemberdeclarations`|선택 사항입니다. `Function` `Operator` `Property` `Sub` 구조체의 *메서드 멤버로* 사용 되는,, 또는 프로시저의 0 개 이상 선언입니다.|
|`End Structure`|필수 사항입니다. 정의를 종료 `Structure` 합니다.|

## <a name="remarks"></a>설명

`Structure`문은 사용자 지정할 수 있는 복합 값 형식을 정의 합니다. *구조* 는 이전 버전의 Visual Basic UDT (사용자 정의 형식)를 일반화 한 것입니다. 자세한 내용은 [구조체](../../programming-guide/language-features/data-types/structures.md)를 참조 하세요.

구조체는 클래스와 동일한 기능을 대부분 지원 합니다. 예를 들어 구조체에는 속성 및 프로시저가 포함 될 수 있고, 인터페이스를 구현할 수 있으며, 매개 변수가 있는 생성자를 포함할 수 있습니다. 그러나 상속, 선언 및 사용과 같은 영역의 구조와 클래스 사이에는 상당한 차이가 있습니다. 또한 클래스는 참조 형식이 고 구조체는 값 형식입니다. 자세한 내용은 [구조체 및 클래스](../../programming-guide/language-features/data-types/structures-and-classes.md)를 참조 하세요.

는 `Structure` 네임 스페이스 또는 모듈 수준 에서만 사용할 수 있습니다. 즉, 구조체의 *선언 컨텍스트* 는 소스 파일, 네임 스페이스, 클래스, 구조체, 모듈 또는 인터페이스 여야 하며 프로시저 또는 블록일 수 없습니다. 자세한 내용은 [선언 컨텍스트 및 기본 액세스 수준](declaration-contexts-and-default-access-levels.md)을 참조하세요.

구조체는 기본적으로 [Friend](../modifiers/friend.md) 액세스를 사용 합니다. 액세스 한정자를 사용 하 여 액세스 수준을 조정할 수 있습니다. 자세한 내용은 [Visual Basic의 액세스 수준](../../programming-guide/language-features/declared-elements/access-levels.md)을 참조 하세요.

## <a name="rules"></a>규칙

- **중첩할.** 다른 구조체 내에서 한 구조체를 정의할 수 있습니다. 외부 구조체를 *포함 하는 구조체* 라고 하며 내부 구조를 *중첩 된 구조체* 라고 합니다. 그러나 포함 하는 구조체를 통해 중첩 된 구조체의 멤버에 액세스할 수 없습니다. 대신, 중첩 된 구조체의 데이터 형식 변수를 선언 해야 합니다.

- **멤버 선언입니다.** 구조체의 모든 멤버를 선언 해야 합니다. 구조체 멤버는 [보호할](../modifiers/protected.md) 수 없으며 `Protected Friend` 구조체에서 상속 될 수 없습니다. 그러나 구조체 자체는 또는 일 수 있습니다 `Protected` `Protected Friend` .
  
     구조체에는 0개 이상의 비공유 변수 또는 비공유, 비사용자 정의 이벤트를 선언할 수 있습니다. 상수, 속성 및 프로시저 중 일부가 비공유 인 경우에도이를 사용할 수 없습니다.

- **초기.** 구조체의 비공유 데이터 멤버 값은 해당 선언의 일부로 초기화할 수 없습니다. 구조체의 매개 변수가 있는 생성자를 사용 하 여 이러한 데이터 멤버를 초기화 하거나 구조체의 인스턴스를 만든 후에는 멤버에 값을 할당 해야 합니다.

- **상.** 구조체는 모든 구조체가 상속 하는 이외의 형식에서 상속할 수 없습니다 <xref:System.ValueType> . 특히 한 구조체는 다른 구조체에서 상속할 수 없습니다.

     구조체 정의에서 [Inherits 문을](inherits-statement.md) 사용 하 여를 지정할 수도 없습니다 <xref:System.ValueType> .

- **구현이.** 구조체에서 [Implements 문을](implements-statement.md)사용 하는 경우에서 지정 하는 모든 인터페이스에서 정의 된 모든 멤버를 구현 해야 합니다 `interfacenames` .

- **기본 속성입니다.** 구조체는 [기본](../modifiers/default.md) 한정자를 사용 하 여 최대 하나의 속성을 *기본 속성* 으로 지정할 수 있습니다. 자세한 내용은 [기본값](../modifiers/default.md)을 참조 하세요.

## <a name="behavior"></a>동작

- **액세스 수준입니다.** 구조체 내에서 각 멤버를 고유한 액세스 수준으로 선언할 수 있습니다. 모든 구조체 멤버는 기본적으로 [공용](../modifiers/public.md) 액세스로 사용 됩니다. 구조체 자체의 액세스 수준이 더 제한적인 경우 액세스 한정자를 사용 하 여 액세스 수준을 조정 하는 경우에도이는 해당 멤버에 대 한 액세스를 자동으로 제한 합니다.

- **범위.** 구조체는 포함 하는 네임 스페이스, 클래스, 구조체 또는 모듈 전체의 범위 내에 있습니다.

     모든 구조체 멤버의 범위는 전체 구조입니다.

- **수명.** 구조체 자체가 수명이 아닙니다. 대신 해당 구조체의 각 인스턴스에는 다른 모든 인스턴스와 독립적인 수명이 있습니다.

     인스턴스의 수명은 [새 Operator](../operators/new-operator.md) 절에서 생성 될 때 시작 됩니다. 이를 보유 하는 변수의 수명이 종료 되 면 종료 됩니다.

     구조 인스턴스의 수명은 확장할 수 없습니다. 정적 구조체 기능의 근사값은 모듈에서 제공 합니다. 자세한 내용은 [Module 문](module-statement.md)을 참조 하세요.

     구조체 멤버의 수명은 선언 된 방법과 위치에 따라 달라 집니다. 자세한 내용은 [클래스 문의](class-statement.md)"수명"을 참조 하세요.

- **조인의.** 구조체 외부의 코드는 멤버의 이름을 해당 구조체의 이름으로 한 정해야 합니다.

     중첩 된 구조체 내의 코드가 프로그래밍 요소에 대 한 정규화 되지 않은 참조를 만드는 경우, Visual Basic는 중첩 된 구조체의 첫 번째 요소를 검색 한 다음 해당 요소를 포함 하는 구조체에서 가장 바깥쪽 포함 요소로 검색 합니다. 자세한 내용은 [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)을 참조하세요.

- **메모리 소비** 모든 복합 데이터 형식과 마찬가지로 해당 멤버의 명목상 저장소 할당을 함께 추가 하 여 구조의 총 메모리 소비량을 안전 하 게 계산할 수 없습니다. 또한 메모리의 저장소 순서가 선언 순서와 동일 하다는 것을 안전 하 게 가정할 수 없습니다. 구조의 저장소 레이아웃을 제어 해야 하는 경우에는 특성을 문에 적용할 수 있습니다 <xref:System.Runtime.InteropServices.StructLayoutAttribute> `Structure` .

## <a name="example"></a>예제

다음 예에서는 문을 사용 하 여 `Structure` 직원에 대 한 관련 데이터 집합을 정의 합니다. `Public`, `Friend` 및 멤버를 사용 하 여 `Private` 데이터 항목의 민감도를 반영 하는 방법을 보여 줍니다. 또한 프로시저, 속성 및 이벤트 멤버도 보여 줍니다.

[!code-vb[VbVbalrStatements#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#57)]

S를 사용 하는 방법에 대 한 자세한 내용은 `Structure` [구조체 변수](../../programming-guide/language-features/data-types/structure-variables.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

- [Class 문](class-statement.md)
- [Interface 문](interface-statement.md)
- [Module 문](module-statement.md)
- [Dim 문](dim-statement.md)
- [Const 문](const-statement.md)
- [Enum 문](enum-statement.md)
- [Event 문](event-statement.md)
- [Operator Statement](operator-statement.md)
- [Property Statement](property-statement.md)
- [구조체와 클래스](../../programming-guide/language-features/data-types/structures-and-classes.md)
