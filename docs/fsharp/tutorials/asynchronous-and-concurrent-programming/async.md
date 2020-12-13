---
title: 비동기 프로그래밍
description: 'F #에서 핵심 함수형 프로그래밍 개념에서 파생 된 언어 수준 프로그래밍 모델을 기반으로 비동기에 대 한 명확한 지원을 제공 하는 방법에 대해 알아봅니다.'
ms.date: 08/15/2020
ms.openlocfilehash: 8bf8d6987187377cc1f44e77141b5d70d873f849
ms.sourcegitcommit: fcbe432482464b1639decad78cc4dc8387c6269e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97366817"
---
# <a name="async-programming-in-f"></a>F #의 비동기 프로그래밍\#

비동기 프로그래밍은 다양 한 이유로 최신 응용 프로그램에 필수적인 메커니즘입니다. 대부분의 개발자가 직면 하는 두 가지 주요 사용 사례는 다음과 같습니다.

- 많은 수의 동시 들어오는 요청을 처리할 수 있는 서버 프로세스를 제공 하는 동시에 프로세스의 외부 시스템 또는 서비스에서 기다립니다 입력을 요청 하는 동안 시스템 리소스를 최소화 합니다.
- 백그라운드 작업을 동시에 진행 하는 동안 응답성이 뛰어난 UI 또는 주 스레드 유지 관리

백그라운드 작업은 종종 여러 스레드를 사용 하는 경우를 제외 하 고 비동기 및 다중 스레딩의 개념을 별도로 고려 하는 것이 중요 합니다. 사실 이러한 문제는 별개의 문제 이며 다른 항목을 의미 하지는 않습니다. 이 문서에서는 별도의 개념에 대해 자세히 설명 합니다.

## <a name="asynchrony-defined"></a>비동기 정의 됨

이전 점-비동기은 여러 스레드를 사용 하는 것과 독립적입니다. 조금 더 자세히 설명 합니다. 경우에 따라 관련 된 세 가지 개념은 서로 독립적입니다.

- 동시성 여러 계산이 겹치는 기간 동안 실행 되는 경우
- 병렬로 단일 계산의 여러 계산 또는 여러 부분이 정확히 동시에 실행 되는 경우
- 비동기 하나 이상의 계산이 주 프로그램 흐름과 별도로 실행 될 수 있는 경우

세 가지 모두 직교 개념 이지만 특히 함께 사용 하는 경우에는 쉽게 연결할 수 있습니다. 예를 들어 여러 비동기 계산을 동시에 실행 해야 할 수 있습니다. 이 관계는 병렬 처리 또는 비동기가 서로를 의미 하는 것은 아닙니다.

"Etymology" 라는 단어를 고려 하는 경우에는 두 가지 관련이 있습니다.

- "not"을 의미 하는 "a"입니다.
- "동기", 즉 "동시" 의미를 의미 합니다.

이러한 두 용어를 함께 배치 하는 경우 "비동기"는 "동시에" 없음을 의미 합니다. 간단하죠. 이 정의에서는 동시성 또는 병렬 처리의 영향을 주지 않습니다. 이는 실제로도 마찬가지입니다.

실제로 F #의 비동기 계산은 주 프로그램 흐름과 독립적으로 실행 되도록 예약 됩니다. 이러한 독립적인 실행은 동시성이 나 병렬 처리를 의미 하지 않으며 계산이 항상 백그라운드에서 발생 한다는 것을 의미 하지는 않습니다. 실제로 비동기 계산은 계산의 특성과 계산을 실행 하는 환경에 따라 동기적으로 실행 될 수도 있습니다.

가장 중요 한 요점은는 비동기 계산이 주 프로그램 흐름과 독립적 이라고 하는 것입니다. 비동기 계산이 실행 되는 시기 또는 방법에 대 한 보장은 거의 없지만 오케스트레이션 하 고 예약 하는 몇 가지 방법이 있습니다. 이 문서의 나머지 부분에서는 F # 비동기의 핵심 개념 및 F #에 기본 제공 된 형식, 함수 및 식을 사용 하는 방법에 대해 살펴봅니다.

## <a name="core-concepts"></a>핵심 개념

F #에서 비동기 프로그래밍은 세 가지 핵심 개념을 중심으로 합니다.

- 구성 가능한 `Async<'T>` 비동기 계산을 나타내는 형식입니다.
- 비동기 `Async` 작업을 예약 하 고, 비동기 계산을 구성 하 고, 비동기 결과를 변환 하는 데 사용할 수 있는 모듈 함수
- `async { }`비동기 계산을 작성 하 고 제어 하기 위한 편리한 구문을 제공 하는 [계산 식](../../language-reference/computation-expressions.md)입니다.

