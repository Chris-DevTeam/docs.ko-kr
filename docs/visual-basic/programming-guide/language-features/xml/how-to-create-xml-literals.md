---
description: '자세히 알아보기: 방법: XML 리터럴 만들기 (Visual Basic)'
title: '방법: XML 리터럴 만들기'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: 0e57b037d0567002fd570025e147771c4fab38f4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433293"
---
# <a name="how-to-create-xml-literals-visual-basic"></a>방법: XML 리터럴 만들기(Visual Basic)

XML 리터럴을 사용 하 여 코드에서 직접 XML 문서, 조각 또는 요소를 만들 수 있습니다. 이 항목의 예제에서는 세 개의 자식 요소가 있는 XML 요소를 만드는 방법 및 XML 문서를 만드는 방법을 보여 줍니다.  
  
 Api를 사용 하 여 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 개체를 만들 수도 있습니다 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] . 자세한 내용은 <xref:System.Xml.Linq.XElement>를 참조하세요.  
  
### <a name="to-create-an-xml-element"></a>XML 요소를 만들려면  
  
- 실제 XML 구문과 동일한 XML 리터럴 구문을 사용 하 여 XML 인라인을 만듭니다.  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     코드를 실행합니다. 이 코드의 출력은 다음과 같습니다.  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a>XML 문서를 만들려면  
  
- XML 문서 인라인을 만듭니다. 다음 코드는 리터럴 구문, XML 선언, 처리 명령, 주석 및 다른 요소를 포함 하는 요소를 포함 하는 XML 문서를 만듭니다.  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
     코드를 실행합니다. 이 코드의 출력은 다음과 같습니다.  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a>추가 정보

- [XML](index.md)
- [Visual Basic에서 XML 만들기](creating-xml.md)
- [XML 요소 리터럴](../../../language-reference/xml-literals/xml-element-literal.md)
- [XML 문서 리터럴](../../../language-reference/xml-literals/xml-document-literal.md)
