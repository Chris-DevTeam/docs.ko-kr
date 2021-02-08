---
description: '자세한 정보: 오버플로 (Visual Basic Run-Time 오류)'
title: 오버플로가 발생했습니다(Visual Basic 런타임 오류).
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: a01a8916e09f9278dbdf6d594c5ef84d63b04c51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795458"
---
# <a name="overflow-visual-basic-run-time-error"></a>오버플로가 발생했습니다(Visual Basic 런타임 오류).

할당 대상의 제한을 초과 하는 할당을 시도할 때 오버플로가 발생 합니다.  
  
## <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
1. 할당, 계산 및 데이터 형식 변환 결과가 너무 커서 해당 값 유형에 허용 되는 변수 범위 내에 표시 되지 않도록 하 고 필요한 경우 더 큰 범위의 값을 보유할 수 있는 유형의 변수에 값을 할당 합니다.  
  
2. 속성에 대 한 할당이 속성의 범위에 맞게 설정 되었는지 확인 합니다.  
  
3. 정수로 강제 변환 된 계산에 사용 되는 숫자의 결과가 정수 보다 크지 않은지 확인 하십시오.  
  
## <a name="see-also"></a>참고 항목

- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [데이터 형식](../data-types/index.md)
- [오류 형식](../../programming-guide/language-features/error-types.md)
