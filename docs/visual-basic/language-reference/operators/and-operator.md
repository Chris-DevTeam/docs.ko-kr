---
description: '다음에 대 한 자세한 정보: And 연산자 (Visual Basic)'
title: And 연산자
ms.date: 07/20/2015
f1_keywords:
- vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
ms.openlocfilehash: 238ef0b2f14f2014da6e65684bfac183e03d963e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774280"
---
# <a name="and-operator-visual-basic"></a>And 연산자(Visual Basic)

두 식에 논리 결합을 수행 `Boolean` 하거나 두 숫자 식에 비트 결합을 수행 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>부분  

 `result`  
 필수 요소. 임의의 `Boolean` 또는 숫자 식입니다. 부울 비교의 경우 `result` 는 두 값의 논리적 결합입니다 `Boolean` . 비트 연산의 경우 `result` 는 두 숫자 비트 패턴의 비트 결합을 나타내는 숫자 값입니다.  
  
 `expression1`  
 필수 요소. 임의의 `Boolean` 또는 숫자 식입니다.  
  
 `expression2`  
 필수 요소. 임의의 `Boolean` 또는 숫자 식입니다.  
  
## <a name="remarks"></a>설명  

 부울 비교의 경우와 `result` 가 `True` 모두 `expression1` `expression2` 로 계산 되는 경우에만가입니다 `True` . 다음 표에서는를 결정 하는 방법을 보여 줍니다 `result` .  
  
|`expression1`가 인 경우|및 `expression2` 가|의 값 `result` 이 인 경우|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> 부울 비교에서 `And` 연산자는 항상 프로시저 호출을 포함 하는 두 식을 모두 계산 합니다. [AndAlso 연산자](andalso-operator.md) 는 *단락* 을 수행 합니다. 즉,가 이면 `expression1` 이 `False` `expression2` 계산 되지 않습니다.  
  
 숫자 값에 적용 되는 `And` 연산자는 두 숫자 식에서 동일 하 게 배치 된 비트의 비트 비교를 수행 하 고 `result` 다음 표에 따라의 해당 비트를 설정 합니다.  
  
|비트가 `expression1` 인 경우|그리고의 비트 `expression2` 는|`result`의 비트는|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
> 논리 및 비트 연산자는 다른 산술 및 관계형 연산자 보다 낮은 우선 순위를 가지 므로 정확한 결과를 얻으려면 모든 비트 연산을 괄호로 묶어야 합니다.  
  
## <a name="data-types"></a>데이터 형식  

 피연산자가 하나의 `Boolean` 식과 하나의 숫자 식으로 구성 된 경우 Visual Basic는 `Boolean` 식을 숫자 값으로 변환 하 고 (에 대해-1의 경우 `True` `False` ) 비트 연산을 수행 합니다.  
  
 부울 비교의 경우 결과의 데이터 형식은 `Boolean` 입니다. 비트 비교의 경우 결과 데이터 형식은 및의 데이터 형식에 적합 한 숫자 형식입니다 `expression1` `expression2` . [연산자 결과의 데이터 형식](data-types-of-operator-results.md)에서 "관계형 및 비트 비교" 표를 참조 하세요.  
  
> [!NOTE]
> `And`연산자를 *오버 로드할* 수 있습니다. 즉, 피연산자가 해당 클래스 또는 구조체의 형식일 때 클래스 또는 구조체의 동작을 다시 정의할 수 있습니다. 코드가 이러한 클래스 또는 구조체에서이 연산자를 사용 하는 경우 다시 정의 된 동작을 이해 해야 합니다. 자세한 내용은 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)을 참조하세요.  
  
## <a name="example"></a>예제  

 다음 예에서는 연산자를 사용 `And` 하 여 두 식에 논리 결합을 수행 합니다. 결과는 `Boolean` 두 식이 모두 인지 여부를 나타내는 값입니다 `True` .  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 앞의 예제에서는 `True` 각각 및의 결과 `False` 를 생성 합니다.  
  
## <a name="example"></a>예제  

 다음 예에서는 연산자를 사용 `And` 하 여 두 숫자 식의 개별 비트에 논리 결합을 수행 합니다. 피연산자의 해당 비트가 둘 다 1로 설정 된 경우 결과 패턴의 비트가 설정 됩니다.  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 앞의 예제에서는 각각 8, 2 및 0의 결과를 생성 합니다.  
  
## <a name="see-also"></a>참고 항목

- [논리/비트 연산자(Visual Basic)](logical-bitwise-operators.md)
- [Visual Basic에서의 연산자 우선 순위](operator-precedence.md)
- [기능별 연산자 목록](operators-listed-by-functionality.md)
- [AndAlso 연산자](andalso-operator.md)
- [Visual Basic의 논리 및 비트 연산자](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
