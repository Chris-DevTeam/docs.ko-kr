---
description: '자세한 정보: 인스턴스 잠김 예외 동작'
title: 인스턴스 잠금 예외 동작
ms.date: 03/30/2017
ms.assetid: 164a5419-315c-4987-ad72-54cbdb88d402
ms.openlocfilehash: ebbd86aad0f2e628f2656392fd464e3c1436c148
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792676"
---
# <a name="instance-locked-exception-action"></a>인스턴스 잠금 예외 동작

SQL 워크플로 인스턴스 저장소의 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> 속성을 사용하면 SQL 지속성 공급자가 <xref:System.Runtime.DurableInstancing.InstanceLockedException>을 수신할 때 수행해야 하는 동작을 지정할 수 있습니다. 지속성 공급자가 현재 다른 서비스 호스트에 의해 잠긴 워크플로 서비스 인스턴스를 잠그려고 하면 이 예외가 발생합니다. 이 속성의 값은 <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>, <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry> 및 <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>입니다. 기본값은 <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>입니다. 다음 목록에서는 세 가지 옵션에 대해 설명합니다.  
  
- <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>. 서비스 호스트는 워크플로 서비스 인스턴스를 잠그려고 시도 하지 않고을 <xref:System.Runtime.DurableInstancing.InstanceLockedException> 호출자에 게 전달 합니다.  워크플로가 60 초를 초과 하는 기간 동안 메모리에 유지 되는 경우 <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry> 재시도로를 사용 합니다. 기본값은 <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>입니다.  
  
- <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry>. 서비스 호스트가 다시 시도 사이에 선형 간격을 사용하여 워크플로 서비스 인스턴스의 잠금을 다시 시도하고 시퀀스 끝에 호출자에게 <xref:System.Runtime.DurableInstancing.InstanceLockedException>을 전달합니다. 워크플로가 메모리에 약 5-60초 사이에 유지되어 있고 워크플로를 업로드하기 전에 모든 메시지를 처리하기 위해 같은 호스트에서 같은 인스턴스로 전송 중인 메시지가 모든 메시지를 더 많이 처리할 수 있는 지점에 일괄적으로 도착하면 <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry>를 사용하여 리소스를 낭비하지 않고 지연 시간을 가장 많이 줄일 수 있습니다.  
  
- <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>. 서비스 호스트가 다시 시도 사이에 지수 형식의 백오프 간격을 사용하여 워크플로 서비스 인스턴스의 잠금을 다시 시도하고 시퀀스 끝에 호출자에게 예외를 전달합니다. 워크플로가 매우 짧은 시간(5초 이내) 동안 메모리에 유지되거나 웹 팜이 크고 다른 메시지가 같은 호스트에 전달될 수 있는 기회가 그리 크지 않을 경우 <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>를 사용하여 지연 시간을 가장 많이 줄일 수 있습니다.  
  
 인스턴스 잠금 예외 동작 기능은 다음 시나리오를 지원합니다. 모든 시나리오에서 SqlWorkflowInstanceStore의 instanceLockedExceptionAction 속성이 <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry> 또는 <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>로 설정되어 있는 경우 호스트는 인스턴스에 대한 잠금을 주기적으로 투명하게 다시 시도합니다.  
  
1. **응용 프로그램 도메인 정상 종료 및 중첩 재활용을 사용합니다.** 워크플로 서비스 인스턴스를 실행 중인 서비스 호스트가 있는 **appdomain** 을 재활용 하 고 이전 **appdomain** 을 정상적으로 종료 하는 동안 새 **appdomain** 을 새 요청을 병렬로 처리 하는 것으로 가정 합니다. 워크플로 서비스 인스턴스가 유휴 상태가 될 때까지 종료를 중지했다가 인스턴스를 유지하고 언로드합니다. 인스턴스를 잠그기 위해 새 **AppDomain** 의 호스트가 시도 하면이 발생 <xref:System.Runtime.DurableInstancing.InstanceLockedException> 합니다.  
  
2. **유형이 같은 서버 팜에서 지속형 워크플로 수평 확장.** 워크플로 인스턴스가 실행 중인 서버 팜 노드가 충돌하고 워크플로 호스트가 실행 중인 인스턴스에 대한 잠금을 제거할 수 없다고 가정합니다. 다른 팜 노드에서 실행 중인 서비스 호스트가 워크플로 인스턴스에 대한 메시지를 수신한 후 해당 인스턴스를 잠그려고 시도하면 <xref:System.Runtime.DurableInstancing.InstanceLockedException>이 발생합니다. 잠금을 갱신하려는 호스트가 더 이상 존재하기 않기 때문에 잠금이 잠시 후 만료됩니다.  
  
     **유형이 같은 서버 팜에서 지속형 워크플로 수평 확장.**   NLB(Network Load Balancer) 뒤의 여러 호스트를 사용하는 지속형 워크플로를 수평으로 확장하고, 팜의 노드에서 실행 중인 워크플로 호스트에서 워크플로 인스턴스를 로드하고 메시지를 처리하며, NLB에 인스턴스를 이미 실행 중인 호스트에 메시지를 전달하는 라우팅 알고리즘이 없기 때문에 인스턴스에 대한 다음 메시지가 다른 노드에서 실행 중인 호스트에 라우팅된다고 가정합니다. 메시지가 수신되면 두 번째 호스트에서 워크플로 인스턴스를 로드하려고 시도합니다. 그러면 첫 번째 호스트에서 인스턴스를 잠갔기 때문에 <xref:System.Runtime.DurableInstancing.InstanceLockedException>이 발생합니다. 첫 번째 호스트에서 첫 번째 메시지를 처리한 후 인스턴스를 잠금 해제하면 두 번째 호스트에서 다음에 재시도할 때 인스턴스를 잠가 인스턴스를 로드한 후 두 번째 메시지를 처리할 수 있습니다.
