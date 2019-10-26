---
title: 기본 인터페이스 메서드를 사용하여 mixin 형식 만들기
description: 기본 인터페이스 멤버를 사용하여 구현자에 대한 선택적 기본 구현으로 인터페이스를 확장할 수 있습니다.
ms.date: 10/04/2019
ms.openlocfilehash: 4dee97226420139d9cd09ad75d7c8caf4967273d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321569"
---
# <a name="tutorial-mix-in-functionality-when-creating-classes-using-interfaces-with-default-interface-methods"></a><span data-ttu-id="dd8ea-103">자습서: 기본 인터페이스 메서드를 사용하는 인터페이스를 통해 클래스를 만드는 경우의 기능 혼합</span><span class="sxs-lookup"><span data-stu-id="dd8ea-103">Tutorial: Mix in functionality when creating classes using interfaces with default interface methods</span></span>

<span data-ttu-id="dd8ea-104">.NET Core 3.0의 C# 8.0에서부터, 인터페이스 멤버 선언 시 구현을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-104">Beginning with C# 8.0 on .NET Core 3.0, you can define an implementation when you declare a member of an interface.</span></span> <span data-ttu-id="dd8ea-105">이 기능은 인터페이스에 선언된 기능에 대한 기본 구현을 정의할 수 있는 새로운 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-105">This feature provides new capabilities where you can define default implementations for features declared in interfaces.</span></span> <span data-ttu-id="dd8ea-106">클래스는 기능을 재정의할 시기, 기본 기능을 사용할 시기 및 불연속 기능에 대한 지원을 선언하지 않을 시기를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-106">Classes can pick when to override functionality, when to use the default functionality, and when not to declare support for discrete features.</span></span>

<span data-ttu-id="dd8ea-107">이 자습서에서는 다음과 같은 작업을 수행하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-107">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="dd8ea-108">불연속 기능을 설명하는 구현을 사용하여 인터페이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-108">Create interfaces with implementations that describe discrete features.</span></span>
> * <span data-ttu-id="dd8ea-109">기본 구현을 사용하는 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-109">Create classes that use the default implementations.</span></span>
> * <span data-ttu-id="dd8ea-110">기본 구현의 일부 또는 전체를 재정의하는 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-110">Create classes that override some or all of the default implementations.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dd8ea-111">전제 조건</span><span class="sxs-lookup"><span data-stu-id="dd8ea-111">Prerequisites</span></span>

<span data-ttu-id="dd8ea-112">C# 8.0 컴파일러를 포함하여 .NET Core를 실행하도록 머신을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-112">You’ll need to set up your machine to run .NET Core, including the C# 8.0 compiler.</span></span> <span data-ttu-id="dd8ea-113">C# 8.0 컴파일러는 [Visual Studio 2019 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) 또는 [.NET Core 3.0 SDK 및 이후 버전](https://dotnet.microsoft.com/download/dotnet-core)부터 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-113">The C# 8.0 compiler is available starting with [Visual Studio 2019, 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), or the [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or later.</span></span>

## <a name="limitations-of-extension-methods"></a><span data-ttu-id="dd8ea-114">확장 메서드의 제한 사항</span><span class="sxs-lookup"><span data-stu-id="dd8ea-114">Limitations of extension methods</span></span>

<span data-ttu-id="dd8ea-115">인터페이스의 일부로 나타나는 동작을 구현할 수 있는 한 가지 방법은 기본 동작을 제공하는 [확장 메서드](../programming-guide/classes-and-structs/extension-methods.md)를 정의하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-115">One way you can implement behavior that appears as part of an interface is to define [extension methods](../programming-guide/classes-and-structs/extension-methods.md) that provide the default behavior.</span></span> <span data-ttu-id="dd8ea-116">인터페이스는 해당 멤버를 구현하는 클래스에 더 큰 노출 영역을 제공하는 동시에 최소 멤버 집합을 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-116">Interfaces declare a minimum set of members while providing a greater surface area for any class that implements that interface.</span></span> <span data-ttu-id="dd8ea-117">예를 들어 <xref:System.Linq.Enumerable>의 확장 메서드는 모든 시퀀스가 LINQ 쿼리의 원본이 되도록 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-117">For example, the extension methods in <xref:System.Linq.Enumerable> provide the implementation for any sequence to be the source of a LINQ query.</span></span>

