---
description: '자세한 정보: 선택 사항 (Visual Basic)'
title: Optional
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: d9a61371364d87745203363dbc0a641cec9660a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666084"
---
# <a name="optional-visual-basic"></a>Optional(Visual Basic)

프로시저를 호출할 때 프로시저 인수를 생략할 수 있도록 지정 합니다.

## <a name="remarks"></a>설명

각 선택적 매개 변수에 대해 상수 식을 해당 매개 변수의 기본값으로 지정 해야 합니다. 식이 [Nothing](../nothing.md)으로 평가 되 면 value 데이터 형식의 기본값이 매개 변수의 기본값으로 사용 됩니다.

매개 변수 목록에 선택적 매개 변수가 포함 된 경우 뒤에 오는 모든 매개 변수도 선택 사항 이어야 합니다.

`Optional` 한정자는 다음 컨텍스트에서 사용할 수 있습니다.

- [Declare 문](../statements/declare-statement.md)

- [Function 문](../statements/function-statement.md)

- [Property Statement](../statements/property-statement.md)

- [Sub 문](../statements/sub-statement.md)

> [!NOTE]
> 선택적 매개 변수를 사용 하거나 사용 하지 않고 프로시저를 호출 하는 경우 위치 또는 이름을 기준으로 인수를 전달할 수 있습니다. 자세한 내용은 [위치 및 이름으로 인수 전달](../../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)을 참조 하세요.

> [!NOTE]
> 오버 로드를 사용 하 여 선택적 매개 변수가 있는 프로시저를 정의할 수도 있습니다. 선택적 매개 변수 하나가 있는 경우 매개 변수를 허용 하는 프로시저의 오버 로드 된 버전 두 개와 그렇지 않은 버전을 정의할 수 있습니다. 자세한 내용은 [Procedure Overloading](../../programming-guide/language-features/procedures/procedure-overloading.md)을 참조하세요.

## <a name="example"></a>예제

다음 예에서는 선택적 매개 변수를 포함 하는 프로시저를 정의 합니다.

```vb
Public Function FindMatches(ByRef values As List(Of String),
                            ByVal searchString As String,
                            Optional ByVal matchCase As Boolean = False) As List(Of String)

    Dim results As IEnumerable(Of String)

    If matchCase Then
        results = From v In values
                  Where v.Contains(searchString)
    Else
        results = From v In values
                  Where UCase(v).Contains(UCase(searchString))
    End If

    Return results.ToList()
End Function
```

## <a name="example"></a>예제

다음 예제에서는 위치로 전달 된 인수 및 이름으로 전달 된 인수를 사용 하 여 프로시저를 호출 하는 방법을 보여 줍니다. 프로시저에는 두 가지 선택적 매개 변수가 있습니다.

[!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]

## <a name="see-also"></a>참고 항목

- [매개 변수 목록](../statements/parameter-list.md)
- [선택적 매개 변수](../../programming-guide/language-features/procedures/optional-parameters.md)
- [C++ 키워드](../keywords/index.md)
