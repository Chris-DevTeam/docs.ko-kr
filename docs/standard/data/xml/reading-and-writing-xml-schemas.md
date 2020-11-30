---
title: XML 스키마 읽기 및 쓰기
description: SOM(스키마 개체 모델) API를 사용하여 .NET의 파일 또는 다른 소스에서 XSD(XML 스키마 정의 언어) 스키마를 읽고 씁니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
ms.openlocfilehash: 7ba736272579451cf30c5e78026ffaa4186e03c9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686854"
---
# <a name="reading-and-writing-xml-schemas"></a>XML 스키마 읽기 및 쓰기

SOM(스키마 개체 모델) API를 사용하여 파일 또는 기타 소스에서 XSD(XML 스키마 정의 언어) 스키마를 읽고 쓸 수 있으며 W3C(World Wide Web 컨소시엄) XML 스키마 권장 사항에 정의된 구조에 매핑되는 <xref:System.Xml.Schema?displayProperty=nameWithType> 네임스페이스에서 클래스를 사용하여 메모리 내 XML 스키마를 빌드할 수 있습니다.  
  
## <a name="reading-and-writing-xml-schemas"></a>XML 스키마 읽기 및 쓰기  

 <xref:System.Xml.Schema.XmlSchema> 클래스는 XML 스키마를 읽고 쓰는 <xref:System.Xml.Schema.XmlSchema.Read%2A> 및 <xref:System.Xml.Schema.XmlSchema.Write%2A> 메서드를 제공합니다. <xref:System.Xml.Schema.XmlSchema.Read%2A> 메서드는 XML 스키마를 나타내는 <xref:System.Xml.Schema.XmlSchema> 개체를 반환하며 선택적 <xref:System.Xml.Schema.ValidationEventHandler>를 매개 변수로 사용하여 XML 스키마를 읽는 동안 발생한 스키마 유효성 검사 경고 및 오류를 처리합니다.  
  
 <xref:System.Xml.Schema.XmlSchema.Write%2A> 메서드는 XML 스키마를 <xref:System.IO.Stream>, <xref:System.IO.TextWriter> 및 <xref:System.Xml.XmlWriter> 개체에 작성하고 선택적 <xref:System.Xml.XmlNamespaceManager> 개체를 매개 변수로 사용할 수 있습니다. <xref:System.Xml.XmlNamespaceManager>를 사용하여 XML 스키마에서 발생한 네임스페이스를 처리합니다. <xref:System.Xml.XmlNamespaceManager> 클래스에 대한 자세한 내용은 [XML 문서의 네임스페이스 관리](managing-namespaces-in-an-xml-document.md)를 참조하세요.  
  
 다음 코드 예제에서는 파일에서 XML 스키마를 읽고 쓰는 방법을 보여 줍니다. 이 코드 예제에서는 `example.xsd` 파일을 가져와서 <xref:System.Xml.Schema.XmlSchema>`static` 메서드를 사용하여 <xref:System.Xml.Schema.XmlSchema.Read%2A> 개체로 읽어온 다음 이 파일을 콘솔 및 새 `new.xsd` 파일에 씁니다. 또한 이 코드 예제에서는 <xref:System.Xml.Schema.ValidationEventHandler>를 `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> 메서드에 매개 변수로 제공하여 XML 스키마를 읽는 동안 발생한 스키마 유효성 검사 경고 또는 오류를 처리합니다. <xref:System.Xml.Schema.ValidationEventHandler>를 지정하지 않으면(`null`) 경고 또는 오류가 보고되지 않습니다.  
  
 [!code-cpp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaReadWriteExample/CPP/XmlSchemaReadWriteExample.cpp#1)]
 [!code-csharp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaReadWriteExample/CS/XmlSchemaReadWriteExample.cs#1)]
 [!code-vb[XmlSchemaReadWriteExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaReadWriteExample/VB/XmlSchemaReadWriteExample.vb#1)]  
  
 이 예제에서는 `example.xsd`를 입력으로 사용합니다.  
  
```xml  
<?xml version="1.0"?>  
<xs:schema id="play" targetNamespace="http://tempuri.org/play.xsd" elementFormDefault="qualified" xmlns="http://tempuri.org/play.xsd" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name='myShoeSize'>  
        <xs:complexType>  
            <xs:simpleContent>  
                <xs:extension base='xs:decimal'>  
                    <xs:attribute name='sizing' type='xs:string' />  
                </xs:extension>  
            </xs:simpleContent>  
        </xs:complexType>  
    </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a>참조

- [XML 스키마 개체 모델 개요](xml-schema-object-model-overview.md)
- [XML 스키마 빌드](building-xml-schemas.md)
- [XML 스키마 통과](traversing-xml-schemas.md)
- [XML 스키마 편집](editing-xml-schemas.md)
- [XML 스키마 포함하기 또는 가져오기](including-or-importing-xml-schemas.md)
- [스키마 컴파일을 위한 XmlSchemaSet](xmlschemaset-for-schema-compilation.md)
- [Post-Schema Compilation Infoset](post-schema-compilation-infoset.md)
- [XML 문서의 네임스페이스 관리](managing-namespaces-in-an-xml-document.md)
