---
description: '자세한 정보: BC36629: Nullable 형식 유추는이 컨텍스트에서 지원 되지 않습니다.'
title: 이 컨텍스트에서는 nullable 형식을 유추할 수 없습니다.
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 915f964d55068f39b0468e2c47cc6e5538be1a6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795627"
---
# <a name="bc36629-nullable-type-inference-is-not-supported-in-this-context"></a>BC36629:이 컨텍스트에서는 Nullable 형식 유추를 지원 하지 않습니다.

값 형식과 구조체를 nullable로 선언할 수 있습니다.

```vb
Dim a? As Integer
Dim b As Integer?
```

 그러나 nullable 선언을 형식 유추와 함께 사용할 수 없습니다. 다음 예에서는이 오류가 발생 합니다.

```vb
' Not valid.
' Dim c? = 10
' Dim d? = a
```

 **오류 ID:** BC36629

## <a name="to-correct-this-error"></a>이 오류를 해결하려면

- `As`절을 사용 하 여 변수를 nullable 값 형식으로 선언 합니다.

## <a name="see-also"></a>참고 항목

- [Nullable 값 형식](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [지역 형식 유추](../../programming-guide/language-features/variables/local-type-inference.md)
