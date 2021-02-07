---
description: '자세히 알아보기: 하나 이상의 참조 커서를 사용 하 여 데이터 집합 채우기'
title: 하나 이상의 REF CURSOR를 사용하여 데이터 세트 필터링
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 99863e79-5b00-467e-a105-4ffa42de3ff7
ms.openlocfilehash: 6df871a9ab708a4275f15a136f3f99b6a98e1fe1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724156"
---
# <a name="filling-a-dataset-using-one-or-more-ref-cursors"></a>하나 이상의 REF CURSOR를 사용하여 데이터 세트 필터링

이 Microsoft Visual Basic 예제에서는 두 개의 REF CURSOR 매개 변수를 반환하는 PL/SQL 저장 프로시저를 실행하고 반환되는 행으로 <xref:System.Data.DataSet>을 채웁니다.

```vb
Private Sub Button1_Click(ByVal sender As Object, _
  ByVal e As System.EventArgs) Handles Button1.Click

  Dim connString As New String(_
    "Data Source=Oracle9i;User ID=scott;Password=[PLACEHOLDER];")
  Dim ds As New DataSet()
    Using conn As New OracleConnection(connString)
    Dim cmd As New OracleCommand()

    cmd.Connection = conn
    cmd.CommandText = "CURSPKG.OPEN_TWO_CURSORS"
    cmd.CommandType = CommandType.StoredProcedure
    cmd.Parameters.Add(New OracleParameter( _
      "EMPCURSOR", OracleType.Cursor)).Direction = _
      ParameterDirection.Output
    cmd.Parameters.Add(New OracleParameter( _
      "DEPTCURSOR", OracleType.Cursor)).Direction = _
       ParameterDirection.Output

    Dim da As New OracleDataAdapter(cmd)
    da.TableMappings.Add("Table", "Emp")
    da.TableMappings.Add("Table1", "Dept")
    da.Fill(ds)

    ds.Relations.Add("EmpDept", ds.Tables("Dept").Columns("Deptno"), _
      ds.Tables("Emp").Columns("Deptno"), False)

    DataGrid1.DataSource = ds.Tables("Dept")
  End Using
```

## <a name="see-also"></a>참고 항목

- [Oracle REF CURSOR](oracle-ref-cursors.md)
- [ADO.NET 개요](ado-net-overview.md)
