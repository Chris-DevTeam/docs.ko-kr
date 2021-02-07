---
description: '자세한 정보: Delegate 문'
title: Delegate 문
ms.date: 07/20/2015
f1_keywords:
- vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
ms.openlocfilehash: 3fbf3d7b47b465fd0850f01170e02b19b7b93b4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673819"
---
# <a name="delegate-statement"></a>Delegate 문

대리자를 선언 하는 데 사용 됩니다. 대리자는 `Shared` 형식의 메서드 또는 개체의 인스턴스 메서드를 참조 하는 참조 형식입니다. 매개 변수와 반환 형식이 일치 하는 프로시저를 사용 하 여이 대리자 클래스의 인스턴스를 만들 수 있습니다. 그런 다음 나중에 대리자 인스턴스를 통해 프로시저를 호출할 수 있습니다.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>부분  
  
|용어|정의|  
|---|---|  
|`attrlist`|선택 사항입니다. 이 대리자에 적용 되는 특성의 목록입니다. 여러 특성은 쉼표로 구분합니다. [특성 목록을](attribute-list.md) 꺾쇠 괄호 (" `<` " 및 "")로 묶어야 합니다 `>` .|  
|`accessmodifier`|선택 사항입니다. 대리자에 액세스할 수 있는 코드를 지정 합니다. 다음 중 하나일 수 있습니다.<br /><br /> - [공용](../modifiers/public.md). 대리자를 선언 하는 요소에 액세스할 수 있는 모든 코드는이 개체에 액세스할 수 있습니다.<br />-   [Protected](../modifiers/protected.md). 대리자의 클래스 또는 파생 클래스 내의 코드만 액세스할 수 있습니다.<br />-   [Friend](../modifiers/friend.md). 동일한 어셈블리 내의 코드만 대리자에 액세스할 수 있습니다.<br />- [개인](../modifiers/private.md). 대리자를 선언 하는 요소 내의 코드만 액세스할 수 있습니다.<br /><br /> - [보호 된 Friend](../modifiers/protected-friend.md) 대리자의 클래스, 파생 클래스 또는 동일한 어셈블리 내의 코드만 대리자에 액세스할 수 있습니다. <br />- [개인 보호](../modifiers/private-protected.md) 대리자의 클래스 또는 동일한 어셈블리의 파생 클래스에 있는 코드만 대리자에 액세스할 수 있습니다. |  
|`Shadows`|선택 사항입니다. 이 대리자가 기본 클래스에서 동일 하 게 명명 된 프로그래밍 요소 또는 오버 로드 된 요소 집합을 요소가 하 고 숨기는 것을 나타냅니다. 모든 종류의 선언된 요소를 다른 종류로 섀도잉할 수 있습니다.<br /><br /> 섀도잉된 요소는 섀도잉 요소에 액세스할 수 없는 위치를 제외하고 해당 요소를 섀도잉하는 파생 클래스 내에서 사용할 수 없습니다. 예를 들어 `Private` 요소가 기본 클래스 요소를 숨기는 경우 요소에 액세스할 수 있는 권한이 없는 코드는 `Private` 대신 기본 클래스 요소에 액세스 합니다.|  
|`Sub`|선택 사항 이지만 또는 중 하나를 `Sub` `Function` 표시 해야 합니다. 는 값을 반환 하지 않는 대리자 프로시저로이 프로시저를 선언 `Sub` 합니다.|  
|`Function`|선택 사항 이지만 또는 중 하나를 `Sub` `Function` 표시 해야 합니다. 는 `Function` 값을 반환 하는 대리자 프로시저로이 프로시저를 선언 합니다.|  
|`name`|필수 사항입니다. 대리자 형식의 이름입니다. 표준 변수 명명 규칙을 따릅니다.|  
|`typeparamlist`|선택 사항입니다. 이 대리자의 형식 매개 변수 목록입니다. 여러 형식 매개 변수는 쉼표로 구분 됩니다. 필요에 따라 `In` 및 제네릭 한정자를 사용 하 여 각 형식 매개 변수를 variant로 선언할 수 있습니다 `Out` . [형식 목록을](type-list.md) 괄호로 묶고 키워드를 사용 해야 합니다 `Of` .|  
|`parameterlist`|선택 사항입니다. 프로시저를 호출할 때 프로시저에 전달 되는 매개 변수 목록입니다. [매개 변수 목록을](parameter-list.md) 괄호로 묶어야 합니다.|  
|`type`|프로시저를 지정 하는 경우 필요 `Function` 합니다. 반환 값의 데이터 형식입니다.|  
  
## <a name="remarks"></a>설명  

 `Delegate`문은 대리자 클래스의 매개 변수 및 반환 형식을 정의 합니다. 매개 변수와 반환 형식이 일치 하는 프로시저를 사용 하 여이 대리자 클래스의 인스턴스를 만들 수 있습니다. 그런 다음 대리자의 메서드를 호출 하 여 대리자 인스턴스를 통해 나중에 프로시저를 호출할 수 있습니다 `Invoke` .  
  
 대리자는 네임 스페이스, 모듈, 클래스 또는 구조 수준에서 선언 될 수 있지만 프로시저 내에서 선언할 수 없습니다.  
  
 각 대리자 클래스는 개체 메서드의 사양이 전달되는 생성자를 정의합니다. 대리자 생성자에 대한 인수는 메서드 또는 람다 식에 대한 참조여야 합니다.  
  
 메서드에 대한 참조를 지정하려면 다음 구문을 사용합니다.  
  
 `AddressOf` [`expression`.]`methodname`  
  
 `expression`의 컴파일 타임 형식은 해당 시그니처가 대리자 클래스의 시그니처와 일치하는 지정된 이름의 메서드를 포함하는 클래스 또는 인터페이스의 이름이어야 합니다. `methodname`은 공유 메서드이거나 인스턴스 메서드일 수 있습니다. `methodname`은 클래스의 기본 메서드에 대해 대리자를 만들더라도 선택 사항이 아닙니다.  
  
 람다 식을 지정하려면 다음 구문을 사용합니다.  
  
 `Function` ([`parm` As `type`, `parm2` As `type2`, ...]) `expression`  
  
 함수의 시그니처는 대리자 형식의 시그니처와 일치해야 합니다. 람다 식에 대 한 자세한 내용은 [람다 식](../../programming-guide/language-features/procedures/lambda-expressions.md)을 참조 하세요.  
  
 대리자에 대한 자세한 내용은 [대리자](../../programming-guide/language-features/delegates/index.md)를 참조하세요.  
  
## <a name="example"></a>예제  

 다음 예에서는 문을 사용 하 여 `Delegate` 두 개의 숫자에서 작동 하 고 숫자를 반환 하는 대리자를 선언 합니다. `DelegateTest`메서드는이 형식의 대리자 인스턴스를 사용 하 여 숫자 쌍에 대해 작동 하는 데 사용 합니다.  
  
 [!code-vb[VbVbalrDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>참고 항목

- [AddressOf 연산자](../operators/addressof-operator.md)
- [으로](of-clause.md)
- [대리자](../../programming-guide/language-features/delegates/index.md)
- [방법: 제네릭 클래스 사용](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Visual Basic의 제네릭 형식](../../programming-guide/language-features/data-types/generic-types.md)
- [공 분산 및 반공 분산](../../programming-guide/concepts/covariance-contravariance/index.md)
- [위치](../modifiers/in-generic-modifier.md)
- [Out](../modifiers/out-generic-modifier.md)
