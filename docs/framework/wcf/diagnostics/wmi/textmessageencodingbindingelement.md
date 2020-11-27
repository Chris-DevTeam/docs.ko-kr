---
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: 551761af255681dd2c2dbb9e40b7103c95cd2e0a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267223"
---
# <a name="textmessageencodingbindingelement"></a>TextMessageEncodingBindingElement

TextMessageEncodingBindingElement  
  
## <a name="syntax"></a>구문  
  
```csharp
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>메서드  

 TextMessageEncodingBindingElement 클래스는 메서드를 정의하지 않습니다.  
  
## <a name="properties"></a>속성  

 TextMessageEncodingBindingElement 클래스에는 다음과 같은 속성이 있습니다.  
  
### <a name="encoding"></a>Encoding  

 데이터 형식: 문자열  
  
 액세스 형식: 읽기 전용  
  
 바인딩에서 메시지를 내보낼 때 사용되는 문자 집합 인코딩입니다.  
  
### <a name="maxreadpoolsize"></a>MaxReadPoolSize  

 데이터 형식: sint32  
  
 액세스 형식: 읽기 전용  
  
 새 판독기를 할당하지 않고 동시에 읽을 수 있는 메시지 수를 정의하는 정수입니다.  
  
### <a name="maxwritepoolsize"></a>MaxWritePoolSize  

 데이터 형식: sint32  
  
 액세스 형식: 읽기 전용  
  
 새 작성기를 할당하지 않고 동시에 보낼 수 있는 메시지 수를 정의하는 정수입니다.  
  
### <a name="readerquotas"></a>ReaderQuotas  

 데이터 형식: XmlDictionaryReaderQuotas  
  
 액세스 형식: 읽기 전용  
  
 판독기의 할당량입니다.  
  
## <a name="requirements"></a>요구 사항  
  
|MOF|Servicemodel.mof에 선언되어 있습니다.|  
|---------|-----------------------------------|  
|네임스페이스|root\ServiceModel에 정의되어 있습니다.|  
  
## <a name="see-also"></a>참고 항목

- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
