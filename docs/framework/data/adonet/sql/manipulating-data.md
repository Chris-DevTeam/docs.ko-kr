---
description: '자세히 알아보기: 데이터 조작'
title: 데이터 조작
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51096a2e-8b38-4c4d-a523-799bfdb7ec69
ms.openlocfilehash: dba948fe923e709f6564e6c64fd9adce7f3f15f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767689"
---
# <a name="manipulating-data"></a>데이터 조작

MARS(Multiple Active Result Sets)가 도입되기 전에는 개발자가 여러 연결 또는 서버 쪽 커서를 사용하여 특정 시나리오를 해결해야 했습니다. 또한 트랜잭션 상황에서 다중 연결을 사용하는 경우 **sp_getbindtoken** 및 **sp_bindsession** 으로 바인딩된 연결을 사용해야 했습니다. 다음 시나리오에서는 여러 연결 대신 MARS 사용 연결을 사용하는 방법을 보여 줍니다.  
  
## <a name="using-multiple-commands-with-mars"></a>MARS로 여러 명령 사용  

 다음 콘솔 애플리케이션에서는 MARS가 설정된 상태에서 두 개의 <xref:System.Data.SqlClient.SqlCommand> 개체와 단일 <xref:System.Data.SqlClient.SqlConnection> 개체와 함께 두 개의 <xref:System.Data.SqlClient.SqlDataReader> 개체를 사용하는 방법을 보여 줍니다.  
  
### <a name="example"></a>예제  

 이 예제에서는 **AdventureWorks** 데이터베이스에 대한 단일 연결을 엽니다. <xref:System.Data.SqlClient.SqlCommand> 개체를 사용하여 <xref:System.Data.SqlClient.SqlDataReader>를 만듭니다. 판독기를 사용하면 첫 번째 <xref:System.Data.SqlClient.SqlDataReader>의 데이터를 두 번째 판독기의 WHERE 절에 대한 입력으로 사용하여 두 번째 <xref:System.Data.SqlClient.SqlDataReader>가 열립니다.  
  
> [!NOTE]
> 다음 예제에서는 SQL Server에 포함된 샘플 **AdventureWorks** 데이터베이스를 사용합니다. 샘플 코드에 제공된 연결 문자열은 데이터베이스가 로컬 컴퓨터에 설치되어 있고 사용 가능한 것으로 가정합니다. 사용자 환경에 필요한 경우 연결 문자열을 수정합니다.  
  
