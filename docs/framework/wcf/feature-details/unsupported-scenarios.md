---
description: '자세한 정보: 지원 되지 않는 시나리오'
title: 지원되지 않는 시나리오
ms.date: 03/30/2017
ms.assetid: 72027d0f-146d-40c5-9d72-e94392c8bb40
ms.openlocfilehash: 7547a1acc060a6611a4750e512501cd314bed702
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726756"
---
# <a name="unsupported-scenarios"></a>지원되지 않는 시나리오

다양 한 이유로 WCF (Windows Communication Foundation)는 특정 보안 시나리오를 지원 하지 않습니다. 예를 들어 Windows XP Home Edition은 SSPI 또는 Kerberos 인증 프로토콜을 구현 하지 않으므로 WCF는 해당 플랫폼에서 Windows 인증을 사용 하는 서비스 실행을 지원 하지 않습니다. Windows XP Home Edition에서 WCF를 실행 하는 경우 사용자 이름/암호 및 HTTP/HTTPS 통합 인증과 같은 다른 인증 메커니즘을 사용할 수 있습니다.

## <a name="impersonation-scenarios"></a>가장 시나리오

### <a name="impersonated-identity-might-not-flow-when-clients-make-asynchronous-calls"></a>클라이언트에서 비동기 호출을 수행할 때 가장 id가 전달 되지 않을 수 있습니다.

 WCF 클라이언트가 가장을 사용하여 Windows 인증을 통해 WCF 서비스로 비동기 호출을 수행할 때 가장 ID 대신 클라이언트 프로세스 ID로 인증이 수행될 수 있습니다.

### <a name="windows-xp-and-secure-context-token-cookie-enabled"></a>Windows XP 및 보안 컨텍스트 토큰 쿠키 사용

WCF는 가장을 지원 하지 않으며 <xref:System.InvalidOperationException> 다음 조건에 해당할 경우이 throw 됩니다.

- 운영 체제가 Windows XP입니다.

- 인증 모드에서 Windows ID를 생성하는 경우

- <xref:System.ServiceModel.OperationBehaviorAttribute>의 <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> 속성이 <xref:System.ServiceModel.ImpersonationOption.Required>로 설정됩니다.

- 상태 기반 SCT(보안 컨텍스트 토큰)가 만들어지는 경우(기본값: 만들기 사용 안 함)

 상태 기반 SCT는 사용자 지정 바인딩을 통해서만 만들 수 있습니다. 자세한 내용은 [방법: 보안 세션에 대 한 보안 컨텍스트 토큰 만들기](how-to-create-a-security-context-token-for-a-secure-session.md)를 참조 하세요. 코드에서 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 또는 메서드를 사용 하 여 보안 바인딩 요소 (또는)를 만들고 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%28System.Boolean%29?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%28System.ServiceModel.Channels.SecurityBindingElement%2CSystem.Boolean%29?displayProperty=nameWithType> `requireCancellation` 매개 변수를로 설정 `false` 하 여 토큰을 사용 하도록 설정 합니다. 매개 변수는 SCT 캐싱을 참조합니다. 값을 `false`로 설정하면 상태 기반 SCT 기능을 사용할 수 있습니다.

 또는 구성에서는 <`customBinding`> 만든 다음 <> 요소를 추가 하 `security` 고 특성을 ws-secureconversation로 설정 하 고 특성을로 설정 하 여 토큰을 사용 하도록 설정 합니다 `authenticationMode` `requireSecurityContextCancellation` `true` .

> [!NOTE]
> 앞의 요구 사항은 각기 고유합니다. 예를 들어, <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A>는 Windows ID를 생성하는 바인딩 요소를 만들지만 SCT를 설정하지 않습니다. 따라서 `Required` WINDOWS XP의 옵션과 함께 사용할 수 있습니다.

### <a name="possible-aspnet-conflict"></a>가능한 ASP.NET 충돌

WCF 및 ASP.NET는 모두 가장을 사용 하거나 사용 하지 않도록 설정할 수 있습니다. ASP.NET가 WCF 응용 프로그램을 호스트 하는 경우 WCF와 ASP.NET 구성 설정 사이에 충돌이 있을 수 있습니다. 충돌이 발생 하는 경우 속성이로 설정 되지 않은 경우 WCF 설정이 우선적으로 적용 됩니다 <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> <xref:System.ServiceModel.ImpersonationOption.NotAllowed> .이 경우 ASP.NET 가장 설정이 우선적으로 적용 됩니다.

### <a name="assembly-loads-may-fail-under-impersonation"></a>가장 하는 동안 어셈블리 로드가 실패할 수 있음

