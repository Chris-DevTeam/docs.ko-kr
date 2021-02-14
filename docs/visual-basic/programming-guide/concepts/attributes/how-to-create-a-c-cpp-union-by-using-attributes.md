---
description: '자세히 알아보기: 방법: 특성을 사용 하 여 C/c + + 공용 구조체 만들기 (Visual Basic)'
title: '방법: 특성을 사용 하 여 C-C + + 공용 구조체 만들기'
ms.date: 07/20/2015
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
ms.openlocfilehash: 10717ec97efe866f4c3993cc26789f29d97b148a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437750"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a>방법: 특성을 사용하여 C/C++ 공용 구조체 만들기(Visual Basic)

특성을 사용하면 메모리에서 구조체가 레이아웃되는 방식을 사용자 지정할 수 있습니다. 예를 들어 `StructLayout(LayoutKind.Explicit)` 및 `FieldOffset` 특성을 사용하여 C/C++에서 공용 구조체로 알려진 항목을 만들 수 있습니다.

## <a name="example"></a>예제

이 코드 세그먼트에서 `TestUnion`의 모든 필드는 메모리의 같은 위치에서 시작합니다.

```vb
' Add an Imports statement for System.Runtime.InteropServices.

<System.Runtime.InteropServices.StructLayout(
      System.Runtime.InteropServices.LayoutKind.Explicit)>
Structure TestUnion
    <System.Runtime.InteropServices.FieldOffset(0)>
    Public i As Integer

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public d As Double

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public c As Char

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public b As Byte
End Structure
```

## <a name="example"></a>예제

다음은 명시적으로 설정된 다른 위치에서 필드가 시작하는 또 다른 예제입니다.

```vb
' Add an Imports statement for System.Runtime.InteropServices.

 <System.Runtime.InteropServices.StructLayout(
      System.Runtime.InteropServices.LayoutKind.Explicit)>
Structure TestExplicit
     <System.Runtime.InteropServices.FieldOffset(0)>
     Public lg As Long

     <System.Runtime.InteropServices.FieldOffset(0)>
     Public i1 As Integer

     <System.Runtime.InteropServices.FieldOffset(4)>
     Public i2 As Integer

     <System.Runtime.InteropServices.FieldOffset(8)>
     Public d As Double

     <System.Runtime.InteropServices.FieldOffset(12)>
     Public c As Char

     <System.Runtime.InteropServices.FieldOffset(14)>
     Public b As Byte
 End Structure
```

두 개의 정수 필드 `i1` 및 `i2`는 `lg`와 동일한 메모리 위치를 공유합니다. 구조체 레이아웃에 대한 이러한 종류의 제어는 플랫폼 호출을 사용할 때 유용합니다.

## <a name="see-also"></a>참고 항목

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Visual Basic 프로그래밍 가이드](../../index.md)
- [특성](../../../../standard/attributes/index.md)
- [리플렉션(Visual Basic)](../reflection.md)
- [특성(Visual Basic)](../../../language-reference/attributes.md)
- [사용자 지정 특성 만들기(Visual Basic)](creating-custom-attributes.md)
- [리플렉션을 사용하여 특성 액세스(Visual Basic)](accessing-attributes-by-using-reflection.md)
