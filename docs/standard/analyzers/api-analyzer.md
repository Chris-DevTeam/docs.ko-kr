---
title: .NET API 분석기
description: .NET API 분석기가 사용되지 않는 API 및 플랫폼 호환성 문제를 발견하는 데 어떻게 도움이 되는지 알아봅니다.
author: oliag
ms.date: 02/20/2020
ms.openlocfilehash: 47ef2368692aee56ebd3db7803cbde7368d38049
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94819606"
---
# <a name="net-api-analyzer"></a>.NET API 분석기

.NET API 분석기는 여러 플랫폼에서 C# API에 대한 잠재적 호환성 위험을 검색하고 사용되지 않는 API에 대한 호출을 감지하는 Roslyn 분석기입니다. 모든 개발 단계의 모든 C# 개발자에게 유용할 수 있습니다.

API 분석기는 NuGet 패키지 [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/)로 제공됩니다. 이 패키지를 프로젝트에서 참조한 후에는 패키지가 코드를 자동으로 모니터링하고 문제가 있는 API 사용을 표시합니다. 전구를 클릭하여 가능한 수정 사항에 대한 제안을 확인할 수도 있습니다. 드롭다운 메뉴에는 경고를 표시하지 않은 옵션이 포함됩니다.

> [!NOTE]
> .NET API 분석기는 여전히 시험판 버전입니다.

## <a name="prerequisites"></a>사전 요구 사항

- Visual Studio 2017 이상 버전 또는 Mac용 Visual Studio(모든 버전).

## <a name="discover-deprecated-apis"></a>사용되지 않는 API 검색

### <a name="what-are-deprecated-apis"></a>사용되지 않는 API란 무엇인가요?

