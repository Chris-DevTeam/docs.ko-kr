---
title: 스레드 및 스레딩 사용
description: 여러 작업을 동시에 수행(다중 스레딩)하는 애플리케이션을 작성할 수 있도록 .NET에서 스레드와 스레딩을 사용하는 방법에 대해 알아봅니다.
ms.date: 08/08/2018
helpviewer_keywords:
- threading [.NET], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
ms.openlocfilehash: 85968cfb1a228826429876e525f0c8452f97cfc4
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826094"
---
# <a name="using-threads-and-threading"></a>스레드 및 스레딩 사용

.NET에서는 동시에 여러 작업을 수행하는 애플리케이션을 작성할 수 있습니다. 다른 작업을 지연시킬 수 있는 작업은 별도 스레드에서 실행할 수 있으며, 이 프로세스를 *다중 스레딩* 또는 *자유 스레딩* 이라고 합니다.  
  
다중 스레딩을 사용하는 애플리케이션은 프로세서를 많이 사용하는 작업이 별도 스레드에서 실행될 때 사용자 인터페이스가 활성 상태로 유지되기 때문에 사용자 입력에 더 빠르게 응답합니다. 또한 다중 스레딩은 작업이 증가함에 따라 스레드를 추가할 수 있으므로 확장 가능한 애플리케이션을 만들 때에도 유용합니다.

> [!NOTE]
> 애플리케이션 스레드의 동작을 보다 강력하게 제어해야 하는 경우 직접 스레드를 관리할 수 있습니다. 그러나 <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> 및 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 클래스, [PLINQ(병렬 LINQ)](../parallel-programming/introduction-to-plinq.md), <xref:System.Collections.Concurrent?displayProperty=nameWithType> 네임스페이스의 새로운 동시 컬렉션 클래스, 그리고 스레드가 아닌 작업 개념을 기반으로 하는 새로운 프로그래밍 모델로 인해 다중 스레드 프로그래밍이 매우 간소화되었습니다. 자세한 내용은 [병렬 프로그래밍](../parallel-programming/index.md) 및 [TPL(작업 병렬 라이브러리)](../parallel-programming/task-parallel-library-tpl.md)을 참조하세요.

## <a name="how-to-create-and-start-a-new-thread"></a>방법: 새 스레드 만들기 및 시작

<xref:System.Threading.Thread?displayProperty=nameWithType> 클래스의 새 인스턴스를 만들고 생성자에 대한 새 스레드에서 실행하려는 메서드의 이름을 제공하여 새 스레드를 만듭니다. 생성된 스레드를 시작하려면 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> 메서드를 호출합니다. 자세한 내용 및 예제는 [스레드 만들기 및 시작할 때 데이터 전달](creating-threads-and-passing-data-at-start-time.md) 문서 및 <xref:System.Threading.Thread> API 참조를 참조하세요.

## <a name="how-to-stop-a-thread"></a>방법: 스레드 중지

스레드의 실행을 종료하려면 <xref:System.Threading.CancellationToken?displayProperty=nameWithType>을 사용합니다. 이 메서드는 스레드를 협조적으로 중지하는 단일화된 방법을 제공합니다. 자세한 내용은 [관리형 스레드의 취소](cancellation-in-managed-threads.md)를 참조하세요.

경우에 따라 스레드의 협조적 중지가 불가할 수 있는데, 이는 협조적 취소를 위해 설계되지 않은 타사 코드를 실행하기 때문입니다. 이 경우 실행을 강제로 종료하는 것이 좋습니다. 스레드 실행을 강제로 종료하려면 .NET Framework에서 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 메서드를 사용할 수 있습니다. 해당 메서드는 호출되는 스레드에서 <xref:System.Threading.ThreadAbortException>을 발생시킵니다. 자세한 내용은 [스레드 제거](destroying-threads.md)를 참조하세요. .NET Core는 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 메서드를 지원하지 않습니다. .NET Core에서 강제로 타사 코드 실행을 종료해야 하는 경우 별도의 프로세스에서 실행하고 <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>를 사용합니다.

<xref:System.Threading.CancellationToken?displayProperty=nameWithType>은 .NET Framework 4 이전 버전에는 사용할 수 없습니다. 이전 .NET Framework 버전에서 스레드를 중지하려면 스레드 동기화 기법을 사용하여 협조적 취소를 수동으로 구현합니다. 예를 들어 `shouldStop` 일회성 부울 필드를 만든 다음 이를 사용하여 스레드에 의해 실행되는 코드의 중지를 요청할 수 있습니다. 자세한 내용은 C# 참조의 [volatile](../../csharp/language-reference/keywords/volatile.md)과 <xref:System.Threading.Volatile?displayProperty=nameWithType>을 참조하세요.

<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> 메서드를 사용하여 호출 스레드가 중지 중인 스레드가 종료될 때까지 기다리도록 합니다.

## <a name="how-to-pause-or-interrupt-a-thread"></a>방법: 스레드 일시 중지 또는 중단

<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> 메서드를 사용하여 지정된 시간 동안 현재 스레드를 일시 중지합니다. <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 메서드를 호출하여 차단된 스레드를 중단할 수 있습니다. 자세한 내용은 [스레드 일시 중지 및 중단](pausing-and-resuming-threads.md)을 참조하세요.

## <a name="thread-properties"></a>스레드 속성

다음 표에서는 <xref:System.Threading.Thread> 속성의 일부를 보여줍니다.  
  
|속성|설명|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|스레드가 시작되었으며 정상적으로 종료 또는 중단되지 않은 경우 `true`를 반환합니다.|  
|<xref:System.Threading.Thread.IsBackground%2A>|스레드가 백그라운드 스레드인지를 나타내는 부울을 가져오거나 설정합니다. 백그라운드 스레드는 포그라운드 스레드와 유사하지만 백그라운드 스레드의 경우 프로세스가 중지되도록 허용합니다. 프로세스에 속하는 모든 포그라운드 스레드가 중지되면 공용 언어 런타임은 여전히 활성 상태인 백그라운드 스레드에 대해 <xref:System.Threading.Thread.Abort%2A> 메서드를 호출하여 프로세스를 종료합니다. 자세한 내용은 [포그라운드 및 백그라운드 스레드](foreground-and-background-threads.md)를 참조하세요.|  
|<xref:System.Threading.Thread.Name%2A>|스레드의 이름을 가져오거나 설정합니다. 대체로 디버그할 때 개별 스레드를 찾는 데 사용됩니다.|  
|<xref:System.Threading.Thread.Priority%2A>|운영 체제에서 스레드 예약의 우선 순위를 지정하는 데 사용되는 <xref:System.Threading.ThreadPriority> 값을 가져오거나 설정합니다. 자세한 내용은 [스레드 예약](scheduling-threads.md) 및 <xref:System.Threading.ThreadPriority> 참조를 참조하세요.|  
|<xref:System.Threading.Thread.ThreadState%2A>|현재 스레드의 상태를 포함하는 <xref:System.Threading.ThreadState> 값을 가져옵니다.|  

## <a name="see-also"></a>참조

- <xref:System.Threading.Thread?displayProperty=nameWithType>
- [스레드 및 스레딩](threads-and-threading.md)
- [병렬 프로그래밍](../parallel-programming/index.md)
