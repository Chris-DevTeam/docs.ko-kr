---
description: '자세한 정보: <variablename> 루프 범위와 단계 변수는 같은 형식으로 확장 되지 않으므로 BC30982: type의 형식을 유추할 수 없습니다.'
title: 루프 범위와 단계 변수는 같은 형식으로 변환할 수 없으므로 '<variablename>' 형식을 확대 변환할 수 없습니다.
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: 399e021500813127df6ecede2534783df09ac8dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641163"
---
# <a name="bc30982-type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>BC30982: \<variablename> 루프 범위와 단계 변수가 동일한 형식으로 확장 되지 않으므로 ' '의 형식을 유추할 수 없습니다.

`For...Next`다음 조건이 true 이기 때문에 컴파일러가 루프 제어 변수의 데이터 형식을 유추할 수 없는 루프를 작성 했습니다.

- `As` 절을 사용하여 루프 제어 변수의 데이터 형식을 지정하지 않았습니다.

- 루프 범위와 단계 변수에 두 개 이상의 데이터 형식이 포함되어 있습니다.

- 데이터 형식 간에 표준 변환이 없습니다.

 따라서 컴파일러가 루프 제어 변수의 데이터 형식을 유추할 수 없습니다.

 다음 예제에서 단계 변수는 문자이 고 루프 범위는 두 정수입니다. 문자와 정수 사이에는 표준 변환이 없기 때문에이 오류가 보고 됩니다.

```vb
Dim stepVar = "1"c
Dim m = 0
Dim n = 20

' Not valid.
' For i = 1 To 10 Step stepVar
    ' Loop processing
' Next
```

**오류 ID:** BC30982

## <a name="to-correct-this-error"></a>이 오류를 해결하려면

- 필요에 따라 루프 범위와 단계 변수의 형식을 변경 하 여 그 중 하나 이상이 다른 형식으로 확장 될 수 있도록 합니다. 앞의 예제에서는의 형식을로 변경 합니다 `stepVar` `Integer` .

  ```vb
  Dim stepVar = 1
  ```

  또는

  ```vb
  Dim stepVar As Integer = 1
  ```

- 명시적 변환 함수를 사용 하 여 루프 범위와 단계 변수를 적절 한 형식으로 변환 합니다. 앞의 예제에서 `Val` 함수를에 적용 `stepVar` 합니다.

  ```vb
  For i = 1 To 10 Step Val(stepVar)
      ' Loop processing
  Next
  ```

## <a name="see-also"></a>참고 항목

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [For...Next 문](../statements/for-next-statement.md)
- [암시적 변환과 명시적 변환](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [지역 형식 유추](../../programming-guide/language-features/variables/local-type-inference.md)
- [Option Infer 문](../statements/option-infer-statement.md)
- [형식 변환 함수](../functions/type-conversion-functions.md)
- [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
