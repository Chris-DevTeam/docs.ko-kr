---
title: 네임스페이스 접두사 속성 변경
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
ms.openlocfilehash: 14a59a9fdc602e63822a62c102cbffa32d6ba850
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830274"
---
# <a name="changing-namespace-prefix-properties"></a>네임스페이스 접두사 속성 변경
**XmlNode** 클래스를 사용하면 지정된 노드와 연결된 네임스페이스 접두사를 변경할 수 있습니다. 예를 들어, 다음 코드에서는 변경될 요소의 접두사를 보여 줍니다.  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "b"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>");  
XmlElement e = doc.DocumentElement;
e.Prefix = "b";  
Console.WriteLine(doc.InnerXml);  
```  
  
 **출력**  
  
```xml  
<b:test xmlns:a="123" xmlns:b="456" />  
```  
  
 노드의 접두사를 변경해도 해당 네임스페이스는 변경되지 않습니다. 네임스페이스는 노드를 만들 때만 설정될 수 있습니다. 트리를 유지하는 경우 설정된 접두사에 맞게 새 네임스페이스 특성이 계속 유지될 수 있습니다. 새 네임스페이스를 만들 수 없으면 노드가 해당 로컬 이름 및 네임스페이스를 유지하도록 접두사가 변경됩니다. 다음 예제에서는 추가될 네임스페이스 특성을 보여 줍니다.  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<test xmlns='123'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "a"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<test xmlns='123'/>");  
XmlElement e = doc.DocumentElement;
e.Prefix = "a";  
Console.WriteLine(doc.InnerXml);  
```  
  
 **출력**  
  
```xml  
<a:test xmlns="123" xmlns:a="123" />  
```  
  
 **doc.InnerXml** 을 호출한 결과로 트리가 문자열에 유지된 경우에는 `test` 요소의 네임스페이스를 유지하기 위해 `xmlns:a='123'` 특성이 추가되었습니다. 원래 `'123'`이었으며 `'123'`을 유지했습니다.  
  
## <a name="see-also"></a>참조

- [XML DOM(문서 개체 모델)](xml-document-object-model-dom.md)
