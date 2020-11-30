---
title: DOM에서 노드 제거
ms.date: 03/30/2017
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
ms.openlocfilehash: 5b1a6dfb2da4556e0332441a8e56679aee37a091
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686659"
---
# <a name="removing-nodes-from-the-dom"></a>DOM에서 노드 제거

XML DOM(문서 개체 모델)에서 노드를 제거하려면 <xref:System.Xml.XmlNode.RemoveChild%2A> 메서드를 사용하여 특정 노드를 제거합니다. 이때 삭제하는 노드가 리프 노드가 아닌 경우 이 노드에 속한 하위 트리도 제거됩니다.  
  
 DOM에서 여러 노드를 제거하려면 <xref:System.Xml.XmlNode.RemoveAll%2A> 메서드를 사용하여 현재 노드의 모든 자식 및 특성을(해당 사항이 있을 경우) 제거합니다.  
  
 <xref:System.Xml.XmlNamedNodeMap>으로 작업하는 경우 <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> 메서드를 사용하여 노드를 제거할 수 있습니다.  
  
 특성을 제거하려면 [DOM의 요소 노드에서 특성 제거](removing-attributes-from-an-element-node-in-the-dom.md)를 참조하세요.  
  
## <a name="see-also"></a>참조

- [XML DOM(문서 개체 모델)](xml-document-object-model-dom.md)
