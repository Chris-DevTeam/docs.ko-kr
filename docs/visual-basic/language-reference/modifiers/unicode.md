---
description: '자세한 정보: 유니코드 (Visual Basic)'
title: 유니코드(Unicode)
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: b0c71d8fdefe3f0d240201e0d57265e5c6081d50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700717"
---
# <a name="unicode-visual-basic"></a>Unicode(Visual Basic)

선언 되는 외부 프로시저의 이름에 관계 없이 모든 문자열을 유니코드 값으로 마샬링하 Visual Basic 하도록 지정 합니다.  
  
 프로젝트 외부에서 정의 된 프로시저를 호출 하는 경우 Visual Basic 컴파일러는 프로시저를 올바르게 호출 하기 위해 가져야 하는 정보에 액세스할 수 없습니다. 이 정보에는 프로시저가 있는 위치, 식별 방법, 호출 시퀀스 및 반환 형식, 사용 하는 문자열 문자 집합이 포함 됩니다. [Declare 문은](../statements/declare-statement.md) 외부 프로시저에 대 한 참조를 만들고이 필요한 정보를 제공 합니다.  
  
 `charsetmodifier` `Declare` 문의 부분은 외부 프로시저를 호출 하는 동안 문자열을 마샬링하는 문자 집합 정보를 제공 합니다. 외부 파일에서 외부 프로시저 이름을 검색 Visual Basic는 방법에도 영향을 줍니다. `Unicode`한정자는 Visual Basic 모든 문자열을 유니코드 값으로 마샬링하고 검색 하는 동안 해당 이름을 수정 하지 않고 프로시저를 조회 하도록 지정 합니다.  
  
 문자 집합 한정자가 지정 되지 않은 경우 `Ansi` 가 기본값입니다.  
  
## <a name="remarks"></a>설명  

 `Unicode`이 컨텍스트에서는 한정자를 사용할 수 있습니다.  
  
 [Declare 문](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>스마트 디바이스 개발자 노트  

 이 키워드는 지원 되지 않습니다.  
  
## <a name="see-also"></a>참고 항목

- [Ansi](ansi.md)
- [자동](auto.md)
- [C++ 키워드](../keywords/index.md)
