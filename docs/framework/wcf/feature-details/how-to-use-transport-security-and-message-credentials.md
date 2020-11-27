---
title: '방법: 전송 보안 및 메시지 자격 증명 사용'
description: WCF에서 전송 및 메시지 보안 모드를 제공 하는 메시지 자격 증명을 사용 하 여 전송 보안을 구현 하는 방법을 알아봅니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
ms.openlocfilehash: dbf04572e19d0dfc2508b3f8c3295ffae78ca0f4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268315"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a>방법: 전송 보안 및 메시지 자격 증명 사용

전송 및 메시지 자격 증명을 모두 사용 하 여 서비스를 보호 하는 것은 Windows Communication Foundation (WCF)에서 전송 및 메시지 보안 모드를 모두 사용 하는 것입니다. 요컨대, 전송 계층 보안은 무결성과 기밀성을 제공하고, 메시지 계층 보안은 엄격한 전송 보안 메커니즘에서는 제공되지 않는 다양한 자격 증명을 제공합니다. 이 항목에서는 <xref:System.ServiceModel.WSHttpBinding> 및 <xref:System.ServiceModel.NetTcpBinding> 바인딩을 사용하여 메시지 자격 증명을 통해 전송을 구현하는 기본 단계를 보여 줍니다. 보안 모드를 설정 하는 방법에 대 한 자세한 내용은 [방법: 보안 모드 설정](../how-to-set-the-security-mode.md)을 참조 하세요.  
  
 보안 모드를 `TransportWithMessageCredential`로 설정하면 전송에서 전송 수준 보안을 제공하는 실제 메커니즘을 결정합니다. HTTP의 경우 메커니즘이 HTTPS(HTTP를 통한 SSL(Secure Sockets Layer))이고, TCP의 경우 TCP 또는 Windows를 통한 SSL입니다.  
  
 전송이 HTTP(<xref:System.ServiceModel.WSHttpBinding> 사용)인 경우 HTTP를 통한 SSL 전송 수준 보안이 제공됩니다. 이 경우 이 항목의 뒷부분에 설명된 것처럼 포트에 바인딩된 SSL 인증서를 사용하여 서비스를 호스팅하는 컴퓨터를 구성해야 합니다.  
  
 전송이 TCP(<xref:System.ServiceModel.NetTcpBinding> 사용)인 경우 기본적으로 Windows 보안 또는 TCP를 통한 SSL 전송 수준 보안이 제공됩니다. TCP를 통한 SSL을 사용할 경우 이 항목의 뒷부분에 설명된 것처럼 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> 메서드를 사용하여 인증서를 지정해야 합니다.  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a>전송 보안에 대해 인증서와 함께 WSHttpBinding을 사용하려면(코드)  
  
1. HttpCfg.exe 도구를 사용하여 시스템의 포트에 SSL 인증서를 바인딩합니다. 자세한 내용은 [방법: SSL 인증서로 포트 구성](how-to-configure-a-port-with-an-ssl-certificate.md)을 참조 하세요.  
  
2. <xref:System.ServiceModel.WSHttpBinding> 클래스의 인스턴스를 만들고 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> 속성을 <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>로 설정합니다.  
  
3. <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> 속성을 적절한 값으로 설정합니다. (자세한 내용은 [자격 증명 유형 선택](selecting-a-credential-type.md)을 참조 하세요.) 다음 코드에서는 값을 사용 합니다 <xref:System.ServiceModel.MessageCredentialType.Certificate> .  
  
4. 적절한 기본 주소를 사용하여 <xref:System.Uri> 클래스의 인스턴스를 만듭니다. 주소에서는 "HTTPS" 스키마를 사용하고 시스템의 실제 이름과 SSL 인증서가 바인딩되는 포트 번호를 포함해야 합니다. 또는 구성에서 기본 주소를 설정할 수 있습니다.  
  
5. ph x="1" /&gt; 메서드를 사용하여 서비스 엔드포인트를 추가합니다.  
  
6. 다음 코드에 표시된 것처럼 <xref:System.ServiceModel.ServiceHost> 인스턴스를 만들고 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 메서드를 호출합니다.  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a>전송 보안에 대해 인증서와 함께 NetTcpBinding을 사용하려면(코드)  
  
1. <xref:System.ServiceModel.NetTcpBinding> 클래스의 인스턴스를 만들고 <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> 속성을 <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>로 설정합니다.  
  
2. <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A>을 적절한 값으로 설정합니다. 다음 코드에서는 <xref:System.ServiceModel.MessageCredentialType.Certificate> 값을 사용합니다.  
  
3. 적절한 기본 주소를 사용하여 <xref:System.Uri> 클래스의 인스턴스를 만듭니다. 주소에서 "net.tcp" 스키마를 사용해야 합니다. 또는 구성에서 기본 주소를 설정할 수 있습니다.  
  
