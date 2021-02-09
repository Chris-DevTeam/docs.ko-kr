---
title: 애플리케이션 게시
description: .NET 애플리케이션을 게시하는 방법을 알아봅니다. .NET에서는 플랫폼별 또는 플랫폼 간 앱을 게시할 수 있습니다. 앱을 자체 포함이나 프레임워크 종속으로 게시할 수 있습니다. 각 모드는 사용자가 앱을 실행하는 방법에 영향을 줍니다.
ms.date: 02/05/2021
ms.openlocfilehash: 3f10aae139626bd2b09f71b32eaf2d680890e100
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699781"
---
# <a name="net-application-publishing-overview"></a>.NET 애플리케이션 게시 개요

.NET을 사용하여 만든 애플리케이션은 두 가지 모드로 게시할 수 있으며, 모드에 따라 사용자가 앱을 실행하는 방법에 영향을 줍니다.

앱을 ‘자체 포함’으로 게시하면 .NET 런타임 및 라이브러리와 해당 애플리케이션 및 관련 종속성을 포함하는 애플리케이션이 생성됩니다. 애플리케이션 사용자는 .NET 런타임이 설치되지 않은 머신에서 실행 파일을 실행할 수 있습니다.

앱을 프레임워크 종속으로 게시하면 애플리케이션 자체와 관련 종속성만 포함하는 애플리케이션이 생성됩니다. 애플리케이션 사용자가 .NET 런타임을 별도로 설치해야 합니다.

두 게시 모드 모두 기본적으로 플랫폼별 실행 파일을 생성합니다. 프레임워크 종속 애플리케이션은 실행 파일 없이 만들 수 있으며 이 경우 플랫폼 간 애플리케이션입니다.

실행 파일을 생성할 때 RID(런타임 식별자)로 대상 플랫폼을 지정할 수 있습니다. RID에 대한 자세한 내용은 [.NET RID 카탈로그](../rid-catalog.md)를 참조하세요.

다음 표에서는 앱을 프레임워크 종속 또는 자체 포함으로 게시하는 데 사용되는 명령을 SDK 버전 별로 간략하게 설명합니다.