<span data-ttu-id="dd8ea-118">확장 메서드는 선언된 변수 형식을 사용하여 컴파일 시간에 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-118">Extension methods are resolved at compile time, using the declared type of the variable.</span></span> <span data-ttu-id="dd8ea-119">인터페이스를 구현하는 클래스는 모든 확장 메서드에 대해 더 나은 구현을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-119">Classes that implement the interface can provide a better implementation for any extension method.</span></span> <span data-ttu-id="dd8ea-120">컴파일러가 해당 구현을 선택할 수 있도록 변수 선언이 구현 형식과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-120">Variable declarations must match the implementing type to enable the compiler to choose that implementation.</span></span> <span data-ttu-id="dd8ea-121">컴파일 시간 형식이 인터페이스와 일치하는 경우 메서드 호출은 확장 메서드를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-121">When the compile-time type matches the interface, method calls resolve to the extension method.</span></span> <span data-ttu-id="dd8ea-122">확장 메서드의 또 다른 문제는 확장 메서드를 포함하는 클래스에 액세스할 수 있는 모든 위치에서 메서드에 액세스할 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-122">Another concern with extension methods is that those methods are accessible wherever the class containing the extension methods is accessible.</span></span> <span data-ttu-id="dd8ea-123">클래스는 확장 메서드에 선언된 기능을 제공해야 하는지 제공하지 않아야 하는지 여부에 관계없이 선언할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-123">Classes cannot declare if they should or should not provide features declared in extension methods.</span></span>

<span data-ttu-id="dd8ea-124">C# 8.0부터 기본 구현을 인터페이스 메서드로 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-124">Starting with C# 8.0, you can declare the default implementations as interface methods.</span></span> <span data-ttu-id="dd8ea-125">그러면 모든 클래스에서 자동으로 기본 구현을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-125">Then, every class automatically uses the default implementation.</span></span> <span data-ttu-id="dd8ea-126">더 나은 구현을 제공할 수 있는 모든 클래스는 더 나은 알고리즘으로 인터페이스 메서드를 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-126">Any class that can provide a better implementation can override the interface method definition with a better algorithm.</span></span> <span data-ttu-id="dd8ea-127">어떤 의미에서 이 기술은 [확장 메서드](../programming-guide/classes-and-structs/extension-methods.md)를 사용하는 방법과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-127">In one sense, this technique sounds similar to how you could use [extension methods](../programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="dd8ea-128">이 문서에서는 기본 인터페이스 구현에서 새 시나리오를 사용하도록 설정하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-128">In this article, you'll learn how default interface implementations enable new scenarios.</span></span>

## <a name="design-the-application"></a><span data-ttu-id="dd8ea-129">애플리케이션 설계</span><span class="sxs-lookup"><span data-stu-id="dd8ea-129">Design the application</span></span>

<span data-ttu-id="dd8ea-130">홈 자동화 애플리케이션을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-130">Consider a home automation application.</span></span> <span data-ttu-id="dd8ea-131">집 전체에서 사용할 수 있는 다양한 광원 및 표시등이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-131">You probably have many different types of lights and indicators that could be used throughout the house.</span></span> <span data-ttu-id="dd8ea-132">모든 광원은 켜고 끄고 현재 상태를 보고할 수 있도록 API가 지원되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-132">Every light must support APIs to turn them on and off, and to report the current state.</span></span> <span data-ttu-id="dd8ea-133">일부 광원 및 표시등은 다음과 같은 다른 기능을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-133">Some lights and indicators may support other features, such as:</span></span>

