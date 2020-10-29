---
title: SYSLIB0010 경고
description: 컴파일 시간 경고 SYSLIB0010을 생성하는 사용되지 않음에 대해 알아봅니다.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: dcd331aa5c68381ea29848bc54ee4b1a5e75330d
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333111"
---
# <a name="syslib0010-unsupported-remoting-apis"></a><span data-ttu-id="c420a-103">SYSLIB0010: 지원되지 않는 원격 API</span><span class="sxs-lookup"><span data-stu-id="c420a-103">SYSLIB0010: Unsupported remoting APIs</span></span>

<span data-ttu-id="c420a-104">[.NET Remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))은 레거시 기술이며 인프라는 .NET Framework에만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c420a-104">[.NET remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) is a legacy technology, and the infrastructure exists only in .NET Framework.</span></span> <span data-ttu-id="c420a-105">다음 원격 관련 API는 .NET 5.0부터 사용되지 않는 것으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c420a-105">The following remoting-related APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="c420a-106">코드에서 이러한 API를 사용하면 컴파일 시간에 `SYSLIB0010` 경고가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c420a-106">Using them in code generates warning `SYSLIB0010` at compile time.</span></span>

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType>

## <a name="workaround"></a><span data-ttu-id="c420a-107">해결 방법</span><span class="sxs-lookup"><span data-stu-id="c420a-107">Workaround</span></span>

<span data-ttu-id="c420a-108">WCF 또는 HTTP 기반 REST 서비스를 사용하여 다른 애플리케이션이나 머신에서 개체와 통신하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c420a-108">Consider using WCF or HTTP-based REST services to communicate with objects in other applications or across machines.</span></span> <span data-ttu-id="c420a-109">자세한 내용은 [.NET Core에서 사용할 수 없는 .NET Framework 기술](../porting/net-framework-tech-unavailable.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c420a-109">For more information, see [.NET Framework technologies unavailable on .NET Core](../porting/net-framework-tech-unavailable.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c420a-110">추가 정보</span><span class="sxs-lookup"><span data-stu-id="c420a-110">See also</span></span>

- <span data-ttu-id="c420a-111">[.NET Remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))</span><span class="sxs-lookup"><span data-stu-id="c420a-111">[.NET remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))</span></span>