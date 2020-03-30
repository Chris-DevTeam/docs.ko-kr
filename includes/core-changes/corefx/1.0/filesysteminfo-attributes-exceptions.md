---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449407"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a><span data-ttu-id="adcf3-101">FileSystemInfo.Attributes가 throw하는 UnauthorizedAccessException</span><span class="sxs-lookup"><span data-stu-id="adcf3-101">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>

<span data-ttu-id="adcf3-102">.NET Core에서 호출자가 파일 특성 값을 설정하려고 하지만 쓰기 권한이 없는 경우 <xref:System.UnauthorizedAccessException>이 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="adcf3-102">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown when the caller attempts to set a file attribute value but doesn't have write permission.</span></span>

#### <a name="change-description"></a><span data-ttu-id="adcf3-103">변경 내용 설명</span><span class="sxs-lookup"><span data-stu-id="adcf3-103">Change description</span></span>

<span data-ttu-id="adcf3-104">.NET Framework에서 호출자가 <xref:System.ArgumentException>에서 파일 특성 값을 설정하려고 하지만 쓰기 권한이 없는 경우 <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>이 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="adcf3-104">In .NET Framework, an <xref:System.ArgumentException> is thrown when the caller attempts to set a file attribute value in <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> but doesn't have write permission.</span></span> <span data-ttu-id="adcf3-105">.NET Core에서는 대신 <xref:System.UnauthorizedAccessException>이 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="adcf3-105">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown instead.</span></span> <span data-ttu-id="adcf3-106">(.NET Core에서 호출자가 잘못된 파일 특성을 설정하려고 시도하는 경우 여전히 <xref:System.ArgumentException>이 throw됩니다.)</span><span class="sxs-lookup"><span data-stu-id="adcf3-106">(In .NET Core, an <xref:System.ArgumentException> is still thrown if the caller attempts to set an invalid file attribute.)</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="adcf3-107">도입된 버전</span><span class="sxs-lookup"><span data-stu-id="adcf3-107">Version introduced</span></span>

<span data-ttu-id="adcf3-108">1.0</span><span class="sxs-lookup"><span data-stu-id="adcf3-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="adcf3-109">권장 조치</span><span class="sxs-lookup"><span data-stu-id="adcf3-109">Recommended action</span></span>

<span data-ttu-id="adcf3-110">필요에 따라 `catch` 대신 또는 추가로 <xref:System.UnauthorizedAccessException>을 catch하도록 <xref:System.ArgumentException> 문을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="adcf3-110">Modify any `catch` statements to catch an <xref:System.UnauthorizedAccessException> instead of, or in addition to, an <xref:System.ArgumentException>, as necessary.</span></span>

#### <a name="category"></a><span data-ttu-id="adcf3-111">범주</span><span class="sxs-lookup"><span data-stu-id="adcf3-111">Category</span></span>

<span data-ttu-id="adcf3-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="adcf3-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="adcf3-113">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="adcf3-113">Affected APIs</span></span>

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->