가장 컨텍스트에 어셈블리 로드 액세스 권한이 없고 CLR(공용 언어 런타임)에서 AppDomain에 대한 어셈블리 로드를 처음으로 시도하는 경우 <xref:System.AppDomain>은 오류를 캐시합니다. 가장을 변환한 이후 변환된 컨텍스트에 어셈블리 로드 액세스 권한이 있더라도 후속 어셈블리 로드 시도는 실패합니다. 이는 사용자 컨텍스트가 변경 된 후 CLR에서 로드를 다시 시도 하지 않기 때문입니다. 오류를 복구하려면 애플리케이션 도메인을 다시 시작해야 합니다.

> [!NOTE]
> <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> 클래스의 <xref:System.ServiceModel.Security.WindowsClientCredential> 속성 기본값은 <xref:System.Security.Principal.TokenImpersonationLevel.Identification>입니다. 대부분의 경우 확인 수준 가장 컨텍스트에는 추가 어셈블리 로드 권한이 없습니다. 이는 기본값이므로 일반적인 조건으로 알아 두어야 합니다. 확인 수준 가장은 가장 프로세스에 `SeImpersonate` 권한이 없는 경우에도 발생합니다. 자세한 내용은 [위임 및 가장](delegation-and-impersonation-with-wcf.md)을 참조 하세요.

### <a name="delegation-requires-credential-negotiation"></a>위임에 자격 증명 협상이 필요 합니다.

Kerberos 인증 프로토콜을 위임과 함께 사용하려면 자격 증명 협상이 포함된 Kerberos 프로토콜(multi-leg 또는 multi-step Kerberos라고도 함)을 구현해야 합니다. 자격 증명 협상이 포함되지 않은 Kerberos 프로토콜(one-shot 또는 single-leg Kerberos라고도 함)을 구현하면 예외가 throw됩니다. 자격 증명 협상을 구현 하는 방법에 대 한 자세한 내용은 [Windows 인증 오류 디버깅](debugging-windows-authentication-errors.md)을 참조 하세요.

## <a name="cryptography"></a>암호화

### <a name="sha-256-supported-only-for-symmetric-key-usages"></a>SHA-256은 대칭 키 사용에만 지원 됩니다.

WCF는 시스템에서 제공 하는 바인딩에 알고리즘 모음을 사용 하 여 지정할 수 있는 다양 한 암호화 및 서명 다이제스트 만들기 알고리즘을 지원 합니다. 보안 향상을 위해 WCF는 서명 다이제스트 해시를 만들기 위한 SHA (Secure Hash Algorithm) 2 알고리즘, 특히 SHA-256을 지원 합니다. 이 릴리스는 Kerberos 키와 같은 대칭 키를 사용하는 경우와 메시지 서명에 X.509 인증서를 사용하지 않는 경우에 SHA-256을 지원합니다. WCF는 WinFX에서 현재 RSA-SHA256에 대 한 지원이 부족 하기 때문에 SHA-256 해시를 사용 하 여 RSA 서명 (x.509 인증서에 사용 됨)을 지원 하지 않습니다.

### <a name="fips-compliant-sha-256-hashes-not-supported"></a>FIPS 규격 SHA-256 해시가 지원 되지 않음

WCF는 SHA-256 FIPS 규격 해시를 지원 하지 않으므로, s h a-256를 사용 하는 알고리즘 도구는 FIPS 규격 알고리즘을 사용 해야 하는 시스템의 WCF에서 지원 되지 않습니다.

### <a name="fips-compliant-algorithms-may-fail-if-registry-is-edited"></a>레지스트리를 편집할 경우 FIPS 규격 알고리즘이 실패할 수 있음

로컬 보안 설정 MMC(Microsoft Management Console) 스냅인을 사용하여 FIPS(Federal Information Processing Standards) 규격 알고리즘을 사용하거나 사용하지 않도록 설정할 수 있습니다. 레지스트리에서 설정에 액세스할 수도 있습니다. 그러나 WCF는 레지스트리를 사용 하 여 설정을 다시 설정 하는 것을 지원 하지 않습니다. 1 또는 0 이외의 값을 설정하면 CLR과 운영 체제 간에 일치하지 않는 결과가 발생할 수 있습니다.

### <a name="fips-compliant-aes-encryption-limitation"></a>FIPS 규격 AES 암호화 제한

FIPS 규격 AES 암호화는 id 수준 가장의 이중 콜백에서 작동 하지 않습니다.

### <a name="cngksp-certificates"></a>CNG/KSP 인증서

*암호화 API: 차세대 (CNG)* 는 CryptoAPI의 장기 대체 항목입니다. 이 API는 Windows Vista, Windows Server 2008 이상 버전의 비관리 코드에서 사용할 수 있습니다.

 .NET Framework 4.6.1 및 이전 버전은 레거시 CryptoAPI를 사용 하 여 CNG/KSP 인증서를 처리 하기 때문에 이러한 인증서를 지원 하지 않습니다. .NET Framework 4.6.1 이전 버전에서 이러한 인증서를 사용 하면 예외가 발생 합니다.

 인증서에서 KSP를 사용하는지 여부를 파악하는 방법은 다음 두 가지입니다.

