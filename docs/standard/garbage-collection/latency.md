---
title: 대기 모드
ms.date: 03/30/2017
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
ms.openlocfilehash: 2e7b30a50e2513c567abf2116ab5495e717a8e22
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94831197"
---
# <a name="latency-modes"></a>대기 시간 모드

개체를 회수하려면, 가비지 수집기(GC)가 애플리케이션의 실행 스레드를 모두 중지해야 합니다. 가비지 수집기가 활성 상태인 기간을 *대기 시간* 이라고 합니다.

애플리케이션이 데이터를 검색하거나 콘텐츠를 표시하는 경우와 같은 일부 상황에서는 전체 가비지 컬렉션이 중요한 시간에 발생하여 성능이 저하될 수 있습니다. <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> 속성을 <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> 값 중 하나로 설정하여 가비지 수집기의 개입을 조정할 수 있습니다.

## <a name="low-latency-settings"></a>짧은 대기 시간 설정

"짧은" 대기 시간 설정을 사용하면 가비지 수집기의 애플리케이션 개입이 줄어듭니다. 가비지 수집은 좀 더 적은 양의 메모리를 회수합니다.

<xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> 열거형은 두 개의 짧은 대기 시간 설정을 제공합니다.

- [GCLatencyMode.LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency)는 2세대 컬렉션을 사용하지 않고 0세대 및 1세대 컬렉션만 수행합니다. 짧은 시간 동안에만 사용할 수 있습니다. 긴 시간 동안 사용하여 시스템의 메모리 사용량이 많을 경우 가비지 수집기가 애플리케이션을 잠시 중지하고 시간 결정적 작업을 방해할 수 있는 수집을 트리거합니다. 이 설정은 워크스테이션 가비지 컬렉션에서만 사용할 수 있습니다.

- [GCLatencyMode.SustainedLowLatency](xref:System.Runtime.GCLatencyMode.SustainedLowLatency)는 2세대 포그라운드 컬렉션을 사용하지 않고 0세대, 1세대 및 2세대 백그라운드 컬렉션만 수행합니다. 오랜 시간 동안 사용할 수 있으며 워크스테이션 및 서버 가비지 컬렉션 모두에 대해 사용할 수 있습니다. 백그라운드 가비지 수집을 사용하지 않을 경우 이 설정을 사용할 수 없습니다.

대기 시간이 짧은 기간 중에는 다음이 발생하지 않는 한 2세대 컬렉션이 사용되지 않습니다.

- 시스템에 운영 체제에서 메모리 부족 알림을 받습니다.

- 애플리케이션 코드는 <xref:System.GC.Collect%2A?displayProperty=nameWithType> 메서드를 호출하고 `generation` 매개 변수에 대해 2를 지정하여 수집을 줄입니다.

## <a name="scenarios"></a>시나리오

다음 표에서는 <xref:System.Runtime.GCLatencyMode> 값을 사용하는 애플리케이션 시나리오를 보여 줍니다.

|대기 시간 모드|애플리케이션 시나리오|
|------------------|---------------------------|
|<xref:System.Runtime.GCLatencyMode.Batch>|UI(사용자 인터페이스) 또는 서버 쪽 작업이 없는 애플리케이션.<br /><br />백그라운드 가비지 수집을 사용하지 않도록 설정하면, 이 설정이 워크스테이션 및 서버 가비지 수집의 기본 모드입니다. 또한 <xref:System.Runtime.GCLatencyMode.Batch> 모드에서 [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) 설정을 재정의합니다. 즉, 백그라운드 또는 동시 컬렉션을 방지합니다.|
|<xref:System.Runtime.GCLatencyMode.Interactive>|UI가 있는 대부분의 애플리케이션의 경우.<br /><br />워크스테이션 및 서버 가비지 수집의 기본 모드입니다. 그러나 앱이 호스트되는 경우 호스팅 프로세스의 가비지 수집기 설정이 우선적으로 적용됩니다.|
|<xref:System.Runtime.GCLatencyMode.LowLatency>|가비지 수집기의 방해로 인한 영향을 받을 수 있는 단기간의 시간이 중요한 작업이 있는 애플리케이션(예: 예를 들어, 애니메이션이나 데이터 획득 함수를 렌더링하는 애플리케이션입니다.|
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|가비지 수집기의 방해로 인한 영향을 받을 수 있는 포함된 기간이지만 잠재적으로 장기간의 시간 결정적인 작업이 있는 애플리케이션(예: 거래 시간 동안 시장 데이터가 변경될 때 빠른 응답 시간을 필요로 하는 애플리케이션)<br /><br />이 모드에서는 다른 모드보다 관리되는 힙 크기가 더 큽니다. 관리되는 힙을 압축하지 않기 때문에 조각화의 수준이 더 높을 수 있습니다. 충분한 메모리를 사용할 수 있는지 확인하세요.|

## <a name="guidelines-for-using-low-latency"></a>짧은 대기 시간 사용에 대한 지침

[GCLatencyMode.LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) 모드를 사용하는 경우 다음과 같은 지침을 고려합니다.

- 짧은 대기 시간 기간을 가능한 한 짧게 유지합니다.

- 짧은 대기 시간 기간 중 많은 양의 메모리를 할당하지 마세요. 가비지 수집에서 확보하는 개체 수가 더 적기 때문에 메모리 부족 알림이 발생할 수 있습니다.

- 짧은 대기 시간 모드에서는 새 할당 수, 특히 대형 개체 힙 및 고정 개체에 대한 할당 수를 최소화합니다.

- 할당할 수 있는 스레드를 확인합니다. <xref:System.Runtime.GCSettings.LatencyMode%2A> 속성 설정은 프로세스 전체에 적용되므로, 할당되는 모든 스레드에서 <xref:System.OutOfMemoryException> 예외가 생성될 수 있습니다.

- 제약이 있는 실행 영역에서 짧은 대기 시간 코드를 래핑합니다. 자세한 내용은 [제약이 있는 실행 영역](../../framework/performance/constrained-execution-regions.md)을 참조하세요.

- <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> 메서드를 호출하여 짧은 대기 시간 기간 중 2세대 수집을 강제할 수 있습니다.

## <a name="see-also"></a>참고 항목

- <xref:System.GC?displayProperty=nameWithType>
- [인덱싱된 컬렉션](induced.md)
- [가비지 수집](index.md)
