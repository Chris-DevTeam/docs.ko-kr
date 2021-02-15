---
description: '자세히 알아보기: 방법: 상속 된 변수 숨기기 (Visual Basic)'
title: '방법: 상속된 변수 숨기기'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
- variables [Visual Basic], hiding inherited
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
ms.openlocfilehash: be2de980e27b318151c795ae36bd92a01d47d55e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429899"
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a>방법: 상속된 변수 숨기기(Visual Basic)

파생 클래스는 기본 클래스의 모든 정의를 상속 합니다. 기본 클래스의 요소와 같은 이름을 사용 하 여 변수를 정의 하려면 파생 클래스에서 변수를 정의할 때 기본 클래스 요소 *를 숨기 거 나 숨길* 수 있습니다. 이 작업을 수행 하는 경우 파생 클래스의 코드는 숨기는 메커니즘을 명시적으로 우회 하지 않는 한 변수에 액세스 합니다.

상속 된 변수를 숨기려는 또 다른 이유는 기본 클래스 수정 버전 으로부터 보호 하는 것입니다. 기본 클래스는 상속 하는 요소를 변경 하는 변경 될 수 있습니다. 이 경우 `Shadows` 한정자는 파생 클래스의 참조를 기본 클래스 요소가 아니라 변수로 확인 하도록 합니다.

## <a name="to-hide-an-inherited-variable"></a>상속 된 변수를 숨기려면

1. 숨기려는 변수가 클래스 수준 (프로시저 외부)에서 선언 되어야 합니다. 그렇지 않으면 숨길 필요가 없습니다.
  
2. 파생 클래스 내에서 변수를 선언 하는 [Dim 문을](../../../language-reference/statements/dim-statement.md) 작성 합니다. 상속 된 변수의 이름과 동일한 이름을 사용 합니다.

3. 선언에 [Shadows](../../../language-reference/modifiers/shadows.md) 키워드를 포함 합니다.

     파생 클래스의 코드가 변수 이름을 참조 하는 경우 컴파일러는 변수에 대 한 참조를 확인 합니다.

     다음 예에서는 상속 된 변수를 숨기는 방법을 보여 줍니다.
  
    ```vb  
    Public Class ShadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class ShadowDerivedClass  
        Inherits ShadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub ShowStrings()  
            Dim s As String = $"Unqualified shadowString: {shadowString}{vbCrLf}MyBase.shadowString: {MyBase.shadowString}"
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     앞의 예제에서는 `shadowString` 기본 클래스에서 변수를 선언 하 고 파생 클래스에서 해당 변수를 숨깁니다. `ShowStrings`파생 클래스의 프로시저는 이름이 한정 되지 않은 경우 문자열의 숨김 버전을 표시 합니다 `shadowString` . 그런 다음 `shadowString` 키워드를 사용 하 여 정규화 된 버전을 표시 `MyBase` 합니다.  
  
## <a name="robust-programming"></a>강력한 프로그래밍

섀도잉 시 이름이 같은 변수의 버전이 두 개 이상 도입 되었습니다. 코드 문이 변수 이름을 참조 하는 경우 컴파일러가 참조를 확인 하는 버전은 코드 문의 위치 및 한정 된 문자열이 있는지 여부와 같은 요소에 따라 달라 집니다. 이로 인해 숨겨진 변수의 의도 하지 않은 버전을 참조 하는 위험이 늘어날 수 있습니다. 숨겨진 변수에 대 한 모든 참조를 정규화 하 여이 위험을 낮출 수 있습니다.

## <a name="see-also"></a>추가 정보

- [References to Declared Elements](references-to-declared-elements.md)
- [Visual Basic에서 숨김](shadowing.md)
- [섀도잉과 재정의 간의 차이점](differences-between-shadowing-and-overriding.md)
- [방법: 사용자 변수와 이름이 같은 변수 숨기기](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [방법: 파생 클래스에 의해 숨겨진 변수에 액세스](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [재정의](../../../language-reference/modifiers/overrides.md)
- [Me, My, MyBase 및 MyClass](../../program-structure/me-my-mybase-and-myclass.md)
- [상속 기본 사항](../objects-and-classes/inheritance-basics.md)
