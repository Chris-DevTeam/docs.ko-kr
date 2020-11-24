---
title: 16진수 문자열과 숫자 형식 간 변환 방법 - C# 프로그래밍 가이드
description: 16진수 문자열과 숫자 형식 간에 변환하는 방법을 알아봅니다. 코드 예제를 살펴보고 사용 가능한 추가 리소스를 확인합니다.
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: fc2ffd24a67f026bd0c78e7d604a0147cf57ba49
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099161"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a>16진수 문자열과 숫자 형식 간 변환 방법(C# 프로그래밍 가이드)

이 예제에서는 다음 작업을 수행하는 방법을 보여 줍니다.  
  
- [string](../../language-reference/builtin-types/reference-types.md)에 있는 각 문자의 16진수 값을 가져옵니다.  
  
- 16진수 문자열의 각 값에 해당하는 [char](../../language-reference/builtin-types/char.md)을 가져옵니다.  
  
- 16진수 `string`을 [int](../../language-reference/builtin-types/integral-numeric-types.md)로 변환합니다.  
  
- 16진수 `string`을 [float](../../language-reference/builtin-types/floating-point-numeric-types.md)로 변환합니다.  
  
- [byte](../../language-reference/builtin-types/integral-numeric-types.md) 배열을 16진수 `string`으로 변환합니다.  
  
## <a name="example"></a>예제  

 이 예제에서는 `string`에 있는 각 문자의 16진수 값을 출력합니다. 먼저 `string`을 문자 배열로 구문 분석합니다. 그런 다음 각 문자에서 <xref:System.Convert.ToInt32%28System.Char%29>를 호출하여 해당 숫자 값을 가져옵니다. 마지막으로, `string`에서 숫자의 형식을 16진수 표현으로 지정합니다.  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a>예제  

 이 예제에서는 16진수 값의 `string`을 구문 분석하고 각 16진수 값에 해당하는 문자를 출력합니다. 먼저 [Split(Char\[\])](xref:System.String.Split(System.Char[])) 메서드를 호출하여 각 16진수 값을 배열의 개별 `string`으로 가져옵니다. 그런 다음 <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29>를 호출하여 16진수 값을 [int](../../language-reference/builtin-types/integral-numeric-types.md)로 표현된 10진수 값으로 변환합니다. 다음은 문자 코드에 해당하는 문자를 가져오는 두 가지 방법을 보여 줍니다. 첫 번째 방법은 정수 인수에 해당하는 문자를 `string`으로 반환하는 <xref:System.Char.ConvertFromUtf32%28System.Int32%29>를 사용합니다. 두 번째 방법은 `int`를 [char](../../language-reference/builtin-types/char.md)로 명시적으로 캐스팅합니다.  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a>예제  

 이 예제에서는 <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> 메서드를 호출하여 16진수 `string`을 정수로 변환하는 방법을 보여 줍니다.  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a>예제  

 다음 예제에서는 <xref:System.BitConverter?displayProperty=nameWithType> 클래스 및 <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> 메서드를 사용하여 16진수 `string`을 [float](../../language-reference/builtin-types/floating-point-numeric-types.md)로 변환하는 방법을 보여 줍니다.  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a>예제  

 다음 예제에서는 <xref:System.BitConverter?displayProperty=nameWithType> 클래스를 사용하여 [byte](../../language-reference/builtin-types/integral-numeric-types.md) 배열을 16진수 문자열로 변환하는 방법을 보여 줍니다.  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a>참조

- [표준 숫자 형식 문자열](../../../standard/base-types/standard-numeric-format-strings.md)
- [형식](./index.md)
- [문자열이 숫자 값을 나타내는지 확인 방법](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