다음 예제에서는 이러한 세 가지 개념을 확인할 수 있습니다.

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn $"File {fileName} has %d{bytes.Length} bytes"
    }

[<EntryPoint>]
let main argv =
    printTotalFileBytes "path-to-file.txt"
    |> Async.RunSynchronously

    Console.Read() |> ignore
    0
```

이 예제에서 함수는 `printTotalFileBytes` 형식입니다 `string -> Async<unit>` . 함수를 호출 하면 실제로 비동기 계산이 실행 되지 않습니다. 대신 `Async<unit>` 비동기적으로 실행할 작업의 *사양* 역할을 하는를 반환 합니다. `Async.AwaitTask`의 결과를 <xref:System.IO.File.ReadAllBytesAsync%2A> 적절 한 형식으로 변환 하는 본문에서를 호출 합니다.

또 다른 중요 한 줄은에 대 한 호출입니다 `Async.RunSynchronously` . 이는 실제로 F # 비동기 계산을 실행 하려는 경우 호출 해야 하는 비동기 모듈 시작 함수 중 하나입니다.

이는 c #/Visual Basic의 프로그래밍 스타일과 기본적인 차이점입니다 `async` . F #에서 비동기 계산은 **콜드 작업** 으로 간주할 수 있습니다. 실제로를 실행 하려면 명시적으로 시작 해야 합니다. 이는 c # 또는 Visual Basic 보다 훨씬 쉽게 비동기 작업을 결합 하 고 시퀀스를 수행할 수 있기 때문에 몇 가지 이점이 있습니다.

## <a name="combine-asynchronous-computations"></a>비동기 계산 결합

다음은 계산을 결합 하 여 이전 예제를 기반으로 하는 예제입니다.

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn $"File {fileName} has %d{bytes.Length} bytes"
    }

[<EntryPoint>]
let main argv =
    argv
    |> Seq.map printTotalFileBytes
    |> Async.Parallel
    |> Async.Ignore
    |> Async.RunSynchronously

    0
```

여기에서 볼 수 있듯이 함수에는 `main` 몇 가지 추가 요소가 있습니다. 개념적으로 다음을 수행 합니다.

1. 를 사용 하 여 명령줄 인수를 계산 시퀀스로 변환 `Async<unit>` `Seq.map` 합니다.
2. 계산을 `Async<'T[]>` 실행 하는 동시에 실행을 예약 하 고 실행 하는를 만듭니다 `printTotalFileBytes` .
3. `Async<unit>`병렬 계산을 실행 하 고 해당 결과를 무시 하는을 만듭니다 ( `unit[]` ).
4. 를 사용 하 여 전체 구성 된 계산을 명시적으로 실행 `Async.RunSynchronously` 하면이 작업이 완료 될 때까지 차단 됩니다.

이 프로그램이 실행 될 때는 `printTotalFileBytes` 각 명령줄 인수에 대해 병렬로 실행 됩니다. 비동기 계산은 프로그램 흐름과 별개로 실행 되므로 정보를 인쇄 하 고 실행을 완료 하는 순서가 정의 되어 있지 않습니다. 계산은 병렬로 예약 되지만 실행 순서는 보장 되지 않습니다.

## <a name="sequence-asynchronous-computations"></a>시퀀스 비동기 계산

`Async<'T>`는 이미 실행 중인 태스크가 아니라 작업 사양 이므로 더 복잡 한 변환을 쉽게 수행할 수 있습니다. 다음은 비동기 계산 집합을 시퀀스 하 여 한 번 실행 하는 예제입니다.

```fsharp
let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn $"File {fileName} has %d{bytes.Length} bytes"
    }

[<EntryPoint>]
let main argv =
    argv
    |> Seq.map printTotalFileBytes
    |> Async.Sequential
    |> Async.Ignore
    |> Async.RunSynchronously
    |> ignore
```

이렇게 하면 병렬로 일정을 `printTotalFileBytes` 예약 하는 대신의 요소 순서에 따라 실행 되도록 예약 됩니다 `argv` . 선행 계산의 실행이 완료 될 때까지 각 연속 작업이 예약 되지 않기 때문에 계산이 실행에 겹치지 않도록 시퀀싱 됩니다.

## <a name="important-async-module-functions"></a>중요 한 비동기 모듈 함수

