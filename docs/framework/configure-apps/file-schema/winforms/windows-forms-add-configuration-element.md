---
description: '자세한 정보: 구성 요소 Windows Forms 추가'
title: 구성 요소 Windows Forms 추가
ms.date: 04/07/2017
helpviewer_keywords:
- Windows Forms Add configuration element
- configuring Windows Forms applications
ms.assetid: 3e3e04de-99d1-4658-b716-44cb669d9589
ms.openlocfilehash: a0db81e0dd86f9ee6f2a47183100645ece78280c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773259"
---
# <a name="windows-forms-add-configuration-element"></a>구성 요소 Windows Forms 추가

`<add>`요소는 Windows Form 앱이 .NET Framework 4.7 이상에서 Windows Forms 앱에 추가 된 기능을 지원 하는지 여부를 지정 하는 미리 정의 된 키를 추가 합니다.

## <a name="syntax"></a>구문

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="key-name" value="key-value" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

| attribute | 설명 |
| --------- | ----------- |
| `key`     | 필수 특성입니다. 특정 Windows Forms 사용자 지정 가능 기능에 해당 하는 미리 정의 된 키 이름입니다. |
| `value`   | 필수 특성입니다. `key`에 할당할 값입니다. |

### <a name="key-attribute-names-and-associated-values"></a>`key` 특성 이름 및 관련 값

| `key` 이름 | 값 | 설명 |
| ---------- | ------ | ----------- |
| "AnchorLayout.DisableSinglePassControlScaling" | "true" &#124; "false"입니다. | 앵커 된 컨트롤이 단일 패스에서 확장 되는지 여부를 나타냅니다. 단일 패스 크기 조정을 사용 하지 않도록 설정 하려면 "true"로 설정 합니다. 그렇지 않으면 false입니다. 자세한 내용은 [설명](#remarks) 의 "단일 패스 크기 조정" 섹션을 참조 하세요. |
| "DpiAwareness" | "PerMonitorV2" &#124; "false" | 응용 프로그램이 DPI를 인식 하는지 여부를 나타냅니다. Dpi 인식을 지원 하려면 키를 "PerMonitorV2"로 설정 합니다. 그렇지 않으면 "false"로 설정 합니다. DPI 인식은 옵트인 (opt in) 기능입니다. Windows Forms의 높은 DPI 지원 기능을 활용 하려면 해당 값을 "PerMonitorV2"로 설정 해야 합니다. 자세한 내용은 [설명](#remarks) 부분을 참조 하세요. |
| "CheckedListBox" | "true" &#124; "false"입니다. | <xref:System.Windows.Forms.CheckedListBox>컨트롤에서 .NET Framework 4.7에 도입 된 크기 조정 및 레이아웃 향상 기능을 사용 하는지 여부를 나타냅니다. 크기 조정 및 레이아웃 개선을 옵트아웃 (opt in) 하려면 "true"로 설정 합니다. 그렇지 않으면 "false"입니다. |
| "DataGridView. DisableHighDpiImprovements 된 기능" | "true" &#124; "false"입니다. | <xref:System.Windows.Forms.DataGridView>.NET Framework 4.7에 컨트롤 크기 조정 및 레이아웃 향상 기능이 도입 되었는지 여부를 나타냅니다. DPI 인식에서 옵트아웃 (opt out) 하려면 "true"로 설정 합니다. 그렇지 않으면 "false"입니다. |
| "DisableDpiChangedMessageHandling" | "true" &#124; "false"입니다. | DPI 크기 조정 변경과 관련 된 메시지 수신을 옵트아웃 하려면 "true"로 설정 합니다. 그렇지 않으면 "false"입니다. 자세한 내용은 [설명](#remarks) 부분을 참조 하세요. |
| EnableWindowsFormsHighDpiAutoResizing | "true" &#124; "false"입니다. | DPI 크기 조정 변경으로 인해 Windows Forms 응용 프로그램의 크기가 자동으로 조정 되는지 여부를 나타냅니다. 자동 크기 조정을 사용 하도록 설정 하려면 "true"로 설정 합니다. 그렇지 않으면 false입니다. |
| "DisableSinglePassControlScaling" | "true" &#124; "false"입니다. | <xref:System.Windows.Forms.Form>가 단일 패스로 확장 되는지 여부를 나타냅니다. 단일 패스 크기 조정을 사용 하지 않도록 설정 하려면 "true"로 설정 합니다. 그렇지 않으면 false입니다. 자세한 내용은 [설명](#remarks) 의 "단일 패스 크기 조정" 섹션을 참조 하세요. |
| "MonthCalendar. DisableSinglePassControlScaling" | "true" &#124; "false"입니다. | <xref:System.Windows.Forms.MonthCalendar>단일 패스에서 컨트롤의 크기를 조정할지 여부를 나타냅니다. 단일 패스 크기 조정을 사용 하지 않도록 설정 하려면 "true"로 설정 합니다. 그렇지 않으면 false입니다. 자세한 내용은 [설명](#remarks) 의 "단일 패스 크기 조정" 섹션을 참조 하세요. |
| "Toolstrip. DisableHighDpiImprovements" | "true" &#124; "false"입니다. | <xref:System.Windows.Forms.ToolStrip>컨트롤에서 .NET Framework 4.7에 도입 된 크기 조정 및 레이아웃 향상 기능을 사용 하는지 여부를 나타냅니다. DPI 인식에서 옵트아웃 (opt out) 하려면 "true"로 설정 합니다. 그렇지 않으면 "false"입니다. |

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

