---
title: dotnet tool install 명령
description: dotnet tool install 명령은 머신에 지정된 .NET 도구를 설치합니다.
ms.date: 02/14/2020
ms.openlocfilehash: b04e7fd24edce5d5da67cdd83fbea797118689b4
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206483"
---
# <a name="dotnet-tool-install"></a>dotnet tool install

**이 문서의 적용 대상:**  ✔️ .NET Core 2.1 SDK 이상 버전

## <a name="name"></a>이름

`dotnet tool install` - 머신에 지정된 [.NET 도구](global-tools.md)를 설치합니다.

## <a name="synopsis"></a>개요

```dotnetcli
dotnet tool install <PACKAGE_NAME> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install -h|--help
```

## <a name="description"></a>설명

`dotnet tool install` 명령은 머신에 .NET 도구를 설치하는 방법을 제공합니다. 이 명령을 사용하려면 다음 설치 옵션 중 하나를 지정합니다.

* 전역 도구를 기본 위치에 설치하려면 `--global` 옵션을 사용합니다.
* 전역 도구를 사용자 지정 위치에 설치하려면 `--tool-path` 옵션을 사용합니다.
* 로컬 도구를 설치하려면 `--global` 및 `--tool-path` 옵션을 생략합니다.

**로컬 도구는 .NET Core SDK 3.0부터 사용할 수 있습니다.**

`-g` 또는 `--global` 옵션을 지정하면 전역 도구는 기본적으로 다음 디렉터리에 설치됩니다.

| OS          | 경로                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

로컬 도구는 현재 디렉터리 아래의 *.config* 디렉터리에 있는 *dotnet-tools.json* 파일에 추가됩니다. 매니페스트 파일이 아직 없는 경우 다음 명령을 실행하여 만듭니다.

```dotnetcli
dotnet new tool-manifest
```

자세한 내용은 [로컬 도구 설치](global-tools.md#install-a-local-tool)를 참조하세요.

## <a name="arguments"></a>인수

- **`PACKAGE_NAME`**

  설치할 .NET 도구를 포함하는 NuGet 패키지의 이름/ID입니다.

## <a name="options"></a>옵션

- **`--add-source <SOURCE>`**

  설치 중에 사용할 추가 NuGet 패키지 원본을 추가합니다. 피드는 우선 순위에 따라 순차적으로 액세스하는 것이 아니라 병렬로 액세스합니다. 동일한 패키지와 버전이 여러 피드에 있는 경우 가장 빠른 피드가 적용됩니다. 자세한 내용은 [NuGet 패키지를 설치하면 어떻게 되나요?](/nuget/concepts/package-installation-process)를 참조하세요.

- **`--configfile <FILE>`**

  사용할 NuGet 구성(*nuget.config*) 파일입니다.

- **`--framework <FRAMEWORK>`**

  도구를 설치할 [대상 프레임워크](../../standard/frameworks.md)를 지정합니다. 기본적으로 .NET SDK는 가장 적합한 대상 프레임워크를 선택하려고 합니다.

- **`-g|--global`**

  사용자 전체 설치임을 지정합니다. `--tool-path` 옵션과 함께 사용할 수 없습니다. `--global` 및 `--tool-path` 옵션을 모두 생략하면 로컬 도구 설치가 지정됩니다.

- **`-h|--help`**

  명령에 대한 간단한 도움말을 출력합니다.

- **`--tool-path <PATH>`**

  전역 도구를 설치할 위치를 지정합니다. 경로는 절대 또는 상대 경로일 수 있습니다. 경로가 존재하지 않는 경우 이 명령은 해당 경로를 만들려고 합니다. `--global` 및 `--tool-path` 옵션을 모두 생략하면 로컬 도구 설치가 지정됩니다.

- **`-v|--verbosity <LEVEL>`**

  명령의 세부 정보 표시 수준을 설정합니다. 허용되는 값은 `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, `diag[nostic]`입니다.

- **`--version <VERSION_NUMBER>`**

  설치할 도구의 버전입니다. 기본적으로 안정적인 최신 버전이 설치됩니다. 도구의 미리 보기 또는 이전 버전을 설치할 경우 이 옵션을 사용합니다.

## <a name="examples"></a>예

- **`dotnet tool install -g dotnetsay`**

  [dotnetsay](https://www.nuget.org/packages/dotnetsay/)를 기본 위치에 전역 도구로 설치합니다.

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  [dotnetsay](https://www.nuget.org/packages/dotnetsay/)를 특정 Windows 디렉터리에 전역 도구로 설치합니다.

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  [dotnetsay](https://www.nuget.org/packages/dotnetsay/)를 특정 Linux/macOS 디렉터리에 전역 도구로 설치합니다.

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  [dotnetsay](https://www.nuget.org/packages/dotnetsay/)의 버전 2.0.0을 전역 도구로 설치합니다.

- **`dotnet tool install dotnetsay`**

  [dotnetsay](https://www.nuget.org/packages/dotnetsay/)를 현재 디렉터리용 로컬 도구로 설치합니다.

## <a name="see-also"></a>참조

- [.NET 도구](global-tools.md)
- [자습서: .NET CLI를 사용하여 .NET 전역 도구 설치 및 사용](global-tools-how-to-use.md)
- [자습서: .NET CLI를 사용하여 .NET 로컬 도구 설치 및 사용](local-tools-how-to-use.md)
