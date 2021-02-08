---
description: "자세한 정보: BC32126: ' system.string (Of T) '의 메서드는 ' AddressOf ' 연산자의 피연산자로 사용할 수 없습니다."
title: "'System.Nullable(Of T)'의 메서드는 'AddressOf' 연산자의 피연산자로 사용할 수 없습니다."
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: 5ddf2f11bab3193423a3294a7f96afe68f0e5dce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795796"
---
# <a name="bc32126-methods-of-systemnullableof-t-cannot-be-used-as-operands-of-the-addressof-operator"></a>BC32126: ' System.object (Of T) '의 메서드는 ' AddressOf ' 연산자의 피연산자로 사용할 수 없습니다.

문은 `AddressOf` 구조체의 프로시저를 나타내는 피연산자와 함께 연산자를 사용 합니다 <xref:System.Nullable%601> .

 **오류 ID:** BC32126

## <a name="to-correct-this-error"></a>이 오류를 해결하려면

- 절의 프로시저 이름을 `AddressOf` 의 멤버가 아닌 피연산자로 바꿉니다 <xref:System.Nullable%601> .

- 사용 하려는의 메서드를 래핑하는 클래스를 작성 <xref:System.Nullable%601> 합니다. 다음 예제에서 `NullableWrapper` 클래스는 라는 새 메서드를 정의 `GetValueOrDefault` 합니다. 이 새 메서드는의 멤버가 아니므로 <xref:System.Nullable%601> `nullInstance` nullable 형식의 인스턴스인에 적용 하 여에 대 한 인수를 형성할 수 있습니다 `AddressOf` .

```vb
Module Module1

    Delegate Function Deleg() As Integer

    Sub Main()
        Dim nullInstance As New Nullable(Of Integer)(1)

        Dim del As Deleg

        ' GetValueOrDefault is a method of the Nullable generic
        ' type. It cannot be used as an operand of AddressOf.
        ' del = AddressOf nullInstance.GetValueOrDefault

        ' The following line uses the GetValueOrDefault method
        ' defined in the NullableWrapper class.
        del = AddressOf (New NullableWrapper(
            Of Integer)(nullInstance)).GetValueOrDefault

        Console.WriteLine(del.Invoke())
    End Sub

    Class NullableWrapper(Of T As Structure)
        Private m_Value As Nullable(Of T)

        Sub New(ByVal Value As Nullable(Of T))
            m_Value = Value
        End Sub

        Public Function GetValueOrDefault() As T
            Return m_Value.Value
        End Function
    End Class
End Module
```

## <a name="see-also"></a>참고 항목

- <xref:System.Nullable%601>
- [AddressOf 연산자](../operators/addressof-operator.md)
- [Nullable 값 형식](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Visual Basic의 제네릭 형식](../../programming-guide/language-features/data-types/generic-types.md)