- <span data-ttu-id="dd8ea-134">광원을 켜고 타이머에 맞춰 끕니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-134">Turn light on, then turn it off after a timer.</span></span>
- <span data-ttu-id="dd8ea-135">일정 시간 동안 광원이 깜박입니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-135">Blink the light for a period of time.</span></span>

<span data-ttu-id="dd8ea-136">이러한 확장 기능 중 일부는 최소 설정을 지원하는 디바이스에서 에뮬레이트될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-136">Some of these extended capabilities could be emulated in devices that support the minimal set.</span></span> <span data-ttu-id="dd8ea-137">이는 기본 구현을 제공한다는 의미입니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-137">That indicates providing a default implementation.</span></span> <span data-ttu-id="dd8ea-138">더 많은 기능이 내장된 디바이스의 경우 디바이스 소프트웨어는 기본 기능을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-138">For those devices that have more capabilities built in, the device software would use the native capabilities.</span></span> <span data-ttu-id="dd8ea-139">다른 광원의 경우 인터페이스를 구현하고 기본 구현을 사용하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-139">For other lights, they could choose to implement the interface and use the default implementation.</span></span>

<span data-ttu-id="dd8ea-140">기본 인터페이스 멤버는 이 시나리오에서 확장 메서드보다 더 나은 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-140">Default interface members is a better solution for this scenario than extension methods.</span></span> <span data-ttu-id="dd8ea-141">클래스 작성자는 구현할 인터페이스를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-141">Class authors can control which interfaces they choose to implement.</span></span> <span data-ttu-id="dd8ea-142">선택한 인터페이스는 메서드로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-142">Those interfaces they choose are available as methods.</span></span> <span data-ttu-id="dd8ea-143">또한 기본 인터페이스 메서드는 기본적으로 가상이기 때문에 메서드 디스패치는 항상 클래스에서 구현을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-143">In addition, because default interface methods are virtual by default, the method dispatch always chooses the implementation in the class.</span></span> 

<span data-ttu-id="dd8ea-144">이러한 차이점을 보여주는 코드를 만들어 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-144">Let's create the code to demonstrate these differences.</span></span>

## <a name="create-interfaces"></a><span data-ttu-id="dd8ea-145">인터페이스 만들기</span><span class="sxs-lookup"><span data-stu-id="dd8ea-145">Create interfaces</span></span>

<span data-ttu-id="dd8ea-146">모든 광원의 동작을 정의하는 인터페이스를 만드는 것부터 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-146">Start by creating the interface that defines the behavior for all lights:</span></span>

[!code-csharp[Declare base interface](~/samples/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetILightInterfaceV1)]

<span data-ttu-id="dd8ea-147">기본 오버헤드 광원 픽스쳐는 다음 코드와 같이 이 인터페이스를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-147">A basic overhead light fixture might implement this interface as shown in the following code:</span></span>

[!code-csharp[First overhead light](~/samples/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetOverheadLightV1)]

<span data-ttu-id="dd8ea-148">이 자습서에서 코드는 IoT 디바이스를 구동하지 않지만 콘솔에 메시지를 작성하여 해당 활동을 에뮬레이트합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-148">In this tutorial, the code doesn't drive IoT devices, but emulates those activities by writing messages to the console.</span></span> <span data-ttu-id="dd8ea-149">집을 자동화하지 않고 코드를 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-149">You can explore the code without automating your house.</span></span>

<span data-ttu-id="dd8ea-150">다음으로 시간 제한 후 자동으로 꺼질 수 있는 광원의 인터페이스를 정의해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-150">Next, let's define the interface for a light that can automatically turn off after a timeout:</span></span>

[!code-csharp[pure Timer interface](~/samples/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetPureTimerInterface)]

<span data-ttu-id="dd8ea-151">기본 구현을 오버헤드 광원에 추가할 수 있지만, 이 인터페이스 정의를 수정하여 `virtual` 기본 구현을 제공하는 것이 더 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-151">You could add a basic implementation to the overhead light, but a better solution is to modify this interface definition to provide a `virtual` default implementation:</span></span>

