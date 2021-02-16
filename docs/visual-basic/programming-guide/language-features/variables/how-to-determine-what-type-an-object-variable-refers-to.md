---
description: '자세한 정보: 방법: 개체 변수가 참조 하는 형식 확인 (Visual Basic)'
title: '방법: 개체 변수가 참조하는 형식 확인'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 699a8c5c075fc923a61a66f617c255f193cd8797
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481924"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>방법: 개체 변수가 참조하는 형식 확인(Visual Basic)

개체 변수는 다른 곳에 저장 된 데이터에 대 한 포인터를 포함 합니다. 런타임에 변경 될 수 있는 데이터의 형식입니다. 언제 든 지 메서드를 사용 하 여 <xref:System.Type.GetTypeCode%2A> 현재 런타임 형식을 확인 하거나 [TypeOf 연산자](../../../language-reference/operators/typeof-operator.md) 를 사용 하 여 현재 런타임 형식이 지정 된 형식과 호환 되는지 확인할 수 있습니다.

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>개체 변수가 현재 참조 하는 정확한 형식을 확인 하려면

1. 개체 변수에서 메서드를 호출 <xref:System.Object.GetType%2A> 하 여 개체를 검색 <xref:System.Type?displayProperty=nameWithType> 합니다.

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. 클래스에서 <xref:System.Type?displayProperty=nameWithType> 공유 메서드를 호출 하 여 <xref:System.Type.GetTypeCode%2A> <xref:System.TypeCode> 개체의 형식에 대 한 열거형 값을 검색 합니다.

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    <xref:System.TypeCode>와 같은 원하는 열거형 멤버에 대해 열거형 값을 테스트할 수 있습니다 `Double` .

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>개체 변수의 형식이 지정 된 형식과 호환 되는지 여부를 확인 하려면

- `TypeOf` [Is 연산자](../../../language-reference/operators/is-operator.md) 와 함께 연산자를 사용 하 여 ... `TypeOf` 식으로 개체를 테스트 합니다. `Is`

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    `TypeOf`... `Is` 식은 `True` 개체의 런타임 형식이 지정 된 형식과 호환 되는 경우를 반환 합니다.

    호환성 기준은 지정 된 형식이 클래스, 구조체 또는 인터페이스 인지에 따라 달라 집니다. 일반적으로이 형식은 개체가와 동일한 형식 이거나,에서 상속 되거나, 지정 된 형식을 구현 하는 경우 호환 됩니다. 자세한 내용은 [TypeOf 연산자](../../../language-reference/operators/typeof-operator.md)를 참조 하세요.

## <a name="compile-the-code"></a>코드 컴파일

지정 된 형식은 변수나 식일 수 없습니다. 클래스, 구조체 또는 인터페이스와 같은 정의 된 형식의 이름 이어야 합니다. 여기에는 및와 같은 내장 형식이 포함 됩니다 `Integer` `String` .

## <a name="see-also"></a>추가 정보

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [개체 변수](object-variables.md)
- [개체 변수 값](object-variable-values.md)
- [Object Data Type](../../../language-reference/data-types/object-data-type.md)