- `p/invoke`에 대해 `CertGetCertificateContextProperty`를 실행하고 반환되는 `dwProvType`에서 `CertGetCertificateContextProperty`이 있는지 확인합니다.

- 명령줄에서 명령을 사용 하 여  `certutil` 인증서를 쿼리 합니다. 자세한 내용은 [인증서 문제 해결을 위한 Certutil 작업](/previous-versions/orphan-topics/ws.10/cc772619(v=ws.10))을 참조 하세요.

## <a name="message-security-fails-if-using-aspnet-impersonation-and-aspnet-compatibility-is-required"></a>ASP.NET 가장 및 ASP.NET 호환성을 사용 해야 하는 경우 메시지 보안 실패

WCF는 클라이언트 인증이 발생 하는 것을 방지할 수 있기 때문에 다음과 같은 설정 조합을 지원 하지 않습니다.

- ASP.NET 가장을 사용할 수 있습니다. Web.config 파일에서 `impersonate` <> 요소의 특성을로 설정 하 여이 작업을 수행 `identity` `true` 합니다.

- ASP.NET 호환성 모드는의 특성을로 설정 하 여 사용할 수 `aspNetCompatibilityEnabled` [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md) `true` 있습니다.

- 메시지 모드 보안이 사용됩니다.

해결 방법은 ASP.NET 호환 모드를 해제 하는 것입니다. 또는 ASP.NET 호환 모드가 필요한 경우 ASP.NET 가장 기능을 사용 하지 않도록 설정 하 고 WCF에서 제공 하는 가장을 대신 사용 합니다. 자세한 내용은 [위임 및 가장](delegation-and-impersonation-with-wcf.md)을 참조 하세요.

## <a name="ipv6-literal-address-failure"></a>IPv6 리터럴 주소 오류

클라이언트와 서비스가 동일한 컴퓨터에 있고 IPv6 리터럴 주소가 서비스에 사용되는 경우 보안 요청이 실패합니다.

 리터럴 IPv6 주소는 서비스와 클라이언트가 서로 다른 컴퓨터에 있는 경우에 작동됩니다.

## <a name="wsdl-retrieval-failures-with-federated-trust"></a>페더레이션된 트러스트를 사용 하는 WSDL 검색 오류

WCF에는 페더레이션된 트러스트 체인의 각 노드에 대해 정확히 하나의 WSDL 문서가 필요 합니다. 엔드포인트를 지정할 때 루프를 설정하지 않도록 주의해야 합니다. 루프를 발생시킬 수 있는 한 가지 방법은 같은 WSDL 문서에 두 개 이상의 링크가 포함된 페더레이션 신뢰 체인에 대해 WSDL 다운로드를 사용하는 것입니다. 이 문제를 일으킬 수 있는 일반적인 시나리오로 보안 토큰 서버와 서비스가 동일한 ServiceHost 내에 포함된 페더레이션 서비스를 들 수 있습니다.

 다음과 같은 세 엔드포인트 주소가 있는 서비스를 이러한 상황의 예로 들 수 있습니다.

- `http://localhost/CalculatorService/service` (서비스)

- `http://localhost/CalculatorService/issue_ticket` (STS)

- `http://localhost/CalculatorService/mex` (메타 데이터 끝점)

 이 경우 예외가 throw됩니다.

 ph x="1" /&gt; 엔드포인트를 다른 곳에 넣어 이 시나리오가 작동하게 만들 수 있습니다.

## <a name="wsdl-import-attributes-can-be-lost"></a>WSDL 가져오기 특성이 손실 될 수 있습니다.

WSDL 가져오기를 실행할 때는 WCF에서 `<wst:Claims>` 템플릿의 `RST` 요소에 대한 특성을 추적하지 않게 됩니다. WSDL 가져오기 중에 클레임 형식 컬렉션을 직접 사용하지 않고 `<Claims>` 또는 `WSFederationHttpBinding.Security.Message.TokenRequestParameters`에서 직접 `IssuedSecurityTokenRequestParameters.AdditionalRequestParameters`를 지정하는 경우에 이 문제가 발생합니다.  가져오기 중에 특성이 손실되므로 바인딩이 WSDL을 통해 제대로 라운드트립되지 않고 클라이언트측에서 잘못됩니다.

 문제를 해결하려면 가져오기를 실행한 후 클라이언트에서 직접 바인딩을 수정합니다.

## <a name="see-also"></a>참고 항목

- [Security Considerations](security-considerations-in-wcf.md)
- [정보 공개](information-disclosure.md)
- [권한 상승](elevation-of-privilege.md)
- [서비스 거부](denial-of-service.md)
- [변조](tampering.md)
- [재생 공격](replay-attacks.md)
