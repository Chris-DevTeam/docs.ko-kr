---
description: '자세한 정보: 데이터 원본에서 데이터 업데이트'
title: 데이터 원본에서 데이터 업데이트
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: a55d6a53f4607908fa279474419803eac3963909
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766571"
---
# <a name="updating-data-in-a-data-source"></a>데이터 원본에서 데이터 업데이트

INSERT, UPDATE 또는 DELETE와 같이 데이터를 수정하는 SQL 문은 행을 반환하지 않습니다. 마찬가지로 대부분의 저장 프로시저도 동작을 수행하기는 하지만 행을 반환하지는 않습니다. 행을 반환하지 않는 명령을 실행하려면 필요한 **Parameters** 를 포함하여 적절한 SQL 명령 및 **Connection** 으로 **Command** 개체를 만듭니다. **Command** 개체의 **ExecuteNonQuery** 메서드를 사용 하 여 명령을 실행 합니다.  
  
 **ExecuteNonQuery** 메서드는 실행된 문 또는 저장 프로시저의 영향을 받는 행의 수를 나타내는 정수를 반환합니다. 여러 문을 실행하는 경우 반환되는 값은 실행된 모든 문에 의해 영향을 받는 레코드의 합계입니다.  
  
## <a name="example"></a>예  

 다음 코드 예제에서는 **ExecuteNonQuery** 를 사용하여 레코드를 데이터베이스에 삽입하기 위한 INSERT 문을 실행합니다.  
  
```vb  
' Assumes connection is a valid SqlConnection.  
connection.Open()  
  
Dim queryString As String = "INSERT INTO Customers " & _  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
Dim recordsAffected As Int32 = command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
string queryString = "INSERT INTO Customers " +  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
Int32 recordsAffected = command.ExecuteNonQuery();  
```  
  
 다음 코드 예제에서는 [카탈로그 작업 수행](performing-catalog-operations.md)에 있는 샘플 코드에서 만든 저장 프로시저를 실행합니다. 저장 프로시저가 행을 반환하지 않으므로 **ExecuteNonQuery** 메서드가 사용되지만 저장 프로시저는 입력 매개 변수를 받고 출력 매개 변수와 반환 값을 반환합니다.  
  
 개체의 경우 <xref:System.Data.OleDb.OleDbCommand> **ReturnValue** 매개 변수를 먼저 **Parameters** 컬렉션에 추가 해야 합니다.  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim command As SqlCommand = _  
   New SqlCommand("InsertCategory" , connection)  
command.CommandType = CommandType.StoredProcedure  
  
Dim parameter As SqlParameter = _  
 command.Parameters.Add("@RowCount", SqlDbType.Int)  
parameter.Direction = ParameterDirection.ReturnValue  
  
parameter = command.Parameters.Add( _  
  "@CategoryName", SqlDbType.NChar, 15)  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int)  
parameter.Direction = ParameterDirection.Output  
  
command.Parameters("@CategoryName").Value = "New Category"  
command.ExecuteNonQuery()  
  
Dim categoryID As Int32 = CInt(command.Parameters("@Identity").Value)  
Dim rowCount As Int32 = CInt(command.Parameters("@RowCount").Value)
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlCommand command = new SqlCommand("InsertCategory" , connection);  
command.CommandType = CommandType.StoredProcedure;  
  
SqlParameter parameter = command.Parameters.Add(  
  "@RowCount", SqlDbType.Int);  
parameter.Direction = ParameterDirection.ReturnValue;  
  
parameter = command.Parameters.Add(  
  "@CategoryName", SqlDbType.NChar, 15);  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int);  
parameter.Direction = ParameterDirection.Output;  
  
command.Parameters["@CategoryName"].Value = "New Category";  
command.ExecuteNonQuery();  
  
Int32 categoryID = (Int32) command.Parameters["@Identity"].Value;  
Int32 rowCount = (Int32) command.Parameters["@RowCount"].Value;  
```  
  
## <a name="see-also"></a>참고 항목

- [명령을 사용 하 여 데이터 수정](using-commands-to-modify-data.md)
- [DataAdapters로 데이터 원본 업데이트](updating-data-sources-with-dataadapters.md)
- [명령 및 매개 변수](commands-and-parameters.md)
- [ADO.NET 개요](ado-net-overview.md)
