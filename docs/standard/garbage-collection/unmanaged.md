---
title: 관리되지 않는 리소스 정리
description: 파일, 창, 네트워크나 데이터베이스 연결과 같이 .NET 가비지 수집기에서 처리하지 않는 비관리형 리소스를 정리하는 방법을 참조하세요.
ms.date: 05/13/2020
helpviewer_keywords:
- Close method
- Dispose method
- garbage collector
- garbage collection, unmanaged resources
- cleanup operations
- explicit cleanups
- unmanaged resource cleanup
- Finalize method
ms.assetid: a17b0066-71c2-4ba4-9822-8e19332fc213
ms.openlocfilehash: edfb01411df3d974073a397a20f58acdcd8521f3
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94827505"
---
# <a name="cleaning-up-unmanaged-resources"></a>관리되지 않는 리소스 정리

사용자 애플리케이션에서 만들어지는 대부분의 개체에 대해 [.NET 가비지 수집기](index.md)를 사용하여 메모리 관리를 처리할 수 있습니다. 그러나 관리되지 않는 리소스를 포함하는 개체를 만든 경우에는 해당 개체의 사용을 마치면 이러한 리소스를 명시적으로 해제해야 합니다. 가장 일반적인 형태의 관리되지 않는 리소스로는 파일, 창, 네트워크 연결 또는 데이터베이스 연결 등의 운영 체제 리소스를 래핑하는 개체를 들 수 있습니다. 가비지 수집기에서는 관리되지 않는 리소스를 캡슐화하는 개체의 수명을 추적할 수 있지만, 관리되지 않는 리소스를 해제하고 정리하는 방법에 대해서는 알 수 없습니다.

형식이 관리되지 않는 리소스를 사용하는 경우 다음을 수행해야 합니다.

- [삭제 패턴](implementing-dispose.md)을 구현합니다. 이를 수행하려면 관리되지 않는 리소스의 명확한 해제를 활성화하기 위해 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 구현을 제공해야 합니다. 개체 및 해당 개체에서 사용하는 리소스가 더 이상 필요하지 않은 경우 형식의 소비자가 <xref:System.IDisposable.Dispose%2A>를 호출합니다. <xref:System.IDisposable.Dispose%2A> 메서드가 관리되지 않는 리소스를 즉시 해제합니다.

- 형식의 소비자가 실수로 <xref:System.IDisposable.Dispose%2A>를 호출하지 않은 경우 관리되지 않는 리소스가 해제되는 방법을 제공합니다. 이때 다음과 같은 두 가지 방법을 사용할 수 있습니다.

  - SafeHandle을 사용하여 관리되지 않는 리소스를 래핑합니다. 이것이 권장되는 방법입니다. SafeHandle은 <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> 추상 클래스에서 파생되며, 강력한 <xref:System.Object.Finalize%2A> 메서드를 포함합니다. SafeHandle을 사용하면 <xref:System.IDisposable> 인터페이스를 간단하게 구현하고 <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> 구현에서 SafeHandle의 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 메서드를 호출할 수 있습니다. <xref:System.IDisposable.Dispose%2A> 메서드가 호출되지 않는 경우 가비지 수집기에 의해 SafeHandle의 종료자가 자동으로 호출됩니다.

    **또는**

  - <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 메서드를 재정의합니다. 종료를 사용하면 형식의 소비자가 명확하게 삭제할 수 있도록 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>를 호출하지 못한 경우 관리되지 않는 리소스가 명확하지 않게 해제됩니다. <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 메서드를 재정의하여 [종료자](../../csharp/programming-guide/classes-and-structs/destructors.md)를 정의합니다.

  > [!WARNING]
  > 그러나 개체 종료가 복잡하고 오류가 발생하기 쉬운 작업일 수 있기 때문에 고유한 종료자를 제공하는 대신 SafeHandle을 사용하는 것이 좋습니다.

그러면 형식의 소비자가 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 구현을 직접 호출하여 관리되지 않는 리소스가 사용하는 메모리를 확보할 수 있습니다. <xref:System.IDisposable.Dispose%2A> 메서드를 제대로 구현하면 SafeHandle의 <xref:System.Object.Finalize%2A> 메서드 또는 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 메서드의 고유한 재정의가 <xref:System.IDisposable.Dispose%2A> 메서드가 호출되지 않는 경우 리소스를 정리하는 보호 기능이 됩니다.

## <a name="in-this-section"></a>단원 내용

[Dispose 메서드 구현](implementing-dispose.md)에서는 관리되지 않는 리소스를 해제하기 위해 Dispose 패턴을 구현하는 방법을 설명합니다.

[`IDisposable`을 구현하는 개체 사용](using-objects.md)에서는 형식의 소비자가 해당 <xref:System.IDisposable.Dispose%2A> 구현이 호출되도록 확인하는 방법을 설명합니다. 이를 수행하려면 C# `using`(또는 Visual Basic `Using`) 문을 사용하는 것이 좋습니다.

## <a name="reference"></a>참고

| 형식/멤버 | 설명 |
|--|--|
| <xref:System.IDisposable?displayProperty=nameWithType> | 관리되지 않은 리소스 해제를 위한 <xref:System.IDisposable.Dispose%2A> 메서드를 정의합니다. |
| <xref:System.Object.Finalize%2A?displayProperty=nameWithType> | 관리되지 않는 리소스가 <xref:System.IDisposable.Dispose%2A> 메서드에 의해 해제되지 않은 경우 개체 종료 기능을 제공합니다. |
| <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> | 종료를 표시하지 않습니다. 이 메서드는 종료자가 실행되지 않도록 방지하기 위해 통상 `Dispose` 메서드에서 호출됩니다. |