[!code-csharp[Timer interface](~/samples/csharp/tutorials/mixins-with-interfaces/ITimerLight.cs?name=SnippetTimerLightFinal)]

<span data-ttu-id="dd8ea-152">이러한 변경 사항 추가로 `OverheadLight` 클래스는 인터페이스에 대한 지원을 선언하여 타이머 함수를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-152">By adding that change, the `OverheadLight` class can implement the timer function by declaring support for the interface:</span></span>

```csharp
public class OverheadLight : ITimerLight { }
```

<span data-ttu-id="dd8ea-153">다른 광원 형식은 보다 정교한 프로토콜을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-153">A different light type may support a more sophisticated protocol.</span></span> <span data-ttu-id="dd8ea-154">다음 코드와 같이 `TurnOnFor`에 대한 자체 구현을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-154">It can provide its own implementation for `TurnOnFor`, as shown in the following code:</span></span>

[!code-csharp[Override the timer function](~/samples/csharp/tutorials/mixins-with-interfaces/HalogenLight.cs?name=SnippetHalogenLight)]

<span data-ttu-id="dd8ea-155">가상 클래스 메서드를 재정의하는 것과 달리 `HalogenLight` 클래스의 `TurnOnFor` 선언에는 `override` 키워드가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-155">Unlike overriding virtual class methods, the declaration of `TurnOnFor` in the `HalogenLight` class does not use the `override` keyword.</span></span> 

## <a name="mix-and-match-capabilities"></a><span data-ttu-id="dd8ea-156">조합 및 일치 기능</span><span class="sxs-lookup"><span data-stu-id="dd8ea-156">Mix and match capabilities</span></span>

<span data-ttu-id="dd8ea-157">고급 기능을 도입할수록 기본 인터페이스 방법의 장점이 더 명확해집니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-157">The advantages of default interface methods become clearer as you introduce more advanced capabilities.</span></span> <span data-ttu-id="dd8ea-158">인터페이스를 사용하면 기능을 조합하고 일치시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-158">Using interfaces enables you to mix and match capabilities.</span></span> <span data-ttu-id="dd8ea-159">또한 각 클래스 작성자가 기본 구현과 사용자 지정 구현 중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-159">It also enables each class author to choose between the default implementation and a custom implementation.</span></span> <span data-ttu-id="dd8ea-160">깜박이는 광원에 대한 기본 구현으로 인터페이스를 추가해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-160">Let's add an interface with a default implementation for a blinking light:</span></span>

[!code-csharp[Define the blinking light interface](~/samples/csharp/tutorials/mixins-with-interfaces/IBlinkingLight.cs?name=SnippetBlinkingLight)]

<span data-ttu-id="dd8ea-161">기본 구현을 사용하면 모든 광원이 깜박일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-161">The default implementation enables any light to blink.</span></span> <span data-ttu-id="dd8ea-162">오버헤드 광원은 기본 구현을 사용하여 타이머 및 깜박임 기능을 모두 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-162">The overhead light can add both timer and blink capabilities using the default implementation:</span></span>

[!code-csharp[Use the default blink function](~/samples/csharp/tutorials/mixins-with-interfaces/OverheadLight.cs?name=SnippetOverheadLight)]

<span data-ttu-id="dd8ea-163">새로운 광원 형식인 `LEDLight`는 timer 함수와 blink 함수를 직접 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-163">A new light type, the `LEDLight` supports both the timer function and the blink function directly.</span></span> <span data-ttu-id="dd8ea-164">이 광원 스타일은 `ITimerLight` 및 `IBlinkingLight` 인터페이스를 모두 구현하고 `Blink` 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-164">This light style implements both the `ITimerLight` and `IBlinkingLight` interfaces, and overrides the `Blink` method:</span></span>

[!code-csharp[Override the blink function](~/samples/csharp/tutorials/mixins-with-interfaces/LEDLight.cs?name=SnippetLEDLight)]

<span data-ttu-id="dd8ea-165">`ExtraFancyLight`는 blink 및 timer 함수를 직접 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-165">An `ExtraFancyLight` might support both blink and timer functions directly:</span></span>

