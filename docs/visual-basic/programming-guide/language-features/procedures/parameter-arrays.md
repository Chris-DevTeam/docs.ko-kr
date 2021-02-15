---
description: '자세한 정보: 매개 변수 배열 (Visual Basic)'
title: 매개 변수 배열
ms.date: 07/20/2015
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
ms.openlocfilehash: e71524d9d62f0ece3a8310934eba15e9db16aaa1
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100427585"
---
# <a name="parameter-arrays-visual-basic"></a>매개 변수 배열(Visual Basic)

일반적으로 프로시저 선언에서 지정 하는 것 보다 더 많은 인수를 사용 하 여 프로시저를 호출할 수 없습니다. 무제한 개수의 인수가 필요한 경우 프로시저에서 매개 변수에 대 한 값 배열을 허용할 수 있도록 *매개 변수 배열을* 선언할 수 있습니다. 프로시저를 정의할 때 매개 변수 배열의 요소 수를 몰라도 됩니다. 배열 크기는 프로시저를 호출할 때마다 개별적으로 결정 됩니다.  
  
## <a name="declaring-a-paramarray"></a>ParamArray 선언  

 [ParamArray](../../../language-reference/modifiers/paramarray.md) 키워드를 사용 하 여 매개 변수 목록에서 매개 변수 배열을 나타냅니다. 다음 규칙이 적용됩니다.  
  
- 프로시저는 하나의 매개 변수 배열만 정의할 수 있으며 프로시저 정의에서 마지막 매개 변수 여야 합니다.  
  
- 매개 변수 배열은 값으로 전달 되어야 합니다. 프로시저 정의에 [ByVal](../../../language-reference/modifiers/byval.md) 키워드를 명시적으로 포함 하는 것이 좋은 프로그래밍 습관입니다.  
  
- 매개 변수 배열은 자동으로 선택 사항입니다. 기본값은 매개 변수 배열의 요소 형식에 대 한 빈 1 차원 배열입니다.  
  
- 매개 변수 배열 앞의 모든 매개 변수는 필수 여야 합니다. 매개 변수 배열은 유일한 선택적 매개 변수 여야 합니다.  
  
## <a name="calling-a-paramarray"></a>ParamArray 호출  

 매개 변수 배열을 정의 하는 프로시저를 호출 하는 경우 다음 중 한 가지 방법으로 인수를 제공할 수 있습니다.  
  
- 아무 작업도 수행 하지 않습니다. 즉, [ParamArray](../../../language-reference/modifiers/paramarray.md) 인수를 생략할 수 있습니다. 이 경우 빈 배열이 프로시저에 전달 됩니다. [Nothing](../../../language-reference/nothing.md) 키워드를 명시적으로 전달 하면 null 배열이 프로시저에 전달 되 고 호출 된 프로시저에서이 조건을 확인 하지 않는 경우 NullReferenceException이 발생할 수 있습니다.
  
- 쉼표로 구분 된 임의 개수의 인수 목록입니다. 각 인수의 데이터 형식은 요소 형식으로 암시적으로 변환할 수 있어야 합니다 `ParamArray` .  
  
- 매개 변수 배열의 요소 형식과 동일한 요소 형식의 배열입니다.  
  
 모든 경우에서 프로시저 내의 코드는 매개 변수 배열을 데이터 형식과 동일한 데이터 형식의 요소가 포함 된 1 차원 배열로 처리 합니다 `ParamArray` .  
  
> [!IMPORTANT]
> 무한정 클 수 있는 배열을 처리할 때마다 응용 프로그램의 내부 용량을 overrunning 위험이 있습니다. 매개 변수 배열을 허용 하는 경우 호출 코드에서 전달 된 배열의 크기를 테스트 해야 합니다. 응용 프로그램에 너무 클 경우 적절 한 단계를 수행 합니다. 자세한 내용은 [배열](../arrays/index.md)을 참조하세요.  
  
## <a name="example"></a>예  

 다음 예제에서는 함수를 정의 하 고 호출 합니다 `calcSum` . `ParamArray`매개 변수에 대 한 한정자를 `args` 사용 하면 함수에서 다양 한 수의 인수를 사용할 수 있습니다.  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 다음 예제에서는 매개 변수 배열을 사용 하 여 프로시저를 정의 하 고 매개 변수 배열에 전달 된 모든 배열 요소의 값을 출력 합니다.  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a>추가 정보

- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [절차](./index.md)
- [프로시저 매개 변수 및 인수](./procedure-parameters-and-arguments.md)
- [값 또는 참조로 인수 전달](./passing-arguments-by-value-and-by-reference.md)
- [위치 및 이름으로 인수 전달](./passing-arguments-by-position-and-by-name.md)
- [선택적 매개 변수](./optional-parameters.md)
- [프로시저 오버로딩](./procedure-overloading.md)
- [배열](../arrays/index.md)
- [선택 사항](../../../language-reference/modifiers/optional.md)
