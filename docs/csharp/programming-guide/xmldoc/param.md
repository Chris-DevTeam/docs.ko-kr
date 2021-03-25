---
title: <param> - C# 프로그래밍 가이드
description: XML <param> 태그에 대해 알아봅니다. 이 태그는 메서드의 매개 변수 중 하나를 설명하기 위해 메서드 선언에 대한 주석에서 사용됩니다.
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 1385365b2cdf18563686fdf4a5a1b17b89feafcd
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477987"
---
# <a name="param-c-programming-guide"></a>\<param>(C# 프로그래밍 가이드)

## <a name="syntax"></a>구문

```xml
<param name="name">description</param>
```

## <a name="parameters"></a>매개 변수

- `name`

  메서드 매개 변수의 이름입니다. 이름을 큰따옴표(“ ”)로 묶습니다.

- `description`

  매개 변수에 대한 설명입니다.

## <a name="remarks"></a>설명

`<param>` 태그는 메서드의 매개 변수 중 하나를 설명하기 위해 메서드 선언에 대한 주석에서 사용해야 합니다. 여러 매개 변수를 문서화하려면 여러 개의 `<param>` 태그를 사용합니다.

`<param>` 태그에 대한 텍스트는 IntelliSense, 개체 브라우저, 코드 주석 웹 보고서에 표시됩니다.

[**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile)로 컴파일하여 문서 주석을 파일로 처리합니다.

## <a name="example"></a>예제

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a>참조

- [C# 프로그래밍 가이드](../index.md)
- [문서 주석에 대한 권장 태그](./recommended-tags-for-documentation-comments.md)
