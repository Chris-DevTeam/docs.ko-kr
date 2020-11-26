---
title: UI 자동화를 사용하여 텍스트 상자에 콘텐츠 추가
description: .NET의 Microsoft UI 자동화를 사용 하 여 한 줄 텍스트 상자에 콘텐츠를 추가 하는 방법의 예를 참조 하세요.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
ms.openlocfilehash: 9108cb586700474f7f855751000944212a3cef29
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235729"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a>UI 자동화를 사용하여 텍스트 상자에 콘텐츠 추가

> [!NOTE]
> 이 설명서는 <xref:System.Windows.Automation> 네임스페이스에 정의된 관리되는 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 클래스를 사용하려는 .NET Framework 개발자를 위한 것입니다. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]에 대한 최신 정보는 [Windows 자동화 API: UI 자동화](/windows/win32/winauto/entry-uiauto-win32)를 참조하세요.  
  
 이 항목에는를 사용 하 여 텍스트를 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 한 줄 텍스트 상자에 삽입 하는 방법을 보여 주는 예제 코드가 있습니다. 이 적용 되지 않는 여러 줄 및 서식 있는 텍스트 컨트롤에 대 한 대체 방법이 제공 됩니다 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . 비교를 위해이 예제에서는 Win32 메서드를 사용 하 여 동일한 결과를 얻는 방법도 보여 줍니다.  
  
## <a name="example"></a>예제  

 다음 예제에서는 대상 응용 프로그램의 텍스트 컨트롤 시퀀스를 단계별로 안내 합니다. 각 텍스트 컨트롤은 <xref:System.Windows.Automation.ValuePattern> 메서드를 사용 하 여 개체에서 개체를 얻을 수 있는지 여부를 확인 하기 위해 테스트 됩니다 <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> . 텍스트 컨트롤이를 지원 하면 <xref:System.Windows.Automation.ValuePattern> <xref:System.Windows.Automation.ValuePattern.SetValue%2A> 메서드를 사용 하 여 텍스트 컨트롤에 사용자 정의 문자열을 삽입 합니다. 그렇지 않으면 <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> 메서드가 사용 됩니다.  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a>참고 항목

- [TextPattern Insert 텍스트 샘플](/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))