[!code-csharp[Override the blink and timer function](~/samples/csharp/tutorials/mixins-with-interfaces/ExtraFancyLight.cs?name=SnippetExtraFancyLight)]

<span data-ttu-id="dd8ea-166">이전에 만든 `HalogenLight`는 깜박임을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-166">The `HalogenLight` you created earlier doesn't support blinking.</span></span> <span data-ttu-id="dd8ea-167">따라서 지원되는 인터페이스 목록에 `IBlinkingLight`를 추가하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-167">So, don't add the `IBlinkingLight` to the list of its supported interfaces.</span></span>

## <a name="detect-the-light-types-using-pattern-matching"></a><span data-ttu-id="dd8ea-168">패턴 일치를 사용하여 광원 형식 검색</span><span class="sxs-lookup"><span data-stu-id="dd8ea-168">Detect the light types using pattern matching</span></span>

<span data-ttu-id="dd8ea-169">다음으로 몇 가지 테스트 코드를 작성해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-169">Next, let's write some test code.</span></span> <span data-ttu-id="dd8ea-170">C#의 [패턴 일치](../pattern-matching.md) 기능을 사용하여 지원되는 인터페이스를 검사하고 광원의 기능을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-170">You can make use of C#'s [pattern matching](../pattern-matching.md) feature to determine a light's capabilities by examining which interfaces it supports.</span></span>  <span data-ttu-id="dd8ea-171">다음 메서드는 각 광원의 지원되는 기능을 연습합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-171">The following method exercises the supported capabilities of each light:</span></span>