```vb  
Option Strict On  
Option Explicit On  
  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Module Module1  
  Sub Main()  
    ' By default, MARS is disabled when connecting  
    ' to a MARS-enabled host.  
    ' It must be enabled in the connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    Dim vendorID As Integer  
  
    Dim vendorCmd As SqlCommand  
    Dim productCmd As SqlCommand  
    Dim productReader As SqlDataReader  
  
    Dim vendorSQL As String = & _
      "SELECT VendorId, Name FROM Purchasing.Vendor"  
    Dim productSQL As String = _  
        "SELECT Production.Product.Name FROM Production.Product " & _  
        "INNER JOIN Purchasing.ProductVendor " & _  
        "ON Production.Product.ProductID = " & _  
        "Purchasing.ProductVendor.ProductID " & _  
        "WHERE Purchasing.ProductVendor.VendorID = @VendorId"  
  
    Using awConnection As New SqlConnection(connectionString)  
      vendorCmd = New SqlCommand(vendorSQL, awConnection)  
      productCmd = New SqlCommand(productSQL, awConnection)  
      productCmd.Parameters.Add("@VendorId", SqlDbType.Int)  
  
      awConnection.Open()  
      Using vendorReader As SqlDataReader = vendorCmd.ExecuteReader()  
        While vendorReader.Read()  
          Console.WriteLine(vendorReader("Name"))  
  
          vendorID = CInt(vendorReader("VendorId"))  
  
          productCmd.Parameters("@VendorId").Value = vendorID  
  
          ' The following line of code requires  
          ' a MARS-enabled connection.  
          productReader = productCmd.ExecuteReader()  
          Using productReader  
            While productReader.Read()  
              Console.WriteLine("  " & CStr(productReader("Name")))  
            End While  
          End Using  
        End While  
      End Using  
    End Using  
  
    Console.WriteLine("Press any key to continue")  
    Console.ReadLine()  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=(local);Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks; MultipleActiveResultSets=True"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Class1  
{  
static void Main()  
{  
  // By default, MARS is disabled when connecting  
  // to a MARS-enabled host.  
  // It must be enabled in the connection string.  
  string connectionString = GetConnectionString();  
  
  int vendorID;  
  SqlDataReader productReader = null;  
  string vendorSQL =
    "SELECT VendorId, Name FROM Purchasing.Vendor";  
  string productSQL =
    "SELECT Production.Product.Name FROM Production.Product " +  
    "INNER JOIN Purchasing.ProductVendor " +  
    "ON Production.Product.ProductID = " +
    "Purchasing.ProductVendor.ProductID " +  
    "WHERE Purchasing.ProductVendor.VendorID = @VendorId";  
  
  using (SqlConnection awConnection =
    new SqlConnection(connectionString))  
  {  
    SqlCommand vendorCmd = new SqlCommand(vendorSQL, awConnection);  
    SqlCommand productCmd =
      new SqlCommand(productSQL, awConnection);  
  
    productCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
    awConnection.Open();  
    using (SqlDataReader vendorReader = vendorCmd.ExecuteReader())  
    {  
      while (vendorReader.Read())  
      {  
        Console.WriteLine(vendorReader["Name"]);  
  
        vendorID = (int)vendorReader["VendorId"];  
  
        productCmd.Parameters["@VendorId"].Value = vendorID;  
        // The following line of code requires  
        // a MARS-enabled connection.  
        productReader = productCmd.ExecuteReader();  
        using (productReader)  
        {  
          while (productReader.Read())  
          {  
            Console.WriteLine("  " +  
              productReader["Name"].ToString());  
          }  
        }  
      }  
  }  
      Console.WriteLine("Press any key to continue");  
      Console.ReadLine();  
    }  
  }  
  private static string GetConnectionString()  
  {  
    // To avoid storing the connection string in your code,  
    // you can retrieve it from a configuration file.  
    return "Data Source=(local);Integrated Security=SSPI;" +
      "Initial Catalog=AdventureWorks;MultipleActiveResultSets=True";  
  }  
}  
```  
  
## <a name="reading-and-updating-data-with-mars"></a>MARS로 데이터 읽기 및 업데이트  

 MARS를 사용하면 둘 이상의 보류 중인 작업을 포함하는 읽기 작업 및 DML(데이터 조작 언어) 작업 모두에 하나의 연결을 사용할 수 있습니다. 이 기능을 사용하면 애플리케이션에서 연결 사용 오류를 처리할 필요가 없습니다. 또한 MARS는 일반적으로 더 많은 리소스를 사용하는 서버 쪽 커서의 사용자를 대체할 수 있습니다. 마지막으로 여러 작업이 단일 연결에서 실행될 수 있으므로 동일한 트랜잭션 컨텍스트를 공유하여 **sp_getbindtoken** 및 **sp_bindsession** 시스템 저장 프로시저를 사용할 필요가 없습니다.  
  
### <a name="example"></a>예제  

 다음 콘솔 애플리케이션에서는 MARS가 설정된 상태에서 세 개의 <xref:System.Data.SqlClient.SqlCommand> 개체와 단일 <xref:System.Data.SqlClient.SqlConnection> 개체와 함께 두 개의 <xref:System.Data.SqlClient.SqlDataReader> 개체를 사용하는 방법을 보여 줍니다. 첫 번째 명령 개체는 신용 등급이 5인 공급업체 목록을 검색합니다. 두 번째 명령 개체는 <xref:System.Data.SqlClient.SqlDataReader>에서 제공한 공급업체 ID를 사용하여 특정 공급업체의 모든 제품을 두 번째 <xref:System.Data.SqlClient.SqlDataReader>에 로드합니다. 두 번째 <xref:System.Data.SqlClient.SqlDataReader>는 각 제품 레코드를 방문합니다. 또한 새로운 **OnOrderQty** 를 확인하기 위한 계산을 수행합니다. 그런 다음 세 번째 명령 개체를 사용하여 **ProductVendor** 테이블을 새 값으로 업데이트합니다. 이 전체 프로세스는 단일 트랜잭션 내에서 발생하며 마지막에는 롤백됩니다.  
  
