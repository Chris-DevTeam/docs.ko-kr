---
description: '자세히 알아보기: XML에서 데이터 집합 스키마 정보 로드'
title: XML에서 데이터 세트 스키마 정보 로드
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: dd3a327270d6f8e3086d7206dd6f44290415c55e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652109"
---
# <a name="loading-dataset-schema-information-from-xml"></a>XML에서 데이터 세트 스키마 정보 로드

의 스키마 <xref:System.Data.DataSet> (테이블, 열, 관계 및 제약 조건)는 프로그래밍 방식으로 정의 하거나,의 **Fill** 또는 **FillSchema** 메서드에 의해 만들어지거나 <xref:System.Data.Common.DataAdapter> , XML 문서에서 로드 될 수 있습니다. XML 문서에서 **데이터 집합** 스키마 정보를 로드 하기 위해 **데이터 집합** 의 **readxmlschema** 또는 **InferXmlSchema** 메서드를 사용할 수 있습니다. **Readxmlschema** 를 사용 하면 XSD (xml 스키마 정의 언어) 스키마가 포함 된 문서나 인라인 xml 스키마를 사용 하는 xml 문서에서 **데이터 집합** 스키마 정보를 로드 하거나 유추할 수 있습니다. **InferXmlSchema** 를 사용 하면 지정한 특정 xml 네임 스페이스를 무시 하 고 xml 문서에서 스키마를 유추할 수 있습니다.  
  
> [!NOTE]
> 웹 서비스 또는 XML serialization을 사용 하 여 XSD 구문을 사용 하 여 메모리 내에 생성 된 **데이터 집합** 을 전송 하는 경우 (예: 중첩 된 관계) **데이터 집합** 의 테이블 순서가 유지 되지 않을 수 있습니다. 따라서이 경우에는 **데이터 집합** 의 수신자가 테이블 순서에 종속 되지 않아야 합니다. 그러나 전송 중인 **데이터 집합** 의 스키마를 메모리 내에서 만들지 않고 XSD 파일에서 읽는 경우에는 항상 테이블 순서가 유지 됩니다.  
  
