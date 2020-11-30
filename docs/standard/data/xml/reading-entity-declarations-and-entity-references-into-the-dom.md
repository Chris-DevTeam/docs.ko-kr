---
title: DOM에 엔터티 선언 및 엔터티 참조 읽어오기
ms.date: 03/30/2017
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
ms.openlocfilehash: 8af9e4c1aedc588bcbf3b4f43e9e562fda2f3ce3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686828"
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a>DOM에 엔터티 선언 및 엔터티 참조 읽어오기

엔터티는 XML에서 내용 또는 태그 대신 사용되는 이름을 나타내는 선언입니다. 엔터티는 두 부분으로 구성됩니다. 먼저 엔터티 선언을 사용하여 이름을 대체 내용에 연결해야 합니다. 엔터티 선언은 DTD(문서 종류 정의) 또는 XML 스키마에 `<!ENTITY name "value">` 구문을 사용하여 만듭니다. 그러면 엔터티 선언에 정의된 이름이 XML에서 사용됩니다. XML에서 사용될 경우 이 이름을 엔터티 참조라고 합니다. 예를 들어, 다음 엔터티 선언은 "Microsoft Press"라는 내용과 연결될 `publisher`라는 이름의 엔터티를 선언합니다.  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 다음 예제에서는 XML에서 엔터티 참조로 이 엔터티 선언을 사용하는 방법을 보여 줍니다.  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 문서가 메모리에 로드되면 일부 파서는 자동으로 엔터티를 확장합니다. 따라서 XML을 메모리에 읽어오면 엔터티 선언이 기억되고 저장됩니다. 그런 다음 파서가 일반 엔터티 참조를 식별하는 `&;` 문자를 발견하면 엔터티 선언 테이블에서 해당 이름을 찾습니다. `&publisher;` 참조는 해당 참조가 나타내는 내용으로 대체됩니다. 다음 XML을 사용한다고 가정합니다.  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 엔터티 참조를 확장하고 `&publisher;`를 Microsoft Press라는 내용으로 바꿔 다음과 같은 확장된 XML을 얻을 수 있습니다.  
  
 **출력**  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 엔터티에는 여러 종류가 있습니다. 다음 다이어그램은 엔터티 형식과 용어의 분류를 보여 줍니다.  
  
 ![엔터티 형식 계층 구조의 순서도](media/entity-hierarchy.gif "Entity_hierarchy")  
  
 기본적으로 이 XML DOM(문서 개체 모델)의 Microsoft .NET Framework 구현은 XML이 로드될 때 엔터티 참조를 유지하고 엔터티를 확장하지 않습니다. 즉, 문서를 DOM에 로드할 때 참조 변수 `&publisher;`를 포함하는 **XmlEntityReference** 노드가 생성되며 자식 노드는 DTD에 선언된 엔터티의 내용을 나타냅니다.  
  
 다음 다이어그램은 `<!ENTITY publisher "Microsoft Press">` 엔터티 선언을 사용하여 해당 선언에서 생성된 **XmlEntity** 및 **XmlText** 노드를 보여줍니다.  
  
 ![엔터티 선언에서 만든 노드](media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")  
  
 엔터티 참조가 확장되는 경우와 그렇지 않은 경우에 메모리의 DOM 트리에 생성되는 노드가 달라집니다. 생성되는 노드의 차이점은 [엔터티 참조 유지](entity-references-are-preserved.md) 및 [유지되지 않고 확장되는 엔터티 참조](entity-references-are-expanded-and-not-preserved.md) 항목에서 설명합니다.  
  
## <a name="see-also"></a>참조

- [XML DOM(문서 개체 모델)](xml-document-object-model-dom.md)
