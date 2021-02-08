---
description: '자세한 정보: 하위 식 (Visual Basic)'
title: 하위 식
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: e47aa8f9707701b5fd9d90fb3fabb31e9c052b53
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795289"
---
# <a name="sub-expression-visual-basic"></a>하위 식(Visual Basic)

서브루틴 람다 식을 정의 하는 매개 변수 및 코드를 선언 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a>부분  
  
|용어|정의|  
|---|---|  
|`parameterlist`|선택 사항입니다. 프로시저의 매개 변수를 나타내는 지역 변수 이름 목록입니다. 목록이 비어 있는 경우에도 괄호가 있어야 합니다. 자세한 내용은 [Parameter List](../statements/parameter-list.md)을 참조하세요.|  
|`statement`|필수 사항입니다. 단일 문입니다.|  
|`statements`|필수 사항입니다. 문 목록입니다.|  
  
## <a name="remarks"></a>설명  

 *람다 식은* 이름이 없고 하나 이상의 문을 실행 하는 서브루틴입니다. 에 대 한 인수를 제외 하 고 대리자 형식을 사용할 수 있는 모든 위치에서 람다 식을 사용할 수 있습니다 `RemoveHandler` . 대리자에 대 한 자세한 내용과 대리자에 람다 식을 사용 하는 방법에 대 한 자세한 내용은 [Delegate 문](../statements/delegate-statement.md) 및 [완화 된 대리자 변환](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)을 참조 하세요.  
  
## <a name="lambda-expression-syntax"></a>람다 식 구문  

 람다 식의 구문은 표준 서브루틴의 구문과 유사 합니다. 차이점은 다음과 같습니다.  
  
- 람다 식에 이름이 없습니다.  
  
- 람다 식에는 또는와 같은 한정자를 사용할 수 없습니다 `Overloads` `Overrides` .  
  
- 한 줄로 된 람다 식의 본문은 식이 아니라 문 이어야 합니다. 본문은 sub 프로시저에 대 한 호출로 구성 될 수 있지만 함수 프로시저에 대 한 호출로 구성 될 수 없습니다.  
  
- 람다 식에서 모든 매개 변수에는 지정 된 데이터 형식이 있어야 합니다. 그렇지 않으면 모든 매개 변수가 유추 되어야 합니다.  
  
- `ParamArray`람다 식에는 선택적 매개 변수와 매개 변수를 사용할 수 없습니다.  
  
- 람다 식에는 제네릭 매개 변수를 사용할 수 없습니다.  
  
## <a name="example"></a>예제  

 다음은 값을 콘솔에 쓰는 람다 식의 예입니다. 이 예제에서는 서브루틴의 단일 줄 및 여러 줄 람다 식 구문을 보여 줍니다. 더 많은 예제는 [람다 식](../../programming-guide/language-features/procedures/lambda-expressions.md)을 참조 하세요.  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>참고 항목

- [Sub 문](../statements/sub-statement.md)
- [람다 식](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [연산자 및 식](../../programming-guide/language-features/operators-and-expressions/index.md)
- [문](../../programming-guide/language-features/statements.md)
- [완화된 대리자 변환](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
