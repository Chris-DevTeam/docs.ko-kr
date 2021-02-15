---
description: '자세한 정보: 방법: 문자열의 문자 쿼리 (LINQ) (Visual Basic)'
title: '방법: 문자열에서 문자 쿼리(LINQ)'
ms.date: 07/20/2015
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
ms.openlocfilehash: bd8fabc06e88c83ae4e89079378ad67efb13c446
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425752"
---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a>방법: 문자열의 문자 쿼리 (LINQ) (Visual Basic)

<xref:System.String> 클래스는 제네릭 <xref:System.Collections.Generic.IEnumerable%601> 인터페이스를 구현하기 때문에 모든 문자열을 문자 시퀀스로 쿼리할 수 있습니다. 그러나 LINQ는 일반적으로 이 용도로 사용되지 않습니다. 복잡한 패턴 일치 작업의 경우 <xref:System.Text.RegularExpressions.Regex> 클래스를 사용합니다.

## <a name="example"></a>예제

다음 예제에서는 문자열을 쿼리하여 문자열에 포함된 숫자 자릿수를 확인합니다. 쿼리가 처음 실행된 후 "다시 사용"됩니다. 이 작업은 쿼리 자체가 실제 결과를 저장하지 않기 때문에 가능합니다.

```vb
Class QueryAString

    Shared Sub Main()

        ' A string is an IEnumerable data source.
        Dim aString As String = "ABCDE99F-J74-12-89A"

        ' Select only those characters that are numbers
        Dim stringQuery = From ch In aString
                          Where Char.IsDigit(ch)
                          Select ch
        ' Execute the query
        For Each c As Char In stringQuery
            Console.Write(c & " ")
        Next

        ' Call the Count method on the existing query.
        Dim count As Integer = stringQuery.Count()
        Console.WriteLine(System.Environment.NewLine & "Count = " & count)

        ' Select all characters before the first '-'
        Dim stringQuery2 = aString.TakeWhile(Function(c) c <> "-")

        ' Execute the second query
        For Each ch In stringQuery2
            Console.Write(ch)
        Next

        Console.WriteLine(System.Environment.NewLine & "Press any key to exit")
        Console.ReadKey()
    End Sub
End Class
' Output:
' 9 9 7 4 1 2 8 9
' Count = 8
' ABCDE99F
```

## <a name="compile-the-code"></a>코드 컴파일

System.xml `Imports` 네임 스페이스에 대 한 문을 사용 하 여 Visual Basic 콘솔 응용 프로그램 프로젝트를 만듭니다.

## <a name="see-also"></a>추가 정보

- [LINQ 및 문자열(Visual Basic)](linq-and-strings.md)
- [정규식을 사용 하 여 LINQ 쿼리를 결합 하는 방법 (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md)
