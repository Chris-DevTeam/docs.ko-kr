---
title: UI 자동화를 사용하여 텍스트 특성 가져오기
description: UI 자동화를 사용 하 여 텍스트 특성을 가져오는 방법에 대해 알아봅니다. 텍스트 범위에서 텍스트 특성을 가져오는 코드 예제를 참조 하세요.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting, text attributes
- UI Automation, getting text attributes
- text attributes, getting
ms.assetid: fdefc6c3-b836-4cfe-8dec-1484bfdc5551
ms.openlocfilehash: 2c59c42e2ba6b67381ab9f70da51bd51ad4330c9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96282329"
---
# <a name="obtain-text-attributes-using-ui-automation"></a>UI 자동화를 사용하여 텍스트 특성 가져오기

> [!NOTE]
> 이 설명서는 <xref:System.Windows.Automation> 네임스페이스에 정의된 관리되는 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 클래스를 사용하려는 .NET Framework 개발자를 위한 것입니다. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]에 대한 최신 정보는 [Windows 자동화 API: UI 자동화](/windows/win32/winauto/entry-uiauto-win32)를 참조하세요.  
  
 이 항목에서는 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 을 사용하여 텍스트 범위에서 텍스트 특성을 가져오는 방법을 보여줍니다. 텍스트 범위는 문서 내에서 캐럿의 현재 위치(또는 중복 제거 선택 항목), 연속적인 텍스트 선택 항목, 분리형 텍스트 선택 항목의 컬렉션 또는 문서의 전체 텍스트 내용에 해당될 수 있습니다.  
  
## <a name="example"></a>예제  

 다음 코드 예제는 텍스트 범위에서 <xref:System.Windows.Automation.TextPattern.FontNameAttribute> 를 가져오는 방법을 보여 줍니다.  
  
 [!code-csharp[UIATextPattern_snip#StartTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#starttarget)]
 [!code-vb[UIATextPattern_snip#StartTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#starttarget)]  
[!code-csharp[UIATextPattern_snip#GetTextElement](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#gettextelement)]
[!code-vb[UIATextPattern_snip#GetTextElement](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#gettextelement)]  
[!code-csharp[UIATextPattern_snip#FontName](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#fontname)]
[!code-vb[UIATextPattern_snip#FontName](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#fontname)]  
  
 <xref:System.Windows.Automation.TextPattern> 컨트롤 패턴은 <xref:System.Windows.Automation.Text.TextPatternRange> 클래스와 함께 기본 텍스트 특성, 속성 및 메서드를 지원합니다. <xref:System.Windows.Automation.TextPattern> 또는 <xref:System.Windows.Automation.Text.TextPatternRange> 에서 지원되지 않는 컨트롤 관련 기능의 경우 <xref:System.Windows.Automation.AutomationElement>클래스는 UI 자동화 클라이언트가 해당되는 기본 개체 모델에 액세스할 수 있는 메서드를 제공합니다.  
  
## <a name="see-also"></a>참고 항목

- [UI 자동화 TextPattern 개요](ui-automation-textpattern-overview.md)
- [UI 자동화를 사용하여 텍스트 상자에 콘텐츠 추가](add-content-to-a-text-box-using-ui-automation.md)
- [UI 자동화를 사용하여 텍스트 찾기 및 강조](find-and-highlight-text-using-ui-automation.md)
- [UI 자동화 컨트롤 패턴 개요](ui-automation-control-patterns-overview.md)
- [클라이언트용 UI 자동화 컨트롤 패턴](ui-automation-control-patterns-for-clients.md)
- [UI 자동화를 사용하여 혼합 텍스트 특성 정보 가져오기](obtain-mixed-text-attribute-details-using-ui-automation.md)
