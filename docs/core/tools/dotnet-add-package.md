---
title: dotnet add package 명령
description: ‘dotnet add package’ 명령은 NuGet 패키지 참조를 프로젝트에 추가하는 편리한 옵션을 제공합니다.
ms.date: 11/11/2020
ms.openlocfilehash: 10373b3b69c669323674b192d54cd277a5828f24
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94556877"
---
# <a name="dotnet-add-package"></a>dotnet add package

**이 문서의 적용 대상:** ✔️ .NET Core 2.x SDK 이상 버전

## <a name="name"></a>이름

`dotnet add package` - 패키지 참조를 프로젝트 파일에 추가합니다.

## <a name="synopsis"></a>개요

```dotnetcli
dotnet add [<PROJECT>] package <PACKAGE_NAME>
    [-f|--framework <FRAMEWORK>] [--interactive]
    [-n|--no-restore] [--package-directory <PACKAGE_DIRECTORY>]
    [--prerelease] [-s|--source <SOURCE>] [-v|--version <VERSION>]

dotnet add package -h|--help
```

## <a name="description"></a>설명

`dotnet add package` 명령은 패키지 참조를 프로젝트 파일에 추가하는 편리한 옵션을 제공합니다. 명령을 실행한 후 패키지가 프로젝트의 프레임워크와 호환되는지 확인하는 호환성 검사가 있습니다. 검사를 통과하면 `<PackageReference>` 요소가 프로젝트 파일에 추가되고 [dotnet restore](dotnet-restore.md)가 실행됩니다.

예를 들어 `Newtonsoft.Json`를 *ToDo.csproj* 에 추가하면 다음 예제와 유사한 출력이 생성됩니다.

```console
Writing C:\Users\me\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\Temp\projects\consoleproj\consoleproj.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 79ms
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg 232ms
log  : Installing Newtonsoft.Json 12.0.1.
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '12.0.1' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

이제 *ToDo.csproj* 파일에 참조되는 패키지에 대한 [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) 요소가 포함됩니다.

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

### <a name="implicit-restore"></a>암시적 복원

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

## <a name="arguments"></a>인수

- **`PROJECT`**

  프로젝트 파일을 지정합니다. 지정하지 않으면 이 명령은 현재 디렉터리에서 검색합니다.

- **`PACKAGE_NAME`**

  추가할 패키지 참조입니다.

## <a name="options"></a>옵션

- **`-f|--framework <FRAMEWORK>`**

  특정 [프레임워크](../../standard/frameworks.md)를 대상으로 하는 경우에만 패키지 참조를 추가합니다.

- **`-h|--help`**

  명령에 대한 간단한 도움말을 출력합니다.

- **`--interactive`**

  명령이 중지되고 사용자 입력 또는 작업을 대기할 수 있도록 허용합니다(예: 인증 완료). .NET Core 2.1 SDK 버전 2.1.400 이상에서 사용할 수 있습니다.

- **`-n|--no-restore`**

  복원 미리 보기 및 호환성 검사를 수행하지 않고 패키지 참조를 추가합니다.

- **`--package-directory <PACKAGE_DIRECTORY>`**

  패키지를 복원할 디렉터리입니다. 기본 패키지 복원 위치는 Windows에서는 `%userprofile%\.nuget\packages`이고, macOS 및 Linux에서는 `~/.nuget/packages`입니다. 자세한 내용은 [NuGet에서 글로벌 패키지, 캐시 및 임시 폴더 관리](/nuget/consume-packages/managing-the-global-packages-and-cache-folders)를 참조하세요.

- **`--prerelease`**

  시험판 패키지를 설치할 수 있습니다.

- **`-s|--source <SOURCE>`**

  복원 작업 중에 사용할 NuGet 패키지 소스의 URI입니다.

- **`-v|--version <VERSION>`**

  패키지의 버전입니다. [NuGet 패키지 버전 관리](/nuget/reference/package-versioning)를 참조하세요.

## <a name="examples"></a>예

- `Newtonsoft.Json` NuGet 패키지를 프로젝트에 추가합니다.

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- 특정 버전의 패키지를 프로젝트에 추가합니다.

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- 특정 NuGet 소스를 사용하여 패키지를 추가합니다.

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a>참조

- [NuGet에서 글로벌 패키지, 캐시 및 임시 폴더 관리](/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [NuGet 패키지 버전 관리](/nuget/reference/package-versioning)