F #에서 비동기 코드를 작성 하는 경우 일반적으로 계산 예약을 처리 하는 프레임 워크와 상호 작용 합니다. 그러나이 경우에는 항상 그렇지는 않지만 비동기 작업을 예약 하는 데 사용할 수 있는 다양 한 함수를 이해 하는 것이 좋습니다.

F # 비동기 계산은 이미 실행 중인 작업의 표현이 아니라 작업의 _사양_ 이므로 시작 함수를 사용 하 여 명시적으로 시작 해야 합니다. 여러 컨텍스트에서 유용 하 게 사용할 수 있는 여러 [비동기 시작 메서드가](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#section0) 있습니다. 다음 섹션에서는 몇 가지 일반적인 시작 함수에 대해 설명 합니다.

### <a name="asyncstartchild"></a>Async. StartChild

비동기 계산 내에서 자식 계산을 시작 합니다. 이렇게 하면 여러 비동기 계산을 동시에 실행할 수 있습니다. 자식 계산은 부모 계산과 함께 취소 토큰을 공유 합니다. 부모 계산이 취소 되 면 자식 계산도 취소 됩니다.

서명:

```fsharp
computation: Async<'T> * timeout: ?int -> Async<Async<'T>>
```

사용해야 하는 경우:

- 한 번에 여러 비동기 계산을 동시에 실행 하는 것이 아니라 동시에 병렬로 예약 하지 않으려는 경우
- 자식 계산의 수명을 부모 계산의 수명에 연결 하려는 경우

조사할 내용:

- 를 사용 하 여 여러 계산을 시작 `Async.StartChild` 하는 것은 병렬로 예약 하는 것과는 다릅니다. 계산을 병렬로 예약 하려는 경우를 사용 `Async.Parallel` 합니다.
- 부모 계산을 취소 하면 시작 된 모든 자식 계산의 취소가 트리거됩니다.

### <a name="asyncstartimmediate"></a>StartImmediate

현재 운영 체제 스레드에서 즉시 시작 하는 비동기 계산을 실행 합니다. 이는 계산 중에 호출 스레드에서 무언가를 업데이트 해야 하는 경우에 유용 합니다. 예를 들어 비동기 계산에서 UI를 업데이트 해야 하는 경우 (예: 진행률 표시줄 업데이트)을 `Async.StartImmediate` 사용 해야 합니다.

서명:

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

사용해야 하는 경우:

- 비동기 계산의 중간에 있는 호출 스레드에서 무언가를 업데이트 해야 하는 경우입니다.

조사할 내용:

- 비동기 계산의 코드는 예약 되어야 하는 모든 스레드에 대해 실행 됩니다. 이는 해당 스레드가 UI 스레드와 같은 특정 방식으로 중요 한 경우 문제가 될 수 있습니다. 이러한 경우 `Async.StartImmediate` 는 사용 하기에 적합 하지 않을 수 있습니다.

### <a name="asyncstartastask"></a>Async.startastask

스레드 풀에서 계산을 실행 합니다. <xref:System.Threading.Tasks.Task%601>계산이 종료 된 후 (결과 생성, 예외 throw 또는 취소 됨) 해당 상태에서 완료 되는를 반환 합니다. 취소 토큰을 제공 하지 않으면 기본 취소 토큰이 사용 됩니다.

서명:

```fsharp
computation: Async<'T> * taskCreationOptions: ?TaskCreationOptions * cancellationToken: ?CancellationToken -> Task<'T>
```

사용해야 하는 경우:

- <xref:System.Threading.Tasks.Task%601>비동기 계산 결과를 나타내기 위해를 생성 하는 .NET API를 호출 해야 하는 경우

조사할 내용:

- 이 호출은 추가 개체를 할당 하며이 `Task` 는 자주 사용 되는 경우 오버 헤드를 증가 시킬 수 있습니다.

### <a name="asyncparallel"></a>Async. Parallel

병렬로 실행 되는 비동기 계산의 시퀀스를 예약 하 여 결과 배열을 제공 된 순서 대로 생성 합니다. 매개 변수를 지정 하 여 병렬 처리 수준을 선택적으로 조정/제한 할 수 있습니다 `maxDegreeOfParallelism` .

서명:

```fsharp
computations: seq<Async<'T>> * ?maxDegreeOfParallelism: int -> Async<'T[]>
```

사용하는 시기:

- 계산 집합을 동시에 실행 해야 하며 실행 순서에 의존 하지 않는 경우
- 모든 작업이 완료 될 때까지 병렬로 예약 된 계산 결과가 필요 하지 않은 경우

조사할 내용:

