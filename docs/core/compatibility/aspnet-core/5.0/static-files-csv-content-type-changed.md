---
title: '호환성이 손상되는 변경: 정적 파일: CSV 콘텐츠 형식이 표준 규격으로 변경됨'
description: 'ASP.NET Core 5.0의 호환성이 손상되는 변경에 대해 알아보기. 정적 파일: CSV 콘텐츠 형식이 표준 규격으로 변경됨'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c94a0cf213970d20559b7c061d8be220b43961e0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760056"
---
# <a name="static-files-csv-content-type-changed-to-standards-compliant"></a>정적 파일: CSV 콘텐츠 형식이 표준 규격으로 변경됨

ASP.NET Core 5.0에서는 [정적 파일 미들웨어](/aspnet/core/fundamentals/static-files)가 *.csv* 파일에 사용하는 `Content-Type` 응답 헤더 값이 표준 규격 값 `text/csv`로 변경되었습니다.

이 문제에 대한 자세한 내용은 [dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385)를 참조하세요.

## <a name="version-introduced"></a>도입된 버전

5.0 미리 보기 1

## <a name="old-behavior"></a>이전 동작

`Content-Type` 헤더 값 `application/octet-stream`이 사용되었습니다.

## <a name="new-behavior"></a>새 동작

`Content-Type` 헤더 값 `text/csv`가 사용됩니다.

## <a name="reason-for-change"></a>변경 이유

[RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) 표준을 준수합니다.

## <a name="recommended-action"></a>권장 조치

앱이 이 변경의 영향을 받는 경우에는 파일 확장명-MIME 형식 매핑을 사용자 지정할 수 있습니다. `application/octet-stream` MIME 형식으로 되돌리려면 `Startup.Configure`에서 <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> 메서드 호출을 수정합니다. 예를 들어:

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

매핑을 사용자 지정하는 방법에 대한 자세한 내용은 [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider)를 참조하세요.

## <a name="affected-apis"></a>영향을 받는 API

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
