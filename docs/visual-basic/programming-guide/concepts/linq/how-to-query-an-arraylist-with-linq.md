---
description: '자세한 정보: 방법: LINQ를 사용 하 여 ArrayList 쿼리 (Visual Basic)'
title: '방법: LINQ를 사용하여 ArrayList 쿼리'
ms.date: 07/20/2015
ms.assetid: 176358a9-d765-4b57-9557-7feb4428138d
ms.openlocfilehash: df7c6e1cee6d8e37074ce209f3bea97a402d8dbe
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428521"
---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a>방법: LINQ를 사용 하 여 ArrayList 쿼리 (Visual Basic)

LINQ를 사용하여 <xref:System.Collections.ArrayList> 등의 제네릭이 아닌 <xref:System.Collections.IEnumerable> 컬렉션을 쿼리하는 경우 컬렉션에 있는 개체의 특정 형식을 반영하도록 범위 변수의 형식을 명시적으로 선언해야 합니다. 예를 들어 개체의가 있는 <xref:System.Collections.ArrayList> 경우 `Student` [from 절](../../../language-reference/queries/from-clause.md) 은 다음과 같습니다.

```vb
Dim query = From student As Student In arrList
'...
```

범위 변수의 형식을 지정하여 <xref:System.Collections.ArrayList>의 각 항목을 `Student`로 캐스팅합니다.

명시적 형식 범위 변수를 쿼리 식에 사용하는 것은 <xref:System.Linq.Enumerable.Cast%2A> 메서드 호출과 같습니다. 지정된 캐스트를 수행할 수 없는 경우 <xref:System.Linq.Enumerable.Cast%2A>에서 예외를 throw합니다. <xref:System.Linq.Enumerable.Cast%2A> 및 <xref:System.Linq.Enumerable.OfType%2A>은 제네릭이 아닌 <xref:System.Collections.IEnumerable> 형식에서 작동하는 두 가지 표준 쿼리 연산자 메서드입니다. Visual Basic에서 <xref:System.Linq.Enumerable.Cast%2A> 데이터 소스에 대해 메서드를 명시적으로 호출 하 여 특정 범위 변수 형식을 확인 해야 합니다. 자세한 내용은 [쿼리 작업의 형식 관계 (Visual Basic)](type-relationships-in-query-operations.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 <xref:System.Collections.ArrayList>에 대한 단순 쿼리를 보여 줍니다. 이 예제에서는 코드가 <xref:System.Collections.ArrayList.Add%2A> 메서드를 호출할 때 개체 이니셜라이저를 사용하지만 요구 사항은 아닙니다.

```vb
Imports System.Collections
Imports System.Linq

Module Module1

    Public Class Student
        Public Property FirstName As String
        Public Property LastName As String
        Public Property Scores As Integer()
    End Class

    Sub Main()

        Dim student1 As New Student With {.FirstName = "Svetlana",
                                     .LastName = "Omelchenko",
                                     .Scores = New Integer() {98, 92, 81, 60}}
        Dim student2 As New Student With {.FirstName = "Claire",
                                    .LastName = "O'Donnell",
                                    .Scores = New Integer() {75, 84, 91, 39}}
        Dim student3 As New Student With {.FirstName = "Cesar",
                                    .LastName = "Garcia",
                                    .Scores = New Integer() {97, 89, 85, 82}}
        Dim student4 As New Student With {.FirstName = "Sven",
                                    .LastName = "Mortensen",
                                    .Scores = New Integer() {88, 94, 65, 91}}

        Dim arrList As New ArrayList()
        arrList.Add(student1)
        arrList.Add(student2)
        arrList.Add(student3)
        arrList.Add(student4)

        ' Use an explicit type for non-generic collections
        Dim query = From student As Student In arrList
                    Where student.Scores(0) > 95
                    Select student

        For Each student As Student In query
            Console.WriteLine(student.LastName & ": " & student.Scores(0))
        Next
        ' Keep the console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub

End Module
' Output:
'   Omelchenko: 98
'   Garcia: 97
```

## <a name="see-also"></a>참조

- [LINQ to Objects(Visual Basic)](linq-to-objects.md)
