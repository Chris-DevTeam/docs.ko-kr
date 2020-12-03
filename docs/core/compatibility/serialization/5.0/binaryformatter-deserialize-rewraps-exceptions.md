---
title: '호환성이 손상되는 변경: BinaryFormatter.Deserialize가 일부 예외를 다시 래핑함'
description: BinaryFormatter.Deserialize가 SerializationException 내에서 일부 예외 개체를 다시 래핑하는 .NET 5.0의 호환성이 손상되는 변경에 대해 알아봅니다.
ms.date: 08/18/2020
ms.openlocfilehash: 90dc4cce6785fdb38644cca2a2e9aff65eb7a313
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759684"
---
# <a name="binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception"></a>BinaryFormatter.Deserialize가 SerializationException에서 일부 예외를 다시 래핑

이제 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> 메서드는 예외를 호출자에게 전파하기 전에 <xref:System.Runtime.Serialization.SerializationException> 내부에서 일부 예외 개체를 다시 래핑합니다.

## <a name="change-description"></a>변경 내용 설명

이전에는 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> 메서드가 <xref:System.ArgumentNullException> 같은 임의 예외에서 스택을 호출자에게 전파하도록 허용했습니다.

.NET 5.0 이상에서 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> 메서드는 잘못된 deserialization 작업으로 인해 발생하는 예외를 더 적극적으로 catch하여 <xref:System.Runtime.Serialization.SerializationException>에 래핑합니다.

## <a name="version-introduced"></a>도입된 버전

5.0

## <a name="recommended-action"></a>권장 조치

대부분의 경우 아무 작업도 수행할 필요가 없습니다. 그러나 호출 사이트가 throw되는 특정 예외에 종속된 경우 다음 예제와 같이 외부 <xref:System.Runtime.Serialization.SerializationException>에서 예외를 래핑 해제할 수 있습니다.

```csharp
Stream inputStream = GetInputStream();
var formatter = new BinaryFormatter();

try
{
    object deserialized = formatter.Deserialize(inputStream);
}
catch (MyException myEx)
{
    // Handle 'myEx' here in case it was thrown directly.
}
catch (SerializationException serEx) when (serEx.InnerException is MyException myEx)
{
    // Handle 'myEx' here in case it was wrapped in SerializationException.
}
```

## <a name="affected-apis"></a>영향을 받는 API

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`

### Category

Serialization

-->
