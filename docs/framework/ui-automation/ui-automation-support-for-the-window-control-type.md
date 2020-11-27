---
title: Window 컨트롤 형식에 대한 UI 자동화 지원
description: Window 컨트롤 형식에 대 한 UI 자동화 지원에 대 한 정보를 가져옵니다. 필요한 트리 구조, 속성, 컨트롤 패턴 및 이벤트에 대해 알아봅니다.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Window control type
- Window control type
- control types, Window
ms.assetid: 53be78a6-cdcc-4af3-a464-5927d19c54e8
ms.openlocfilehash: 675f9cfdf1fb2be8519a671e2fd798520412296d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281271"
---
# <a name="ui-automation-support-for-the-window-control-type"></a>Window 컨트롤 형식에 대한 UI 자동화 지원

> [!NOTE]
> 이 설명서는 <xref:System.Windows.Automation> 네임스페이스에 정의된 관리되는 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 클래스를 사용하려는 .NET Framework 개발자를 위한 것입니다. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]에 대한 최신 정보는 [Windows 자동화 API: UI 자동화](/windows/win32/winauto/entry-uiauto-win32)를 참조하세요.  
  
 이 항목에서는 Window 컨트롤 형식에 대한 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 지원 정보를 제공합니다. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]에서, 컨트롤 형식은 <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> 속성을 사용하기 위해 컨트롤이 충족해야 하는 조건 집합입니다. 이 조건에는 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 트리 구조, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 속성 값, 컨트롤 패턴에 대한 특정 지침이 포함됩니다.  
  
 창 컨트롤은 제목 표시줄, 클라이언트 및 다른 개체와 같은 자식 개체를 포함하는 창 프레임으로 구성되어 있습니다.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]다음 섹션의 요구 사항은 Window 컨트롤 형식을 구현 하는 모든 컨트롤 ( [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] 예를 들어, Win32 또는 Windows Forms에 적용 됩니다.  
  
## <a name="required-ui-automation-tree-structure"></a>필요한 UI 자동화 트리 구조  

 다음 표는 창 컨트롤과 관련된 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 트리의 컨트롤 뷰 및 콘텐츠 뷰를 보여주고 각 뷰에 포함될 수 있는 내용에 대해 설명합니다. 트리에 대 한 자세한 내용은 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [UI 자동화 트리 개요](ui-automation-tree-overview.md)를 참조 하세요.  
  
|컨트롤 뷰|콘텐츠 뷰|  
|------------------|------------------|  
|시간 범위|시간 범위|  
  
## <a name="required-ui-automation-properties"></a>필요한 UI 자동화 속성  

 다음 표에서는 값 또는 정의가 창 컨트롤과 특별히 관련된 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 속성을 나열하여 보여줍니다. 속성에 대 한 자세한 내용은 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [클라이언트에 대 한 UI 자동화 속성](ui-automation-properties-for-clients.md)을 참조 하세요.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 속성|값|참고|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|메모를 참조하세요.|이 속성의 값은 애플리케이션의 모든 컨트롤에서 고유해야 합니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|메모를 참조하세요.|전체 컨트롤이 포함된 가장 바깥쪽 사각형입니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|메모를 참조하세요.|창 컨트롤에는 창을 선택하거나 선택 취소할 수 있는 클릭 가능한 지점이 있어야 합니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|시간 범위|이 값은 모든 UI 프레임워크에 대해 동일합니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|창 컨트롤은 항상 콘텐츠여야 합니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|창 컨트롤 항상 컨트롤이어야 합니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|메모를 참조하세요.|컨트롤이 키보드 포커스를 받을 수 있으면 해당 컨트롤은 이 속성을 지원해야 합니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`null`|창 컨트롤에는 정적 창 레이블이 없습니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"window"|Window 컨트롤 형식에 해당하는 지역화된 문자열입니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|메모를 참조하세요.|창 컨트롤에는 사용자가 항목에 대해 가장 의미 있는 식별자로 연결할 사항과 관련된 기본 창 요소가 항상 포함됩니다.|  
  
## <a name="required-ui-automation-control-patterns"></a>필요한 UI 자동화 컨트롤 패턴  

 다음 표에서는 창 컨트롤에서 지원되는 데 필요한 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 컨트롤 패턴을 나열하여 보여줍니다. 컨트롤 패턴에 대한 자세한 내용은 [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md)를 참조하세요.  
  
|컨트롤 패턴|지원|메모|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider>|조건부|창에 도킹될 수 있는 기능이 있으면 지원되어야 합니다.|  
|<xref:System.Windows.Automation.Provider.ITransformProvider>|필수|화면에서 창을 이동, 크기 조정 또는 회전할 수 있습니다.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider>|필수|창에 대한 특정 작업을 수행합니다.|  
  
## <a name="required-ui-automation-events"></a>필요한 UI 자동화 이벤트  

 다음 표에서는 모든 창 컨트롤에서 지원되는 데 필요한 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 이벤트를 나열하여 보여줍니다. 이벤트에 대한 자세한 내용은 [UI Automation Events Overview](ui-automation-events-overview.md)를 참조하세요.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 이벤트|지원|메모|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AsyncContentLoadedEvent>|필수|없음|  
|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|필수|없음|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> 속성 변경 이벤트.|필수|없음|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 속성 변경 이벤트.|필수|없음|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> 속성 변경 이벤트.|필수|없음|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|필수|없음|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> 속성 변경 이벤트.|필수|없음|  
|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|필수|없음|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> 속성 변경 이벤트.|개체|없음|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> 속성 변경 이벤트.|개체|없음|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> 속성 변경 이벤트.|개체|없음|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> 속성 변경 이벤트.|개체|없음|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> 속성 변경 이벤트.|개체|없음|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> 속성 변경 이벤트.|개체|없음|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent>|필수|없음|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent>|필수|없음|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowVisualStateProperty> 속성 변경 이벤트.|개체|없음|  
  
## <a name="see-also"></a>참고 항목

- <xref:System.Windows.Automation.ControlType.Window>
- [UI 자동화 컨트롤 형식 개요](ui-automation-control-types-overview.md)
- [UI 자동화 개요](ui-automation-overview.md)
