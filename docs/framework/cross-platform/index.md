---
title: .NET Framework로 여러 플랫폼 개발
ms.date: 10/21/2020
ms.assetid: b153baaa-130c-4169-860b-e580591de91e
ms.openlocfilehash: ef8fae4238f404d650528d25ab873fa48e2c0703
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687742"
---
# <a name="develop-for-multiple-platforms-with-net-framework"></a><span data-ttu-id="0e609-102">.NET Framework로 여러 플랫폼 개발</span><span class="sxs-lookup"><span data-stu-id="0e609-102">Develop for multiple platforms with .NET Framework</span></span>

<span data-ttu-id="0e609-103">.NET Framework 및 Visual Studio를 사용하여 Microsoft 플랫폼과 Microsoft 이외의 플랫폼 둘 모두에서 사용할 수 있는 앱을 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e609-103">You can develop apps for both Microsoft and non-Microsoft platforms by using .NET Framework and Visual Studio.</span></span>

[!INCLUDE [net-framework-future](../../../includes/net-framework-future.md)]

## <a name="options-for-cross-platform-development"></a><span data-ttu-id="0e609-104">플랫폼 간 개발 옵션</span><span class="sxs-lookup"><span data-stu-id="0e609-104">Options for cross-platform development</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

<span data-ttu-id="0e609-105">여러 플랫폼용으로 개발하기 위해 소스 코드 또는 바이너리를 공유하고 .NET Framework 코드와 Windows 런타임 API 간에 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e609-105">To develop for multiple platforms, you can share source code or binaries, and you can make calls between .NET Framework code and Windows Runtime APIs.</span></span>

