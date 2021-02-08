---
description: '자세한 내용은 다음에 대해 자세히 알아보세요. BC30801: 숫자 레이블 뒤에 콜론이와 야 합니다.'
title: 숫자 레이블 뒤에는 콜론이 와야 합니다.
ms.date: 07/20/2015
f1_keywords:
- vbc30801
- bc30801
helpviewer_keywords:
- BC30801
ms.assetid: 67743319-2d1c-496e-bfd9-22b046b43b5a
ms.openlocfilehash: 4c179cc6b74f323c330b093af988f33173e901fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795965"
---
# <a name="bc30801-labels-that-are-numbers-must-be-followed-by-colons"></a>BC30801: 숫자 레이블 뒤에는 콜론이와 야 합니다.

줄 번호는 다른 종류의 레이블과 동일한 규칙을 따르고 콜론을 포함 해야 합니다.

 **오류 ID:** BC30801

## <a name="to-correct-this-error"></a>이 오류를 해결하려면

- 코드 줄의 시작 부분에 숫자 뒤에 콜론을 추가 합니다. 예를 들어:

    ```vb
    400:    X += 1
    ```

## <a name="see-also"></a>참고 항목

- [GoTo 문](../statements/goto-statement.md)