.NET 제품군은 고객의 요구 사항을 더 잘 해결하기 위해 지속적으로 업그레이드되는 대규모 제품 집합입니다. 일부 API를 더 이상 사용하지 않고 새 API를 교체하는 것은 자연스러운 일입니다. 더 나은 대체가 있는 경우 API는 사용되지 않는 것으로 간주합니다. API가 사용되지 않으며 사용되면 안 된다는 것을 알리는 한 가지 방법은 <xref:System.ObsoleteAttribute> 특성을 사용하여 표시하는 것입니다. 이 방법의 단점은 모든 사용되지 않는 API에 대한 진단 ID가 하나만 있다는 것입니다(C#의 경우 [CS0612](../../csharp/misc/cs0612.md)). 이는 다음을 의미합니다.

- 각 사례에 대한 전용 문서를 포함할 수는 없습니다.
- 특정 경고 범주를 표시하지 않을 수는 없습니다. 모든 경고를 표시하거나 아무것도 표시하지 않을 수는 없습니다.
- 사용자에게 새로운 사용 중단을 알리려면 참조된 어셈블리 또는 대상 패키지를 업데이트해야 합니다.

API 분석기는 개별 경고 표시를 제어할 수 있는 DE(사용 중단 오류)로 시작하는 API 관련 오류 코드를 사용합니다. 분석기가 식별하는 사용되지 않는 API는 [dotnet/platform-compat](https://github.com/dotnet/platform-compat) 리포지토리에서 정의됩니다.

### <a name="add-the-api-analyzer-to-your-project"></a>프로젝트에 API 분석기 추가

1. Visual Studio를 엽니다.
2. 분석기를 실행하려는 프로젝트를 엽니다.
3. **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **NuGet 패키지 관리** 를 선택합니다. (이 옵션은 **프로젝트** 메뉴에서도 사용 가능합니다.)
4. NuGet 패키지 관리자 탭에서
   1. 패키지 원본으로 "nuget.org"를 선택합니다.
   2. **찾아보기** 탭으로 이동합니다.
   3. **시험판 포함** 을 선택합니다.
   4. **Microsoft.DotNet.Analyzers.Compatibility** 를 검색합니다.
   5. 목록에서 해당 패키지를 선택합니다.
   6. **설치** 단추를 선택합니다.
   7. **변경 내용 미리 보기** 대화 상자에서 **확인** 단추를 선택한 다음, 나열된 패키지의 사용 조건에 동의하는 경우 **라이선스 승인** 대화 상자에서 **동의함** 단추를 선택합니다.

### <a name="use-the-api-analyzer"></a>API 분석기 사용

<xref:System.Net.WebClient>와 같은 사용되지 않는 API가 코드에서 사용되는 경우 API 분석기는 녹색 물결선으로 API를 강조 표시합니다. API 호출을 마우스로 가리키면 다음 예제와 같이 API 사용 중단에 대한 정보가 포함된 전구가 표시됩니다.

![왼쪽에 있는 녹색 물결선과 전구가 있는 WebClient API의 스크린샷](media/api-analyzer/green-squiggle.jpg)

다음 예제(`DE004`)와 같이 **오류 목록** 창에는 사용되지 않는 API별 고유 ID가 포함된 경고가 있습니다.

![경고 ID 및 설명을 표시하는 오류 목록 창의 스크린샷](media/api-analyzer/warnings-id-and-descriptions.jpg "경고가 포함된 오류 목록 창입니다.")

ID를 클릭하면 API가 사용되지 않는 이유에 대한 자세한 정보와 사용할 수 있는 대체 API에 대한 제안이 있는 웹 페이지로 이동합니다.

강조 표시된 멤버를 마우스 오른쪽 단추로 클릭하고 **\<diagnostic ID> 제거** 를 선택하여 모든 경고를 제거할 수 있습니다. 경고를 표시하지 않는 두 가지 방법이 있습니다.

- [로컬로(소스)](#suppress-warnings-locally)
- [전역으로(비표시 오류(Suppression) 파일)](#suppress-warnings-globally) - 권장됨

### <a name="suppress-warnings-locally"></a>로컬로 경고 표시 안 함

로컬로 경고를 제거하려면 경고를 제거할 멤버를 마우스 오른쪽 단추로 클릭한 다음, **빠른 작업 및 리팩터링** >  **‘진단 ID’\<diagnostic ID> 제거** > **소스** 를 선택합니다. [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) 경고 전처리기 지시문이 정의된 범위의 소스 코드에 추가됩니다. ![#pragma warning disable로 묶인 코드의 스크린샷](media/api-analyzer/suppress-in-source.jpg)

### <a name="suppress-warnings-globally"></a>전역으로 경고 표시 안 함

전역으로 경고를 제거하려면 경고를 제거할 멤버를 마우스 오른쪽 단추로 클릭한 다음, **빠른 작업 및 리팩터링** >  **‘진단 ID’\<diagnostic ID> 제거** > **비표시 오류(Suppression) 파일** 을 선택합니다.

![Visual Studio에서 경고를 제거하는 옵션을 보여 주는 마우스 오른쪽 단추 클릭 메뉴의 스크린샷](media/api-analyzer/suppress-in-sup-file.jpg)

*GlobalSuppressions.cs* 파일이 첫 번째 비표시 오류(Supression) 후에 프로젝트에 추가됩니다. 새 전역 비표시 오류(Supression)가 이 파일에 추가됩니다.

![솔루션 탐색기에 있는 GlobalSuppressions.cs 파일의 스크린샷](media/api-analyzer/suppression-file.jpg)

전역 비표시 오류(Supression)는 여러 프로젝트에서 API 사용의 일관성을 보장하는 권장 방법입니다.

## <a name="discover-cross-platform-issues"></a>플랫폼 간 문제 검색

> [!NOTE]
> .NET 5.0에서는 이 기능을 대체하는 [플랫폼 호환성 분석기](platform-compat-analyzer.md)를 도입했습니다. 플랫폼 호환성 분석기는 .NET SDK에 포함되어 있으며(별도로 설치할 필요 없음) 기본적으로 켜져 있습니다.

사용되지 않는 API와 비슷하게 분석기는 플랫폼 간이 아닌 모든 API를 식별합니다. 예를 들어 <xref:System.Console.WindowWidth?displayProperty=nameWithType>는 Windows에서 작동하지만 Linux 및 macOS에서는 작동하지 않습니다. 진단 ID는 **오류 목록** 창에 표시됩니다. 마우스 오른쪽 단추를 클릭하고 **빠른 작업 및 리팩터링** 을 선택하여 해당 경고를 표시하지 않을 수 있습니다. 예를 들어 두 개의 옵션(사용되지 않는 멤버를 계속 사용하고 경고를 표시하지 않음 또는 전혀 사용하지 않음)이 있는 사용 중단 사례와 달리, 여기서는 특정 플랫폼에 대한 코드만 개발하는 경우 코드를 실행할 계획이 없는 모든 다른 플랫폼에 대한 모든 경고를 표시하지 않을 수 있습니다. 이렇게 하려면 프로젝트 파일을 편집하고 무시할 모든 플랫폼을 나열하는 `PlatformCompatIgnore` 속성을 추가하면 됩니다. 허용되는 값은 `Linux`, `macOS` 및 `Windows`입니다.

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

코드가 여러 플랫폼을 대상으로 하고 이들 중 일부에서 지원되지 않는 API를 활용하려는 경우 코드의 해당 파트를 `if` 문으로 보호할 수 있습니다.

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

대상 프레임워크/운영 체제별로 조건부로 컴파일할 수도 있지만 현재는 해당 작업을 [수동으로](../frameworks.md#how-to-specify-a-target-framework) 수행해야 합니다.

## <a name="supported-diagnostics"></a>지원되는 진단

현재 분석기는 다음과 같은 경우를 처리합니다.

- <xref:System.PlatformNotSupportedException>(PC001)을 throw하는 .NET Standard API 사용.
- .NET Framework 4.6.1(PC002)에서 사용할 수 없는 .NET Standard API 사용.
- UWP(PC003)에 존재하지 않는 네이티브 API 사용
- Delegate.BeginInvoke 및 EndInvoke API(PC004) 사용.
- 사용되지 않음(DEXXXX)으로 표시된 API 사용.

## <a name="ci-machine"></a>CI 컴퓨터

이러한 모든 진단은 IDE뿐 아니라 명령줄에서도 CI 서버가 포함된 프로젝트 빌드의 일부로 사용할 수 있습니다.

## <a name="configuration"></a>Configuration

사용자는 진단을 처리하는 방법을 경고, 오류, 제안 또는 해제로 결정합니다. 예를 들어 설계자가 호환성 문제를 오류로 처리하도록 결정하면 일부 사용되지 않는 API에 대한 호출은 경고를 생성하지만 다른 API에 대한 호출은 제안만 생성합니다. 이 방법은 진단 ID 및 프로젝트별로 별도로 구성할 수 있습니다. **솔루션 탐색기** 에서 이를 수행하려면 프로젝트 아래의 **종속성** 노드로 이동합니다. 노드 **종속성** > **분석** > **Microsoft.DotNet.Analyzers.Compatibility** 를 확장합니다. 진단 ID를 마우스 오른쪽 단추로 클릭하고 **규칙 집합 심각도 설정** 을 선택한 다음, 원하는 옵션을 선택합니다.

![진단 및 규칙 집합 심각도가 있는 팝업 대화 상자를 보여 주는 솔루션 탐색기의 스크린샷](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a>참조

- [API 분석기 소개](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) 블로그 게시물.
- YouTube의 [API 분석기](https://youtu.be/eeBEahYXGd0) 데모 동영상.
- [플랫폼 호환성 분석기](platform-compat-analyzer.md)
