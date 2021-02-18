---
description: '자세한 정보: -define(Visual Basic)'
title: -define
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: 9d6394ecad8e59d64ef3c51312ac85562ba3ec2c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466980"
---
# <a name="-define-visual-basic"></a>-define(Visual Basic)

조건부 컴파일러 상수를 정의합니다.  
  
## <a name="syntax"></a>구문  
  
```console  
-define:["]symbol[=value][,symbol[=value]]["]  
```

또는

```console  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a>인수  
  
|용어|정의|  
|---|---|  
|`symbol`|필수 요소. 정의할 기호입니다.|  
|`value`|선택 사항입니다. `symbol`을 할당할 값입니다. `value`가 문자열이면 따옴표 대신 백슬래시/따옴표 시퀀스(\\")로 묶어야 합니다. 값을 지정하지 않으면 True가 지정됩니다.|  
  
## <a name="remarks"></a>설명  

 `-define` 옵션은 `-define`로 정의된 상수가 공용상수이며 프로젝트의 모든 파일에 적용된다는 점을 제외하고 원본 파일에서 `#Const` 전처리기 지시문을 사용하는 것과 유사한 효과가 있습니다.  
  
 이 옵션으로 만든 기호를 `#If`...`Then`...`#Else` 지시문과 함께 사용하면 소스 파일을 조건부 컴파일할 수 있습니다.  
  
 `-d`는 약식 `-define`입니다.  
  
 쉼표를 사용해 기호 정의를 구분하여 `-define`으로 여러 기호를 정의할 수 있습니다.  
  
|Visual Studio 통합 개발 환경에서 -define을 설정하려면 다음을 수행합니다.|  
|---|  
|1.  **솔루션 탐색기** 에서 프로젝트를 선택합니다. **프로젝트** 메뉴에서 **속성** 을 클릭합니다. <br />2.  **컴파일** 탭을 클릭합니다.<br />3.  **고급** 을 클릭합니다.<br />4.  **사용자 지정 상수** 상자의 값을 수정합니다.|  
  
## <a name="example"></a>예제  

 다음 코드는 두 조건부 컴파일러 상수를 정의한 다음 사용합니다.  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a>참조

- [Visual Basic 명령줄 컴파일러](index.md)
- [#If...Then...#Else 지시문](../../language-reference/directives/if-then-else-directives.md)
- [#Const 지시문](../../language-reference/directives/const-directive.md)
- [샘플 컴파일 명령줄](sample-compilation-command-lines.md)
