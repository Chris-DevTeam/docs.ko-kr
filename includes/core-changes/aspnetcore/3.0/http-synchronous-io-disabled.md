---
ms.openlocfilehash: 53d2c989120c92f4e2d18f50ce4b364bd4c9b604
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032549"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a>HTTP: 모든 서버에서 동기 IO 비활성화

ASP.NET Core 3.0부터 동기 서버 작업은 기본적으로 비활성화되어 있습니다.

#### <a name="change-description"></a>변경 내용 설명

`AllowSynchronousIO`는 `HttpRequest.Body.Read`, `HttpResponse.Body.Write` 및 `Stream.Flush`와 같은 동기 IO API를 사용하거나 사용하지 않도록 설정하는 각 서버의 옵션입니다. 이러한 API는 오랫동안 스레드 고갈과 앱 중지의 원인이었습니다. ASP.NET Core 3.0 미리 보기 3부터 이러한 동기 작업은 기본적으로 비활성화되어 있습니다.

영향을 받는 서버:

- Kestrel
- HttpSys
- IIS In-Process
- TestServer

다음과 유사한 오류가 예상됩니다.

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

각 서버에는 이 동작을 제어하는 `AllowSynchronousIO` 옵션이 있으며 모든 항목에 대한 기본값은 이제 `false`입니다.

이 동작은 요청에 따라 임시 완화로 재정의할 수도 있습니다. 예를 들어:

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

`TextWriter` 또는 `Dispose`에서 동기 API를 호출하는 다른 스트림에 문제가 있는 경우 대신 새 `DisposeAsync` API를 호출합니다.

토론은 [dotnet/aspnetcore#7644](https://github.com/dotnet/aspnetcore/issues/7644)를 참조하세요.

#### <a name="version-introduced"></a>도입된 버전

3.0

#### <a name="old-behavior"></a>이전 동작

기본적으로 `HttpRequest.Body.Read`, `HttpResponse.Body.Write` 및 `Stream.Flush`가 허용됩니다.

#### <a name="new-behavior"></a>새 동작

이러한 동기 API는 기본적으로 허용되지 않습니다.

다음과 유사한 오류가 예상됩니다.

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a>변경 이유

이러한 동기 API는 오랫동안 스레드 고갈과 앱 중지의 원인이었습니다. ASP.NET Core 3.0 미리 보기 3부터 동기 작업은 기본적으로 비활성화되어 있습니다.

#### <a name="recommended-action"></a>권장 조치

비동기 버전의 메서드를 사용합니다. 이 동작은 요청에 따라 임시 완화로 재정의할 수도 있습니다.

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a>범주

ASP.NET Core

#### <a name="affected-apis"></a>영향을 받는 API

- <xref:System.IO.Stream.Flush%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.IO.Stream.Flush`
- `Overload:System.IO.Stream.Read`
- `Overload:System.IO.Stream.Write`

-->
