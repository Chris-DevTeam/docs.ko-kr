---
title: 암호화 및 네트워크 보안-WCF 개발자를 위한 gRPC
description: GRPC의 네트워크 보안 및 암호화에 대 한 몇 가지 참고 사항
ms.date: 12/15/2020
ms.openlocfilehash: 0735158ed69ce425c4f00eed6c42689b888a1885
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938626"
---
# <a name="encryption-and-network-security"></a>암호화 및 네트워크 보안

WCF (Windows Communication Foundation)의 네트워크 보안 모델은 광범위 하 고 복잡 합니다. HTTPS 또는 TLS over TCP를 사용 하는 전송 수준 보안 및 WS-Security 사양을 사용 하 여 개별 메시지를 암호화 하는 메시지 수준 보안을 포함 합니다.

gRPC는 기본 HTTP/2 프로토콜에 대 한 보안 네트워킹을 유지 합니다 .이 프로토콜은 TLS 인증서를 사용 하 여 보호할 수 있습니다.

웹 브라우저는 HTTP/2에 대 한 TLS 연결을 사용 하지만 대부분의 프로그래밍 클라이언트는를 포함 합니다. NET의 `HttpClient` 는 암호화 되지 않은 연결에 대해 HTTP/2를 사용할 수 있습니다. `HttpClient` 에서는 기본적으로 암호화가 필요 하지만 스위치를 사용 하 여이 동작을 재정의할 수 있습니다 <xref:System.AppContext> .

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

공용 Api의 경우 항상 TLS 연결을 사용 하 고 적절 한 SSL 기관에서 서비스에 대 한 유효한 인증서를 제공 해야 합니다. 전체 기능 [을 제공 하는 통합](https://letsencrypt.org) SSL 인증서를 제공 하 고 대부분의 호스팅 인프라는 일반적인 플러그 인 또는 확장을 사용 하 여 사전에 암호화 표준을 지원 합니다.

회사 네트워크에 있는 내부 서비스의 경우에도 TLS를 사용 하 여 gRPC 서비스로 들어오고 나가는 네트워크 트래픽을 보호 하는 것이 좋습니다.

Kubernetes에서 실행 되는 서비스 간에 명시적 TLS를 사용 해야 하는 경우 클러스터 내 인증 기관 및 인증서 관리자 컨트롤러 (예: 인증서 관리자 [)](https://docs.cert-manager.io/en/latest/)를 사용 하는 것이 좋습니다. 그런 다음 배포 시 서비스에 인증서를 자동으로 할당할 수 있습니다.

>[!div class="step-by-step"]
>[이전](channel-credentials.md)
>[다음](grpc-in-production.md)
