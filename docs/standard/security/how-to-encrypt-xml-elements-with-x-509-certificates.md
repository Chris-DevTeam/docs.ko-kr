---
title: '방법: X.509 인증서로 XML 요소 암호화'
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET], X.509 certificates
- cryptography [.NET], X.509 certificates
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: 761f1c66-631c-47af-aa86-ad9c50cfa453
ms.openlocfilehash: 5007404c1e6e872c169ce7ce71425f14d20d3a25
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820191"
---
# <a name="how-to-encrypt-xml-elements-with-x509-certificates"></a>방법: X.509 인증서로 XML 요소 암호화

<xref:System.Security.Cryptography.Xml> 네임스페이스의 클래스를 사용하여 XML 문서 내의 요소를 암호화할 수 있습니다.  XML 암호화는 데이터가 쉽게 읽혀질 염려 없이 암호화된 XML 데이터를 교환하거나 저장하는 표준 방법입니다.  XML 암호화 표준에 대 한 자세한 내용은에 있는 XML 암호화에 대 한 World Wide Web 컨소시엄 (W3C) 사양을 참조 하십시오 <https://www.w3.org/TR/xmldsig-core/> .  
  
 XML 암호화를 사용하여 암호화된 XML 데이터가 포함된 <`EncryptedData`> 요소의 문서나 XML 요소를 대체할 수 있습니다. <`EncryptedData`> 요소는 암호화 중에 사용된 키와 프로세스에 대한 정보가 들어 있는 하위 요소를 포함할 수 있습니다.  XML 암호화를 사용하면 문서에 암호화된 여러 요소가 포함될 수 있고 한 요소가 여러 번 암호화될 수 있습니다.  이 절차의 코드 예제에서는 나중에 암호 해독 과정에서 사용할 수 있는 다른 여러 하위 요소와 함께 <`EncryptedData`> 요소를 생성하는 방법을 보여 줍니다.  
  
이 예제에서는 두 키를 사용하여 XML 요소를 암호화합니다. 이 예제에서는 메서드를 사용 하 여 프로그래밍 방식으로 인증서를 검색 하 고이를 사용 하 여 XML 요소를 암호화 합니다 <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> . 내부적으로 <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> 메서드는 별도의 세션 키를 만들고 XML 문서를 암호화하는 데 사용합니다. 이 메서드는 세션 키를 암호화하고 이를 암호화된 XML과 함께 새 <`EncryptedData`> 요소 내부에 저장합니다.  

XML 요소의 암호를 해독 하려면 메서드를 호출 합니다 <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> .이 메서드는 저장소에서 x.509 인증서를 자동으로 검색 하 고 필요한 암호 해독을 수행 합니다.  이 절차를 사용하여 암호화된 XML 요소를 암호 해독하는 방법에 대한 자세한 내용은 [방법: X.509 인증서로 XML 요소 암호 해독](how-to-decrypt-xml-elements-with-x-509-certificates.md)을 참조하세요.  
  
이 예제는 여러 애플리케이션이 암호화된 데이터를 공유해야 하거나 애플리케이션이 실행되는 시간 사이에 암호화된 데이터를 저장해야 경우에 적합합니다.  
  
### <a name="to-encrypt-an-xml-element-with-an-x509-certificate"></a>X.509 인증서로 XML 요소를 암호화하려면  

이 예제를 실행 하려면 테스트 인증서를 만들어 인증서 저장소에 저장 해야 합니다. 해당 작업에 대 한 지침은 Windows [인증서 생성 도구 (Makecert.exe)](/windows/desktop/SecCrypto/makecert)에 대해서만 제공 됩니다.

1. [Makecert.exe](/windows/desktop/SecCrypto/makecert) 를 사용 하 여 테스트 x.509 인증서를 생성 하 고 로컬 사용자 저장소에 넣습니다. 교환 키를 생성해야 하며 키를 내보낼 수 있도록 설정해야 합니다. 다음 명령을 실행합니다.  
  
    ```console  
    makecert -r -pe -n "CN=XML_ENC_TEST_CERT" -b 01/01/2020 -e 01/01/2025 -sky exchange -ss my  
    ```  
  
