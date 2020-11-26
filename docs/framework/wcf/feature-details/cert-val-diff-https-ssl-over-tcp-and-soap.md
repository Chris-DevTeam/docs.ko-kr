---
title: HTTPS, TCP를 통한 SSL 및 SOAP 보안의 인증서 유효성 검사 차이점
description: HTTPS 또는 TCP 외에도 WCF에서 제공 하는 메시지 계층 (SOAP) 보안을 사용 하는 인증서와 WCF가 이러한 인증서의 유효성을 검사 하는 방법에 대해 알아봅니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
ms.openlocfilehash: 9be640f892fd1fcc21711114415902335f9031bd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244850"
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a>HTTPS, TCP를 통한 SSL 및 SOAP 보안의 인증서 유효성 검사 차이점

HTTP (HTTPS) 또는 TCP를 통한 TLS (전송 계층 보안) 외에도 SOAP (메시지 계층) 보안을 사용 하 여 WCF (Windows Communication Foundation)에서 인증서를 사용할 수 있습니다. 이 항목에서는 이러한 인증서의 유효성을 검사하는 방법의 차이점에 대해 설명합니다.  
  
## <a name="validation-of-https-client-certificates"></a>HTTPS 클라이언트 인증서 유효성 검사  

 HTTPS를 사용하여 클라이언트와 서비스 간에 통신하는 경우 클라이언트에서 서비스를 인증하는 데 사용하는 인증서는 신뢰 체인을 지원해야 합니다. 즉, 신뢰할 수 있는 루트 인증 기관에 연결되어야 합니다. 연결되지 않은 경우 HTTP 계층에서 "원격 서버에서 (403) 사용할 수 없음 오류를 반환했습니다."라는 메시지와 함께 <xref:System.Net.WebException>이 발생합니다. WCF는이 예외를로 표시 <xref:System.ServiceModel.Security.MessageSecurityException> 합니다.  
  
## <a name="validation-of-https-service-certificates"></a>HTTPS 서비스 인증서 유효성 검사  

 HTTPS를 사용하여 클라이언트와 서비스 간에 통신하는 경우 서버에서 인증하는 데 사용하는 인증서는 신뢰 체인을 기본적으로 지원해야 합니다. 즉, 신뢰할 수 있는 루트 인증 기관에 연결되어야 합니다. 인증서가 해지되었는지 여부를 확인하기 위해 온라인 확인을 수행하지는 않습니다. 다음 코드에서처럼 <xref:System.Net.Security.RemoteCertificateValidationCallback> 콜백을 등록하여 이 동작을 재정의할 수 있습니다.  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)]
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 여기서 `ValidateServerCertificate`의 서명은 다음과 같습니다.  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 `ValidateServerCertificate`를 구현하면 클라이언트 애플리케이션 개발자가 서비스 인증서의 유효성을 검사하는 데 필요하다고 판단하는 확인 사항을 수행할 수 있습니다.  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a>TCP를 통한 SSL 또는 SOAP 보안에서 클라이언트 인증서 유효성 검사  

 TCP를 통한 SSL(Secure Sockets Layer) 또는 SOAP 메시지 보안을 사용하는 경우 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> 클래스의 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> 속성 값에 따라 클라이언트 인증서의 유효성을 검사합니다. 속성은 <xref:System.ServiceModel.Security.X509CertificateValidationMode> 값 중 하나로 설정됩니다. <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> 클래스의 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> 속성 값에 따라 해지 확인을 수행합니다. 속성은 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 값 중 하나로 설정됩니다.  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a>TCP를 통한 SSL 또는 SOAP 보안에서 서비스 인증서 유효성 검사  

 TCP를 통한 SSL 또는 SOAP 메시지 보안을 사용하는 경우 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> 클래스의 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> 속성 값에 따라 서비스 인증서의 유효성을 검사합니다. 속성은 <xref:System.ServiceModel.Security.X509CertificateValidationMode> 값 중 하나로 설정됩니다.  
  
 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> 클래스의 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> 속성 값에 따라 해지 확인을 수행합니다. 속성은 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 값 중 하나로 설정됩니다.  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a>참고 항목

- <xref:System.Net.Security.RemoteCertificateValidationCallback>
- [인증서 사용](working-with-certificates.md)
