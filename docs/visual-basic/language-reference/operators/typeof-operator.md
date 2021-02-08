---
description: '자세한 정보: TypeOf 연산자 (Visual Basic)'
title: TypeOf 연산자
ms.date: 07/20/2015
f1_keywords:
- TypeOf
- vb.TypeOf
helpviewer_keywords:
- types [Visual Basic], compatible
- comparison operators [Visual Basic]
- TypeOf...Is expression
- data types [Visual Basic], compatible
- TypeOf operator [Visual Basic]
- compatible data types [Visual Basic]
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
ms.openlocfilehash: 59a03095b2abbaa304221b30402b9a058954db63
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795237"
---
# <a name="typeof-operator-visual-basic"></a>TypeOf 연산자(Visual Basic)

식의 결과에 대 한 런타임 형식이 지정 된 형식과 호환 되는지 여부를 확인 합니다.
  
## <a name="syntax"></a>Syntax  
  
```vb  
result = TypeOf objectexpression Is typename  
```  
  
```vb  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a>부분  

 `result`  
 반환됨. `Boolean` 값입니다.  
  
 `objectexpression`  
 필수 사항입니다. 참조 형식으로 계산되는 모든 식입니다.  
  
 `typename`  
 필수 사항입니다. 모든 데이터 형식 이름입니다.  
  
## <a name="remarks"></a>설명  

 `TypeOf` 연산자는 `objectexpression`의 런타임 형식이 `typename`과 호환되는지 여부를 결정합니다. 호환성은 `typename`의 형식 범주에 따라 달라집니다. 다음 표에서 호환성이 결정되는 방법을 보여 줍니다.  
  
|`typename`의 형식 범주|호환성 조건|  
|---------------------------------|-----------------------------|  
|인스턴스|`objectexpression`이 `typename` 형식이거나 `typename`에서 상속됩니다.|  
|구조체|`objectexpression`이 `typename` 형식입니다.|  
|인터페이스|`objectexpression`이 `typename`을 구현하거나 `typename`을 구현하는 클래스에서 상속됩니다.|  
  
 `objectexpression`의 런타임 형식이 호환성 조건을 충족하면 `result`가 `True`이고, 그렇지 않으면 `result`가 `False`입니다.  `objectexpression`이 null이면 `TypeOf`...`Is`는 `False`를 반환하고 ...`IsNot`은 `True`를 반환합니다.  
  
 `TypeOf`는 항상 `Is` 키워드와 함께 사용되어 `TypeOf`...`Is` 식을 생성하거나 `IsNot` 키워드와 함께 사용되어 `TypeOf`...`IsNot` 식을 생성합니다.  
  
## <a name="example"></a>예제  

 다음 예제에서는 `TypeOf`...`Is` 식을 사용하여 데이터 형식이 다양한 두 개체 참조 변수의 형식 호환성을 테스트합니다.  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 `refInteger` 변수에 `Integer`의 런타임 형식이 있습니다. 이 변수는 `Integer`와 호환되지만 `Double`과는 호환되지 않습니다. `refForm` 변수에 <xref:System.Windows.Forms.Form>의 런타임 형식이 있습니다. 이 변수는 해당 형식이기 때문에 <xref:System.Windows.Forms.Form>과 호환되고, <xref:System.Windows.Forms.Form>이 <xref:System.Windows.Forms.Control>에서 상속되기 때문에 <xref:System.Windows.Forms.Control>과 호환되며, <xref:System.Windows.Forms.Form>이 <xref:System.ComponentModel.IComponent>를 구현하는 <xref:System.ComponentModel.Component>에서 상속되기 때문에 <xref:System.ComponentModel.IComponent>와 호환됩니다. 그러나 `refForm`은 <xref:System.Windows.Forms.Label>과 호환되지 않습니다.  
  
## <a name="see-also"></a>참고 항목

- [Is 연산자](is-operator.md)
- [IsNot 연산자](isnot-operator.md)
- [Comparison Operators in Visual Basic](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic에서의 연산자 우선 순위](operator-precedence.md)
- [기능별 연산자 목록](operators-listed-by-functionality.md)
- [연산자 및 식](../../programming-guide/language-features/operators-and-expressions/index.md)