2. <xref:System.Security.Cryptography.X509Certificates.X509Store> 개체를 만들고 초기화하여 현재 사용자 저장소를 엽니다.  
  
     [!code-csharp[HowToEncryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#2)]  
  
3. 읽기 전용 모드로 저장소를 엽니다.  
  
     [!code-csharp[HowToEncryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#3)]  
  
4. 저장소에 있는 모든 인증서를 사용하여 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2Collection>을 초기화합니다.  
  
     [!code-csharp[HowToEncryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#4)]  
  
5. 저장소에 있는 인증서를 열거하고 해당 이름을 가진 인증서를 찾습니다.  이 예제에서 인증서의 이름은 `"CN=XML_ENC_TEST_CERT"`입니다.  
  
     [!code-csharp[HowToEncryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#5)]  
  
6. 인증서를 찾은 후 저장소를 닫습니다.  
  
     [!code-csharp[HowToEncryptXMLElementX509#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementX509#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#6)]  
  
7. 디스크에서 XML 파일을 로드하여 <xref:System.Xml.XmlDocument> 개체를 만듭니다.  <xref:System.Xml.XmlDocument> 개체는 암호화할 XML 요소를 포함합니다.  
  
     [!code-csharp[HowToEncryptXMLElementX509#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementX509#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#7)]  
  
8. <xref:System.Xml.XmlDocument> 개체에서 지정된 요소를 찾고 암호화할 요소를 나타내는 <xref:System.Xml.XmlElement> 개체를 새로 만듭니다.  이 예제에서는 `"creditcard"` 요소가 암호화됩니다.  
  
     [!code-csharp[HowToEncryptXMLElementX509#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementX509#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#8)]  
  
9. <xref:System.Security.Cryptography.Xml.EncryptedXml> 클래스의 새 인스턴스를 만들고 X.509 인증서를 사용하여 지정된 요소를 암호화하는 데 사용합니다.  <xref:System.Security.Cryptography.Xml.EncryptedXml.Encrypt%2A> 메서드는 암호화된 요소를 <xref:System.Security.Cryptography.Xml.EncryptedData> 개체로 반환합니다.  
  
     [!code-csharp[HowToEncryptXMLElementX509#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementX509#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#9)]  
  
10. 원본 <xref:System.Xml.XmlDocument> 개체의 요소를 <xref:System.Security.Cryptography.Xml.EncryptedData> 요소로 바꿉니다.  
  
     [!code-csharp[HowToEncryptXMLElementX509#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementX509#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#10)]  
  
11. <xref:System.Xml.XmlDocument> 개체를 저장합니다.  
  
     [!code-csharp[HowToEncryptXMLElementX509#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementX509#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#11)]  
  
## <a name="example"></a>예제  
 이 예제에서는 `"test.xml"`이라는 파일이 컴파일된 프로그램과 동일한 디렉터리에 있다고 가정합니다.  또한 `"test.xml"`에 `"creditcard"` 요소가 포함되어 있다고 가정합니다.  `test.xml`이라는 파일에 다음 XML을 배치하고 이 예제에서 사용할 수 있습니다.  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>코드 컴파일  
  
- .NET Framework를 대상으로 하는 프로젝트에서에 대 한 참조를 포함 `System.Security.dll` 합니다.

- .NET Core 또는 .NET 5를 대상으로 하는 프로젝트에서 NuGet 패키지 [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)를 설치 합니다.
  
- <xref:System.Xml>, <xref:System.Security.Cryptography> 및 <xref:System.Security.Cryptography.Xml> 네임스페이스를 포함합니다.  
  
## <a name="net-security"></a>.NET 보안
  
이 예제에서 사용된 X.509 인증서는 테스트 전용입니다.  응용 프로그램은 신뢰할 수 있는 인증 기관에서 생성 한 x.509 인증서를 사용 해야 합니다.  
  
## <a name="see-also"></a>참고 항목

- [암호화 모델](cryptography-model.md)
- [암호화 서비스](cryptographic-services.md)
- [플랫폼 간 암호화](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [방법: X.509 인증서로 XML 요소 해독](how-to-decrypt-xml-elements-with-x-509-certificates.md)
- [ASP.NET Core 데이터 보호](/aspnet/core/security/data-protection/introduction)
