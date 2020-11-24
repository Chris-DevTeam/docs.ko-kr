---
title: XslTransform의 출력
ms.date: 03/30/2017
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
ms.openlocfilehash: 765f6f9a91cc44a55ab0d66ed71f19f60ef81a56
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830066"
---
# <a name="outputs-from-an-xsltransform"></a>XslTransform의 출력
스타일시트는 `<xsl:output>` 특성과 `method` 문을 함께 사용하여 출력 형식을 결정할 수 있기 때문에 다음 표에서는 출력을 쓸 때 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 메서드를 사용하고 출력 형식이 <xref:System.IO.Stream>이나 <xref:System.IO.TextWriter>로 선언된 경우의 출력 형식을 보여 줍니다.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> 클래스는 .NET Framework 2.0에서 사용되지 않습니다. <xref:System.Xml.Xsl.XslCompiledTransform> 클래스를 사용하여 XSLT(Extensible Stylesheet Language for Transformations) 변환을 수행할 수 있습니다. 자세한 내용은 [XslCompiledTransform 클래스 사용](using-the-xslcompiledtransform-class.md) 및 [XslTransform 클래스에서 마이그레이션](migrating-from-the-xsltransform-class.md)을 참조하세요.  
  
 스타일시트는 `<xsl:output>` 특성과 `method` 문을 함께 사용하여 출력 형식을 결정할 수 있기 때문에 다음 표에서는 출력을 쓸 때 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 메서드를 사용하고 출력 형식이 <xref:System.IO.Stream>이나 <xref:System.IO.TextWriter>로 선언된 경우의 출력 형식을 보여 줍니다. 다음 표에서는 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 메서드와 `<xsl:output>` 문을 함께 사용하여 출력 형식이 선언된 경우의 결과를 설명합니다.  
  
|\<xsl:output method = > 특성|결과 형식|  
|-----------------------------------------|-------------------|  
|method="xml"|XML|  
|method="html"|HTML|  
|method="text"|텍스트|  
  
> [!NOTE]
> 참고: <xref:System.Xml.Xsl.XslTransform.Transform%2A> 메서드의 출력이 <xref:System.Xml.XmlReader> 또는 <xref:System.Xml.XmlWriter>이면 `<xsl:output>` 문은 무시됩니다.  
  
 다음 특성은 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 메서드 출력이 <xref:System.IO.Stream> 또는 <xref:System.IO.TextWriter>인 경우에 지원됩니다.  
  
- encoding*  
  
- omit-xml-declaration  
  
- 독립 실행형  
  
- doctype-public  
  
- doctype-system  
  
- cdata-section-elements  
  
- indent  
  
    > [!NOTE]
    > \*<xref:System.Xml.Xsl.XslTransform.Transform%2A> 메서드에서 <xref:System.IO.TextWriter>에 해당 출력을 보내는 동안에는 인코딩 특성이 무시됩니다. 대신 <xref:System.IO.TextWriter>의 인코딩 속성이 사용됩니다.
  
 다음 특성은 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 메서드 출력이 <xref:System.IO.Stream>인 경우에 무시됩니다.  
  
- version: 항상 1.0  
  
- media-type: 미디어 형식  
  
## <a name="escaping-special-characters"></a>특수 문자 이스케이프  
 `<xsl:text disable-output-escaping>` 태그는 특수 문자를 XML 형식으로 이스케이프해야 하는지(예: `<&lt>` 기호 대신 `"<"` 사용), 현재 상태로 유지해야 하는지 여부를 나타내는 데 사용됩니다. `disable-output-escaping` 특성은 <xref:System.Xml.XmlReader> 또는 <xref:System.Xml.XmlWriter> 개체로 변형될 때 무시되며 특수 문자에는 영향을 주지 않습니다.  
  
## <a name="see-also"></a>참조

- [XslTransform 클래스의 XSLT 프로세서 구현](xsltransform-class-implements-the-xslt-processor.md)
