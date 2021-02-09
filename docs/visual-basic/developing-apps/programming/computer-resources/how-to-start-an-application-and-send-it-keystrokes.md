---
description: '자세한 정보: 방법: 애플리케이션 시작 및 키 입력 보내기(Visual Basic)'
title: '방법: 애플리케이션 시작 및 키 입력 보내기 - Visual Basic'
ms.date: 10/23/2019
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: ea54b940b528e0833d9c7a6cbef67f65a4cb4f6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666461"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a>방법: 애플리케이션 시작 및 키 입력 보내기(Visual Basic)

이 예제에서는 <xref:Microsoft.VisualBasic.Interaction.Shell%2A> 메서드를 사용하여 메모장 애플리케이션을 시작한 다음, [My.Computer.Keyboard.SendKeys](xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A) 메서드를 통해 키 입력을 보내 문장을 출력합니다.

## <a name="example"></a>예제

[!code-vb[VbVbalrMyComputer#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#25)]

## <a name="robust-programming"></a>강력한 프로그래밍

요청된 프로세스 식별자를 가진 애플리케이션을 찾을 수 없는 경우 <xref:System.ArgumentException> 예외가 발생합니다.  
  
## <a name="net-framework-security"></a>.NET Framework 보안

`Shell` 함수에 대한 호출은 완전 신뢰가 필요합니다(<xref:System.Security.SecurityException> 클래스).

## <a name="see-also"></a>참고 항목

- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