- 모든 계산이 완료 되 면 결과 값 배열에만 액세스할 수 있습니다.
- 예약을 종료할 때마다 계산이 실행 됩니다. 이 동작은 실행 순서에 의존할 수 없음을 의미 합니다.

### <a name="asyncsequential"></a>Async. 순차

전달 되는 순서 대로 실행 되는 비동기 계산의 시퀀스를 예약 합니다. 첫 번째 계산이 실행 되 고, 그 다음에는 식으로 실행 됩니다. 계산이 병렬로 실행 되지 않습니다.

서명:

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

사용하는 시기:

- 여러 계산을 순서 대로 실행 해야 하는 경우

조사할 내용:

- 모든 계산이 완료 되 면 결과 값 배열에만 액세스할 수 있습니다.
- 계산은이 함수로 전달 되는 순서 대로 실행 되므로 결과가 반환 되기 전에 시간이 더 걸릴 수 있습니다.

### <a name="asyncawaittask"></a>Async. AwaitTask

지정 된가 완료 될 때까지 대기 하 <xref:System.Threading.Tasks.Task%601> 고 그 결과를로 반환 하는 비동기 계산을 반환 합니다. `Async<'T>`

서명:

```fsharp
task: Task<'T> -> Async<'T>
```

사용해야 하는 경우:

- <xref:System.Threading.Tasks.Task%601>F # 비동기 계산 내에서을 반환 하는 .NET API를 사용 하는 경우.

조사할 내용:

- 예외는 <xref:System.AggregateException> 작업 병렬 라이브러리의 규칙에 따라 래핑됩니다 .이 동작은 F # async가 일반적으로 발생 하는 예외와는 다릅니다.

### <a name="asynccatch"></a>Async. Catch

지정 된를 실행 하 고를 반환 하는 비동기 계산을 만듭니다 `Async<'T>` `Async<Choice<'T, exn>>` . 지정 된가 `Async<'T>` 성공적으로 완료 되 면 `Choice1Of2` 결과 값과 함께이 반환 됩니다. 완료 되기 전에 예외가 throw 되 면 `Choice2of2` 발생 한 예외와 함께이 반환 됩니다. 여러 계산으로 구성 된 비동기 계산에서 사용 되는 경우 이러한 계산 중 하나가 예외를 throw 하는 경우 포괄 계산이 완전히 중지 됩니다.

서명:

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

사용해야 하는 경우:

- 예외가 발생 하 여 실패할 수 있는 비동기 작업을 수행할 때 호출자에서 해당 예외를 처리 하려는 경우

조사할 내용:

- 결합 또는 시퀀스 된 비동기 계산을 사용 하는 경우 "내부" 계산 중 하나가 예외를 throw 하는 경우 포괄 계산이 완전히 중지 됩니다.

### <a name="asyncignore"></a>Async. 무시

지정 된 계산을 실행 하지만 해당 결과를 삭제 하는 비동기 계산을 만듭니다.

서명:

```fsharp
computation: Async<'T> -> Async<unit>
```

사용해야 하는 경우:

- 비동기 계산을 수행 하는 경우에는 해당 결과가 필요 하지 않습니다. 이는 `ignore` 비동기 코드가 아닌 코드에 대 한 함수와 유사 합니다.

조사할 내용:

- 를 사용 하려는 경우 `Async.Ignore` `Async.Start` 또는에서 요구 하는 다른 기능을 사용 하려는 경우 `Async<unit>` 결과를 삭제 하는 것이 좋습니다. 형식 서명에 맞게 결과를 삭제 하지 않습니다.

### <a name="asyncrunsynchronously"></a>RunSynchronously

비동기 계산을 실행 하 고 호출 스레드에서 해당 결과를 기다립니다 합니다. 계산에서 예외를 양보 하는 경우 예외를 전파 합니다. 이 호출이 차단 되 고 있습니다.

서명:

```fsharp
computation: Async<'T> * timeout: ?int * cancellationToken: ?CancellationToken -> 'T
```

사용하는 시기:

- 필요할 경우 응용 프로그램에서 실행 파일에 대 한 진입점에서 한 번만 사용 합니다.
- 성능이 걱정 되지 않으며 다른 비동기 작업 집합을 한 번에 실행 하려는 경우.

조사할 내용:

- 호출은 `Async.RunSynchronously` 실행이 완료 될 때까지 호출 스레드를 차단 합니다.

### <a name="asyncstart"></a>Async. 시작