> [!NOTE]
> 다음 예제에서는 SQL Server에 포함된 샘플 **AdventureWorks** 데이터베이스를 사용합니다. 샘플 코드에 제공된 연결 문자열은 데이터베이스가 로컬 컴퓨터에 설치되어 있고 사용 가능한 것으로 가정합니다. 사용자 환경에 필요한 경우 연결 문자열을 수정합니다.  
  
```vb  
Option Strict On  
Option Explicit On  
  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    ' By default, MARS is disabled when connecting  
    ' to a MARS-enabled host.  
    ' It must be enabled in the connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    Dim updateTx As SqlTransaction  
    Dim vendorCmd As SqlCommand  
    Dim prodVendCmd As SqlCommand  
    Dim updateCmd As SqlCommand  
  
    Dim prodVendReader As SqlDataReader  
  
    Dim vendorID As Integer  
    Dim productID As Integer  
    Dim minOrderQty As Integer  
    Dim maxOrderQty As Integer  
    Dim onOrderQty As Integer  
    Dim recordsUpdated As Integer  
    Dim totalRecordsUpdated As Integer  
  
    Dim vendorSQL As String = _  
        "SELECT VendorID, Name FROM Purchasing.Vendor " & _  
        "WHERE CreditRating = 5"  
    Dim prodVendSQL As String = _  
        "SELECT ProductID, MaxOrderQty, MinOrderQty, OnOrderQty " & _  
        "FROM Purchasing.ProductVendor " & _  
        "WHERE VendorID = @VendorID"  
    Dim updateSQL As String = _  
        "UPDATE Purchasing.ProductVendor " & _
        "SET OnOrderQty = @OrderQty " & _  
        "WHERE ProductID = @ProductID AND VendorID = @VendorID"  
  
    Using awConnection As New SqlConnection(connectionString)  
      awConnection.Open()  
      updateTx = awConnection.BeginTransaction()  
  
      vendorCmd = New SqlCommand(vendorSQL, awConnection)  
      vendorCmd.Transaction = updateTx  
  
      prodVendCmd = New SqlCommand(prodVendSQL, awConnection)  
      prodVendCmd.Transaction = updateTx  
      prodVendCmd.Parameters.Add("@VendorId", SqlDbType.Int)  
  
      updateCmd = New SqlCommand(updateSQL, awConnection)  
      updateCmd.Transaction = updateTx  
      updateCmd.Parameters.Add("@OrderQty", SqlDbType.Int)  
      updateCmd.Parameters.Add("@ProductID", SqlDbType.Int)  
      updateCmd.Parameters.Add("@VendorID", SqlDbType.Int)  
  
      Using vendorReader As SqlDataReader = vendorCmd.ExecuteReader()  
        While vendorReader.Read()  
          Console.WriteLine(vendorReader("Name"))  
  
          vendorID = CInt(vendorReader("VendorID"))  
          prodVendCmd.Parameters("@VendorID").Value = vendorID  
          prodVendReader = prodVendCmd.ExecuteReader()  
  
          Using prodVendReader  
            While (prodVendReader.Read)  
              productID = CInt(prodVendReader("ProductID"))  
  
              If IsDBNull(prodVendReader("OnOrderQty")) Then  
                minOrderQty = CInt(prodVendReader("MinOrderQty"))  
                onOrderQty = minOrderQty  
              Else  
                maxOrderQty = CInt(prodVendReader("MaxOrderQty"))  
                onOrderQty = CInt(maxOrderQty / 2)  
              End If  
  
              updateCmd.Parameters("@OrderQty").Value = onOrderQty  
              updateCmd.Parameters("@ProductID").Value = productID  
              updateCmd.Parameters("@VendorID").Value = vendorID  
  
              recordsUpdated = updateCmd.ExecuteNonQuery()  
              totalRecordsUpdated += recordsUpdated  
            End While  
          End Using  
        End While  
      End Using  
  
      Console.WriteLine("Total Records Updated: " & _
        CStr(totalRecordsUpdated))  
      updateTx.Rollback()  
      Console.WriteLine("Transaction Rolled Back")  
    End Using  
  
    Console.WriteLine("Press any key to continue")  
    Console.ReadLine()  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=(local);Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks;MultipleActiveResultSets=True"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
static void Main()  
{  
  // By default, MARS is disabled when connecting  
  // to a MARS-enabled host.  
  // It must be enabled in the connection string.  
  string connectionString = GetConnectionString();  
  
  SqlTransaction updateTx = null;  
  SqlCommand vendorCmd = null;  
  SqlCommand prodVendCmd = null;  
  SqlCommand updateCmd = null;  
  
  SqlDataReader prodVendReader = null;  
  
  int vendorID = 0;  
  int productID = 0;  
  int minOrderQty = 0;  
  int maxOrderQty = 0;  
  int onOrderQty = 0;  
  int recordsUpdated = 0;  
  int totalRecordsUpdated = 0;  
  
  string vendorSQL =  
      "SELECT VendorID, Name FROM Purchasing.Vendor " +
      "WHERE CreditRating = 5";  
  string prodVendSQL =  
      "SELECT ProductID, MaxOrderQty, MinOrderQty, OnOrderQty " +  
      "FROM Purchasing.ProductVendor " +
      "WHERE VendorID = @VendorID";  
  string updateSQL =  
      "UPDATE Purchasing.ProductVendor " +
      "SET OnOrderQty = @OrderQty " +  
      "WHERE ProductID = @ProductID AND VendorID = @VendorID";  
  
  using (SqlConnection awConnection =
    new SqlConnection(connectionString))  
  {  
    awConnection.Open();  
    updateTx = awConnection.BeginTransaction();  
  
    vendorCmd = new SqlCommand(vendorSQL, awConnection);  
    vendorCmd.Transaction = updateTx;  
  
    prodVendCmd = new SqlCommand(prodVendSQL, awConnection);  
    prodVendCmd.Transaction = updateTx;  
    prodVendCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
    updateCmd = new SqlCommand(updateSQL, awConnection);  
    updateCmd.Transaction = updateTx;  
    updateCmd.Parameters.Add("@OrderQty", SqlDbType.Int);  
    updateCmd.Parameters.Add("@ProductID", SqlDbType.Int);  
    updateCmd.Parameters.Add("@VendorID", SqlDbType.Int);  
  
    using (SqlDataReader vendorReader = vendorCmd.ExecuteReader())  
    {  
      while (vendorReader.Read())  
      {  
        Console.WriteLine(vendorReader["Name"]);  
  
        vendorID = (int) vendorReader["VendorID"];  
        prodVendCmd.Parameters["@VendorID"].Value = vendorID;  
        prodVendReader = prodVendCmd.ExecuteReader();  
  
        using (prodVendReader)  
        {  
          while (prodVendReader.Read())  
          {  
            productID = (int) prodVendReader["ProductID"];  
  
            if (prodVendReader["OnOrderQty"] == DBNull.Value)  
            {  
              minOrderQty = (int) prodVendReader["MinOrderQty"];  
              onOrderQty = minOrderQty;  
            }  
            else  
            {  
              maxOrderQty = (int) prodVendReader["MaxOrderQty"];  
              onOrderQty = (int)(maxOrderQty / 2);  
            }  
  
            updateCmd.Parameters["@OrderQty"].Value = onOrderQty;  
            updateCmd.Parameters["@ProductID"].Value = productID;  
            updateCmd.Parameters["@VendorID"].Value = vendorID;  
  
            recordsUpdated = updateCmd.ExecuteNonQuery();  
            totalRecordsUpdated += recordsUpdated;  
          }  
        }  
      }  
    }  
    Console.WriteLine("Total Records Updated: " +
      totalRecordsUpdated.ToString());  
    updateTx.Rollback();  
    Console.WriteLine("Transaction Rolled Back");  
  }  
  
  Console.WriteLine("Press any key to continue");  
  Console.ReadLine();  
}  
private static string GetConnectionString()  
{  
  // To avoid storing the connection string in your code,  
  // you can retrieve it from a configuration file.  
  return "Data Source=(local);Integrated Security=SSPI;" +
    "Initial Catalog=AdventureWorks;" +
    "MultipleActiveResultSets=True";  
  }  
}  
```  
  
## <a name="see-also"></a>참조

- [MARS(Multiple Active Result Sets)](multiple-active-result-sets-mars.md)
- [ADO.NET 개요](../ado-net-overview.md)
