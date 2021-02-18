---
description: '자세한 정보: -optionstrict'
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: ad58c7775eaa77c1bf693629cf12cc70e4222920
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475905"
---
# <a name="-optionstrict"></a>-optionstrict

엄격한 형식 의미 체계를 적용하여 암시적 형식 변환을 제한합니다.

## <a name="syntax"></a>구문

```console
-optionstrict[+ | -]
-optionstrict[:custom]
```

## <a name="arguments"></a>인수

`+` &#124; `-`  
선택 사항입니다. `-optionstrict+` 옵션은 암시적 형식 변환을 제한합니다. 이 옵션의 기본값은 `-optionstrict-`입니다. `-optionstrict+` 옵션은 `-optionstrict`와 동일합니다. 허용 형식 의미 체계에 둘 다 사용할 수 있습니다.

`custom`  
필수 요소. 엄격한 언어 의미 체계를 준수하지 않을 경우 경고합니다.

## <a name="remarks"></a>설명

`-optionstrict+`가 적용되면 확장 형식 변환만 암시적으로 수행할 수 있습니다. 정수 형식 개체에 `Decimal` 형식 개체를 할당하는 등의 암시적 축소 형식 변환은 오류로 보고됩니다.

암시적 축소 형식 변환에 대한 경고를 생성하려면 `-optionstrict:custom`을 사용합니다. `-nowarn:numberlist`를 사용하여 특정 경고를 무시하고, `-warnaserror:numberlist`를 사용하여 특정 경고를 오류로 처리합니다.

### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a>Visual Studio IDE에서 -optionstrict를 설정하려면 다음을 수행합니다.

1. **솔루션 탐색기** 에서 프로젝트를 선택합니다. **프로젝트** 메뉴에서 **속성** 을 클릭합니다.

2. **컴파일** 탭을 클릭합니다.

3. **Option Strict** 상자에서 값을 수정합니다.

### <a name="to-set--optionstrict-programmatically"></a>프로그래밍 방식으로 -optionstrict를 설정하려면

[Option Strict 문](../../language-reference/statements/option-strict-statement.md)을 참조하세요.

## <a name="example"></a>예제

다음 코드에서는 엄격한 형식 의미 체계를 사용하여 `Test.vb`를 컴파일합니다.

```console
vbc -optionstrict+ test.vb
```

## <a name="see-also"></a>참조

- [Visual Basic 명령줄 컴파일러](index.md)
- [-optioncompare](optioncompare.md)
- [-optionexplicit](optionexplicit.md)
- [-optioninfer](optioninfer.md)
- [-nowarn](nowarn.md)
- [-warnaserror(Visual Basic)](warnaserror.md)
- [샘플 컴파일 명령줄](sample-compilation-command-lines.md)
- [Option Strict 문](../../language-reference/statements/option-strict-statement.md)
- [옵션 대화 상자, 프로젝트, Visual Basic 기본값](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
