---
description: '자세한 정보: 방법: Visual Basic에서 직렬 포트로 문자열 보내기'
title: '방법: 직렬 포트로 문자열 보내기'
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: 66dedaab05090af2659701e57b37b4813447b8ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666487"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a>방법: Visual Basic에서 직렬 포트로 문자열 보내기

이 항목에서는 Visual Basic에서 `My.Computer.Ports`를 사용하여 컴퓨터의 직렬 포트에 문자열을 보내는 방법을 설명합니다.  
  
## <a name="example"></a>예제  

 이 예제에서는 COM1 직렬 포트에 문자열을 보냅니다. 컴퓨터의 다른 직렬 포트를 사용해야 할 수도 있습니다.  
  
 `My.Computer.Ports.OpenSerialPort` 메서드를 사용하여 포트에 대한 참조를 가져옵니다. 자세한 내용은 <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>를 참조하세요.  
  
 `Using` 블록을 사용하면 예외를 생성하는 경우 애플리케이션이 직렬 포트를 닫을 수 있습니다. 직렬 포트를 조작하는 모든 코드는 이 블록 안이나 `Try...Catch...Finally` 블록 안에 표시되어야 합니다.  
  
 <xref:System.IO.Ports.SerialPort.WriteLine%2A> 메서드는 데이터를 직렬 포트로 보냅니다.  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a>코드 컴파일  
  
- 이 예제에서는 컴퓨터가 `COM1`을 사용 중이라고 가정합니다.  
  
## <a name="robust-programming"></a>강력한 프로그래밍  

 이 예제에서는 컴퓨터가 `COM1`을 사용 중이라고 가정합니다. 유연성 향상을 위해 코드에서 사용자가 사용 가능한 포트 목록에서 원하는 직렬 포트를 선택할 수 있도록 해야 합니다. 자세한 내용은 [방법: 사용할 수 있는 직렬 포트 표시](how-to-show-available-serial-ports.md)를 참조하세요.  
  
 이 예제에서는 `Using` 블록을 사용하여 예외가 throw되는 경우에도 애플리케이션이 포트를 닫도록 합니다. 자세한 내용은 [using 문](../../../language-reference/statements/using-statement.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [방법: 직렬 포트에 연결된 모뎀 전화 접속](how-to-dial-modems-attached-to-serial-ports.md)
- [방법: 사용 가능한 직렬 포트 표시](how-to-show-available-serial-ports.md)