| 형식                                                                                     | SDK 2.1 | SDK 3.1 | SDK 5.0 | 명령 |
| ---------------------------------------------------------------------------------------  | ------- | ------- | ------- | ------- |
| 현재 플랫폼용 [프레임워크 종속 실행 파일](#publish-framework-dependent) |         | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| 특정 플랫폼용 [프레임워크 종속 실행 파일](#publish-framework-dependent)  |         | ✔️      | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [프레임워크 종속 플랫폼 간 이진 파일](#publish-framework-dependent)               | ✔️      | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [자체 포함 실행 파일](#publish-self-contained)                                    | ✔️      | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

자세한 내용은 [.NET dotnet publish 명령](../tools/dotnet-publish.md)을 참조하세요.

## <a name="produce-an-executable"></a>실행 파일 생성

실행 파일은 여러 플랫폼이 아닌 하나의 운영 체제 및 CPU 아키텍처에만 적용됩니다. 앱을 게시하고 실행 파일을 만들 때 앱을 [자체 포함](#publish-self-contained) 또는 [프레임워크 종속](#publish-framework-dependent)으로 게시할 수 있습니다. 앱을 자체 포함으로 게시하면 .NET 런타임이 앱에 포함되며 앱 사용자는 .NET을 설치하지 않고도 앱을 실행할 수 있습니다. 프레임워크 종속으로 게시된 앱에는 .NET 런타임 및 라이브러리가 포함되지 않으며 앱 및 타사 종속성만 포함됩니다.

실행 파일을 생성하는 명령은 다음과 같습니다.

| 형식                                                                                     | SDK 2.1 | SDK 3.1 | SDK 5.0 | 명령 |
| ---------------------------------------------------------------------------------------- | ------- | ------- | ------- | ------- |
| 현재 플랫폼용 [프레임워크 종속 실행 파일](#publish-framework-dependent) |         | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| 특정 플랫폼용 [프레임워크 종속 실행 파일](#publish-framework-dependent)  |         | ✔️      | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [자체 포함 실행 파일](#publish-self-contained)                                    | ✔️      | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

## <a name="produce-a-cross-platform-binary"></a>플랫폼 간 이진 파일을 생성합니다.

플랫폼 간 이진 파일은 앱을 [프레임워크 종속](#publish-framework-dependent)으로 게시할 때 *dll* 파일 형식으로 생성됩니다. *dll* 파일 이름은 프로젝트 이름을 따라 지정됩니다. 예를 들어 앱 이름이 **word_reader** 이면 *word_reader.dll* 이라는 파일이 만들어집니다. 이러한 방식으로 게시된 앱은 `dotnet <filename.dll>` 명령으로 실행되며 모든 플랫폼에서 실행할 수 있습니다.

플랫폼 간 이진 파일은 대상 .NET 런타임이 이미 설치되어 있는 경우 모든 운영 체제에서 실행할 수 있습니다. 대상 .NET 런타임이 설치되지 않았더라도 앱이 롤포워드되도록 구성된 경우 최신 런타임을 사용하여 앱을 실행할 수 있습니다. 자세한 내용은 [프레임워크 종속 앱 롤포워드](../versions/selection.md#framework-dependent-apps-roll-forward)를 참조하세요.

플랫폼 간 이진 파일을 생성하는 명령은 다음과 같습니다.

| 형식                                                                                 | SDK 2.1 | SDK 3.x | SDK 5.0 | 명령 |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- | ------- |
| [프레임워크 종속 플랫폼 간 이진 파일](#publish-framework-dependent)           | ✔️      | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |

## <a name="publish-framework-dependent"></a>프레임워크 종속 게시

프레임워크 종속으로 게시된 앱은 플랫폼 간이며 .NET 런타임을 포함하지 않습니다. 앱 사용자는 .NET 런타임을 설치해야 합니다.

프레임워크 종속으로 앱을 게시하면 [플랫폼 간 이진 파일](#produce-a-cross-platform-binary)이 *dll* 파일로 생성되며 현재 플랫폼을 대상으로 하는 [플랫폼별 실행 파일](#produce-an-executable)이 생성됩니다. *dll* 은 플랫폼 간 이지만 실행 파일은 그렇지 않습니다. 예를 들어 **word_reader** 라는 앱을 게시하고 Windows를 대상으로 지정하면 *word_reader.exe* 실행 파일이 *word_reader.dll* 과 함께 만들어집니다. Linux 또는 macOS를 대상으로 지정하는 경우에는 *word_reader* 실행 파일이 *word_reader.dll* 과 함께 만들어집니다. RID에 대한 자세한 내용은 [.NET RID 카탈로그](../rid-catalog.md)를 참조하세요.

> [!IMPORTANT]
> .NET SDK 2.1에서는 앱 프레임워크 종속을 게시할 때 플랫폼별 실행 파일이 생성되지 않습니다.

앱의 플랫폼 간 이진 파일은 `dotnet <filename.dll>` 명령으로 실행하며 모든 플랫폼에서 실행할 수 있습니다. 앱에서 플랫폼별 구현을 포함하는 NuGet 패키지를 사용하는 경우 플랫폼의 모든 종속성이 앱과 함께 게시 폴더에 복사됩니다.

[`dotnet publish`](../tools/dotnet-publish.md) 명령에 `-r <RID> --self-contained false` 매개 변수를 전달하여 특정 플랫폼용 실행 파일을 만들 수 있습니다. `-r` 매개 변수를 생략하면 현재 플랫폼의 실행 파일이 만들어집니다. 대상 플랫폼의 플랫폼별 종속성을 포함하는 모든 NuGet 패키지가 게시 폴더에 복사됩니다. 플랫폼별 실행 파일이 필요하지 않은 경우 프로젝트 파일에서 `<UseAppHost>False</UseAppHost>`를 지정할 수 있습니다. .NET SDK 프로젝트에 대한 자세한 내용은 [MSBuild 참조](../project-sdk/msbuild-props.md#useapphost)를 참조하세요.

### <a name="advantages"></a>장점

- **소규모 배포**\
앱과 해당 종속성만 배포됩니다. .NET 런타임 및 라이브러리는 사용자가 설치하며 모든 앱에서 런타임을 공유합니다.

- **플랫폼 간**\
앱과 모든 NET 기반 라이브러리가 다른 운영 체제에서 실행됩니다. 앱의 대상 플랫폼을 정의할 필요가 없습니다. .NET 파일 형식에 대한 자세한 내용은 [.NET 어셈블리 파일 형식](../../standard/assembly/file-format.md)을 참조하세요.

- **패치된 최신 런타임 사용**\
앱은 대상 시스템에 설치된 최신 런타임(대상 .NET 주/부 제품군 내에 있음)을 사용합니다. 즉, 앱에서 패치된 최신 버전의 .NET 런타임을 자동으로 사용합니다. 이 기본 동작은 재정의할 수 있습니다. 자세한 내용은 [프레임워크 종속 앱 롤포워드](../versions/selection.md#framework-dependent-apps-roll-forward)를 참조하세요.

### <a name="disadvantages"></a>단점

- **런타임을 미리 설치해야 함**\
앱에서 대상으로 지정한 .NET 버전이 호스트 시스템에 이미 설치된 경우에만 앱을 실행할 수 있습니다. 앱에서 특정 버전의 .NET을 요구하거나 최신 버전의 .NET을 허용하도록 롤포워드 동작을 구성할 수 있습니다. 자세한 내용은 [프레임워크 종속 앱 롤포워드](../versions/selection.md#framework-dependent-apps-roll-forward)를 참조하세요.

- **.NET이 변경될 수 있음**\
앱이 실행되는 머신에서 .NET 런타임 및 라이브러리가 업데이트될 수 있습니다. 드문 경우이지만 이로 인해 대부분의 앱에서처럼 .NET 라이브러리를 사용하는 경우 앱의 동작이 변경될 수 있습니다. 앱이 최신 버전의 .NET을 사용하는 방법을 구성할 수 있습니다. 자세한 내용은 [프레임워크 종속 앱 롤포워드](../versions/selection.md#framework-dependent-apps-roll-forward)를 참조하세요.

다음 단점은 .NET Core 2.1 SDK에만 적용됩니다.

- **`dotnet` 명령을 사용하여 앱 시작**\
사용자는 `dotnet <filename.dll>` 명령을 실행하여 앱을 시작해야 합니다. .NET Core 2.1 SDK에서는 프레임워크 종속으로 게시된 앱의 경우 플랫폼별 실행 파일을 생성하지 않습니다.

### <a name="examples"></a>예제

플랫폼 간 프레임워크 종속으로 앱을 게시합니다. 현재 플랫폼을 대상으로 하는 실행 파일이 *dll* 파일과 함께 만들어집니다.

```dotnet
dotnet publish
```

플랫폼 간 프레임워크 종속으로 앱을 게시합니다. Linux 64비트 실행 파일이 *dll* 파일과 함께 만들어집니다. 이 명령은 .NET Core SDK 2.1에서는 작동하지 않습니다.

```dotnet
dotnet publish -r linux-x64 --self-contained false
```

## <a name="publish-self-contained"></a>자체 포함 게시

앱을 자체 포함으로 게시하면 플랫폼별 실행 파일이 생성됩니다. 출력 게시 폴더에는 .NET 라이브러리 및 대상 런타임을 포함하여 앱의 모든 구성 요소가 포함됩니다. 앱은 다른 .NET 앱에서 격리되며 로컬로 설치된 공유 런타임을 사용하지 않습니다. 앱 사용자는 .NET을 다운로드하여 설치할 필요가 없습니다.

지정된 대상 플랫폼의 이진 실행 파일이 생성됩니다. 예를 들어 앱의 이름이 **word_reader** 이고 Windows용 자체 포함 실행 파일을 게시하는 경우 *word_reader.exe* 파일이 생성됩니다. Linux 또는 macOS용으로 게시하면 *word_reader* 파일이 생성됩니다. 대상 플랫폼과 아키텍처는 [`dotnet publish`](../tools/dotnet-publish.md) 명령의 `-r <RID>` 매개 변수로 지정합니다. RID에 대한 자세한 내용은 [.NET RID 카탈로그](../rid-catalog.md)를 참조하세요.

앱에 플랫폼별 종속성이 포함된 NuGet 패키지와 같은 플랫폼별 종속성이 있는 경우 해당 종속성이 앱과 함께 게시 폴더에 복사됩니다.

### <a name="advantages"></a>장점

- **.NET 버전 제어**\
앱과 함께 배포되는 .NET 버전을 제어할 수 있습니다.

- **플랫폼별 대상 지정**\
각 플랫폼용 앱을 게시해야 하므로 앱이 실행되는 위치를 알 수 있습니다. .NET에서 새 플랫폼을 도입하는 경우 해당 플랫폼을 대상으로 하는 버전을 릴리스할 때까지 사용자가 해당 플랫폼에서 앱을 실행할 수 없습니다. 사용자가 새 플랫폼에서 앱을 실행하기 전에 앱의 호환성 문제를 테스트할 수 있습니다.

### <a name="disadvantages"></a>단점

- **대규모 배포**\
앱에는 .NET 런타임 및 모든 앱 종속성이 포함되어 있으므로 필요한 다운로드 크기와 하드 드라이브 공간이 [프레임워크 종속](#publish-framework-dependent) 버전보다 큽니다.

  > [!TIP]
  > .NET [*globalization invariant mode*](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)(세계화 고정 모드)를 사용하여 Linux 시스템에서 배포 크기를 약 28MB까지 줄일 수 있습니다. 이렇게 하면 앱이 모든 문화권을 [고정 문화권](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType)처럼 처리합니다.

  > [!TIP]
  > 배포의 크기를 더 줄일 수 있는 [미리 보기 트리밍 기능](trim-self-contained.md)이 있습니다.

- **.NET 버전을 업데이트하기 어려움**\
앱과 함께 배포되는 .NET 런타임은 새 버전의 앱을 릴리스해야만 업그레이드할 수 있습니다. 그러나 .NET은 앱이 실행되는 머신의 프레임워크 라이브러리에 필요한 중요 보안 패치를 업데이트합니다. 이 보안 패치 시나리오에 엔드투엔드 유효성 검사를 실행해야 합니다.

### <a name="examples"></a>예

앱을 자체 포함으로 게시합니다. macOS 64비트 실행 파일이 생성됩니다.

```dotnet
dotnet publish -r osx-x64
```

앱을 자체 포함으로 게시합니다. Windows 64비트 실행 파일이 생성됩니다.

```dotnet
dotnet publish -r win-x64
```

## <a name="publish-with-readytorun-images"></a>ReadyToRun 이미지를 사용하여 게시

ReadyToRun 이미지를 사용하여 게시하면 애플리케이션의 크기를 늘리는 데 드는 비용으로 애플리케이션의 시작 시간이 향상됩니다. ReadyToRun을 사용하여 게시하려면 [ReadyToRun](ready-to-run.md)에서 자세한 내용을 참조하세요.

### <a name="advantages"></a>장점

- **시작 시간 향상**\
애플리케이션은 JIT를 실행하는 데 걸리는 시간을 줄입니다.

### <a name="disadvantages"></a>단점

- **큰 크기**\
애플리케이션은 디스크에서 더 커집니다.

### <a name="examples"></a>예

자체 포함 및 ReadyToRun 앱을 게시합니다. macOS 64비트 실행 파일이 생성됩니다.

```dotnet
dotnet publish -c Release -r osx-x64 -p:PublishReadyToRun=true
```

자체 포함 및 ReadyToRun 앱을 게시합니다. Windows 64비트 실행 파일이 생성됩니다.

```dotnet
dotnet publish -c Release -r win-x64 -p:PublishReadyToRun=true
```

## <a name="see-also"></a>참조

- [.NET CLI를 사용하여 .NET 앱 배포](deploy-with-cli.md)
- [Visual Studio를 사용하여 .NET 앱 배포](deploy-with-vs.md)
- [.NET RID(런타임 식별자) 카탈로그](../rid-catalog.md)
- [사용할 .NET 버전 선택](../versions/selection.md)
