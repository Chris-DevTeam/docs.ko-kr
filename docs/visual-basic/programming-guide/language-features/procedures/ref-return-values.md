---
description: 자세한 내용은 참조 반환 값 지원 (Visual Basic)을 참조 하세요.
title: 참조 반환 값
ms.date: 04/28/2017
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
ms.openlocfilehash: 215a647c68eb7eadd394a1a7842ceb98c46e04a5
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466551"
---
# <a name="support-for-reference-return-values-visual-basic"></a>참조 반환 값 (Visual Basic) 지원

C # 7.0부터 c # 언어는 *참조 반환 값* 을 지원 합니다. 참조 반환 값을 이해 하는 한 가지 방법은 메서드에 참조로 전달 되는 인수와 반대입니다. 참조로 전달 된 인수를 수정 하면 변경 내용이 호출자의 변수 값에 반영 됩니다. 메서드가 호출자에 게 참조 반환 값을 제공 하는 경우 호출자가 참조 반환 값을 수정한 내용이 호출 된 메서드 데이터에 반영 됩니다.

Visual Basic는 참조 반환 값을 사용 하 여 메서드를 작성 하는 것을 허용 하지 않지만 참조 반환 값을 사용할 수 있습니다. 즉, 참조 반환 값을 사용 하 여 메서드를 호출 하 고 해당 반환 값을 수정할 수 있으며 참조 반환 값의 변경 내용이 호출 된 메서드 데이터에 반영 됩니다.

## <a name="modifying-the-ref-return-value-directly"></a>참조 반환 값 직접 수정

항상 성공 하 고 매개 변수를 포함 하지 않는 메서드의 경우 `ByRef` 참조 반환 값을 직접 수정할 수 있습니다. 이렇게 하려면 참조 반환 값을 반환 하는 식에 새 값을 할당 합니다.

다음 c # 예제에서는 `NumericValue.IncrementValue` 내부 값을 증가 시키고이를 참조 반환 값으로 반환 하는 메서드를 정의 합니다.

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

그러면 다음 Visual Basic 예제에서 호출자가 참조 반환 값을 수정 합니다. 메서드 호출을 포함 하는 줄은 `NumericValue.IncrementValue` 메서드에 값을 할당 하지 않습니다. 대신 메서드에서 반환 된 참조 반환 값에 값을 할당 합니다.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>도우미 메서드 사용

다른 경우에는 메서드 호출의 참조 반환 값을 직접 수정 하는 것이 항상 좋은 것은 아닙니다. 예를 들어 문자열을 반환 하는 검색 메서드는 항상 일치 하는 항목을 찾지 못할 수 있습니다. 이 경우 검색에 성공한 경우에만 참조 반환 값을 수정 하려고 합니다.

다음 c # 예제에서는이 시나리오를 보여 줍니다. `Sentence`C #으로 작성 된 클래스를 정의 합니다 .이 클래스에는 `FindNext` 지정 된 부분 문자열로 시작 하는 문장의 다음 단어를 찾는 메서드가 포함 됩니다. 문자열은 참조 반환 값으로 반환되며, 메서드에 참조로 전달된 `Boolean` 변수는 검색에 성공했는지 여부를 나타냅니다. 참조 반환 값은 반환 된 값을 읽을 뿐만 아니라 호출자도 수정할 수 있으며, 수정 내용은 클래스에 내부적으로 포함 된 데이터에 반영 됨을 나타냅니다 `Sentence` .

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

이 경우에는 메서드 호출이 일치 항목을 찾지 못하고 문장의 첫 번째 단어를 반환 하기 때문에 참조 반환 값을 직접 수정 하는 것은 신뢰할 수 없습니다. 이 경우 호출자가 문장의 첫 번째 단어를 실수로 수정 합니다. 호출자가 `null` (또는 Visual Basic)을 반환 하는 경우이를 방지할 수 있습니다 `Nothing` . 그러나이 경우 값이 인 문자열을 수정 하려고 시도 하면이 `Nothing` throw 됩니다 <xref:System.NullReferenceException> . 호출자가를 반환 해도를 방지할 수 <xref:System.String.Empty?displayProperty=nameWithType> 있지만이 경우 호출자는 값이 인 문자열 변수를 정의 해야 합니다 <xref:System.String.Empty?displayProperty=nameWithType> . 호출자가 해당 문자열을 수정할 수 있지만 수정 된 문자열은 클래스에 의해 저장 된 문장의 단어와 관계가 없기 때문에 수정 자체는 목적이 아닙니다 `Sentence` .

이 시나리오를 처리 하는 가장 좋은 방법은 참조 반환 값을 도우미 메서드에 참조로 전달 하는 것입니다. 그런 다음 도우미 메서드는 메서드 호출이 성공 했는지 여부를 확인 하는 논리를 포함 하 고 있는 경우 참조 반환 값을 수정 합니다. 다음 예제에서는 가능한 구현을 제공 합니다.

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>추가 정보

- [값 및 참조로 인수 전달](passing-arguments-by-value-and-by-reference.md)
- [Visual Basic의 프로시저](index.md)
