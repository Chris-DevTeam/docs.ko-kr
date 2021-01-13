---
title: .NET Core RID(런타임 식별자) 카탈로그
description: RID(런타임 식별자)에 대한 정보와 .NET Core에서 RID 사용 방법에 대해 알아봅니다.
ms.date: 12/15/2020
ms.openlocfilehash: 6b45c42d626de41c7d67c66aac7dc31c51c36a22
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970670"
---
# <a name="net-core-rid-catalog"></a>.NET Core RID 카탈로그

RID는 *Runtime Identifier(런타임 식별자)* 의 약어입니다. RID 값은 애플리케이션을 실행하는 대상 플랫폼을 식별하는 데 사용됩니다.
NuGet 패키지에서 .NET 패키지의 플랫폼 관련 자산을 나타내는 데 사용됩니다. RID 값의 예로 `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, `osx.10.12-x64` 등을 들 수 있습니다.
기본 종속성이 있는 패키지의 경우 RID는 패키지를 복원할 수 있는 플랫폼을 지정합니다.

단일 RID는 프로젝트 파일의 `<RuntimeIdentifier>` 요소에 설정할 수 있습니다. 여러 RID는 프로젝트 파일의 `<RuntimeIdentifiers>` 요소에서 세미콜론으로 구분된 목록으로 정의할 수 있습니다. 다음과 같은 [.NET Core CLI 명령](./tools/index.md)을 사용하여 `--runtime` 옵션을 통해서도 사용됩니다.

- [dotnet build](./tools/dotnet-build.md)
- [dotnet clean](./tools/dotnet-clean.md)
- [dotnet pack](./tools/dotnet-pack.md)
- [dotnet publish](./tools/dotnet-publish.md)
- [dotnet restore](./tools/dotnet-restore.md)
- [dotnet run](./tools/dotnet-run.md)
- [dotnet store](./tools/dotnet-store.md)

구체적인 운영 체제를 나타내는 RID는 일반적으로 `[os].[version]-[architecture]-[additional qualifiers]`의 패턴을 따릅니다. 각각은 다음과 같습니다.

- `[os]` - 운영 체제/플랫폼 모니커입니다. 예: `ubuntu`.

- `[version]` - 점으로 구분된(`.`) 버전 번호 형식의 운영 체제 버전입니다. 예: `15.10`.

  - 버전은 마케팅 버전이어서는 **안 됩니다**. 마케팅 버전은 종종 다양한 플랫폼 API 노출 영역이 있는 운영 체제의 여러 개별 버전을 나타내기 때문입니다.

- `[architecture]` - 프로세서 아키텍처입니다. 예를 들면 `x86`, `x64`, `arm`, `arm64` 등입니다.

- `[additional qualifiers]` - 다른 플랫폼을 추가로 구분합니다. 예를 들어 `aot`을 참조하십시오.

## <a name="rid-graph"></a>RID 그래프

RID 그래프 또는 런타임 Fallback 그래프는 서로 호환되는 RID 목록입니다. RID는 [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) 패키지에 정의되어 있습니다. 지원되는 RID 및 RID 그래프 목록은 `dotnet/runtime` 리포지토리에 있는 [*runtime.json*](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) 파일에서 확인할 수 있습니다. 이 파일에서 기본 RID를 제외하고 모든 RID에 `"#import"` 문이 포함되어 있음을 알 수 있습니다. 이러한 문은 호환되는 RID를 나타냅니다.

NuGet에서 패키지를 복원할 때 지정된 런타임에 대한 정확한 일치를 찾으려고 합니다.
정확한 일치를 찾을 수 없는 경우 NuGet은 RID 그래프에 따라 가장 가까운 호환 시스템을 찾을 때까지 그래프를 다시 검색합니다.

다음 예제는 `osx.10.12-x64` RID의 실제 항목입니다.

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

위의 RID는 `osx.10.12-x64`가 `osx.10.11-x64`를 가져오도록 지정합니다. 따라서 NuGet에서 패키지를 복원할 때 패키지에서 `osx.10.12-x64`와 정확히 일치하는 값을 찾으려고 합니다. NuGet이 특정 런타임을 찾을 수 없는 경우 예를 들어 `osx.10.11-x64` 런타임을 지정하는 패키지를 복원할 수 있습니다.

다음 예제에서는 마찬가지로 *runtime.json* 파일에 정의된 약간 더 큰 RID 그래프를 보여 줍니다.

```
    win7-x64    win7-x86
       |   \   /    |
       |   win7     |
       |     |      |
    win-x64  |  win-x86
          \  |  /
            win
             |
            any
