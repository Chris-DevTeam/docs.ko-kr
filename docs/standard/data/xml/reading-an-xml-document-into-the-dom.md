---
title: DOM에 XML 문서 읽어오기
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
ms.openlocfilehash: 61275e9232b3d9e516636869d7153f33133cbd03
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686867"
---
# <a name="reading-an-xml-document-into-the-dom"></a>DOM에 XML 문서 읽어오기

다양한 형식으로 XML 정보를 메모리에 읽어옵니다. 문자열, 스트림, URL, 텍스트 판독기 또는 <xref:System.Xml.XmlReader>에서 파생된 클래스에서 XML 정보를 읽어올 수 있습니다.  
  
 <xref:System.Xml.XmlDocument.Load%2A> 메서드는 문서를 메모리로 가져오며 이 메서드에는 각각의 다양한 형식에서 데이터를 가져오는 데 사용할 수 있는 오버로드된 메서드가 있습니다. 또한 문자열에서 XML을 읽는 <xref:System.Xml.XmlDocument.LoadXml%2A> 메서드도 있습니다.  
  
 XML DOM(문서 개체 모델)이 로드될 때 만들어지는 노드는 각 <xref:System.Xml.XmlDocument.Load%2A> 메서드에 따라 다릅니다. 다음 표에서는 일부 <xref:System.Xml.XmlDocument.Load%2A> 메서드 간의 차이점 및 이러한 차이점을 다루는 항목을 보여 줍니다.  
  
|제목|항목|  
|-------------|-----------|  
|공백 노드 만들기|DOM을 로드하는 데 사용된 개체는 DOM에 생성된 공백 및 유효 공백 노드에 영향을 줍니다. 자세한 내용은 [DOM을 로드할 경우 공백 문자 및 유효 공백 문자 처리](white-space-and-significant-white-space-handling-when-loading-the-dom.md)를 참조하세요.|  
|특정 노드부터 XML 로드 또는 전체 XML 문서 로드|<xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> 메서드를 사용하면 특정 노드에서 DOM으로 데이터를 로드할 수 있습니다. 자세한 내용은. [판독기에서 데이터 로드](load-data-from-a-reader.md)를 참조하세요.|  
|XML을 로드할 때 유효성 검사|DOM으로 XML 데이터를 로드할 때 유효성을 검사할 수 있습니다. <xref:System.Xml.XmlReader> 유효성 검사를 사용하면 됩니다. XML을 로드할 때 유효성 검사에 대한 자세한 내용은 [DOM에서의 XML 문서 유효성 검사](validating-an-xml-document-in-the-dom.md)를 참조하세요.|  
  
 다음 예제에서는 <xref:System.Xml.XmlDocument.LoadXml%2A> 메서드를 사용하여 XML을 로드하고 `data.xml`이라는 텍스트 파일에 데이터를 저장하는 방법을 보여 줍니다.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
        ' Create the XmlDocument.  
        Dim doc As New XmlDocument()  
        doc.LoadXml(("<book genre='novel' ISBN='1-861001-57-5'>" & _  
                    "<title>Pride And Prejudice</title>" & _  
                    "</book>"))  
        ' Save the document to a file.  
        doc.Save("data.xml")  
    End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    public static void Main()  
    {  
        // Create the XmlDocument.  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5'>" +  
                    "<title>Pride And Prejudice</title>" +  
                    "</book>");  
  
        // Save the document to a file.  
        doc.Save("data.xml");  
    }  
}  
```  
  
## <a name="see-also"></a>참조

- [XML DOM(문서 개체 모델)](xml-document-object-model-dom.md)