4. <xref:System.ServiceModel.ServiceHost> 클래스의 인스턴스를 만듭니다.  
  
5. <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> 클래스의 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> 메서드를 사용하여 서비스에 대한 X.509 인증서를 명시적으로 설정합니다.  
  
6. ph x="1" /&gt; 메서드를 사용하여 서비스 엔드포인트를 추가합니다.  
  
7. 다음 코드와 같이 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 메서드를 호출합니다.  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a>전송 보안에 대해 Windows와 함께 NetTcpBinding을 사용하려면(코드)  
  
1. <xref:System.ServiceModel.NetTcpBinding> 클래스의 인스턴스를 만들고 <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> 속성을 <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>로 설정합니다.  
  
2. <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A>을 <xref:System.ServiceModel.TcpClientCredentialType.Windows>로 설정하여 Windows를 사용하도록 전송 보안을 설정합니다. 이 값이 기본값입니다.  
  
3. <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A>을 적절한 값으로 설정합니다. 다음 코드에서는 <xref:System.ServiceModel.MessageCredentialType.Certificate> 값을 사용합니다.  
  
4. 적절한 기본 주소를 사용하여 <xref:System.Uri> 클래스의 인스턴스를 만듭니다. 주소에서 "net.tcp" 스키마를 사용해야 합니다. 또는 구성에서 기본 주소를 설정할 수 있습니다.  
  
5. <xref:System.ServiceModel.ServiceHost> 클래스의 인스턴스를 만듭니다.  
  
6. <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> 클래스의 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> 메서드를 사용하여 서비스에 대한 X.509 인증서를 명시적으로 설정합니다.  
  
7. ph x="1" /&gt; 메서드를 사용하여 서비스 엔드포인트를 추가합니다.  
  
8. 다음 코드와 같이 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 메서드를 호출합니다.  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a>구성 사용  
  
#### <a name="to-use-the-wshttpbinding"></a>WSHttpBinding을 사용하려면  
  
1. 포트에 바인딩된 SSL 인증서를 사용하여 컴퓨터를 구성합니다. 자세한 내용은 [방법: SSL 인증서로 포트 구성](how-to-configure-a-port-with-an-ssl-certificate.md)을 참조 하세요. `transport`이 구성을 사용 하 여 <> 요소 값을 설정할 필요가 없습니다.  
  
2. 메시지 수준 보안에 대한 클라이언트 자격 증명 형식을 지정합니다. 다음 예에서는 `clientCredentialType` <`message`> 요소의 특성을로 설정 합니다 `UserName` .  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a>전송 보안에 대해 인증서와 함께 NetTcpBinding을 사용하려면  
  
1. TCP를 통한 SSL의 경우 `<behaviors>` 요소에서 인증서를 명시적으로 지정해야 합니다. 다음 예제에서는 기본 저장소 위치(로컬 컴퓨터 및 개인 저장소)에서 해당 발급자별로 인증서를 지정합니다.  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
       <behavior name="mySvcBehavior">  
           <serviceCredentials>  
             <serviceCertificate findValue="contoso.com"  
                                 x509FindType="FindByIssuerName" />  
           </serviceCredentials>  
       </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md)바인딩 섹션에를 추가 합니다.  
  
3. 바인딩 요소를 추가하고 `name` 특성을 적절한 값으로 설정합니다.  
  
4. <> 요소를 추가 하 `security` 고 특성을 `mode` 로 설정 `TransportWithMessageCredential` 합니다.  
  
5. <요소를 추가 하 `message>` 고 특성을 `clientCredentialType` 적절 한 값으로 설정 합니다.  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <message clientCredentialType="Windows" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a>전송 보안에 대해 Windows와 함께 NetTcpBinding을 사용하려면  
  
1. 를 [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) 바인딩 섹션에 추가 합니다.  
  
2. <`binding`> 요소를 추가 하 고 `name` 특성을 적절 한 값으로 설정 합니다.  
  
3. <> 요소를 추가 하 `security` 고 특성을 `mode` 로 설정 `TransportWithMessageCredential` 합니다.  
  
4. <> 요소를 추가 하 `transport` 고 `clientCredentialType` 특성을로 설정 `Windows` 합니다.  
  
5. <`message`> 요소를 추가 하 고 `clientCredentialType` 특성을 적절 한 값으로 설정 합니다. 다음 코드에서는 값을 인증서로 설정합니다.  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <transport clientCredentialType="Windows" />  
           <message clientCredentialType="Certificate" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a>참고 항목

- [방법: 보안 모드 설정](../how-to-set-the-security-mode.md)
- [서비스에 보안 설정](../securing-services.md)
- [서비스 및 클라이언트에 보안 설정](securing-services-and-clients.md)
