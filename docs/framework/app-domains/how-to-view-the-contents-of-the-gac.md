---
title: '방법: 글로벌 어셈블리 캐시의 내용 보기'
description: GAC(전역 어셈블리 캐시) 도구(gacutil.exe)를 사용하여 .NET에서 전역 어셈블리 캐시의 콘텐츠를 보는 방법을 알아봅니다.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- GAC (global assembly cache), viewing contents
- list of assemblies in global assembly cache
- Global Assembly Cache tool
ms.assetid: c5f786a0-969b-4f14-9f02-e77c3384d9af
ms.openlocfilehash: 56b4750e6b9338a6c136c16505b5da94f51fd72f
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653597"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a>방법: 글로벌 어셈블리 캐시의 내용 보기

[전역 어셈블리 캐시 도구(Gacutil.exe)](../tools/gacutil-exe-gac-tool.md)를 사용하면 GAC(전역 어셈블리 캐시)의 콘텐츠를 볼 수 있습니다.

## <a name="view-the-assemblies-in-the-gac"></a>GAC의 어셈블리 보기

전역 어셈블리 캐시의 어셈블리 목록을 보려면 [Visual Studio 개발자 명령 프롬프트 또는 Visual Studio 개발자 PowerShell](/visualstudio/ide/reference/command-prompt-powershell)을 열고 다음 명령을 입력합니다.

```shell
gacutil -l
```

또는

```shell
gacutil /l
```

> [!NOTE]
> 이전 버전의 .NET Framework에서는 [Shfusion.dll](/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) Windows 셸 확장을 통해 파일 탐색기에서 전역 어셈블리 캐시를 볼 수 있었습니다. .NET Framework 4부터는 Shfusion.dll이 사용되지 않습니다.

## <a name="see-also"></a>참조

- [어셈블리 및 전역 어셈블리 캐시 사용](working-with-assemblies-and-the-gac.md)
- [Gacutil.exe(전역 어셈블리 캐시 도구)](../tools/gacutil-exe-gac-tool.md)
