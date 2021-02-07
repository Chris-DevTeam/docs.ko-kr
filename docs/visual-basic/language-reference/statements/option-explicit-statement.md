---
description: '자세한 정보: Option Explicit 문 (Visual Basic)'
title: Option Explicit 문
ms.date: 07/20/2015
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
helpviewer_keywords:
- declaring variables [Visual Basic], explicit
- forced variable declaration in Option Explicit statement [Visual Basic]
- Explicit keyword
- explicit variable declaration
- Option Explicit statement [Visual Basic]
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
ms.openlocfilehash: 11f59508125167fde98b4fc359dde7fd7c539b75
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741616"
---
# <a name="option-explicit-statement-visual-basic"></a>Option Explicit 문(Visual Basic)

파일의 모든 변수를 명시적으로 선언 하거나 변수의 암시적 선언을 허용 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a>부분  

 `On`  
 선택 사항입니다. 검사를 사용 하도록 설정 `Option Explicit` 합니다. `On`또는 `Off` 를 지정 하지 않으면 기본값은 `On` 입니다.  
  
 `Off`  
 선택 사항입니다. 검사를 사용 하지 않습니다 `Option Explicit` .  
  
## <a name="remarks"></a>설명  

 `Option Explicit On` `Option Explicit` 파일이 파일에 표시 되 면 또는 문을 사용 하 여 모든 변수를 명시적으로 선언 해야 합니다 `Dim` `ReDim` . 선언 되지 않은 변수 이름을 사용 하려고 하면 컴파일 타임에 오류가 발생 합니다. `Option Explicit Off`문은 변수를 암시적으로 선언할 수 있습니다.  
  
 `Option Explicit` 문은 사용하는 경우 파일에서 다른 소스 코드 문 앞에 나와야 합니다.  
  
> [!NOTE]
> `Option Explicit`일반적으로로 설정 하는 것 `Off` 은 좋은 방법이 아닙니다. 하나 이상의 위치에서 변수 이름을 잘못 입력할 수 있습니다. 그러면 프로그램이 실행될 때 예기치 않은 결과가 발생할 수 있습니다.  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a>Option Explicit 문이 없는 경우  

 소스 코드에 문이 포함 되어 있지 않은 경우에는 `Option Explicit` [컴파일 페이지, 프로젝트 디자이너 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) 에 대 한 **Option Explicit** 설정이 사용 됩니다. 명령줄 컴파일러를 사용 하는 경우 [-옵션 explicit](../../reference/command-line-compiler/optionexplicit.md) 컴파일러 옵션이 사용 됩니다.  
  
#### <a name="to-set-option-explicit-in-the-ide"></a>IDE에서 Option Explicit를 설정 하려면  
  
1. **솔루션 탐색기** 에서 프로젝트를 선택합니다. **프로젝트** 메뉴에서 **속성** 을 클릭합니다.  
  
2. **컴파일** 탭을 클릭합니다.  
  
3. **옵션 Explicit** 상자에서 값을 설정 합니다.  
  
 새 프로젝트를 만들 때 **컴파일** 탭의 **옵션 Explicit** 설정은 **VB 기본값** 대화 상자의 **옵션 explicit** 설정으로 설정 됩니다. **VB 기본값** 대화 상자에 액세스 하려면 **도구** 메뉴에서 **옵션** 을 클릭 합니다. **옵션** 대화 상자에서 **프로젝트 및 솔루션** 을 확장하고 **VB 기본값** 을 클릭합니다. **VB 기본값** 의 초기 기본 설정은 `On` 입니다.  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a>명령줄에서 Option Explicit를 설정 하려면  
  
- **Vbc** 명령에 [-옵션 explicit](../../reference/command-line-compiler/optionexplicit.md) 컴파일러 옵션을 포함 합니다.  
  
## <a name="example"></a>예제  

 다음 예에서는 문을 사용 `Option Explicit` 하 여 모든 변수를 명시적으로 선언 합니다. 선언 되지 않은 변수를 사용 하려고 하면 컴파일 타임에 오류가 발생 합니다.  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a>참고 항목

- [Dim 문](dim-statement.md)
- [ReDim 문](redim-statement.md)
- [Option Compare 문](option-compare-statement.md)
- [Option Strict 문](option-strict-statement.md)
- [-optioncompare](../../reference/command-line-compiler/optioncompare.md)
- [-optionexplicit](../../reference/command-line-compiler/optionexplicit.md)
- [-optionstrict](../../reference/command-line-compiler/optionstrict.md)
- [옵션 대화 상자, 프로젝트, Visual Basic 기본값](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
