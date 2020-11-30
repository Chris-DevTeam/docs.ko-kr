---
title: XML 스키마 작업
ms.date: 03/30/2017
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
ms.openlocfilehash: 0290cd31d9477d2c5a30a6efa907263fed137258
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675492"
---
# <a name="working-with-xml-schemas"></a>XML 스키마 작업

XML 문서 구조, 요소 관계, 데이터 형식, 내용 제약 조건 등을 정의하려면 DTD(문서 종류 정의) 또는 XSD(XML 스키마 정의 언어) 스키마를 사용합니다. XML 문서가 제대로 구성된 것으로 간주되더라도 W3C(World Wide Web 컨소시엄) XML(Extensible Markup Language) 1.0 권장 사항에 정의된 구문 요구 사항을 모두 만족할 경우 제대로 구성되고 DTD나 스키마에 정의된 제약 조건을 준수해야만 유효한 것으로 간주됩니다. 그러므로 유효한 모든 XML 문서가 제대로 구성되었더라도 제대로 구성된 XML 문서가 모두 유효한 것은 아닙니다.  
  
 XML에 대한 자세한 내용은 [W3C XML 1.0 Recommendation](https://www.w3.org/TR/REC-xml/)(W3C XML 1.0 권장 사항)을 참조하세요. XML 스키마에 대한 자세한 내용은 [W3C XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/) 및 [W3C XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/) 권장 사항을 참조하세요.  
  
## <a name="in-this-section"></a>섹션 내용  

 [XML SOM(스키마 개체 모델)](xml-schema-object-model-som.md)  
 파일에서 XSD(XML 스키마 정의 언어) 스키마를 읽거나 프로그래밍 방식으로 메모리 내 스키마를 만들 수 있는 클래스 집합을 제공하는 <xref:System.Xml.Schema?displayProperty=nameWithType> 네임스페이스의 SOM(스키마 개체 모델)에 대해 설명합니다.  
  
 [스키마 컴파일을 위한 XmlSchemaSet](xmlschemaset-for-schema-compilation.md)  
 XSD 스키마를 저장하고 유효성을 검사할 수 있는 캐시인 <xref:System.Xml.Schema.XmlSchemaSet> 클래스에 대해 설명합니다.  
  
 [XmlSchemaValidator 밀어넣기 기반 유효성 검사](xmlschemavalidator-push-based-validation.md)  
 밀어넣기 기반 방식으로 XSD 스키마에 대해 XML 데이터의 유효성을 검사할 수 있는 효과적인 고성능 메커니즘을 제공하는 <xref:System.Xml.Schema.XmlSchemaValidator> 클래스에 대해 설명합니다.  
  
 [XML 스키마 유추](inferring-an-xml-schema.md)  
 <xref:System.Xml.Schema.XmlSchemaInference> 클래스를 사용하여 XML 문서 구조에서 XSD 스키마를 유추하는 방법을 설명합니다.  
  
## <a name="reference"></a>참고  

 <xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader>  
  
## <a name="related-sections"></a>관련 단원  

 [DOM에서의 XML 문서 유효성 검사](validating-an-xml-document-in-the-dom.md)  
 DOM(문서 개체 모델)에서 XML의 유효성을 검사하는 방법을 설명합니다. XML을 DOM에 로드할 때 유효성을 검사하거나 DOM에서 이전에 무효화한 XML 문서의 유효성을 검사할 수 있습니다.  
  
 [XPathNavigator를 사용하여 스키마 유효성 검사](schema-validation-using-xpathnavigator.md)  
 <xref:System.Xml.XPath.XPathNavigator> 클래스를 사용하여 탐색 및 편집하는 XML의 유효성 검사 방법을 설명합니다.
