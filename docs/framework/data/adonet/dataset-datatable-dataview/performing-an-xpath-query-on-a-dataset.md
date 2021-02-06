---
description: '자세한 정보: 데이터 집합에 대 한 XPath 쿼리 수행'
title: 데이터 세트에서 XPath 쿼리 수행
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: 9febcc545f86f048b2d693f8aa6558a1b7883a60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651719"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a>데이터 세트에서 XPath 쿼리 수행

동기화 된와 간의 관계 <xref:System.Data.DataSet> 를 <xref:System.Xml.XmlDataDocument> 사용 하면 XPATH (Xml Path Language) 쿼리와 같은 xml 서비스를 사용 하 여 **XmlDataDocument** 에 액세스 하 고 **데이터 집합** 에 직접 액세스 하는 것 보다 더 편리 하 게 특정 기능을 수행할 수 있습니다. 예를 들어의 **Select** 메서드를 사용 하 여 <xref:System.Data.DataTable> **데이터 집합** 의 다른 테이블에 대 한 관계를 탐색 하는 대신, **데이터 집합과** 동기화 된 **XmlDataDocument** 에서 XPath 쿼리를 수행 하 여 형식의 XML 요소 목록을 가져올 수 있습니다 <xref:System.Xml.XmlNodeList> . 그러면 **XmlNodeList** 의 노드를 <xref:System.Xml.XmlElement> **XmlDataDocument** 의 **GetRowFromElement** 메서드에 전달 하 여 <xref:System.Data.DataRow> 동기화 된 **데이터 집합** 에 있는 테이블의 행에 대 한 일치 하는 참조를 반환할 수 있습니다.  
  
 예를 들어, 다음 코드 샘플에서는 "최하위" XPath 쿼리를 수행합니다. **데이터 집합** 은 **Customers**, **Orders** 및 **OrderDetails** 의 세 테이블로 채워집니다. 이 샘플에서 부모-자식 관계는 먼저 **Customers** 테이블과 **orders** 테이블 간에, 그리고 **orders** 테이블과 **OrderDetails** 테이블 사이에 만들어집니다. 그런 다음 XPath 쿼리가 수행 되어 손자 **OrderDetails** 노드에 값이 43 인 **ProductID** 노드가 있는 **Customers** 노드의 **XmlNodeList** 을 반환 합니다. 기본적으로이 예제에서는 XPath 쿼리를 사용 하 여 **ProductID** 가 43 인 제품을 주문한 고객을 확인 합니다.  
  
```vb  
' Assumes that connection is a valid SqlConnection.  
connection.Open()  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Customers", connection)  
customerAdapter.Fill(dataSet, "Customers")  
  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Orders", connection)  
orderAdapter.Fill(dataSet, "Orders")  
  
Dim detailAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM [Order Details]", connection)  
detailAdapter.Fill(dataSet, "OrderDetails")  
  
connection.Close()  
  
dataSet.Relations.Add("CustOrders", _  
dataSet.Tables("Customers").Columns("CustomerID"), _  
dataSet.Tables("Orders").Columns("CustomerID")).Nested = true  
  
dataSet.Relations.Add("OrderDetail", _  
  dataSet.Tables("Orders").Columns("OrderID"), _  
dataSet.Tables("OrderDetails").Columns("OrderID"), false).Nested = true  
  
Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)
  
Dim nodeList As XmlNodeList = xmlDoc.DocumentElement.SelectNodes( _  
  "descendant::Customers[*/OrderDetails/ProductID=43]")  
  
Dim dataRow As DataRow  
Dim xmlNode As XmlNode  
  
For Each xmlNode In nodeList  
  dataRow = xmlDoc.GetRowFromElement(CType(xmlNode, XmlElement))  
  
  If Not dataRow Is Nothing then Console.WriteLine(xmlRow(0).ToString())  
Next  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection.  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT * FROM Customers", connection);  
customerAdapter.Fill(dataSet, "Customers");  
  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT * FROM Orders", connection);  
orderAdapter.Fill(dataSet, "Orders");  
  
SqlDataAdapter detailAdapter = new SqlDataAdapter(  
  "SELECT * FROM [Order Details]", connection);  
detailAdapter.Fill(dataSet, "OrderDetails");  
  
connection.Close();  
  
dataSet.Relations.Add("CustOrders",  
  dataSet.Tables["Customers"].Columns["CustomerID"],  
 dataSet.Tables["Orders"].Columns["CustomerID"]).Nested = true;  
  
dataSet.Relations.Add("OrderDetail",  
  dataSet.Tables["Orders"].Columns["OrderID"],  
  dataSet.Tables["OrderDetails"].Columns["OrderID"],
  false).Nested = true;  
  
XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);
  
XmlNodeList nodeList = xmlDoc.DocumentElement.SelectNodes(  
  "descendant::Customers[*/OrderDetails/ProductID=43]");  
  
DataRow dataRow;  
foreach (XmlNode xmlNode in nodeList)  
{  
  dataRow = xmlDoc.GetRowFromElement((XmlElement)xmlNode);  
  if (dataRow != null)  
    Console.WriteLine(dataRow[0]);  
}  
```  
  
## <a name="see-also"></a>참조

- [데이터 세트 및 XmlDataDocument 동기화](dataset-and-xmldatadocument-synchronization.md)
- [ADO.NET 개요](../ado-net-overview.md)