[!code-csharp[Test a light's capabilities](~/samples/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetTestLightFunctions)]

<span data-ttu-id="dd8ea-172">`Main` 메서드의 다음 코드는 각 광원 형식을 차례로 만들고 해당 광원을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-172">The following code in your `Main` method creates each light type in sequence and tests that light:</span></span>

[!code-csharp[Test a light's capabilities](~/samples/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetMainMethod)]

## <a name="how-the-compiler-determines-best-implementation"></a><span data-ttu-id="dd8ea-173">컴파일러가 최선의 구현을 결정하는 방법</span><span class="sxs-lookup"><span data-stu-id="dd8ea-173">How the compiler determines best implementation</span></span>

<span data-ttu-id="dd8ea-174">이 시나리오에서는 구현이 없는 기본 인터페이스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-174">This scenario shows a base interface without any implementations.</span></span> <span data-ttu-id="dd8ea-175">`ILight` 인터페이스에 메서드를 추가하면 새로운 복잡성이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-175">Adding a method into the `ILight` interface introduces new complexities.</span></span> <span data-ttu-id="dd8ea-176">기본 인터페이스 메서드를 제어하는 언어 규칙은 여러 파생 인터페이스를 구현하는 구체적인 클래스에 대한 영향을 최소화합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-176">The language rules governing default interface methods minimize the effect on the concrete classes that implement multiple derived interfaces.</span></span> <span data-ttu-id="dd8ea-177">새 메서드로 원래 인터페이스를 개선하여 사용 방법을 변경할 수 있는 방법을 확인해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-177">Let's enhance the original interface with a new method to show how that changes its use.</span></span> <span data-ttu-id="dd8ea-178">모든 표시등 광원은 해당 전원 상태를 열거형 값으로 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-178">Every indicator light can report its power status as an enumerated value:</span></span>

[!code-csharp[Enumeration for power status](~/samples/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetPowerStatus)]

<span data-ttu-id="dd8ea-179">기본 구현에서는 AC 전원이라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-179">The default implementation assumes AC power:</span></span>

[!code-csharp[Report a default power status](~/samples/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetILightInterface)]

<span data-ttu-id="dd8ea-180">`ExtraFancyLight`에서 `ILight` 인터페이스 및 파생된 인터페이스, `ITimerLight` 및 `IBlinkingLight`에 대한 지원을 선언하더라도 이러한 변경 내용은 완전히 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-180">These changes compile cleanly, even though the `ExtraFancyLight` declares support for the `ILight` interface and both derived interfaces, `ITimerLight` and `IBlinkingLight`.</span></span> <span data-ttu-id="dd8ea-181">`ILight` 인터페이스에 선언된 "가장 가까운" 구현은 하나뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-181">There's only one "closest" implementation declared in the `ILight` interface.</span></span> <span data-ttu-id="dd8ea-182">재정의를 선언한 모든 클래스는 하나의 "가장 가까운" 구현이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-182">Any class that declared an override would become the one "closest" implementation.</span></span> <span data-ttu-id="dd8ea-183">이전 클래스에서 다른 파생 인터페이스의 멤버를 재정의하는 예를 살펴보았습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-183">You saw examples in the preceding classes that overrode the members of other derived interfaces.</span></span>

<span data-ttu-id="dd8ea-184">여러 파생 인터페이스에서 동일한 메서드를 재정의하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-184">Avoid overriding the same method in multiple derived interfaces.</span></span> <span data-ttu-id="dd8ea-185">이렇게 하면 클래스가 파생된 두 인터페이스를 모두 구현할 때마다 모호한 메서드 호출을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-185">Doing so creates an ambiguous method call whenever a class implements both derived interfaces.</span></span> <span data-ttu-id="dd8ea-186">컴파일러는 더 나은 단일 메서드를 선택할 수 없으므로 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-186">The compiler can't pick a single better method so it issues an error.</span></span> <span data-ttu-id="dd8ea-187">예를 들어 `IBlinkingLight` 및 `ITimerLight` 모두 `PowerStatus` 재정의를 구현하는 경우 `OverheadLight`는 보다 구체적인 재정의를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-187">For example, if both the `IBlinkingLight` and `ITimerLight` implemented an override of `PowerStatus`, the `OverheadLight` would need to provide a more specific override.</span></span> <span data-ttu-id="dd8ea-188">그렇지 않으면 컴파일러는 두 파생 인터페이스의 구현 사이에서 선택할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-188">Otherwise, the compiler can't pick between the implementations in the two derived interfaces.</span></span> <span data-ttu-id="dd8ea-189">일반적으로 인터페이스 정의를 작게 유지하고 하나의 기능에 집중하여 이러한 상황을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-189">You can usually avoid this situation by keeping interface definitions small and focused on one feature.</span></span> <span data-ttu-id="dd8ea-190">이 시나리오에서 광원의 각 기능은 고유한 인터페이스입니다. 여러 인터페이스는 클래스에 의해서만 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-190">In this scenario, each capability of a light is its own interface; multiple interfaces are only inherited by classes.</span></span>

<span data-ttu-id="dd8ea-191">이 샘플은 클래스에 결합될 수 있는 불연속 기능을 정의할 수 있는 시나리오를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-191">This sample shows one scenario where you can define discrete features that can be mixed into classes.</span></span> <span data-ttu-id="dd8ea-192">클래스가 지원하는 인터페이스를 선언하여 지원되는 기능 집합을 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-192">You declare any set of supported functionality by declaring which interfaces a class supports.</span></span> <span data-ttu-id="dd8ea-193">가상 기본 인터페이스 메서드를 사용하면 클래스가 일부 또는 모든 인터페이스 메서드에 대해 다른 구현을 사용하거나 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-193">The use of virtual default interface methods enables classes to use or define a different implementation for any or all the interface methods.</span></span> <span data-ttu-id="dd8ea-194">이 언어 기능은 빌드 중인 실제 시스템을 모델링하는 새로운 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-194">This language capability provides new ways to model the real-world systems you're building.</span></span> <span data-ttu-id="dd8ea-195">기본 인터페이스 메서드는 해당 기능의 가상 구현을 사용하여 다른 기능을 조합하고 일치시킬 수 있는 관련 클래스를 더 명확하게 표현하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-195">Default interface methods provide a clearer way to express related classes that may mix and match different features using virtual implementations of those capabilities.</span></span>