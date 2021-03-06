---
ms.openlocfilehash: 895d09e4ec39bd4a92ed1f4910da80474334d99b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497923"
---
### <a name="accessibility-improvements-in-wpf"></a>WPF의 접근성 개선 사항

#### <a name="details"></a>설명

**고대비 개선 사항**

- 이제 <xref:System.Windows.Controls.Expander> 컨트롤에 대한 포커스가 표시됩니다. 이전 버전의 .NET Framework에서는 그렇지 않았습니다.
- <xref:System.Windows.Controls.CheckBox> 및 <xref:System.Windows.Controls.RadioButton> 컨트롤의 텍스트를 선택하면 이전 .NET Framework 버전보다 보기 쉽습니다.
- 비활성화된 <xref:System.Windows.Controls.ComboBox>의 테두리는 이제 비활성화된 텍스트와 동일한 색입니다. 이전 버전의 .NET Framework에서는 그렇지 않았습니다.
- 이제 비활성화되고 포커스가 있는 단추는 올바른 테마 색을 사용합니다. 이전 버전의 .NET Framework에서는 그러지 않았습니다.
- 이제는 <xref:System.Windows.Controls.ComboBox> 컨트롤의 스타일이 <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey?displayProperty=nameWithType>으로 설정된 경우 드롭다운 단추가 표시됩니다. 이전 버전의 .NET Framework에서는 그렇지 않았습니다.
- 이제 <xref:System.Windows.Controls.DataGrid> 컨트롤의 정렬 표시기 화살표는 테마 색을 사용합니다. 이전 버전의 .NET Framework에서는 그러지 않았습니다.
- 이제 마우스를 위에 가져가면 기본 하이퍼링크 스타일이 올바른 테마 색으로 변경됩니다. 이전 버전의 .NET Framework에서는 그러지 않았습니다.
- 이제 라디오 단추에서 바로 가기 포커스가 표시됩니다. 이전 버전의 .NET Framework에서는 그렇지 않았습니다.
- 이제 <xref:System.Windows.Controls.DataGrid> 컨트롤의 확인란 열은 바로 가기 포커스 피드백에 예상되는 색을 사용합니다. 이전 버전의 .NET Framework에서는 그러지 않았습니다.
- 이제 바로 가기 포커스 시각적 개체가 <xref:System.Windows.Controls.ComboBox> 및 <xref:System.Windows.Controls.ListBox> 컨트롤에 표시됩니다. 이전 버전의 .NET Framework에서는 그렇지 않았습니다.

**화면 읽기 프로그램 상호 작용 개선 사항**

- 이제 <xref:System.Windows.Controls.Expander> 컨트롤은 화면 읽기 프로그램에서 그룹(확장/축소)으로 올바르게 추가됩니다.
- 이제 <xref:System.Windows.Controls.DataGridCell> 컨트롤은 화면 읽기 프로그램에서 데이터 그리드(지역화됨)으로 올바르게 추가됩니다.
- 이제 화면 읽기 프로그램이 편집 가능한 <xref:System.Windows.Controls.ComboBox>의 이름을 추가합니다.
- <xref:System.Windows.Controls.PasswordBox> 컨트롤은 더 이상 화면 읽기 프로그램에서 “보기의 항목 없음”으로 추가되지 않습니다.

**LiveRegion 지원**

내레이터와 같은 화면 판독기는 현재 포커스가 있는 UI 요소를 설명하는 애플리케이션의 UI(사용자 인터페이스)를 사용자가 이해하는 데 도움을 줍니다. 그러나 화면에서 UI 요소가 변경되고 포커스가 없는 경우 사용자는 알림을 받지 못하고 중요한 정보를 놓칠 수 있습니다. LiveRegions는 이 문제를 해결해야 합니다. 개발자는 화면 판독기 또는 다른 [UI Automation](~/docs/framework/ui-automation/ui-automation-overview.md) 클라이언트에게 UI 요소에 중요한 변경 내용이 만들어졌음을 알리는 데 사용할 수 있습니다. 화면 판독기는 사용자에게 이 변경 내용을 알리는 방법 및 시점을 결정할 수 있습니다. 또한 LiveSetting 속성을 통해 UI에 대한 변경 내용을 사용자에게 알리는 것이 얼마나 중요한지 화면 읽기 프로그램에 알릴 수 있습니다.

#### <a name="suggestion"></a>제안 해결 방법

**이 변경 내용을 옵트인 또는 옵트아웃하는 방법**

애플리케이션이 이러한 변경의 이점을 활용하도록 하기 위해 .NET Framework 4.7.1 이상에서 실행해야 합니다. 애플리케이션은 다음과 같은 방법으로 이러한 변경의 이점을 활용할 수 있습니다.

- .NET Framework 4.7.1을 대상으로 지정합니다. 이는 권장되는 방법입니다. 이러한 서비스 효율성 변경 내용은 .NET Framework 4.7.1 이상을 대상으로 하는 WPF 애플리케이션에서 기본적으로 활성화됩니다.
- 다음 예제와 같이 app config 파일의 `<runtime>` 섹션에 다음 [AppContext 스위치](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)를 추가하고 이를 `false`로 설정하여 레거시 접근성 동작을 옵트아웃합니다.

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
    </startup>
    <runtime>
      <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false'  -->
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
    </runtime>
  </configuration>
  ```

.NET Framework 4.7.1 이상을 대상으로 하고 레거시 접근성 동작을 유지하려는 애플리케이션은 이 AppContext 스위치를 `true`로 명확하게 설정하여 레거시 접근성 기능 사용을 옵트인할 수 있습니다.
UI 자동화 개요는 [UI Automation 개요](~/docs/framework/ui-automation/ui-automation-overview.md)를 참조하세요.

| 이름    | 값       |
|:--------|:------------|
| Scope   | 주요함       |
| 버전 | 4.7.1       |
| 형식    | 대상 변경 |

#### <a name="affected-apis"></a>영향을 받는 API

- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting(System.Windows.DependencyObject,System.Windows.Automation.AutomationLiveSetting)?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting(System.Windows.DependencyObject)?displayProperty=nameWithType>
- <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore?displayProperty=nameWithType>
