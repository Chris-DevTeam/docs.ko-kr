---
title: dotnet tool uninstall 명령
description: dotnet tool uninstall 명령은 머신에서 지정된 .NET 도구를 제거합니다.
ms.date: 02/14/2020
ms.openlocfilehash: 34dffde8f9c930327c6b42d1d89bb4f511959fb2
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634092"
---
# <a name="dotnet-tool-uninstall"></a>dotnet tool uninstall

**이 문서의 적용 대상:**  ✔️ .NET Core 2.1 SDK 이상 버전

## <a name="name"></a>이름

`dotnet tool uninstall` - 머신에서 지정된 [.NET 도구](global-tools.md)를 제거합니다.

## <a name="synopsis"></a>개요

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> -g|--global

dotnet tool uninstall <PACKAGE_NAME> --tool-path <PATH>

dotnet tool uninstall <PACKAGE_NAME>

dotnet tool uninstall -h|--help
```

## <a name="description"></a>설명

`dotnet tool uninstall` 명령은 머신에서 .NET 도구를 제거하는 방법을 제공합니다. 이 명령을 사용하려면 다음 옵션 중 하나를 지정합니다.

* 기본 위치에 설치된 전역 도구를 제거하려면 `--global` 옵션을 사용합니다.
* 사용자 지정 위치에 설치된 전역 도구를 제거하려면 `--tool-path` 옵션을 사용합니다.
* 로컬 도구를 제거하려면 `--global` 및 `--tool-path` 옵션을 생략합니다.

**로컬 도구는 .NET Core SDK 3.0부터 사용할 수 있습니다.**

## <a name="arguments"></a>인수

- **`PACKAGE_NAME`**

  제거할 .NET 도구를 포함하는 NuGet 패키지의 이름/ID입니다. [dotnet tool list](dotnet-tool-list.md) 명령을 사용하여 패키지 이름을 찾을 수 있습니다.

## <a name="options"></a>옵션

- **`-g|--global`**

  사용자 수준 설치에서 제거할 도구임을 지정합니다. `--tool-path` 옵션과 함께 사용할 수 없습니다. `--global` 및 `--tool-path` 옵션을 모두 생략하면 제거할 도구로 로컬 도구를 지정합니다.

- **`-h|--help`**

  명령에 대한 간단한 도움말을 출력합니다.

- **`--tool-path <PATH>`**

  도구를 제거할 위치를 지정합니다. PATH는 절대적이거나 상대적일 수 있습니다. `--global` 옵션과 함께 사용할 수 없습니다. `--global` 및 `--tool-path` 옵션을 모두 생략하면 제거할 도구로 로컬 도구를 지정합니다.

## <a name="examples"></a>예

- **`dotnet tool uninstall -g dotnetsay`**

  [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 전역 도구를 제거합니다.

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  특정 Windows 디렉터리에서 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 전역 도구를 제거합니다.

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  특정 Linux/macOS 디렉터리에서 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 전역 도구를 제거합니다.

- **`dotnet tool uninstall dotnetsay`**

  현재 디렉터리에서 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 로컬 도구를 제거합니다.

## <a name="see-also"></a>참조

- [.NET 도구](global-tools.md)
- [자습서: .NET CLI를 사용하여 .NET 전역 도구 설치 및 사용](global-tools-how-to-use.md)
- [자습서: .NET CLI를 사용하여 .NET 로컬 도구 설치 및 사용](local-tools-how-to-use.md)
