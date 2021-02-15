---
description: '자세한 정보: 연결 연산자 Visual Basic'
title: 연결 연산자
ms.date: 07/20/2015
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
ms.openlocfilehash: 7d007a830e4547f87e937cc7313c248485b4b574
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476399"
---
# <a name="concatenation-operators-in-visual-basic"></a>Visual Basic의 연결 연산자

연결 연산자는 여러 문자열을 단일 문자열로 조인합니다. 연결 연산자에는 `+` 및 `&`의 두 가지가 있습니다. 이 두 연산자는 모두 다음 예제에 나와 있는 것처럼 기본적인 연결 작업을 수행합니다.

```vb
Dim x As String = "Mic" & "ro" & "soft"
Dim y As String = "Mic" + "ro" + "soft"
' The preceding statements set both x and y to "Microsoft".
```

이러한 연산자는 다음 예제에 나와 있는 것처럼 `String` 변수도 연결할 수 있습니다.

[!code-vb[VbVbalrOperators#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#76)]

## <a name="differences-between-the-two-concatenation-operators"></a>두 연결 연산자의 차이점

[+ 연산자](../../../language-reference/operators/addition-operator.md) 에는 두 개의 숫자를 더하는 기본 목적이 있습니다. 그러나 숫자 피연산자와 문자열 피연산자를 연결할 수도 있습니다. `+` 연산자에는 수행할 작업(덧셈, 연결, 컴파일러 오류 생성, 런타임 <xref:System.InvalidCastException> throw)을 결정하는 복잡한 규칙 집합이 있습니다.

[& 연산자](../../../language-reference/operators/concatenation-operator.md) 는 피연산자에 대해서만 정의 `String` 되며의 설정에 관계 없이 항상 피연산자를로 확대 `String` `Option Strict` 합니다. `&` 연산자는 문자열에 대해서만 정의되며 의도하지 않은 변환을 생성할 가능성을 줄이므로 문자열 연결에 사용하는 것이 좋습니다.

## <a name="performance-string-and-stringbuilder"></a>성능: String 및 StringBuilder

문자열에서 연결, 삭제, 대체 등의 조작을 많이 수행하는 경우 <xref:System.Text.StringBuilder> 네임스페이스에서 <xref:System.Text> 클래스를 사용하면 성능을 개선할 수 있습니다. <xref:System.Text.StringBuilder> 개체를 만들고 초기화하려면 추가 명령이 필요하며 최종 값을 `String`으로 변환하려면 또 다른 명령이 필요하지만, <xref:System.Text.StringBuilder>가 더 빠르게 실행되기 때문에 전체적인 작업 시간은 줄일 수 있습니다.

## <a name="see-also"></a>추가 정보

- [Option Strict 문](../../../language-reference/statements/option-strict-statement.md)
- [Visual Basic의 문자열 조작 메서드 유형](../strings/types-of-string-manipulation-methods.md)
- [Visual Basic의 산술 연산자](arithmetic-operators.md)
- [Comparison Operators in Visual Basic](comparison-operators.md)
- [Visual Basic의 논리 및 비트 연산자](logical-and-bitwise-operators.md)
