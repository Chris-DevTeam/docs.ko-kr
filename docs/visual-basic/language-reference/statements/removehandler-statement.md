---
description: '다음에 대 한 자세한 정보: RemoveHandler 문'
title: RemoveHandler 문
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 699db9edfc029b4149246e8b654645040ae6d89e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741304"
---
# <a name="removehandler-statement"></a>RemoveHandler 문

이벤트와 이벤트 처리기 간의 연결을 제거 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>부분  
  
|용어|정의|  
|---|---|  
|`event`|처리 되는 이벤트의 이름입니다.|  
|`eventhandler`|현재 이벤트를 처리 하는 프로시저의 이름입니다.|  
  
## <a name="remarks"></a>설명  

 `AddHandler`및 `RemoveHandler` 문을 사용 하면 프로그램을 실행 하는 동안 언제 든 지 특정 이벤트에 대 한 이벤트 처리를 시작 하 고 중지할 수 있습니다.  
  
> [!NOTE]
> 사용자 지정 이벤트의 경우 `RemoveHandler` 문은 이벤트의 접근자를 호출 합니다 `RemoveHandler` . 사용자 지정 이벤트에 대 한 자세한 내용은 [이벤트 문](event-statement.md)을 참조 하십시오.  
  
## <a name="example"></a>예제  

 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>참고 항목

- [AddHandler 문](addhandler-statement.md)
- [핸들](handles-clause.md)
- [Event 문](event-statement.md)
- [이벤트](../../programming-guide/language-features/events/index.md)
