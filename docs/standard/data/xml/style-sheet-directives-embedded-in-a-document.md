---
title: 문서에 포함된 스타일시트 지시문
ms.date: 03/30/2017
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
ms.openlocfilehash: 25946fd14a82428ae4367cd33511df68e9929203
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818572"
---
# <a name="style-sheet-directives-embedded-in-a-document"></a>문서에 포함된 스타일시트 지시문

기존 XML에 `<?xml:stylesheet?>`의 스타일시트 지시문이 포함된 경우도 있습니다. Microsoft Internet Explorer에서는 `<?xml-stylesheet?>` 구문 대신 이처럼 포함된 지시문이 적용됩니다. 다음 데이터와 같이 XML 데이터에 `<?xml:stylesheet?>` 지시문이 있는 경우 이 데이터를 XML DOM(문서 개체 모델)으로 로드하려고 하면 예외가 throw됩니다.

```xml
<?xml version="1.0" ?>
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>
<root>
    <test>Node 1</test>
    <test>Node 2</test>
</root>
```

이는 `<?xml:stylesheet?>`가 DOM에 대해 유효하지 않은 **ProcessingInstruction** 으로 간주되기 때문입니다. XML 사양의 네임스페이스에 따라 **ProcessingInstruction** 은 정규화된 이름(QName)이 아닌 콜론이 없는 이름(NCName)만 될 수 있습니다.

XML 사양의 네임스페이스에 대해 다룬 6단원의 내용에 따르면, 이 사양에 따라 **Load** 및 **LoadXml** 메서드를 구현할 경우 문서에 다음과 같은 효과가 발생합니다.

- 모든 요소 형식 및 특성 이름에 콜론이 없거나 하나만 있습니다.

- 엔터티 이름, ProcessingInstruction 대상 또는 노테이션 이름에 콜론이 없습니다.

`<?xml:stylesheet?>`에는 콜론이 있으므로 두 번째 규칙을 위반한 것입니다.

W3C(World Wide Web 컨소시엄) [Associating Style Sheets with XML documents 버전 1.0 권장 사항](https://www.w3.org/TR/xml-stylesheet/)에 따라 XSLT 스타일시트를 XML 문서에 연결하는 처리 명령은 콜론 대신 대시를 사용한 `<?xml-stylesheet?>`입니다.

## <a name="see-also"></a>참조

- [XML DOM(문서 개체 모델)](xml-document-object-model-dom.md)
