---
title: <see> - C# 프로그래밍 가이드
description: XML <see> 태그에 대해 알아봅니다. 이 태그를 사용하면 예를 들어 cref 특성을 사용하여 텍스트 내에서 링크를 지정할 수 있습니다.
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 154feca5e7e4f4d3f5313c4ae05cd991e69e298f
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477766"
---
# <a name="see-c-programming-guide"></a>\<see>(C# 프로그래밍 가이드)

## <a name="syntax"></a>구문

```xml
<see cref="member"/>
```

## <a name="parameters"></a>매개 변수

- cref = "`member`"

  현재 컴파일 환경에서 호출할 수 있는 멤버 또는 필드에 대한 참조입니다. 컴파일러는 지정된 코드 요소가 있으며 `member`를 출력 XML의 요소 이름에 전달하는지 확인합니다. *멤버* 는 큰따옴표(“ ”)로 묶으세요.

## <a name="remarks"></a>설명

`<see>` 태그를 사용하면 텍스트 내부에서 링크를 지정할 수 있습니다. 참조 섹션에 텍스트를 배치해야 한다고 지정하려면 [\<seealso>](./seealso.md)를 사용합니다. 코드 요소의 문서 페이지에 대한 내부 하이퍼링크를 만들려면 [cref 특성](./cref-attribute.md)을 사용합니다. 또한 ``href``는 하이퍼링크로 작동하는 유효한 특성입니다.

[**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile)로 컴파일하여 문서 주석을 파일로 처리합니다.

다음 예제에서는 요약 섹션의 `<see>` 태그를 보여 줍니다.

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a>참조

- [C# 프로그래밍 가이드](../index.md)
- [문서 주석에 대한 권장 태그](./recommended-tags-for-documentation-comments.md)
