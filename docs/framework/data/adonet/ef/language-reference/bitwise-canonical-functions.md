---
description: '자세한 정보: 비트 정식 함수'
title: 비트 정식 함수
ms.date: 03/30/2017
ms.assetid: 993868ca-16e3-47b6-9915-c29cd63b0a21
ms.openlocfilehash: a811c707749af2d2fa9472ae2d1444c3f076aeec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697103"
---
# <a name="bitwise-canonical-functions"></a>비트 정식 함수

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]에는 비트 정식 함수가 포함되어 있습니다.  
  
## <a name="remarks"></a>설명  

 다음 표에서는 비트 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 정식 함수를 보여 줍니다. 이러한 함수는 `Null`이 입력되면 `Null`을 반환합니다. 함수의 반환 형식은 인수 형식과 같습니다. 함수가 둘 이상의 인수를 사용하는 경우 인수는 같은 형식이어야 합니다. 서로 다른 형식에서 비트 작업을 수행하려면 명시적으로 같은 형식으로 캐스팅해야 합니다.  
  
|함수|설명|  
|--------------|-----------------|  
|`BitWiseAnd (` `value1` `,`  `value2` `)`|`value1` 및 `value2`의 비트 결합을 `value1` 및 `value2`의 형식으로 반환합니다.<br /><br /> **인수**<br /><br /> `Byte`,, `Int16` `Int32` 및 `Int64` 입니다.<br /><br /> **예제**<br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|`BitWiseNot (` `value` `)`|`value`의 비트 부정을 반환합니다.<br /><br /> **인수**<br /><br /> `Byte`,, `Int16` `Int32` 및 `Int64` 입니다.<br /><br /> **예제**<br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|`BitWiseOr (` `value1` `,`  `value2` `)`|`value1` 및 `value2`의 비트 분리를 `value1` 및 `value2`의 형식으로 반환합니다.<br /><br /> **인수**<br /><br /> `Byte`, `Int16`, `Int32` 및 `Int64`입니다.<br /><br /> **예제**<br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|`BitWiseXor (` `value1` `,`  `value2` `)`|`value1` 및 `value2`의 배타적 비트 분리를 `value1` 및 `value2`의 형식으로 반환합니다.<br /><br /> **인수**<br /><br /> `Byte`, `Int16`, `Int32` 및 `Int64`입니다.<br /><br /> **예제**<br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a>참고 항목

- [정식 함수](canonical-functions.md)
