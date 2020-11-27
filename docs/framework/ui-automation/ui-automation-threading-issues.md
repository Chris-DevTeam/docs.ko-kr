---
title: UI 자동화 스레딩 문제
description: UI 자동화 스레딩 문제에 대해 읽어 보세요. 예를 들어 클라이언트 응용 프로그램이 UI 스레드에서 자체 UI와 상호 작용 하려고 하면 충돌이 발생할 수 있습니다.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
ms.openlocfilehash: 1f17336e6baa2e2baf4cd37a5b39bed913bd3bd2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258649"
---
# <a name="ui-automation-threading-issues"></a>UI 자동화 스레딩 문제

> [!NOTE]
> 이 설명서는 <xref:System.Windows.Automation> 네임스페이스에 정의된 관리되는 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 클래스를 사용하려는 .NET Framework 개발자를 위한 것입니다. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]에 대한 최신 정보는 [Windows 자동화 API: UI 자동화](/windows/win32/winauto/entry-uiauto-win32)를 참조하세요.  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 가 Windows 메시지를 사용하는 방식 때문에 클라이언트 애플리케이션이 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 스레드에서 자체 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 와 상호 작용을 시도할 때 충돌이 발생할 수 있습니다. 이러한 충돌로 인해 성능이 매우 저하되거나 애플리케이션의 응답이 중지될 수 있습니다.  
  
 클라이언트 애플리케이션이 데스크톱의 모든 요소와 상호 작용하도록 구성된 경우 자체 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]를 포함하여 별도 스레드의 모든 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 를 호출해야 합니다. 여기에는 요소 찾기(예: <xref:System.Windows.Automation.TreeWalker> 또는 <xref:System.Windows.Automation.AutomationElement.FindAll%2A> 메서드를 사용하여 찾기)와 컨트롤 패턴 사용이 포함됩니다.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 을 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 이벤트 처리기 내에서 호출하는 것이 안전합니다. 이 이벤트 처리기는 항상 비[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 스레드에서 호출되기 때문입니다. 하지만 클라이언트 애플리케이션의 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]에서 발생할 수 있는 이벤트를 구독할 때는 <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>또는 관련 메서드를 비[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 스레드에서 호출해야 합니다. 동일한 스레드에서 이벤트 처리기를 제거합니다.
