---
description: '자세히 알아보기: 보호 된 Friend (Visual Basic)'
title: Protected Friend
ms.date: 05/10/2018
f1_keywords:
- vb.ProtectedFriend
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: dcc8fd2b1aa99f910f002ac05178d379532fb73d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700977"
---
# <a name="protected-friend-visual-basic"></a>보호 된 Friend (Visual Basic)

`Protected Friend` 키워드 조합은 멤버 액세스 한정자입니다. 선언 된 요소에 대 한 [Friend](friend.md) 액세스와 [보호 된](protected.md) 액세스를 모두 권한을 부여, 동일한 어셈블리, 자체 클래스 및 파생 클래스의 어디에서 나 액세스할 수 있습니다. 클래스의 멤버만 지정할 수 있습니다. 구조체 `Protected Friend` `Protected Friend` 는 상속 될 수 없으므로 구조체의 멤버에는 적용할 수 없습니다.

> [!NOTE]
> Visual Studio에서 F1 도움말을 선택 하 여 `protected friend` [보호](protected.md) 또는 [friend](friend.md)에 대 한 도움말을 제공 합니다. IDE는 복합 단어가 아니라 커서에서 단일 토큰을 선택 합니다.

## <a name="rules"></a>규칙

**선언 컨텍스트.** `Protected Friend`는 클래스 수준 에서만 사용할 수 있습니다. 즉, 요소에 대 한 선언 컨텍스트는 `Protected` 클래스 여야 하며 소스 파일, 네임 스페이스, 인터페이스, 모듈, 구조체 또는 프로시저일 수 없습니다.

## <a name="see-also"></a>참고 항목

- [공용](public.md)
- [보호됨](protected.md)
- [Friend](friend.md)
- [개인](private.md)
- [비공개 보호](./private-protected.md)
- [Visual Basic의 액세스 수준](../../programming-guide/language-features/declared-elements/access-levels.md)
- [절차](../../programming-guide/language-features/procedures/index.md)
- [구조체](../../programming-guide/language-features/data-types/structures.md)
- [개체 및 클래스](../../programming-guide/language-features/objects-and-classes/index.md)
