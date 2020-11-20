---
title: Linux 배포에 .NET 설치
description: Linux에서 .NET 설치를 지원하는 Linux 배포에 대해 알아봅니다.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 6354ef6f0f9af2126312683893d6705b3b4c70f4
ms.sourcegitcommit: c38bf879a2611ff46aacdd529b9f2725f93e18a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2020
ms.locfileid: "94594521"
---
# <a name="install-net-on-linux"></a>Linux에 .NET 설치

> [!div class="op_single_selector"]
>
> - [Windows에 설치](windows.md)
> - [macOS에 설치](macos.md)
> - [Linux에 설치](linux.md)

.NET은 다양한 Linux 배포에서 사용할 수 있습니다. 대부분의 Linux 플랫폼과 배포는 매년 주요 릴리스를 출시하며 .NET 설치에 사용되는 패키지 관리자를 제공하는 경우가 많습니다. 이 문서에서는 현재 지원되는 버전과 사용되는 패키지 관리자에 대해 설명합니다.

이 문서의 나머지 부분은 .NET에서 지원하는 각 주요 Linux 배포를 자세히 다룹니다. 모든 .NET 릴리스는 [.NET 버전이 지원 종료에 도달](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)하거나 Linux 배포가 지원 종료에 도달할 때까지 계속 지원됩니다.

최상의 호환성을 원한다면 장기 릴리스(LTS) 버전을 선택합니다.

## <a name="unsupported-releases"></a>지원되지 않는 릴리스

다음 .NET 버전은 ❌로 더 이상 지원되지 않습니다. 이러한 버전의 다운로드는 여전히 게시된 상태로 유지됩니다.

- 3.0
- 2.2
- 2.0

지원되지 않는 버전은 아래 섹션에 자세히 설명되어 있지 않으며, 설치를 시도할 경우 진행 정도가 다양할 수 있습니다.

## <a name="alpine"></a>Alpine

