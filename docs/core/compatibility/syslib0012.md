---
title: SYSLIB0012 경고
description: 컴파일 시간 경고 SYSLIB0012를 생성하는 사용되지 않음에 대해 알아봅니다.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 2ed93b6eefbaa861faca319f0cc9bf19ac741f3b
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333107"
---
# <a name="syslib0012-assemblycodebase-and-assemblyescapedcodebase-are-obsolete"></a><span data-ttu-id="908db-103">SYSLIB0012: Assembly.CodeBase 및 Assembly.EscapedCodeBase가 사용되지 않음</span><span class="sxs-lookup"><span data-stu-id="908db-103">SYSLIB0012: Assembly.CodeBase and Assembly.EscapedCodeBase are obsolete</span></span>

<span data-ttu-id="908db-104">다음 API는 .NET 5.0부터 사용되지 않는 것으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="908db-104">The following APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="908db-105">코드에서 이러한 API를 사용하면 컴파일 시간에 `SYSLIB0012` 경고가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="908db-105">Using them in code generates warning `SYSLIB0012` at compile time.</span></span>

- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType>

<span data-ttu-id="908db-106">해결 방법</span><span class="sxs-lookup"><span data-stu-id="908db-106">Workaround</span></span>

<span data-ttu-id="908db-107">대신 <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="908db-107">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> instead.</span></span>