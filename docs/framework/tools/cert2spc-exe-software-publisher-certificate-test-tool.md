---
title: Cert2spc.exe(SPC 테스트 도구)
description: Cert2spc.exe 즉, SPC 테스트 도구를 사용합니다. 이 도구는 하나 이상의 X.509 인증서에서 SPC(소프트웨어 게시자 인증서)를 만듭니다.
ms.date: 03/30/2017
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
ms.openlocfilehash: d2bd0fdc07b87a9b21b281669a213a048a407595
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104654208"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a>Cert2spc.exe(SPC 테스트 도구)

SPC(소프트웨어 게시자 인증서) 테스트 도구를 사용하면 하나 이상의 X.509 인증서에서 SPC를 만들 수 있습니다. Cert2spc.exe는 테스트 전용이며, VeriSign 또는 Thawte 같은 인증 기관에서 유효한 SPC를 받을 수 있습니다. X.509 인증서를 만드는 방법은 [Makecert.exe(인증서 작성 도구)](/windows/desktop/SecCrypto/makecert)를 참조하세요.  
  
 이 도구는 자동으로 Visual Studio와 함께 설치됩니다. 도구를 실행하려면 [Visual Studio 개발자 명령 프롬프트 또는 Visual Studio 개발자 PowerShell](/visualstudio/ide/reference/command-prompt-powershell)을 사용합니다.  
  
 명령 프롬프트에 다음을 입력합니다.  
  
## <a name="syntax"></a>구문  
  
```console  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
## <a name="parameters"></a>매개 변수  
  
|인수|Description|  
|--------------|-----------------|  
|`certN.cer`|SPC 파일에 포함할 X.509 인증서의 이름입니다. 여러 개의 이름을 공백으로 구분하여 지정할 수 있습니다.|  
|`crlN.crl`|SPC 파일에 포함할 인증서 해지 목록의 이름입니다. 여러 개의 이름을 공백으로 구분하여 지정할 수 있습니다.|  
|`outputSPCfile.spc`|X.509 인증서가 들어 있는 PKCS #7 개체의 이름을 나타냅니다.|  
  
|옵션|Description|  
|------------|-----------------|  
|**/?**|이 도구의 명령 구문 및 옵션을 표시합니다.|  
  
## <a name="examples"></a>예  

 다음 명령을 사용하여 `myCertificate.cer`에서 SPC를 만들고 이를 `mySPCFile.spc`에 포함시킵니다.  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 다음 명령을 사용하여 `oneCertificate.cer` 및 `twoCertificate.cer`에서 SPC를 만들고 이를 `mySPCFile.spc`에 포함시킵니다.  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a>참조

- [도구](index.md)
- [Makecert.exe(인증서 작성 도구)](/windows/desktop/SecCrypto/makecert)
- [개발자 명령줄 셸](/visualstudio/ide/reference/command-prompt-powershell)
