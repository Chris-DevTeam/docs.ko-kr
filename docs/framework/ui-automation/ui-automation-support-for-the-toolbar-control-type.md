---
title: ToolBar 컨트롤 형식에 대한 UI 자동화 지원
description: ToolBar 컨트롤 형식에 대 한 UI 자동화 지원에 대 한 정보를 가져옵니다. 필요한 트리 구조, 속성, 컨트롤 패턴 및 이벤트에 대해 알아봅니다.
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Toolbar
- UI Automation, Toolbar control type
- ToolBar control type
ms.assetid: 85152efd-f4c5-430c-8878-3371cc598616
ms.openlocfilehash: d365f020eb5dbca47231f4b1b2cb024991df331b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96240240"
---
# <a name="ui-automation-support-for-the-toolbar-control-type"></a>ToolBar 컨트롤 형식에 대한 UI 자동화 지원

> [!NOTE]
> 이 설명서는 <xref:System.Windows.Automation> 네임스페이스에 정의된 관리되는 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 클래스를 사용하려는 .NET Framework 개발자를 위한 것입니다. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]에 대한 최신 정보는 [Windows 자동화 API: UI 자동화](/windows/win32/winauto/entry-uiauto-win32)를 참조하세요.  
  
 이 항목에서는 ToolBar 컨트롤 형식에 대한 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 지원 정보를 제공합니다. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]에서, 컨트롤 형식은 <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> 속성을 사용하기 위해 컨트롤이 충족해야 하는 조건 집합입니다. 이 조건에는 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 트리 구조, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 속성 값, 컨트롤 패턴에 대한 특정 지침이 포함됩니다. 도구 모음 컨트롤을 통해 최종 사용자가 애플리케이션 내에 포함된 명령 및 도구를 활성화할 수 있습니다.  
  
 다음 섹션에서는 ToolBar 컨트롤 형식에 필요한 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 트리 구조, 속성, 컨트롤 패턴, 이벤트를 정의합니다. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]요구 사항은 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] , Win32 또는 Windows Forms 모든 도구 모음 컨트롤에 적용 됩니다.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>

## <a name="required-ui-automation-tree-structure"></a>필요한 UI 자동화 트리 구조  

 다음 표는 도구 모음 컨트롤과 관련된 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 트리의 컨트롤 뷰 및 콘텐츠 뷰를 보여주고 각 뷰에 포함될 수 있는 내용에 대해 설명합니다. 트리에 대 한 자세한 내용은 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [UI 자동화 트리 개요](ui-automation-tree-overview.md)를 참조 하세요.  
  
|컨트롤 뷰|콘텐츠 뷰|  
|------------------|------------------|  
|ToolBar<br /><br /> -다양 한 컨트롤 (0 개 이상)|ToolBar<br /><br /> -다양 한 컨트롤 (0 개 이상)|  
  
 도구 모음 컨트롤에는 하위 트리 내의 모든 컨트롤 형식이 포함될 수 있습니다. 단추, 콤보 상자, 분할 단추를 예로 들 수 있습니다.  
  
<a name="Required_UI_Automation_Properties"></a>

## <a name="required-ui-automation-properties"></a>필요한 UI 자동화 속성  

 다음 표에서는 값 또는 정의가 도구 모음 컨트롤과 특별히 관련된 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 속성을 나열하여 보여줍니다. 속성에 대 한 자세한 내용은 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [클라이언트에 대 한 UI 자동화 속성](ui-automation-properties-for-clients.md)을 참조 하세요.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 속성|값|참고|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|메모를 참조하세요.|이 속성의 값은 애플리케이션의 모든 컨트롤에서 고유해야 합니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|메모를 참조하세요.|전체 컨트롤이 포함된 가장 바깥쪽 사각형입니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|메모를 참조하세요.|경계 사각형이 없는 경우 지원됩니다. 경계 사각형 내의 일부 지점이 클릭 가능하지 않으며 특수화된 적중 테스트를 수행하는 경우 클릭 가능한 지점을 재정의하고 제공하세요.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|메모를 참조하세요.|컨트롤이 키보드 포커스를 받을 수 있으면 해당 컨트롤은 이 속성을 지원해야 합니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|개체|애플리케이션 내에서 둘 이상 사용되는 경우를 제외하고 도구 모음 컨트롤에 이름이 필요하지 않습니다. 도구 모음이 둘 이상 있는 경우, 각 도구 모음에 고유한 이름(예: 서식 또는 개요)이 있어야 합니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|도구 모음 컨트롤에는 레이블이 없습니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ToolBar|이 값은 모든 UI 프레임워크에 대해 동일합니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"tool bar"|ToolBar 컨트롤 형식에 해당하는 지역화된 문자열입니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|도구 모음 컨트롤이 항상 콘텐츠입니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|도구 모음 컨트롤이 항상 컨트롤이어야 합니다.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>

## <a name="required-ui-automation-control-patterns"></a>필요한 UI 자동화 컨트롤 패턴  

 다음 표에서는 도구 모음 컨트롤에서 지원되는 데 필요한 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 컨트롤 패턴을 나열하여 보여줍니다. 컨트롤 패턴에 대한 자세한 내용은 [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md)를 참조하세요.  
  
|컨트롤 패턴|지원|메모|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.ExpandCollapsePattern>|개체|도구 모음을 확장하고 축소하여 더 많은 항목을 표시하려면 이 패턴을 지원해야 합니다.|  
|<xref:System.Windows.Automation.DockPattern>|개체|도구 모음을 화면의 다른 부분에 도킹할 수 있는 경우 이 패턴을 지원해야 합니다.|  
|<xref:System.Windows.Automation.TransformPattern>|개체|도구 모음을 크기 조정, 회전 또는 이동할 수 있는 경우 이 패턴을 지원해야 합니다.|  
  
<a name="Required_UI_Automation_Events"></a>

## <a name="required-ui-automation-events"></a>필요한 UI 자동화 이벤트  

 다음 표에서는 모든 도구 모음 컨트롤에서 지원되는 데 필요한 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 이벤트를 나열하여 보여줍니다. 이벤트에 대한 자세한 내용은 [UI Automation Events Overview](ui-automation-events-overview.md)를 참조하세요.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 이벤트|지원|메모|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> 속성 변경 이벤트.|필수|없음|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> 속성 변경 이벤트.|필수|없음|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 속성 변경 이벤트.|필수|없음|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> 속성 변경 이벤트.|개체|없음|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|필수|없음|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|필수|없음|  
  
## <a name="see-also"></a>참고 항목

- <xref:System.Windows.Automation.ControlType.ToolBar>
- [UI 자동화 컨트롤 형식 개요](ui-automation-control-types-overview.md)
- [UI 자동화 개요](ui-automation-overview.md)
