---
title: '방법: 개체 직렬화'
description: '이 문서에서는 개체를 직렬화하는 방법을 보여 줍니다. XML 스트림이 저장된 전송 형식(예: 스트림 또는 파일)을 선택합니다.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
ms.openlocfilehash: ce8510a987f75ed4110a44ffa9f2ac813d36a5be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678898"
---
# <a name="how-to-serialize-an-object"></a>방법: 개체 직렬화

개체를 serialize하려면 먼저 serialize될 개체를 만들고 해당 public 속성과 필드를 설정합니다. 이렇게 하려면 XML 스트림이 저장될 전송 형식을 스트림 또는 파일 중에서 결정합니다. 예를 들어 XML 스트림을 영구적 형태로 저장해야 하는 경우에는 <xref:System.IO.FileStream> 개체를 만듭니다.  
  
> [!NOTE]
> XML serialization에 대한 다른 예제를 보려면 [XML Serialization 예제](examples-of-xml-serialization.md)를 참조하세요.  
  
### <a name="to-serialize-an-object"></a>개체를 serialize하려면  
  
1. 개체를 만들고 해당 public 필드 및 속성을 설정합니다.  
  
2. 개체의 형식을 사용하여 <xref:System.Xml.Serialization.XmlSerializer>를 생성합니다. 자세한 내용은 <xref:System.Xml.Serialization.XmlSerializer> 클래스 생성자를 참조하십시오.  
  
3. <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> 메서드를 호출하여 개체의 public 속성 및 필드의 파일 표현 또는 XML 스트림을 생성합니다. 다음 예제에서는 파일을 만듭니다.  
  
    ```vb  
    Dim myObject As MySerializableClass = New MySerializableClass()  
    ' Insert code to set properties and fields of the object.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To write to a file, create a StreamWriter object.  
    Dim myWriter As StreamWriter = New StreamWriter("myFileName.xml")  
    mySerializer.Serialize(myWriter, myObject)  
    myWriter.Close()  
    ```  
  
    ```csharp  
    MySerializableClass myObject = new MySerializableClass();  
    // Insert code to set properties and fields of the object.  
    XmlSerializer mySerializer = new
    XmlSerializer(typeof(MySerializableClass));  
    // To write to a file, create a StreamWriter object.  
    StreamWriter myWriter = new StreamWriter("myFileName.xml");  
    mySerializer.Serialize(myWriter, myObject);  
    myWriter.Close();  
    ```  
  
## <a name="see-also"></a>참조

- [XML serialization 소개](introducing-xml-serialization.md)
- [방법: 개체 역직렬화](how-to-deserialize-an-object.md)
