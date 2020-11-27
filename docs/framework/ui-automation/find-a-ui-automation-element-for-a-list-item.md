---
title: 목록 항목의 UI 자동화 요소 찾기
description: 항목의 인덱스를 알 수 있는 경우 목록 항목의 UI 자동화 요소를 찾는 방법을 보여 주는 예제를 참조 하세요.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items, finding elements for
- elements, finding for list items
- UI Automation, finding elements for List items
ms.assetid: c326ad2b-2144-4f64-ae4c-d850c74f95c5
ms.openlocfilehash: 95f6b558cc53b00701232f247f8de7f8c603e3ac
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276479"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a>목록 항목의 UI 자동화 요소 찾기

> [!NOTE]
> 이 설명서는 <xref:System.Windows.Automation> 네임스페이스에 정의된 관리되는 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 클래스를 사용하려는 .NET Framework 개발자를 위한 것입니다. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]에 대한 최신 정보는 [Windows 자동화 API: UI 자동화](/windows/win32/winauto/entry-uiauto-win32)를 참조하세요.  
  
 이 항목에서는 <xref:System.Windows.Automation.AutomationElement> 항목의 인덱스를 알고 있을 때 목록 내의 항목에 대 한를 검색 하는 방법을 보여 줍니다.  
  
## <a name="example"></a>예제  

 다음 예제에서는 목록에서 지정 된 항목을 검색 하는 두 가지 방법, 즉를 사용 하는 방법과를 사용 하는 방법을 보여 줍니다 <xref:System.Windows.Automation.TreeWalker> <xref:System.Windows.Automation.AutomationElement.FindAll%2A> .  
  
 첫 번째 기술은 Win32 컨트롤에서 속도가 더 빠르지만 WPF (Windows Presentation Foundation) 컨트롤의 경우 더 빠릅니다.  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a>참고 항목

- [UI 자동화 요소 가져오기](obtaining-ui-automation-elements.md)