Alpine용 설치 프로그램은 없습니다. [설치 스크립트](linux-alpine.md#scripted-install)를 사용하거나 [수동 설치](linux-alpine.md#manual-install) 지침을 따라야 합니다.

다음 표는 현재 지원되는 .NET 릴리스와 해당 릴리스가 지원되는 Alpine 버전의 목록입니다. 이러한 버전은 [.NET 버전이 지원 종료에 도달](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)하거나 [Alpine 버전이 지원 종료에 도달](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)할 때까지 계속 지원됩니다.

- ✔️는 Alpine 또는 .NET 버전이 계속 지원됨을 나타냅니다.
- ❌는 Alpine 또는 .NET 버전이 해당 Alpine 릴리스에서 지원되지 않음을 나타냅니다.
- Alpine 버전과 .NET 버전 모두에 ✔가 있으면 해당 OS와 .NET 조합은 지원됩니다.

| Alpine                      | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|-----------------------------|---------------|---------------|----------------|
| ✔️ [3.12](linux-alpine.md)  | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ [3.11](linux-alpine.md)  | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ [3.10](linux-alpine.md)  | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |
| ❌ [3.9](linux-alpine.md)   | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |
| ❌ [3.8](linux-alpine.md)   | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |

자세한 내용은 [Alpine에 .NET 설치](linux-alpine.md)를 참조하세요.

## <a name="centos"></a>CentOS

CentOS 7에서는 Yum을 패키지 관리자로 사용하며 CentOS 8에서는 DNF를 사용합니다.

다음 표는 CentOS 7과 CentOS 8에서 현재 지원되는 .NET 릴리스의 목록입니다. 이러한 버전은 [.NET 버전이 지원 종료에 도달](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)하거나 CentOS 버전이 더 이상 지원되지 않을 때까지 계속 지원됩니다.

| CentOS                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](linux-centos.md#centos-8-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ [7](linux-centos.md#centos-7-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |

자세한 내용은 [CentOS에 .NET 설치](linux-centos.md)를 참조하세요.

## <a name="debian"></a>Debian

Debian은 패키지 관리자로 APT(고급 패키지 도구)를 사용합니다.

다음 표는 현재 지원되는 .NET 릴리스와 해당 릴리스가 지원되는 Debian 버전의 목록입니다. 이러한 버전은 [.NET 버전이 지원 종료에 도달](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)하거나 [Debian 버전이 지원 종료에 도달](https://wiki.debian.org/DebianReleases)할 때까지 계속 지원됩니다.

- ✔️는 Debian 또는 .NET 버전이 계속 지원됨을 나타냅니다.
- ❌는 Debian 또는 .NET 버전이 해당 Debian 릴리스에서 지원되지 않음을 나타냅니다.
- Debian 버전과 .NET 버전 모두에 ✔가 있으면 해당 OS와 .NET 조합은 지원됩니다.

| Debian                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [10](linux-debian.md#debian-10-)     | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ [9](linux-debian.md#debian-9-)       | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ❌ [8](linux-debian.md#debian-8-)       | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 |

자세한 내용은 [Debian에 .NET 설치](linux-debian.md)를 참조하세요.

## <a name="fedora"></a>Fedora

Fedora는 패키지 관리자로 DNF를 사용합니다.

다음 표는 현재 지원되는 .NET 릴리스와 해당 릴리스가 지원되는 Fedora 버전의 목록입니다. 이러한 버전은 [.NET 버전이 지원 종료에 도달](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)하거나 [Fedora 버전이 지원 종료에 도달](https://fedoraproject.org/wiki/End_of_life)할 때까지 계속 지원됩니다.

- ✔️는 Fedora 또는 .NET 버전이 계속 지원됨을 나타냅니다.
- ❌는 Fedora 또는 .NET 버전이 해당 Fedora 릴리스에서 지원되지 않음을 나타냅니다.
- Fedora 버전과 .NET 버전 모두에 ✔가 있으면 해당 OS와 .NET 조합은 지원됩니다.

| Fedora                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [33](linux-fedora.md#fedora-33-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ [32](linux-fedora.md#fedora-32-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ❌ [31](linux-fedora.md#fedora-31-) | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |
| ❌ [30](linux-fedora.md#fedora-30-) | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |
| ❌ [29](linux-fedora.md#fedora-29-) | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |
| ❌ [28](linux-fedora.md#fedora-28-) | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 |
| ❌ [27](linux-fedora.md#fedora-27-) | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 |

자세한 내용은 [Fedora에 .NET 설치](linux-fedora.md)를 참조하세요.

## <a name="opensuse"></a>openSUSE

openSUSE에서는 패키지 관리자로 zypper를 사용합니다.

다음 표는 openSUSE 15에서 현재 지원되는 .NET 릴리스의 목록입니다. 이러한 버전은 [.NET 버전이 지원 종료에 도달](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)하거나 openSUSE 버전이 더 이상 지원되지 않을 때까지 계속 지원됩니다.

| openSUSE                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|----------------------------|---------------|---------------|----------------|
| ✔️ [15](linux-opensuse.md#opensuse-15-)     | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |

자세한 내용은 [openSUSE에 .NET 설치](linux-opensuse.md)를 참조하세요.

## <a name="red-hat"></a>Red Hat

Red Hat Enterprise Linux(RHEL)에서는 패키지 관리자로 yum(RHEL 7)과 DNF(RHEL 8)를 사용합니다.

다음 표는 RHEL 7과 RHEL 8에서 현재 지원되는 .NET 릴리스의 목록입니다. 이러한 버전은 [.NET 버전이 지원 종료에 도달](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)하거나 RHEL 버전이 더 이상 지원되지 않을 때까지 계속 지원됩니다.

- ✔️는 RHEL 또는 .NET 버전이 계속 지원됨을 나타냅니다.
- ❌는 RHEL 또는 .NET 버전이 해당 RHEL 릴리스에서 지원되지 않음을 나타냅니다.
- RHEL 버전과 .NET 버전 모두에 ✔가 있으면 해당 OS와 .NET 조합은 지원됩니다.

| RHEL                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](linux-rhel.md#rhel-8-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ [7](linux-rhel.md#rhel-7--net-50) | ✔️ 2.1        | ✔️ [3.1](linux-rhel.md#rhel-7--net-core-31)        | ✔️ [5.0](linux-rhel.md#rhel-7--net-50) |

자세한 내용은 [RHEL에 .NET 설치](linux-rhel.md)를 참조하세요.

## <a name="sles"></a>SLES

SLES에서는 패키지 관리자로 zypper를 사용합니다.

다음 표는 SLES 12 SP2와 SLES 15에서 현재 지원되는 .NET 릴리스의 목록입니다. 이러한 버전은 [.NET 버전이 지원 종료에 도달](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)하거나 SLES 버전이 더 이상 지원되지 않을 때까지 계속 지원됩니다.

- ✔️는 SLES 또는 .NET 버전이 계속 지원됨을 나타냅니다.
- ❌는 SLES 또는 .NET 버전이 해당 SLES 릴리스에서 지원되지 않음을 나타냅니다.
- SLES 버전과 .NET 버전 모두에 ✔가 있으면 해당 OS와 .NET 조합은 지원됩니다.

| SLES                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|------------------------|---------------|---------------|----------------|
| ✔️ [15](linux-sles.md#sles-15-)     | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ [12 SP2](linux-sles.md#sles-12-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |

자세한 내용은 [SLES에 .NET 설치](linux-sles.md)를 참조하세요.

## <a name="ubuntu"></a>Ubuntu

Ubuntu는 패키지 관리자로 APT(고급 패키지 도구)를 사용합니다.

다음 표는 Ubuntu와 .NET의 지원 상태를 나타냅니다.

- ✔️는 Ubuntu 또는 .NET 버전이 계속 지원됨을 나타냅니다.
- ❌는 Ubuntu 또는 .NET 버전이 해당 Ubuntu 릴리스에서 지원되지 않음을 나타냅니다.
- Ubuntu 버전과 .NET 버전 모두에 ✔가 있으면 해당 OS와 .NET 조합은 지원됩니다.

| Ubuntu                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [20.10](linux-ubuntu.md#2010-)       | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ [20.04(LTS)](linux-ubuntu.md#2004-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ❌ [19.10](linux-ubuntu.md#1910-)       | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ❌ [19.04](linux-ubuntu.md#1904-)       | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |
| ❌ [18.10](linux-ubuntu.md#1810-)       | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 |
| ✔️ [18.04(LTS)](linux-ubuntu.md#1804-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ❌ [17.10](linux-ubuntu.md#1710-)       | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 |
| ❌ [17.04](linux-ubuntu.md#1704-)       | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 |
| ❌ [16.10](linux-ubuntu.md#1610-)       | ❌ 2.1        | ❌ 3.1        | ❌ 5.0 |
| ✔️ [16.04(LTS)](linux-ubuntu.md#1604-) | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |

자세한 내용은 [Ubuntu에 .NET 설치](linux-ubuntu.md)를 참조하세요.

## <a name="next-steps"></a>다음 단계

- [.NET이 설치되어 있는지 확인하는 방법](how-to-detect-installed-versions.md?pivots=os-linux)
- [자습서: Visual Studio Code를 사용하여 새 앱 만들기](../tutorials/with-visual-studio-code.md)
- [자습서: .NET 앱 컨테이너화](../docker/build-container.md)
