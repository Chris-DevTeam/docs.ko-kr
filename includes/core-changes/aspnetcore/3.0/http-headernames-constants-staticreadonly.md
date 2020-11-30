---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032530"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a>HTTP: HeaderNames 상수가 정적 readonly로 변경됨

ASP.NET Core 3.0 Preview 5부터 <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>의 필드가 `const`에서 `static readonly`로 변경되었습니다.

토론은 [dotnet/aspnetcore#9514](https://github.com/dotnet/aspnetcore/issues/9514)를 참조하세요.

#### <a name="version-introduced"></a>도입된 버전

3.0

#### <a name="old-behavior"></a>이전 동작

이러한 필드는 `const`가 되는 데 사용됩니다.

#### <a name="new-behavior"></a>새 동작

이러한 필드는 이제 `static readonly`입니다.

#### <a name="reason-for-change"></a>변경 이유

변경 내용:

* 값이 어셈블리 경계를 넘어 포함되지 않도록 하여 필요에 따라 값을 수정할 수 있도록 합니다.
* 참조 같음 검사를 더 빠르게 수행할 수 있습니다.

#### <a name="recommended-action"></a>권장 조치

3\.0에 대해 다시 컴파일합니다. 다음 방법으로 이러한 필드를 사용하는 소스 코드는 더 이상 이렇게 할 수 없습니다.

* 특성 인수로 사용
* `switch` 문의 `case`로 사용
* 다른 `const`를 정의하는 경우

호환성이 손상되는 변경을 해결하려면 자체 정의된 헤더 이름 상수 또는 문자열 리터럴을 사용하도록 전환합니다.

#### <a name="category"></a>범주

ASP.NET Core

#### <a name="affected-apis"></a>영향을 받는 API

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