|<span data-ttu-id="0e609-106">다음을 원하는 경우...</span><span class="sxs-lookup"><span data-stu-id="0e609-106">If you want to...</span></span>|<span data-ttu-id="0e609-107">다음을 사용...</span><span class="sxs-lookup"><span data-stu-id="0e609-107">Use...</span></span>|
|-----------------------|------------|
|<span data-ttu-id="0e609-108">Windows Phone 8.1과 Windows 8.1 앱 간에 소스 코드 공유</span><span class="sxs-lookup"><span data-stu-id="0e609-108">Share source code between Windows Phone 8.1 and Windows 8.1 apps</span></span>|<span data-ttu-id="0e609-109">**공유된 프로젝트** (Visual Studio 2013 업데이트 2의 유니버설 앱 템플릿).</span><span class="sxs-lookup"><span data-stu-id="0e609-109">**Shared projects** (Universal Apps template in Visual Studio 2013, Update 2).</span></span><br /><br /> <span data-ttu-id="0e609-110">- 현재 Visual Basic은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0e609-110">-   Currently no Visual Basic support.</span></span><br /><span data-ttu-id="0e609-111">- #`if` 문을 사용하여 플랫폼별 코드를 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e609-111">-   You can separate platform-specific code by using #`if` statements.</span></span><br /><br /> <span data-ttu-id="0e609-112">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0e609-112">For details, see:</span></span><br /><br /> <span data-ttu-id="0e609-113">-   [코딩 시작](/windows/uwp/get-started/create-uwp-apps)</span><span class="sxs-lookup"><span data-stu-id="0e609-113">-   [Start coding](/windows/uwp/get-started/create-uwp-apps)</span></span><br /><span data-ttu-id="0e609-114">-   [Using Visual Studio to build Universal XAML Apps](https://devblogs.microsoft.com/visualstudio/using-visual-studio-to-build-universal-xaml-apps/)(Visual Studio를 사용하여 유니버설 XAML 앱 빌드)(블로그 게시물)</span><span class="sxs-lookup"><span data-stu-id="0e609-114">-   [Using Visual Studio to build Universal XAML Apps](https://devblogs.microsoft.com/visualstudio/using-visual-studio-to-build-universal-xaml-apps/) (blog post)</span></span><br /><span data-ttu-id="0e609-115">-   [Visual Studio를 사용한 XAML 컨버지드 앱 빌드](https://channel9.msdn.com/Events/Build/2014/3-591)(동영상)</span><span class="sxs-lookup"><span data-stu-id="0e609-115">-   [Using Visual Studio to Build XAML Converged Apps](https://channel9.msdn.com/Events/Build/2014/3-591) (video)</span></span>|
|<span data-ttu-id="0e609-116">여러 플랫폼을 대상으로 하는 앱 간에 바이너리 공유</span><span class="sxs-lookup"><span data-stu-id="0e609-116">Share binaries between apps that target different platforms</span></span>|<span data-ttu-id="0e609-117">플랫폼 제약이 없는 코드를 위한 **이식 가능한 클래스 라이브러리 프로젝트** .</span><span class="sxs-lookup"><span data-stu-id="0e609-117">**Portable Class Library projects** for code that is platform-agnostic.</span></span><br /><br /> <span data-ttu-id="0e609-118">- 이 접근 방식은 일반적으로 비즈니스 논리를 구현하는 코드에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e609-118">-   This approach is typically used for code that implements business logic.</span></span><br /><span data-ttu-id="0e609-119">- Visual Basic 또는 C#을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e609-119">-   You can use Visual Basic or C#.</span></span><br /><span data-ttu-id="0e609-120">- API 지원은 플랫폼별로 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="0e609-120">-   API support varies by platform.</span></span><br /><span data-ttu-id="0e609-121">- Windows 8.1 및 Windows Phone 8.1을 대상으로 하는 이식 가능한 클래스 라이브러리 프로젝트는 Windows 런타임 API 및 XAML을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="0e609-121">-   Portable Class Library projects that target Windows 8.1 and Windows Phone 8.1 support Windows Runtime APIs and XAML.</span></span> <span data-ttu-id="0e609-122">이러한 기능은 이식 가능한 클래스 라이브러리의 이전 버전에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0e609-122">These features aren't available in older versions of the Portable Class Library.</span></span><br /><span data-ttu-id="0e609-123">- 필요한 경우 인터페이스 또는 추상 클래스를 사용하여 플랫폼별 코드를 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e609-123">-   If needed, you can abstract out platform-specific code by using interfaces or abstract classes.</span></span><br /><br /> <span data-ttu-id="0e609-124">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0e609-124">For details, see:</span></span><br /><br /> <span data-ttu-id="0e609-125">-   [이식 가능한 클래스 라이브러리](portable-class-library.md)</span><span class="sxs-lookup"><span data-stu-id="0e609-125">-   [Portable Class Library](portable-class-library.md)</span></span><br /><span data-ttu-id="0e609-126">-   [How to Make Portable Class Libraries Work for You](/archive/blogs/dsplaisted/how-to-make-portable-class-libraries-work-for-you)(이식 가능한 클래스 라이브러리가 작동하도록 설정하는 방법)(블로그 게시물)</span><span class="sxs-lookup"><span data-stu-id="0e609-126">-   [How to Make Portable Class Libraries Work for You](/archive/blogs/dsplaisted/how-to-make-portable-class-libraries-work-for-you) (blog post)</span></span><br /><span data-ttu-id="0e609-127">-   [MVVM과 함께 이식 가능한 클래스 라이브러리 사용](using-portable-class-library-with-model-view-view-model.md)</span><span class="sxs-lookup"><span data-stu-id="0e609-127">-   [Using Portable Class Library with MVVM](using-portable-class-library-with-model-view-view-model.md)</span></span> <br /><span data-ttu-id="0e609-128">-   [여러 플랫폼을 대상으로 하는 라이브러리의 앱 리소스](app-resources-for-libraries-that-target-multiple-platforms.md)</span><span class="sxs-lookup"><span data-stu-id="0e609-128">-   [App Resources for Libraries That Target Multiple Platforms](app-resources-for-libraries-that-target-multiple-platforms.md)</span></span> <br /><span data-ttu-id="0e609-129">-   [.NET 이식성 분석기](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)(Visual Studio 확장)</span><span class="sxs-lookup"><span data-stu-id="0e609-129">-   [.NET Portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) (Visual Studio extension)</span></span>|
|<span data-ttu-id="0e609-130">Windows 8.1 및 Windows Phone 8.1 이외 플랫폼용 앱 간에 소스 코드 공유</span><span class="sxs-lookup"><span data-stu-id="0e609-130">Share source code between apps for platforms other than Windows 8.1 and Windows Phone 8.1</span></span>|<span data-ttu-id="0e609-131">**링크로 추가** 기능.</span><span class="sxs-lookup"><span data-stu-id="0e609-131">**Add as link** feature.</span></span><br /><br /> <span data-ttu-id="0e609-132">- 이 접근 방식은 몇 가지 이유로 두 앱에 공통으로 적용되지만 이식은 가능하지 않은 앱 논리에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="0e609-132">-   This approach is suitable for app logic that's common to both apps but not portable, for some reason.</span></span> <span data-ttu-id="0e609-133">이 기능은 C# 또는 Visual Basic 코드에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e609-133">You can use this feature for C# or Visual Basic code.</span></span><br />     <span data-ttu-id="0e609-134">예를 들어, Windows Phone 8 및 Windows 8은 Windows 런타임 API를 공유하지만 이식 가능한 클래스 라이브러리는 이러한 플랫폼에 Windows 런타임을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0e609-134">For example, Windows Phone 8 and Windows 8 share Windows Runtime APIs, but Portable Class Libraries do not support Windows Runtime for those platforms.</span></span> <span data-ttu-id="0e609-135">`Add as link`를 사용하여 Windows Phone 8 앱과 Windows 8이 대상인 Windows 스토어 앱 간에 공통 Windows 런타임 코드를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e609-135">You can use `Add as link` to share common Windows Runtime code between a Windows Phone 8 app and a Windows Store app that targets Windows 8.</span></span><br /><br /> <span data-ttu-id="0e609-136">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0e609-136">For details, see:</span></span><br /><br /> <span data-ttu-id="0e609-137">-   [Share code with Add as Link](/previous-versions/windows/apps/jj714082(v=vs.105))(링크로 추가 기능을 통해 코드 공유)</span><span class="sxs-lookup"><span data-stu-id="0e609-137">-   [Share code with Add as Link](/previous-versions/windows/apps/jj714082(v=vs.105))</span></span><br /><span data-ttu-id="0e609-138">-   [방법: 프로젝트에 기존 항목 추가](/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0e609-138">-   [How to: Add Existing Items to a Project](/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span></span>|
|<span data-ttu-id="0e609-139">.NET Framework를 사용하여 Windows 스토어 앱 쓰기 또는 .NET Framework 코드에서 Windows 런타임 API 호출</span><span class="sxs-lookup"><span data-stu-id="0e609-139">Write Windows Store apps using the .NET Framework or call Windows Runtime APIs from .NET Framework code</span></span>|<span data-ttu-id="0e609-140">.NET Framework C# 또는 Visual Basic 코드의 **Windows 런타임 API** .NET Framework를 사용하여 Windows 스토어 앱을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0e609-140">**Windows Runtime APIs** from your .NET Framework C# or Visual Basic code, and use the .NET Framework to create Windows Store apps.</span></span> <span data-ttu-id="0e609-141">두 플랫폼 간의 API 차이점을 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e609-141">You should be aware of API differences between the two platforms.</span></span> <span data-ttu-id="0e609-142">그러나 이러한 차이점을 처리하는 데 도움이 되는 클래스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e609-142">However, there are classes to help you work with those differences.</span></span><br /><br /> <span data-ttu-id="0e609-143">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0e609-143">For details, see:</span></span><br /><br /> <span data-ttu-id="0e609-144">-   [Windows 스토어 앱 및 Windows 런타임에 대한 .NET Framework 지원](support-for-windows-store-apps-and-windows-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="0e609-144">-   [.NET Framework Support for Windows Store Apps and Windows Runtime](support-for-windows-store-apps-and-windows-runtime.md)</span></span> <br /><span data-ttu-id="0e609-145">-   [Windows 런타임에 URI 전달](passing-a-uri-to-the-windows-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="0e609-145">-   [Passing a URI to the Windows Runtime](passing-a-uri-to-the-windows-runtime.md)</span></span> <br />-   <xref:System.IO.WindowsRuntimeStreamExtensions><br />-    <xref:System.WindowsRuntimeSystemExtensions>|
|<span data-ttu-id="0e609-146">Microsoft 이외의 플랫폼용 .NET Framework 앱 빌드</span><span class="sxs-lookup"><span data-stu-id="0e609-146">Build .NET Framework apps for non-Microsoft platforms</span></span>|<span data-ttu-id="0e609-147">.NET Framework의 **이식 가능한 클래스 라이브러리 참조 어셈블리** 및 Visual Studio 확장 또는 Xamarin과 같은 타사 도구.</span><span class="sxs-lookup"><span data-stu-id="0e609-147">**Portable Class Library reference assemblies** in the .NET Framework, and a Visual Studio extension or third-party tool such as Xamarin.</span></span><br /><br /> <span data-ttu-id="0e609-148">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0e609-148">For details, see:</span></span><br /><br /> <span data-ttu-id="0e609-149">-   [Portable Class Library now available on all platforms](https://devblogs.microsoft.com/dotnet/portable-class-library-pcl-now-available-on-all-platforms/)(이제 모든 플랫폼에서 이식 가능한 클래스 라이브러리 사용)</span><span class="sxs-lookup"><span data-stu-id="0e609-149">-   [Portable Class Library now available on all platforms.](https://devblogs.microsoft.com/dotnet/portable-class-library-pcl-now-available-on-all-platforms/)</span></span> <span data-ttu-id="0e609-150">(블로그 게시물)</span><span class="sxs-lookup"><span data-stu-id="0e609-150">(blog post)</span></span><br /><span data-ttu-id="0e609-151">-   [Xamarin 설명서](/xamarin)</span><span class="sxs-lookup"><span data-stu-id="0e609-151">-   [Xamarin documentation](/xamarin)</span></span>|
|<span data-ttu-id="0e609-152">플랫폼 간 개발에 JavaScript 및 HTML 사용</span><span class="sxs-lookup"><span data-stu-id="0e609-152">Use JavaScript and HTML for cross-platform development</span></span>|<span data-ttu-id="0e609-153">Windows 8.1 및 Windows Phone 8.1용 Windows 런타임 API에 대해 개발하기 위한 Visual Studio 2013 업데이트 2의 **유니버설 앱 템플릿** .</span><span class="sxs-lookup"><span data-stu-id="0e609-153">**Universal App templates** in Visual Studio 2013, Update 2 to develop against Windows Runtime APIs for Windows 8.1 and Windows Phone 8.1.</span></span> <span data-ttu-id="0e609-154">현재 플랫폼 간 앱을 개발하기 위해 .NET Framework API를 JavaScript 및 HTML과 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0e609-154">Currently, you can't use JavaScript and HTML with .NET Framework APIs to develop cross-platform apps.</span></span><br /><br /> <span data-ttu-id="0e609-155">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0e609-155">For details, see:</span></span><br /><br /> <span data-ttu-id="0e609-156">-   [JavaScript 프로젝트 템플릿](/previous-versions/windows/apps/hh758331(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="0e609-156">-   [JavaScript Project Templates](/previous-versions/windows/apps/hh758331(v=win.10))</span></span><br /><span data-ttu-id="0e609-157">-   [JavaScript를 사용하여 Windows Phone에 Windows 런타임 앱 포팅](/previous-versions/windows/apps/dn636144(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="0e609-157">-   [Porting a Windows Runtime app using JavaScript to Windows Phone](/previous-versions/windows/apps/dn636144(v=win.10))</span></span>|