| 요소 | 설명 |
| ------- | ----------- |
| [`<System.Windows.Forms.ApplicationConfigurationSection>`](index.md) | 새 Windows Forms 응용 프로그램 기능에 대 한 지원을 구성 합니다. |

## <a name="remarks"></a>설명

.NET Framework 4.7부터는 `<System.Windows.Forms.ApplicationConfigurationSection>` 요소를 사용하여 Windows Forms 애플리케이션을 구성해 최신 .NET Framework 릴리스에 추가된 기능을 활용할 수 있습니다.

`<System.Windows.Forms.ApplicationConfigurationSection>`요소를 사용 하면 `<add>` 각각 특정 구성 설정을 정의 하는 하나 이상의 자식 요소를 추가할 수 있습니다.

Windows Forms 높은 DPI 지원에 대 한 개요는 [Windows Forms에서 높은 Dpi 지원](/dotnet/desktop/winforms/high-dpi-support-in-windows-forms)을 참조 하세요.

### <a name="dpiawareness"></a>DpiAwareness

Windows 10 크리에이터 Edition 이상에서 실행 되는 Windows 버전에서 실행 되는 Windows Forms 앱과 .NET Framework 4.7부터 시작 하는 .NET Framework의 대상 버전은 .NET Framework 4.7에 도입 된 높은 DPI 향상 기능을 활용 하도록 구성할 수 있습니다. 여기에는 다음이 포함됩니다.

- 사용자가 Windows Forms 응용 프로그램이 시작 된 후 DPI 또는 배율 인수를 변경 하는 동적 DPI 시나리오에 대 한 지원.

- 컨트롤 및 컨트롤과 같은 여러 Windows Forms 컨트롤의 크기 조정 및 레이아웃이 개선 <xref:System.Windows.Forms.MonthCalendar> <xref:System.Windows.Forms.CheckedListBox> 되었습니다.

높은 DPI 인식은 옵트인 (opt in) 기능입니다. 기본적으로의 값 `DpiAwareness` 은 `false` 입니다. 응용 프로그램 구성 파일에서이 키의 값을로 설정 하 여 Windows Forms ' DPI 인식 지원을 옵트인 (opt in) 할 수 있습니다 `PerMonitorV2` . DPI 인식을 사용 하는 경우 모든 개별 DPI 기능도 사용할 수 있습니다. 여기에는 다음이 포함됩니다.

