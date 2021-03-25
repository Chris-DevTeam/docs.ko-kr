---
title: 비동기 반환 형식(C#)
description: 각 형식 및 추가 리소스에 대한 코드 예제를 통해 C#에서 비동기 메서드의 가능한 반환 형식에 대해 알아봅니다.
ms.date: 08/19/2020
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: 53eb3bedebb99cd829101eee4c2e190c0fb952bf
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653454"
---
# <a name="async-return-types-c"></a>비동기 반환 형식(C#)

비동기 메서드의 반환 형식은 다음과 같을 수 있습니다.

- <xref:System.Threading.Tasks.Task> - 작업을 수행하지만 아무 값도 반환하지 않는 비동기 메서드의 경우
- <xref:System.Threading.Tasks.Task%601> - 값을 반환하는 비동기 메서드의 경우
- `void` - 이벤트 처리기의 경우
- C# 7.0부터 액세스 가능한 `GetAwaiter` 메서드가 있는 모든 형식. `GetAwaiter` 메서드에서 반환된 개체는 <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType> 인터페이스를 구현해야 합니다.
- C# 8.0부터 ‘비동기 스트림’을 반환하는 비동기 메서드의 경우 <xref:System.Collections.Generic.IAsyncEnumerable%601>.

비동기 메서드에 관한 자세한 내용은 [async 및 await를 사용한 비동기 프로그래밍(C#)](./index.md)을 참조하세요.

Windows 워크로드와 관련된 몇 가지 다른 형식도 있습니다.

- <xref:System.Windows.Threading.DispatcherOperation> - Windows로 제한된 비동기 작업에 사용됩니다.
- <xref:Windows.Foundation.IAsyncAction> - 값을 반환하지 않는 UWP의 비동기 작업에 사용됩니다.
- <xref:Windows.Foundation.IAsyncActionWithProgress%601> - 진행률을 보고하지만 값을 반환하지 않는 UWP의 비동기 작업에 사용됩니다.
- <xref:Windows.Foundation.IAsyncOperation%601> - 값을 반환하는 UWP의 비동기 작업에 사용됩니다.
- <xref:Windows.Foundation.IAsyncOperationWithProgress%602> - 진행률을 보고하고 값을 반환하는 UWP의 비동기 작업에 사용됩니다.

## <a name="task-return-type"></a>Task 반환 형식

`return` 문을 포함하지 않거나 피연산자를 반환하지 않는 `return` 문을 포함하는 비동기 메서드의 반환 형식은 일반적으로 <xref:System.Threading.Tasks.Task>입니다. 이러한 메서드는 동기적으로 실행될 경우 `void`를 반환합니다. 비동기 메서드에 대해 <xref:System.Threading.Tasks.Task> 반환 형식을 사용하는 경우 호출된 비동기 메서드가 완료될 때까지 호출 메서드는 `await` 연산자를 사용하여 호출자의 완료를 일시 중단할 수 있습니다.

다음 예제에서 `WaitAndApologizeAsync` 메서드에는 `return` 문이 없으므로 메서드가 <xref:System.Threading.Tasks.Task> 개체를 반환합니다. `Task`를 반환하면 `WaitAndApologizeAsync`가 대기할 수 있습니다. <xref:System.Threading.Tasks.Task> 형식에는 반환 값이 없으므로 `Result` 속성이 포함되지 않습니다.

:::code language="csharp" source="snippets/async-return-types/async-returns2.cs" id="TaskReturn":::

동기 void를 반환하는 메서드에 대한 호출 문과 비슷하게 await 식 대신 await 문을 사용하여 `WaitAndApologizeAsync`가 대기됩니다. 이 경우 await 연산자를 적용하면 값이 산출되지 않습니다. `await`의 오른쪽 피연산자가 <xref:System.Threading.Tasks.Task%601>인 경우 `await` 식의 결과는 `T`입니다. `await`의 오른쪽 피연산자가 <xref:System.Threading.Tasks.Task>인 경우 `await` 및 해당 피연산자는 문입니다.

다음 코드와 같이 `WaitAndApologizeAsync` 호출을 await 연산자의 적용과 구분할 수 있습니다. 그러나 `Task`에는 `Result` 속성이 없으므로 await 연산자가 `Task`에 적용될 때 값이 생성되지 않습니다.

다음 코드에서는 `WaitAndApologizeAsync` 메서드 호출과 해당 메서드에서 반환하는 작업 대기를 구분합니다.

:::code language="csharp" source="snippets/async-return-types/async-returns2a.cs" id="AwaitTask":::

## <a name="tasktresult-return-type"></a>Task\<TResult\> 반환 형식

<xref:System.Threading.Tasks.Task%601> 반환 형식은 피연산자가 `TResult`인 [return](../../../language-reference/keywords/return.md) 문이 포함된 비동기 메서드에 사용합니다.

다음 예제에서 `GetLeisureHoursAsync` 메서드는 정수를 반환하는 `return` 문을 포함합니다. 따라서 메서드 선언은 `Task<int>`의 반환 형식을 지정해야 합니다. <xref:System.Threading.Tasks.Task.FromResult%2A> 비동기 메서드는 <xref:System.DateTime.DayOfWeek>를 반환하는 작업의 자리 표시자입니다.

:::code language="csharp" source="snippets/async-return-types/async-returns1.cs" id="LeisureHours":::

`ShowTodaysInfo` 메서드의 await 식 내에서 `GetLeisureHoursAsync`를 호출하면 await 식이 `GetLeisureHours`에서 반환된 작업에 저장된 정수 값(`leisureHours` 값)을 검색합니다. await 식에 대한 자세한 내용은 [await](../../../language-reference/operators/await.md)를 참조하세요.

다음 코드와 같이 `GetLeisureHoursAsync` 호출을 `await` 적용과 구분하면 `await`가 `Task<T>`에서 결과를 검색하는 방법을 더욱 잘 이해할 수 있습니다. 곧바로 대기 상태가 되지 않는 `GetLeisureHoursAsync` 메서드를 호출하면 메서드 선언에서 예상한 대로 `Task<int>`를 반환합니다. 예제에서 작업이 `getLeisureHoursTask` 변수에 할당됩니다. `getLeisureHoursTask`가 <xref:System.Threading.Tasks.Task%601>이기 때문에 `TResult` 형식의 <xref:System.Threading.Tasks.Task%601.Result> 속성을 포함합니다. 이 경우 `TResult`는 정수 형식을 나타냅니다. `await`가 `getLeisureHoursTask`에 적용되는 경우 await 식은 `getLeisureHoursTask`의 <xref:System.Threading.Tasks.Task%601.Result%2A> 속성 내용으로 평가됩니다. 값은 `ret` 변수에 할당됩니다.

> [!IMPORTANT]
> <xref:System.Threading.Tasks.Task%601.Result%2A> 속성은 차단 속성입니다. 해당 작업이 완료되기 전에 액세스하려고 하면, 작업이 완료되고 값을 사용할 수 있을 때까지 현재 활성화된 스레드가 차단됩니다. 대부분의 경우 속성에 직접 액세스하지 않고 `await`를 사용하여 값에 액세스해야 합니다.
>
> 이전 예제에서는 `Main` 메서드가 애플리케이션 종료 전에 `message`를 콘솔에 인쇄할 수 있도록 <xref:System.Threading.Tasks.Task%601.Result%2A> 속성의 값을 검색하여 주 스레드를 차단했습니다.

:::code language="csharp" source="snippets/async-return-types/async-returns1a.cs" id="StoreTask":::

## <a name="void-return-type"></a>Void 반환 형식

`void`반환 형식이 필요한 비동기 이벤트 처리기에 `void` 반환 형식을 사용합니다. 값을 반환하지 않는 이벤트 처리기 이외의 메서드의 경우 `void`를 반환하는 비동기 메서드를 대기할 수 없기 때문에 <xref:System.Threading.Tasks.Task>를 대신 반환해야 합니다. 해당 메서드의 호출자는 호출된 비동기 메서드가 마치는 것을 기다리지 않고 완료될 때까지 계속 진행해야 합니다. 호출자는 비동기 메서드가 생성하는 모든 값 또는 예외와 독립되어 있어야 합니다.

Void를 반환하는 비동기 메서드의 호출자는 메서드에서 throw되는 예외를 catch할 수 없으므로 처리되지 않은 예외를 사용하면 애플리케이션이 실패할 수 있습니다. <xref:System.Threading.Tasks.Task> 또는 <xref:System.Threading.Tasks.Task%601>를 반환하는 메서드가 예외를 throw하는 경우 이 예외는 반환된 작업에 저장됩니다. 작업이 대기하는 경우 예외가 다시 throw됩니다. 따라서 예외를 생성할 수 있는 모든 비동기 메서드에 <xref:System.Threading.Tasks.Task> 또는 <xref:System.Threading.Tasks.Task%601>의 반환 형식이 있고 메서드 호출이 대기 상태인지 확인해야 합니다.

비동기 메서드에서 예외를 catch하는 방법에 관한 자세한 내용은 [try-catch](../../../language-reference/keywords/try-catch.md) 문서의 [비동기 메서드의 예외](../../../language-reference/keywords/try-catch.md#exceptions-in-async-methods) 섹션을 참조하세요.

다음 예제에서는 비동기 이벤트 처리기의 동작을 보여줍니다. 예제 코드에서 비동기 이벤트 처리기는 주 스레드가 완료되면 이를 알려야 합니다. 그런 다음, 주 스레드는 비동기 이벤트 처리기가 프로그램을 종료하기 전에 완료될 때까지 대기할 수 있습니다.

:::code language="csharp" source="snippets/async-return-types/async-returns3.cs":::

## <a name="generalized-async-return-types-and-valuetasktresult"></a>일반화된 비동기 반환 형식 및 ValueTask\<TResult\>

C# 7.0부터 비동기 메서드는 awaiter 형식의 인스턴스를 반환하는 액세스 가능한 `GetAwaiter` 메서드가 있는 모든 형식을 반환할 수 있습니다. 또한 `GetAwaiter` 메서드가 반환하는 형식에는 <xref:System.Runtime.CompilerServices.AsyncMethodBuilderAttribute?displayProperty=nameWithType> 특성이 있어야 합니다. [작업과 유사한 반환 형식](../../../../../_csharplang/proposals/csharp-7.0/task-types.md)에 대한 기능 사양에서 자세한 내용을 알아볼 수 있습니다.

이 기능은 `await`의 피연산자에 대한 요구 사항을 설명하는 [대기 가능 식](../../../../../_csharplang/spec/expressions.md#awaitable-expressions)을 보완합니다. 일반화된 비동기 반환 형식을 사용하면 컴파일러가 다른 형식을 반환하는 `async` 메서드를 생성할 수 있습니다. 일반화된 비동기 반환 형식은 .NET 라이브러리의 성능 향상을 지원합니다. <xref:System.Threading.Tasks.Task> 및 <xref:System.Threading.Tasks.Task%601>는 참조 형식이므로 특히 타이트 루프에서 할당이 발생하는 경우 성능이 중요한 경로의 메모리 할당으로 인해 성능이 저하될 수 있습니다. 일반화된 반환 형식이 지원되면 추가 메모리 할당을 방지하기 위해 참조 형식 대신 간단한 값 형식을 반환할 수 있습니다.

.NET에서는 <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> 구조체를 일반화된 작업 반환 값의 간단한 구현으로 제공합니다. <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> 형식을 사용하려면 `System.Threading.Tasks.Extensions` NuGet 패키지를 프로젝트에 추가해야 합니다. 다음 예제에서는 <xref:System.Threading.Tasks.ValueTask%601> 구조체를 사용하여 두 주사위 굴리기 값을 검색합니다.

:::code language="csharp" source="snippets/async-return-types/async-valuetask.cs":::

일반화된 비동기 반환 형식 작성은 고급 시나리오이며 매우 특수한 환경에서 사용할 수 있습니다. 비동기 코드에 대한 대부분의 시나리오에 적용되는 `Task`, `Task<T>` 및 `ValueTask<T>` 형식을 대신 사용하는 것이 좋습니다.

## <a name="async-streams-with-iasyncenumerablet"></a>IAsyncEnumerable\<T\>을 사용하는 비동기 스트림

C# 8.0부터 비동기 메서드는 <xref:System.Collections.Generic.IAsyncEnumerable%601>을 통해 표시되는 ‘비동기 스트림’을 반환할 수 있습니다. 비동기 스트림은 반복되는 비동기 호출을 통해 요소가 청크로 생성될 때 스트림에서 읽은 항목을 열거하는 방법을 제공합니다. 다음 예제에서는 비동기 스트림을 생성하는 비동기 메서드를 보여 줍니다.

:::code language="csharp" source="snippets/async-return-types/AsyncStreams.cs" id="GenerateAsyncStream":::

앞의 예제에서는 문자열의 줄을 비동기적으로 읽습니다. 각 줄을 읽은 후에는 코드가 문자열에서 각 단어를 열거합니다. 호출자는 `await foreach` 문을 사용하여 각 단어를 열거합니다. 메서드는 소스 문자열에서 다음 줄을 비동기적으로 읽어야 하는 경우 대기합니다.

## <a name="see-also"></a>참조

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [완료되면 비동기 작업 처리](start-multiple-async-tasks-and-process-them-as-they-complete.md)
- [async 및 await를 사용한 비동기 프로그래밍(C#)](index.md)
- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
