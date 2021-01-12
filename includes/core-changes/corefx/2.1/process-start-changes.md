---
ms.openlocfilehash: dcc64fe651b219ff1416c0afcdb4c6d275160f4b
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97911558"
---
### <a name="change-in-default-value-of-useshellexecute"></a>UseShellExecute의 기본값 변경

<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>의 기본값은 .NET Core에서 `false`입니다. .NET Framework에서의 기본값은 `true`입니다.

#### <a name="change-description"></a>변경 내용 설명

<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> 사용을 통해 애플리케이션을 직접 실행할 수 있습니다. 예를 들어 `Process.Start("mspaint.exe")`와 같은 코드를 사용하면 그림판이 실행됩니다. <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>이 `true`로 설정된 경우 연결된 애플리케이션을 간접적으로 시작할 수도 있습니다. .NET Framework에서 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>의 기본값은 `true`입니다. 따라서 해당 편집기를 사용하여 *.txt* 과 연결한 경우 `Process.Start("mytextfile.txt")`와 같은 코드로 메모장이 시작됩니다. .NET Framework에서 간접적으로 앱을 시작하는 것을 방지하려면 명시적으로 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>을 `false`로 설정해야 합니다. .NET Core에서 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>의 기본값은 `false`입니다. 따라서 기본적으로 `Process.Start`를 호출할 때 연결된 애플리케이션이 시작되지 않습니다.

<xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>의 다음 속성은 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>가 `true`인 경우에만 작동합니다.

- <xref:System.Diagnostics.ProcessStartInfo.CreateNoWindow?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo.ErrorDialog?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo.Verb?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo.WindowStyle?displayProperty=nameWithType>.

이 변경 사항은 성능 사유로 인해 .NET Core에 도입되었습니다. 일반적으로 <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>은 애플리케이션을 직접 시작하는 데 사용됩니다. 앱을 직접 시작하는 경우 Windows 셸을 포함하지 않아도 되며 관련된 성능 비용도 발생하지 않습니다. 이 기본 사례를 더욱 빠르게 하도록 .NET Core는 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>의 기본값을 `false`로 변경합니다. 필요한 경우 느린 경로로 옵트인할 수 있습니다.

#### <a name="version-introduced"></a>도입된 버전

2.1

> [!NOTE]
> 이전 버전의 .NET Core에서 `UseShellExecute`는 Windows에 구현되지 않았습니다.

#### <a name="recommended-action"></a>권장 조치

앱이 이전 동작에 의존하는 경우 <xref:System.Diagnostics.ProcessStartInfo> 개체에서 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute>가 `true`로 설정된 상태에서 <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType>을 호출합니다.

#### <a name="category"></a>범주

핵심 .NET 라이브러리

#### <a name="affected-apis"></a>영향을 받는 API

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