- 키로 제어 되는 DPI 변경 메시지 `DisableDpiChangedMessageHandling` 입니다.

- 키로 제어 되는 동적 DPI 지원 `EnableWindowsFormsHighDpiAutoResizing`

- `Form.DisableSinglePassControlScaling`개별 컨트롤에 대해 <xref:System.Windows.Forms.Form> , 고정 된 `AnchorLayout.DisableSinglePassControlScaling` 컨트롤의 키 및 `MonthCalendar.DisableSinglePassControlScaling` 컨트롤의 키 <xref:System.Windows.Forms.MonthCalendar> 로 제어 되는 단일 패스 컨트롤 크기 조정

- 컨트롤의 키, 컨트롤에 대 한 키 `CheckListBox.DisableHighDpiImprovements` <xref:System.Windows.Forms.CheckedListBox> `DataGridView.DisableHighDpiImprovements` <xref:System.Windows.Forms.DataGridView> 및 `Toolstrip.DisableHighDpiImprovements` <xref:System.Windows.Forms.ToolStrip> 컨트롤의 키로 제어 되는 높은 DPI 크기 조정 및 레이아웃 개선

로 설정 하 여 제공 하는 단일 기본 옵트인 `DpiAwareness` 설정은 `PerMonitorV2` 일반적으로 새 Windows Forms 응용 프로그램에 적합 합니다. 그러나 해당 하는 키를 응용 프로그램 구성 파일에 추가 하 여 개별 높은 DPI의 향상 된 기능을 옵트아웃 (opt out) 할 수 있습니다. 예를 들어 동적 DPI 지원을 제외 하 고 모든 새 DPI 기능을 활용 하려면 응용 프로그램 구성 파일에 다음을 추가 합니다.

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
   <add key="DpiAwareness" value="PerMonitorV2" />
   <!-- Disable dynamic DPI support -->
   <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

일반적으로 프로그래밍 방식으로 처리 하도록 선택 했기 때문에 특정 기능을 옵트아웃 (opt out) 할 수 있습니다.

Windows Forms 응용 프로그램에서 높은 DPI 지원을 활용 하는 방법에 대 한 자세한 내용은 [Windows Forms의 높은 Dpi 지원](/dotnet/desktop/winforms/high-dpi-support-in-windows-forms)을 참조 하세요.

### <a name="disabledpichangedmessagehandling"></a>DisableDpiChangedMessageHandling

.NET Framework 4.7부터 Windows Forms 컨트롤은 DPI 크기 조정의 변경과 관련 된 많은 이벤트를 발생 시킵니다. 여기에는 <xref:System.Windows.Forms.Control.DpiChangedAfterParent> , <xref:System.Windows.Forms.Control.DpiChangedBeforeParent> 및 <xref:System.Windows.Forms.Form.DpiChanged> 이벤트가 포함 됩니다. 키의 값은 `DisableDpiChangedMessageHandling` Windows Forms 응용 프로그램에서 이러한 이벤트가 발생 하는지 여부를 결정 합니다.

### <a name="single-pass-scaling"></a>단일 패스 크기 조정

단일 또는 다중 패스 배율은 사용자 인터페이스의 인식 되는 응답성과 크기가 조정 될 때 사용자 인터페이스 요소의 시각적 모양에 영향을 미칩니다. .NET Framework 4.7부터 Windows Forms는 단일 패스 크기 조정을 사용 합니다. 이전 버전의 .NET Framework에서는 여러 패스를 통해 크기 조정을 수행 했습니다 .이로 인해 일부 컨트롤의 크기가 필요 이상으로 조정 되었습니다. 앱이 이전 동작에 종속 되는 경우에만 단일 패스 크기 조정을 사용 하지 않도록 설정 해야 합니다.

## <a name="see-also"></a>참고 항목

- [Windows Forms 구성 섹션](index.md)
- [Windows Forms의 높은 DPI 지원](/dotnet/desktop/winforms/high-dpi-support-in-windows-forms)
