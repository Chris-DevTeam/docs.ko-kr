---
title: '방법: 글로벌 어셈블리 캐시에 어셈블리 설치'
description: 여러 애플리케이션에서 공유할 수 있도록 어셈블리를 .NET의 GAC(전역 어셈블리 캐시)에 설치합니다. Windows Installer 또는 GAC 유틸리티를 사용합니다.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
ms.openlocfilehash: 0034c6d7a7184e8fc3a6384c829f6bf13aad6cdd
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653467"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>방법: 글로벌 어셈블리 캐시에 어셈블리 설치

GAC(글로벌 어셈블리 캐시)는 여러 애플리케이션이 공유하는 어셈블리를 저장합니다. 다음 구성 요소 중 하나를 사용하여 [글로벌 어셈블리 캐시](gac.md)에 어셈블리를 설치합니다.

- [Windows Installer](#windows-installer)
- [전역 어셈블리 캐시 도구](#global-assembly-cache-tool)

> [!IMPORTANT]
> 강력한 이름의 어셈블리만 전역 어셈블리 캐시에 설치할 수 있습니다. 강력한 이름의 어셈블리를 만드는 방법에 대한 자세한 내용은 [방법: 강력한 이름으로 어셈블리 서명](../../standard/assembly/sign-strong-name.md)을 참조하세요.

## <a name="windows-installer"></a>Windows Installer

Windows 설치 엔진인 [Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache)는 전역 어셈블리 캐시에 어셈블리를 추가하는 권장 방법입니다. Windows Installer는 전역 어셈블리 캐시의 어셈블리 참조 횟수 및 다른 여러 가지 혜택을 제공합니다. Windows Installer용 설치 관리자 패키지를 만들려면 [Visual Studio 2017용 WiX Toolset 확장](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)을 사용하세요.

## <a name="global-assembly-cache-tool"></a>전역 어셈블리 캐시 도구

[.NET 전역 어셈블리 캐시 유틸리티(gacutil.exe)](../tools/gacutil-exe-gac-tool.md)를 사용하여 어셈블리를 전역 어셈블리 캐시에 추가하고 전역 어셈블리 캐시의 콘텐츠를 볼 수 있습니다.

   > [!NOTE]
   > *Gacutil.exe* 는 개발 목적으로만 사용됩니다. 해당 파일을 사용하여 프로덕션 어셈블리를 글로벌 어셈블리 캐시에 설치하지 마세요.

GAC에 어셈블리를 설치하기 위해 *gacutil.exe* 를 사용하는 구문은 다음과 같습니다.

```cmd
gacutil -i <assembly name>
```

이 명령에서 *\<assembly name>* 은 전역 어셈블리 캐시에 설치할 어셈블리의 이름입니다.

*gacutil.exe* 가 시스템 경로에 없는 경우 [Visual Studio 개발자 명령 프롬프트 또는 Visual Studio 개발자 PowerShell](/visualstudio/ide/reference/command-prompt-powershell)을 사용합니다.

다음 예제는 파일 이름이 *hello.dll* 인 어셈블리를 글로벌 어셈블리 캐시에 설치합니다.

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> 이전 버전의 .NET Framework에서는 *Shfusion.dll* Windows 셸 확장을 통해 파일 탐색기로 어셈블리를 끌어와서 설치할 수 있었습니다. .NET Framework 4부터는 *Shfusion.dll* 이 사용되지 않습니다.

## <a name="see-also"></a>참조

- [어셈블리 및 전역 어셈블리 캐시 사용](working-with-assemblies-and-the-gac.md)
- [방법: 글로벌 어셈블리 캐시에서 어셈블리 제거](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil.exe(전역 어셈블리 캐시 도구)](../tools/gacutil-exe-gac-tool.md)
- [방법: 강력한 이름으로 어셈블리 서명](../../standard/assembly/sign-strong-name.md)
