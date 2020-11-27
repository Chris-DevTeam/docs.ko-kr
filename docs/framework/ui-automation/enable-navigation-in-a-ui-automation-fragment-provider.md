---
title: UI 자동화 조각 공급자에서 탐색 사용
description: UI 자동화 공급자에서 조각 내에 있는 요소에 대해 탐색을 사용 하도록 설정 하는 방법을 보여 주는 예제를 읽습니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, enabling navigation in provider
- navigation, enabling in UI Automation provider
ms.assetid: 3cb6092a-58c9-4ca0-84a5-0e54d5d00a0d
ms.openlocfilehash: d8fb67a84b7cba84fe65cd2f87baa6549122d2a2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276505"
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a>UI 자동화 조각 공급자에서 탐색 사용

> [!NOTE]
> 이 설명서는 <xref:System.Windows.Automation> 네임스페이스에 정의된 관리되는 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 클래스를 사용하려는 .NET Framework 개발자를 위한 것입니다. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]에 대한 최신 정보는 [Windows 자동화 API: UI 자동화](/windows/win32/winauto/entry-uiauto-win32)를 참조하세요.  
  
 이 항목에는 UI 자동화 공급자에서 조각 내에 있는 요소에 대해 탐색을 사용 설정하는 방법을 보여주는 예제 코드가 포함되어 있습니다.  
  
## <a name="example"></a>예제  

 다음 예제 코드는 목록 내에 있는 목록 항목의 <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> 을 구현합니다. 부모 요소가 목록 상자 요소이고, 형제 요소는 목록 컬렉션의 다른 항목입니다. 메서드가 유효하지 않은 방향에 대해 `null` 을 반환합니다(Visual Basic의 경우`Nothing` ). 이 경우, 요소에 자식이 없기 때문에 <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> 및 <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>입니다.  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a>참고 항목

- [UI 자동화 공급자 개요](ui-automation-providers-overview.md)
- [서버 쪽 UI 자동화 공급자 구현](server-side-ui-automation-provider-implementation.md)
