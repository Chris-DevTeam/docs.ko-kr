---
ms.openlocfilehash: c01705002ad87a12389078d75ffd0f91f934d36e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497949"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>텍스트 상자가 비활성일 때 WPF TextBox가 선택한 텍스트가 다른 색으로 표시됩니다.

#### <a name="details"></a>설명

.NET Framework 4.5에서 WPF 텍스트 상자 컨트롤이 비활성화될 때(포커스가 없음) 상자 내의 선택된 텍스트는 컨트롤이 활성일 때와 다른 색을 표시합니다.

#### <a name="suggestion"></a>제안 해결 방법

<xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> 속성을 <code>false</code>로 설정하여 이전(.NET Framework 4.0) 동작을 복원할 수 있습니다.

| 이름    | 값       |
|:--------|:------------|
| Scope   |Microsoft Edge|
|버전|4.5|
|형식|런타임|

#### <a name="affected-apis"></a>영향을 받는 API

- <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Windows.Controls.TextBox`

-->