## <a name="readxmlschema"></a>ReadXmlSchema  

 데이터를 로드 하지 않고 XML 문서에서 데이터 **집합** 의 스키마를 로드 하려면 데이터 **집합** 의 **readxmlschema** 메서드를 사용할 수 있습니다. **Readxmlschema** 는 XSD (XML 스키마 정의 언어) 스키마를 사용 하 여 정의 된 **데이터 집합** 스키마를 만듭니다.  
  
 **Readxmlschema** 메서드는 로드할 XML 문서가 포함 된 파일 이름, 스트림 또는 **XmlReader** 의 단일 인수를 사용 합니다. XML 문서에는 스키마만 있을 수도 있고 데이터가 포함된 XML 요소를 가진 스키마 인라인이 있을 수도 있습니다. 인라인 스키마를 XML 스키마로 작성 하는 방법에 대 한 자세한 내용은 [Xml 스키마에서 데이터 집합 관계형 구조 파생 (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)을 참조 하세요.  
  
 **Readxmlschema** 에 전달 된 xml 문서에 인라인 스키마 정보가 포함 되어 있지 않은 경우 **READXMLSCHEMA** 는 xml 문서의 요소에서 스키마를 유추 합니다. **데이터 집합** 에 이미 스키마가 있으면 새 테이블을 추가 하 여 현재 스키마를 확장 하는 것입니다 (아직 없는 경우). 새 열은 기존 테이블에 추가되지 않습니다. 추가 되는 열이 **DataSet** 에 이미 있지만 XML에 있는 열과 호환 되지 않는 형식을 포함 하는 경우 예외가 throw 됩니다. **Readxmlschema** 에서 xml 문서의 스키마를 유추 하는 방법에 대 한 자세한 내용은 [Xml에서 데이터 집합 관계형 구조 유추](inferring-dataset-relational-structure-from-xml.md)를 참조 하세요.  
  
 **Readxmlschema** 는 **데이터 집합** 의 스키마만 로드 하거나 유추 하지만 **데이터 집합** 의 **ReadXml** 메서드는 XML 문서에 포함 된 스키마와 데이터를 모두 로드 하거나 유추 합니다. 자세한 내용은 [XML에서 데이터 집합 로드](loading-a-dataset-from-xml.md)를 참조 하세요.  
  
 다음 코드 예제에서는 XML 문서 또는 스트림에서 **데이터 집합** 스키마를 로드 하는 방법을 보여 줍니다. 첫 번째 예에서는 **Readxmlschema** 메서드에 전달 되는 XML 스키마 파일 이름을 보여 줍니다. 두 번째 예제에서는 **system.web** 을 보여 줍니다.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As New System.IO.StreamReader("schema.xsd")
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema(xmlStream)  
xmlStream.Close()  
```  
  
```csharp  
System.IO.StreamReader xmlStream = new System.IO.StreamReader("schema.xsd");  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema(xmlStream);  
xmlStream.Close();  
```  
  
## <a name="inferxmlschema"></a>InferXmlSchema  

 데이터 **집합** 의 **InferXmlSchema** 메서드를 사용 하 여 XML 문서에서 스키마를 유추 하도록 **데이터 집합** 에 지시할 수도 있습니다. **InferXmlSchema** 는 **InferSchema** 의 **XmlReadMode** (데이터 로드 및 스키마 유추)를 사용 하 여 두 **ReadXml** 를 모두 수행 하는 것과 동일 하 게 작동 하며 읽을 문서에 인라인 스키마가 없는 경우에는 **readxmlschema** 를 사용 합니다. 그러나 **InferXmlSchema** 는 스키마를 유추할 때 무시할 특정 XML 네임 스페이스를 지정할 수 있는 추가 기능을 제공 합니다. **InferXmlSchema** 은 파일 이름, 스트림 또는 **XmlReader** 로 지정 된 XML 문서의 위치를 사용 하 여 두 개의 필수 인수를 사용 합니다. 작업에서 무시할 XML 네임 스페이스의 문자열 배열입니다.  
  
 예를 들어, 다음과 같은 XML을 가정해 봅시다.  
  
```xml  
<NewDataSet xmlns:od="urn:schemas-microsoft-com:officedata">  
<Categories>  
  <CategoryID od:adotype="3">1</CategoryID>
  <CategoryName od:maxLength="15" od:adotype="130">Beverages</CategoryName>
  <Description od:adotype="203">Soft drinks and teas</Description>
</Categories>  
<Products>  
  <ProductID od:adotype="20">1</ProductID>
  <ReorderLevel od:adotype="3">10</ReorderLevel>
  <Discontinued od:adotype="11">0</Discontinued>
</Products>  
</NewDataSet>  
```  
  
 이전 XML 문서의 요소에 대해 지정 된 특성으로 인해 **Readxmlschema** 메서드와 **XmlReadMode** of **InferSchema** 를 사용 하는 **ReadXml** 메서드는 모두 문서의 모든 요소에 대 한 **테이블을 만듭니다**. **Categories**, **CategoryID**, 범주, **설명**, **제품**, **ProductID**, **ReorderLevel** 및 **단종**. 자세한 내용은 [XML에서 데이터 집합 관계형 구조 유추](inferring-dataset-relational-structure-from-xml.md)를 참조 하세요. 그러나 더 적절 한 구조는 **범주** 및 **Products** 테이블만 만든 다음, categories 테이블에 **CategoryID**, **Categories** 및 **Description** 열을 만들고 **Products** 테이블에 **ProductID**, **ReorderLevel** 및 **단종** 열을 만드는 것입니다. 유추 된 스키마가 XML 요소에 지정 된 특성을 무시 하도록 하려면 다음 예제와 같이 **InferXmlSchema** 메서드를 사용 하 고 삭제할 **데이터** 의 XML 네임 스페이스를 지정 합니다.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a>참조

- [데이터 세트에서 XML 사용](using-xml-in-a-dataset.md)
- [XML 스키마에서 데이터 세트 관계형 구조 파생(XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [XML에서 데이터 세트 관계형 구조 유추](inferring-dataset-relational-structure-from-xml.md)
- [XML에서 데이터 세트 로드](loading-a-dataset-from-xml.md)
- [DataSets, DataTables 및 DataViews](index.md)
- [ADO.NET 개요](../ado-net-overview.md)