스레드 풀에서을 반환 하는 비동기 계산을 시작 `unit` 합니다. 는 완료 될 때까지 기다리거나 예외 결과를 관찰 하지 않습니다. 로 시작 하는 중첩 된 계산은 해당 계산을 `Async.Start` 호출한 부모 계산과 독립적으로 시작 되며, 해당 수명은 부모 계산과 연결 되지 않습니다. 부모 계산이 취소 되 면 자식 계산이 취소 되지 않습니다.

서명:

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

다음 경우에만 사용:

- 결과를 생성 하지 않거나 하나를 처리 해야 하는 비동기 계산이 있습니다.
- 비동기 계산의 완료 시기를 알 필요가 없습니다.
- 비동기 계산이 실행 되는 스레드를 걱정 하지 않습니다.
- 실행으로 인해 발생 하는 예외를 인식 하거나 보고할 필요가 없습니다.

조사할 내용:

- 로 시작 된 계산에 의해 발생 `Async.Start` 한 예외는 호출자에 게 전파 되지 않습니다. 호출 스택이 완전히 해제 됩니다.
- 로 시작 하는 모든 작업 (예: 호출 `printfn` )은 `Async.Start` 프로그램 실행의 주 스레드에서 효과가 발생 하지 않습니다.

## <a name="interoperate-with-net"></a>.NET과 상호 운용

[비동기/](../../../standard/async.md)대기 스타일 비동기 프로그래밍을 사용 하는 .net 라이브러리 또는 c # 코드 베이스를 사용 하 여 작업할 수 있습니다. C # 및 대부분의 .NET 라이브러리는 <xref:System.Threading.Tasks.Task%601> 및 형식을의 <xref:System.Threading.Tasks.Task> 핵심 추상화로 사용 하기 때문에 `Async<'T>` 이러한 두 가지 방법 간에 경계를 비동기 합니다.

### <a name="how-to-work-with-net-async-and-taskt"></a>.NET async를 사용 하 여 작업 하는 방법 `Task<T>`

를 사용 하는 .NET 비동기 라이브러리 및 코드 베이스 작업 <xref:System.Threading.Tasks.Task%601> (즉, 반환 값이 있는 비동기 계산)은 간단 하며 F #을 기본적으로 지원 합니다.

함수를 사용 하 여 `Async.AwaitTask` .net 비동기 계산을 대기할 수 있습니다.

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

함수를 사용 하 여 `Async.StartAsTask` .net 호출자에 비동기 계산을 전달할 수 있습니다.

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a>.NET async를 사용 하 여 작업 하는 방법 `Task`

(즉, 값을 반환 하지 않는 .NET 비동기 계산)를 사용 하는 Api를 사용 하려면를로 <xref:System.Threading.Tasks.Task> 변환 하는 추가 함수를 추가 해야 할 수 있습니다 `Async<'T>` <xref:System.Threading.Tasks.Task> .

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

`Async.AwaitTask`을 입력으로 허용 하는가 이미 있는 경우 <xref:System.Threading.Tasks.Task> 이 함수와 이전에 정의 된 `startTaskFromAsyncUnit` 함수를 사용 하면 <xref:System.Threading.Tasks.Task> F # 비동기 계산에서 형식을 시작 하 고 기다릴 수 있습니다.

## <a name="relationship-to-multi-threading"></a>다중 스레딩에 대 한 관계

이 문서 전체에서 스레딩을 언급 했지만 다음 두 가지 중요 한 사항을 기억해 야 합니다.

1. 현재 스레드에서 명시적으로 시작 하지 않는 한 비동기 계산과 스레드 간의 선호도는 없습니다.
1. F #의 비동기 프로그래밍은 다중 스레딩에 대 한 추상화가 아닙니다.

예를 들어 계산은 작업의 특성에 따라 실제로 호출자의 스레드에서 실행 될 수 있습니다. 계산이 "대기 중" 기간 (예: 네트워크 호출이 전송 중인 경우) 사이에서 유용한 작업을 수행 하기 위해 약간의 시간 동안 borrowing "이동" 할 수도 있습니다.

F #은 현재 스레드에서 비동기 계산을 시작 하는 몇 가지 기능을 제공 하지만 (또는 현재 스레드에서 명시적으로는 그렇지 않음) 비동기 일반적으로 특정 스레딩 전략과 연결 되지 않습니다.

## <a name="see-also"></a>참고 항목

- [F # 비동기 프로그래밍 모델](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [Jet의 F # Async 가이드](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [재미 있고 이익을 위한 F #의 비동기 프로그래밍 가이드](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [C #의 Async 및 F #: 비동기 알려진 문제 C #](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
