---
title: DOM을 로드할 경우 공백 문자 및 유효 공백 문자 처리
ms.date: 03/30/2017
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
ms.openlocfilehash: dbb0962dc47ff5847ac78ed4f6252bf8ab9674aa
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818481"
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a>DOM을 로드할 경우 공백 문자 및 유효 공백 문자 처리
문서를 로드할 때 이 옵션을 설정하여 공백을 유지하고 문서 트리에 **XmlWhitespace** 노드를 만들 수 있습니다. 공백 노드를 만들려면 **PreserveWhitespace** 속성을 true로 설정합니다. 이 속성이 기본값인 **false** 로 설정되면 공백 노드가 생성되지 않습니다. **PreserveWhitespace** 플래그 설정에 관계없이 항상 유효 공백 노드가 유지되며 이 데이터를 나타내는 **XmlSignificantWhitespace** 노드가 메모리에 생성됩니다.  
  
 판독기에서 문서가 로드되면 **XmlDocument** 클래스의 **PreserveWhitespace** 플래그 속성 설정은 **XmlTextReader** 의 **WhitespaceHandling** 속성이 **WhitespaceHandling.None** 으로 설정되지 않은 경우에만 **XmlWhitespace** 노드 생성에 영향을 줍니다. 이것은 판독기의 **WhitespaceHandling** 속성 값이 **XmlDocument** 의 해당 플래그 설정보다 우선하기 때문입니다. **XmlSignificantWhitespace** 에 대한 자세한 내용은 <xref:System.Xml.XmlSignificantWhitespace>를 참조하세요.  
  
## <a name="see-also"></a>참조

- [XML DOM(문서 개체 모델)](xml-document-object-model-dom.md)
