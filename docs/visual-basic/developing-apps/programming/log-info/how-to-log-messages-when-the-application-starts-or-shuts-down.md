---
description: '자세한 정보: 방법: 애플리케이션이 시작 또는 종료될 때 메시지 기록(Visual Basic)'
title: '방법: 애플리케이션이 시작 또는 종료될 때 메시지 기록'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: 545a57c3666aa12e3763961d05067face9fe324a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775190"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a>방법: 애플리케이션이 시작 또는 종료될 때 메시지 기록(Visual Basic)

`My.Application.Log` 및 `My.Log` 개체를 사용하여 애플리케이션에서 발생하는 이벤트에 대한 정보를 기록할 수 있습니다. 이 예제에서는 `My.Application.Log.WriteEntry` 및 `Startup` 이벤트에 `Shutdown` 메서드를 사용하여 추적 정보를 쓰는 방법을 보여 줍니다.  
  
### <a name="to-access-the-applications-event-handler-code"></a>애플리케이션의 이벤트 처리기 코드에 액세스하려면  
  
1. **솔루션 탐색기** 에서 프로젝트를 선택합니다. **프로젝트** 메뉴에서 **속성** 을 선택합니다.  
  
2. **애플리케이션** 탭을 클릭합니다.  
  
3. **애플리케이션 이벤트 보기** 단추를 클릭하여 코드 편집기를 엽니다.  
  
     그러면 ApplicationEvents.vb 파일이 열립니다.  
  
### <a name="to-log-messages-when-the-application-starts"></a>애플리케이션이 시작될 때 메시지를 기록하려면  
  
1. 코드 편집기에서 ApplicationEvents.vb 파일을 엽니다. **일반** 메뉴에서 **MyApplication 이벤트** 를 선택합니다.  
  
2. **선언** 메뉴에서 **Startup** 을 선택합니다.  
  
     주 애플리케이션이 실행되기 전에 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> 이벤트가 발생합니다.  
  
3. `My.Application.Log.WriteEntry` 이벤트 처리기에 `Startup` 메서드를 추가합니다.  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a>애플리케이션이 종료될 때 메시지를 기록하려면  
  
1. 코드 편집기에서 ApplicationEvents.vb 파일을 엽니다. **일반** 메뉴에서 **MyApplication 이벤트** 를 선택합니다.  
  
2. **선언** 메뉴에서 **Shutdown** 을 선택합니다.  
  
     주 애플리케이션이 실행된 후 종료되기 전에 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> 이벤트가 발생합니다.  
  
3. `My.Application.Log.WriteEntry` 이벤트 처리기에 `Shutdown` 메서드를 추가합니다.  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a>예제  

 **프로젝트 디자이너** 를 사용하여 코드 편집기에서 애플리케이션 이벤트에 액세스할 수 있습니다. 자세한 내용은 [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)을 참조하세요.  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a>추가 정보

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [프로젝트 디자이너, 애플리케이션 페이지(Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [애플리케이션 로그 작업](working-with-application-logs.md)
