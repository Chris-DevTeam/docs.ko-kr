---
title: .NET 가비지 수집
description: .NET의 가비지 수집에 대해 알아보세요. .NET 가비지 수집기는 애플리케이션의 메모리 할당 및 해제를 관리합니다.
ms.date: 04/21/2020
helpviewer_keywords:
- memory, garbage collection
- garbage collection, automatic memory management
- GC [.NET]
- memory, allocating
- common language runtime, garbage collection
- garbage collector
- cleanup operations
- garbage collection
- memory, releasing
- common language runtime, automatic memory management
- automatic memory management
- runtime, automatic memory management
- runtime, garbage collection
- garbage collection, about
ms.assetid: 22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9
ms.openlocfilehash: 8b1fad3420778c17656614994684930fcd1b62ca
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94827778"
---
# <a name="garbage-collection"></a>가비지 수집

.NET의 가비지 수집기는 애플리케이션의 메모리 할당 및 해제를 관리합니다. 새 개체를 만들 때마다 공용 언어 런타임이 관리되는 힙에서 개체에 대해 메모리를 할당합니다. 관리되는 힙에서 주소 공간을 사용할 수 있다면 런타임은 계속해서 새 개체에 공간을 할당합니다. 그러나 메모리는 무한하지 않습니다. 결국 가비지 수집기는 메모리를 확보하기 위해 수집을 수행해야 합니다. 가비지 수집기의 최적화 엔진은 수행 중인 할당에 따라 수집을 수행하기에 가장 적합한 시간을 결정합니다. 가비지 수집기는 수집을 수행할 때 애플리케이션에서 더 이상 사용하고 있지 않은 관리되는 힙에 있는 개체를 확인하고 해당 메모리를 회수하는 데 필요한 작업을 수행합니다.  
  
## <a name="in-this-section"></a>단원 내용
  
|제목|설명|  
|-----------|-----------------|  
|[가비지 컬렉션 기본 사항](fundamentals.md)|가비지 수집이 작동하는 방법, 관리되는 힙에 개체를 할당하는 방법 및 기타 핵심 개념에 대해 설명합니다.|  
|[워크스테이션 및 서버 가비지 수집](workstation-server-gc.md)|클라이언트 앱의 워크스테이션 가비지 수집과 서버 앱의 서버 가비지 수집의 차이점을 설명합니다.|
|[백그라운드 가비지 수집](background-gc.md)|2세대 수집이 진행 중일 때 이루어지는 0세대 및 1세대 개체의 수집을 가리키는 백그라운드 가비지 수집에 대해 설명합니다.|
|[LOB(Large Object) 힙](large-object-heap.md)|LOH(Large Object 힙)의 개념과 LOB(Large Object)가 가비지 수집되는 방식을 설명합니다.|
|[가비지 수집 및 성능](performance.md)|가비지 수집 및 성능 문제를 진단하는 데 사용할 수 있는 성능 검사에 대해 설명합니다.|  
|[도출된 컬렉션](induced.md)|가비지 수집을 발생시키는 방법에 대해 설명합니다.|  
|[대기 시간 모드](latency.md)|가비지 수집의 실행 시기를 결정하는 모드에 대해 설명합니다.|  
|[공유 웹 호스팅을 위한 최적화](optimization-for-shared-web-hosting.md)|여러 개의 작은 웹 사이트에서 공유하는 서버에서 가비지 수집을 최적화하는 방법을 설명합니다.|  
|[가비지 수집 알림](notifications.md)|전체 가비지 수집이 끝나갈 때와 완료될 때를 확인하는 방법을 설명합니다.|  
|[애플리케이션 도메인 리소스 모니터링](app-domain-resource-monitoring.md)|애플리케이션 도메인별로 CPU 및 메모리 사용량을 모니터링하는 방법을 설명합니다.|  
|[약한 참조](weak-references.md)|애플리케이션에서 개체에 계속 액세스하는 동안 가비지 수집기에서 해당 개체를 수집할 수 있도록 하는 기능에 대해 설명합니다.|  
  
## <a name="reference"></a>참고

- <xref:System.GC?displayProperty=nameWithType>  
- <xref:System.GCCollectionMode?displayProperty=nameWithType>  
- <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
- <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a>참조

- [관리되지 않는 리소스 정리](unmanaged.md)