```

모든 RID는 결국 루트 `any` RID에 다시 매핑됩니다.

RID를 사용할 때는 RID에 대한 다음과 같은 몇 가지 고려 사항을 알고 있어야 합니다.

- 구성 요소 파트를 검색하기 위해 RID를 구문 분석하지 않습니다.
- RID를 프로그래밍 방식으로 빌드하지 마세요.
- 플랫폼에 대해 이미 정의된 RID를 사용합니다.
- RID는 구체적이어야 하므로 실제 RID 값에서 어느 것도 가정하지 마세요.

## <a name="using-rids"></a>RID 사용

RID를 사용할 수 있으려면 어떤 RID가 있는지 알아야 합니다. 새 값이 플랫폼에 정기적으로 추가됩니다.
완전한 최신 버전을 보려면 `dotnet/runtime` 리포지토리에서 [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) 파일을 확인하세요.

.NET Core 2.0 SDK에서는 이식 가능 RID라는 개념을 도입합니다. 이식 가능 RID란 RID 그래프에 새로 추가된 값으로서, 아직 특정 버전 또는 OS 배포에 연결되지 않았으며 .NET Core 2.0 이상을 사용할 때 권장됩니다. 대부분의 배포 RID는 이식 가능 RID에 매핑되므로 이 값은 여러 Linux 배포판을 다룰 때 매우 유용합니다.

다음 목록에서는 각 OS에 사용되는 일반적인 RID의 몇 가지 예를 보여줍니다.

## <a name="windows-rids"></a>Windows RID

자주 사용되는 값만 나열되어 있습니다. 완전한 최신 버전을 보려면 `dotnet/runtime` 리포지토리에서 [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) 파일을 확인하세요.

- 이식 가능(.NET Core 2.0 이상 버전)
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- Windows 7 / Windows Server 2008 R2
  - `win7-x64`
  - `win7-x86`
- Windows 8.1 / Windows Server 2012 R2
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- Windows 10 / Windows Server 2016
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

자세한 내용은 [.NET Core 종속성 및 요구 사항](./install/windows.md#dependencies)을 참조하세요.

## <a name="linux-rids"></a>Linux RID

자주 사용되는 값만 나열되어 있습니다. 완전한 최신 버전을 보려면 `dotnet/runtime` 리포지토리에서 [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) 파일을 확인하세요. 아래에 나열되지 않은 배포를 실행하는 디바이스의 경우, 이식 가능 RID 중 하나와 작동할 수 있습니다. 예를 들어, 여기에 나열되지 않은 Linux 배포를 실행하는 Raspberry Pi 디바이스는 `linux-arm`을 사용하여 대상으로 지정할 수 있습니다.

- 이식 가능
  - `linux-x64`(CentOS, Debian, Fedora, Ubuntu 및 파생 버전을 비롯한 대부분의 데스크톱 배포)
  - `linux-musl-x64` (Alpine Linux와 같이 [musl](https://wiki.musl-libc.org/projects-using-musl.html)을 사용하는 간단한 배포)
  - `linux-arm`(Raspberry Pi 모델 2+의 Raspbian과 같이 ARM에서 실행되는 Linux 배포)
  - `linux-arm64`(Raspberry Pi 모델 3+의 Ubuntu Server 64비트와 같이 64비트 ARM에서 실행되는 Linux 배포)
- Red Hat Enterprise Linux
  - `rhel-x64` (버전 6보다 상위 RHEL의 경우 `linux-x64`로 대체됨)
  - `rhel.6-x64`
- Tizen
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

자세한 내용은 [.NET Core 종속성 및 요구 사항](./install/linux.md)을 참조하세요.

## <a name="macos-rids"></a>macOS RID

macOS RID는 이전 "OSX" 브랜딩을 사용합니다. 자주 사용되는 값만 나열되어 있습니다. 완전한 최신 버전을 보려면 `dotnet/runtime` 리포지토리에서 [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) 파일을 확인하세요.

- 이식 가능
  - `osx-x64` (최소 OS 버전: macOS 10.12 Sierra)
- macOS 10.10 Yosemite
  - `osx.10.10-x64`
- macOS 10.11 El Capitan
  - `osx.10.11-x64`
- macOS 10.12 Sierra
  - `osx.10.12-x64`
- macOS 10.13 High Sierra
  - `osx.10.13-x64`
- macOS 10.14 Mojave
  - `osx.10.14-x64`
- macOS 10.15 Catalina
  - `osx.10.15-x64`
- macOS 11.01 Big Sur
  - `osx.11.0-x64`
  - `osx.11.0-arm64`

자세한 내용은 [.NET Core 종속성 및 요구 사항](./install/macos.md#dependencies)을 참조하세요.

## <a name="see-also"></a>참조

- [런타임 ID](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/readme.md)
