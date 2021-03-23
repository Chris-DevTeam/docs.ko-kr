---
title: XML 문서 주석 - C# 프로그래밍 가이드
description: XML 문서 주석에 대해 알아봅니다. 특수 주석 필드에 XML 요소를 넣어 코드의 설명서를 만들 수 있습니다.
ms.date: 07/20/2015
f1_keywords:
- cs.xml
helpviewer_keywords:
- XML [C#], code comments
- comments [C#], XML
- documentation comments [C#]
- C# source code files
- C# language, XML code comments
- XML documentation comments [C#]
ms.assetid: 803b7f7b-7428-4725-b5db-9a6cff273199
ms.openlocfilehash: d784ec58096e44cf010edd279f682555df58a8ef
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103478389"
---
# <a name="xml-documentation-comments-c-programming-guide"></a>XML 문서 주석(C# 프로그래밍 가이드)

C#에서는 주석이 참조하는 코드 블록 바로 앞의 소스 코드의 특별 주석 필드(세 개의 슬래시로 표시)에 XML 요소를 포함하여 코드에 대한 문서를 만들 수 있습니다. 예를 들면 다음과 같습니다.

```csharp
/// <summary>
///  This class performs an important function.
/// </summary>
public class MyClass {}
```

[**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) 옵션을 사용하여 컴파일하는 경우 컴파일러는 소스 코드에서 모든 XML 태그를 검색하고 XML 문서 파일을 만듭니다. 컴파일러에서 생성한 파일을 기반으로 해서 최종 문서를 만들려면 사용자 지정 도구를 만들거나 [DocFX](https://dotnet.github.io/docfx/) 또는 [Sandcastle](https://github.com/EWSoftware/SHFB)과 같은 도구를 사용하면 됩니다.

XML 요소를 참조하려면(예를 들어, 함수가 XML 문서 주석에서 설명하려는 특정 XML 요소를 처리하는 경우) 표준 인용 메커니즘(`<` 및 `>`)을 사용할 수 있습니다.  코드 참조(`cref`) 요소에서 제네릭 식별자를 참조하려면 이스케이프 문자(예: `cref="List&lt;T&gt;"`) 또는 괄호(`cref="List{T}"`)를 사용할 수 있습니다.  특별한 경우로, 컴파일러는 제네릭 식별자를 참조할 때 문서 주석을 더 쉽게 작성할 수 있도록 괄호를 꺾쇠 괄호로 구문 분석합니다.

> [!NOTE]
> XML 문서 주석은 메타데이터가 아닙니다. 이러한 주석은 컴파일된 어셈블리에 포함되지 않으므로 리플렉션을 통해 액세스할 수 없습니다.

## <a name="in-this-section"></a>단원 내용

- [문서 주석에 대한 권장 태그](./recommended-tags-for-documentation-comments.md)

- [XML 파일 처리](./processing-the-xml-file.md)

- [문서 태그에 대한 구분 기호](./delimiters-for-documentation-tags.md)

- [XML 문서 기능을 사용하는 방법](./how-to-use-the-xml-documentation-features.md)

## <a name="related-sections"></a>관련 단원

자세한 내용은 다음을 참조하세요.

- [**DocumentationFile**(설명서 주석 처리)](../../language-reference/compiler-options/output.md#documentationfile)

## <a name="c-language-specification"></a>C# 언어 사양

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>참조

- [C# 프로그래밍 가이드](../index.md)
