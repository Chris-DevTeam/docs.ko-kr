---
title: WCF 서비스가 웹 팜에서 호스트될 경우 재생 공격 방지
ms.date: 03/30/2017
ms.assetid: 1c2ed695-7a31-4257-92bd-9e9731b886a5
ms.openlocfilehash: 07743795effd3da9a241fd778756dd92d99d78f6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596788"
---
# <a name="preventing-replay-attacks-when-a-wcf-service-is-hosted-in-a-web-farm"></a>WCF 서비스가 웹 팜에서 호스트될 경우 재생 공격 방지
메시지 보안 WCF를 사용할 경우 WCF는 들어오는 메시지에서 NONCE를 만들고 내부 `InMemoryNonceCache`에 생성된 NONCE가 있는지를 확인하여 반복 공격을 방지합니다. 그럴 경우 메시지를 반복으로 삭제합니다. WCF 서비스가 웹 팜에 호스팅된 경우 `InMemoryNonceCache`가 웹 팜의 노드에서 공유되지 않으므로 서비스가 반복 공격에 취약합니다.  이 시나리오를 완화하기 위해 WCF 4.5는 추상 클래스 <xref:System.ServiceModel.Security.NonceCache>에서 클래스를 파생하여 자체 공유 NONCE 캐시를 구현할 수 있도록 하는 확장성 지점을 제공합니다.  
  
## <a name="noncecache-implementation"></a>NonceCache 구현  
 자체 공유 NONCE 캐시를 구현하려면 <xref:System.ServiceModel.Security.NonceCache>에서 클래스를 파생하고 <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> 및 <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> 메서드를 재정의합니다. <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A>는 캐시에 지정된 NONCE가 있는지 여부를 확인합니다. <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A>는 NONCE를 캐시에 추가하려고 합니다. 클래스가 구현되면 인스턴스를 인스턴스화한 다음 클라이언트 측 재생 검색을 위해 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.NonceCache%2A>에 할당하고 서버 측 재생 검색을 위해 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NonceCache%2A>에 할당하여 연결합니다. 이 기능에 대해서는 즉시 구성이 지원되지 않습니다.  
  
## <a name="see-also"></a>참고 항목

- [메시지 보안](message-security-in-wcf.md)
- [SymmetricSecurityBindingElement](../diagnostics/wmi/symmetricsecuritybindingelement.md)
