---
description: "BC31102: ' ' 속성의 ' Set ' 접근자에 <propertyname> 액세스할 수 없음에 대해 자세히 알아보세요."
title: "'<propertyname>' 속성의 'Set' 접근자에 액세스할 수 없습니다."
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: da4d29933ca140bd9fa1a15758b64667013a8032
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675080"
---
# <a name="bc31102-set-accessor-of-property-propertyname-is-not-accessible"></a>BC31102: ' ' 속성의 ' Set ' 접근자 \<propertyname> 에 액세스할 수 없습니다.

문에서 속성의 프로시저에 대 한 액세스 권한이 없는 경우 속성의 값을 저장 하려고 `Set` 합니다.

 [Set 문이](../statements/set-statement.md) 해당 [property 문](../statements/property-statement.md)보다 더 제한적인 액세스 수준으로 표시 되는 경우 다음과 같은 경우에 속성 값을 설정 하려는 시도가 실패할 수 있습니다.

- `Set`문이 [Private](../modifiers/private.md) 으로 표시 되 고 호출 코드가 속성이 정의 된 클래스 또는 구조체 외부에 있습니다.

- `Set`문이 [Protected](../modifiers/protected.md) 로 표시 되어 있고 호출 코드가 속성이 정의 된 클래스 또는 구조체에 없거나 파생 클래스에 없는 경우

- `Set`문이 [Friend](../modifiers/friend.md) 로 표시 되어 있고 호출 코드가 속성이 정의 된 어셈블리와 동일 하지 않습니다.

 **오류 ID:** BC31102

## <a name="to-correct-this-error"></a>이 오류를 해결하려면

- 속성을 정의 하는 소스 코드를 제어할 수 있는 경우 `Set` 속성 자체와 동일한 액세스 수준을 사용 하 여 프로시저를 선언 하는 것이 좋습니다.

- 속성을 정의 하는 소스 코드를 제어할 수 없거나 `Set` 프로시저 액세스 수준을 속성 자체 보다 더 제한 해야 하는 경우 속성 값을 설정 하는 문을 속성에 대 한 액세스를 강화 하는 코드 영역으로 이동 합니다.

## <a name="see-also"></a>참고 항목

- [속성 프로시저](../../programming-guide/language-features/procedures/property-procedures.md)
- [방법: 액세스 수준이 혼합된 속성 선언](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
