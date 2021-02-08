---
description: '자세한 정보: 오류 없이 다시 시작'
title: 오류 없이 계속됩니다.
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: a2284484be65ae975c6e09499ec19e3cfd8d4a04
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792013"
---
# <a name="resume-without-error"></a>오류 없이 계속됩니다.

`Resume`문이 오류 처리 코드 외부에 표시 되었거나 오류가 없는 경우에도 코드를 오류 처리기로 건너뛰었습니다.  
  
## <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
1. `Resume`문을 오류 처리기로 이동 하거나 삭제 합니다.  
  
2. 여러 프로시저에서 레이블로의 점프를 수행할 수 없으므로 오류 처리기를 식별 하는 레이블에 대해 프로시저를 검색 합니다. 문이 아닌 문의 대상으로 지정 된 중복 된 레이블을 찾은 경우 `GoTo` `On Error GoTo` 해당 대상에 동의 하도록 줄 레이블을 변경 합니다.  
  
## <a name="see-also"></a>참고 항목

- [Resume 문](../statements/resume-statement.md)
- [On Error 문](../statements/on-error-statement.md)
