---
description: '자세한 정보: 공유 (Visual Basic)'
title: Shared
ms.date: 07/20/2015
f1_keywords:
- vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
ms.openlocfilehash: 0cc671c67486d01026f2283837448db7b00c1a0a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700756"
---
# <a name="shared-visual-basic"></a>Shared(Visual Basic)

하나 이상의 선언 된 프로그래밍 요소가 클래스 또는 구조체의 특정 인스턴스가 아닌 여러 클래스 또는 구조체와 연결 되도록 지정 합니다.

## <a name="when-to-use-shared"></a>공유를 사용 하는 경우

클래스 또는 구조체의 멤버를 공유 하면 *비공유* 가 아닌 모든 인스턴스에서 사용할 수 있습니다. 여기서 각 인스턴스는 자체 복사본을 유지 합니다. 예를 들어 변수 값이 전체 응용 프로그램에 적용 되는 경우 공유는 유용 합니다. 해당 변수를로 선언 하는 경우 `Shared` 모든 인스턴스가 동일한 저장소 위치에 액세스 하 고 한 인스턴스가 변수의 값을 변경 하는 경우 모든 인스턴스에서 업데이트 된 값에 액세스 합니다.

공유는 멤버의 액세스 수준을 변경 하지 않습니다. 예를 들어 클래스 멤버는 shared 및 private (클래스 내 에서만 액세스할 수 있음) 또는 비공유 및 public 일 수 있습니다. 자세한 내용은 [Visual Basic의 액세스 수준](../../programming-guide/language-features/declared-elements/access-levels.md)을 참조 하세요.

## <a name="rules"></a>규칙

- **선언 컨텍스트.** `Shared`는 모듈 수준에서만 사용할 수 있습니다. 즉, 요소에 대 한 선언 컨텍스트는 `Shared` 클래스 또는 구조체 여야 하며 소스 파일, 네임 스페이스 또는 프로시저일 수 없습니다.

- **결합된 한정자.** `Shared`동일한 선언에서 [Overrides](overrides.md), [Overridable](overridable.md), [NotOverridable](notoverridable.md), [MustOverride](mustoverride.md)또는 [Static](static.md) 을 함께 지정할 수 없습니다.

- **하.** 해당 클래스 또는 구조체의 특정 인스턴스의 변수 이름이 아니라 클래스 또는 구조체 이름으로 정규화 하 여 공유 요소에 액세스 합니다. 클래스 또는 구조체의 인스턴스를 만들어 해당 공유 멤버에 액세스할 필요는 없습니다.

     다음 예에서는 <xref:System.Double.IsNaN%2A> 구조에 의해 노출 되는 공유 프로시저를 호출 합니다 <xref:System.Double> .

     ```vb
     If Double.IsNaN(result) Then Console.WriteLine("Result is mathematically undefined.")
     ```

- **암시적 공유.** `Shared` [Const 문에](../statements/const-statement.md)는 한정자를 사용할 수 없지만 상수는 암시적으로 공유 됩니다. 마찬가지로, 모듈 또는 인터페이스의 멤버를로 선언할 수 `Shared` 없지만 암시적으로 공유 됩니다.

## <a name="behavior"></a>동작

- **저장할.** 공유 변수나 이벤트는 해당 클래스 또는 구조체를 만든 인스턴스 수에 관계 없이 한 번만 메모리에 저장 됩니다. 마찬가지로 공유 프로시저 또는 속성은 하나의 지역 변수 집합만 보유 합니다.

- **인스턴스 변수를 통해 액세스 합니다.** 해당 클래스 또는 구조체의 특정 인스턴스를 포함 하는 변수의 이름으로 정규화 하 여 공유 요소에 액세스할 수 있습니다. 일반적으로 정상적으로 작동 하지만 컴파일러는 경고 메시지를 생성 하 고 변수 대신 클래스 또는 구조체 이름을 통해 액세스를 만듭니다.

- **인스턴스 식을 통해 액세스 합니다.** 클래스 또는 구조체의 인스턴스를 반환 하는 식을 통해 공유 요소에 액세스 하는 경우 컴파일러는 식을 계산 하는 대신 클래스 또는 구조체 이름을 통해 액세스를 만듭니다. 이 액세스는 다른 작업을 수행 하 고 인스턴스를 반환 하는 식을 의도 한 경우 예기치 않은 결과를 생성 합니다. 다음 예에서는 이러한 상황을 보여 줍니다.
  
    ```vb
    Sub Main()
        ' The following line is the preferred way to access Total.
        ShareTotal.Total = 10

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of through
        ' the variable instanceVar. This works as expected and adds
        ' 100 to Total.
        Dim instanceVar As New ShareTotal
        instanceVar.Total += 100

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of calling
        ' ReturnClass(). This adds 1000 to total but does not work as
        ' expected, because the WriteLine in ReturnClass() does not run.
        Console.WriteLine("Value of total is " & CStr(ShareTotal.Total))
        ReturnClass().Total += 1000
    End Sub

    Public Function ReturnClass() As ShareTotal
        Console.WriteLine("Function ReturnClass() called")
        Return New ShareTotal
    End Function

    Public Class ShareTotal
        Public Shared Property Total As Integer
    End Class
    ```

     앞의 예제에서 컴파일러는 코드에서 인스턴스를 통해 공유 속성에 액세스 하는 두 번 모두 경고 메시지를 생성 합니다 `Total` . 각각의 경우에는 클래스를 통해 직접 액세스를 수행 `ShareTotal` 하 고 인스턴스를 사용 하지 않습니다. 프로시저에 대 한 의도 된 호출의 경우 `ReturnClass` 이는에 대 한 호출도 생성 하지 않으므로 `ReturnClass` "함수 returnclass ()를 표시 하는 추가 작업은 수행 되지 않습니다.

`Shared` 한정자는 다음 컨텍스트에서 사용할 수 있습니다.

- [Dim 문](../statements/dim-statement.md)
- [Event 문](../statements/event-statement.md)
- [Function 문](../statements/function-statement.md)
- [Operator Statement](../statements/operator-statement.md)
- [Property Statement](../statements/property-statement.md)
- [Sub 문](../statements/sub-statement.md)
  
## <a name="see-also"></a>참고 항목

- [Overloads](shadows.md)
- [정적](static.md)
- [Visual Basic의 수명](../../programming-guide/language-features/declared-elements/lifetime.md)
- [절차](../../programming-guide/language-features/procedures/index.md)
- [구조체](../../programming-guide/language-features/data-types/structures.md)
- [개체 및 클래스](../../programming-guide/language-features/objects-and-classes/index.md)
