---
title: Protobuf 메시지-WCF 개발자를 위한 gRPC
description: 'Protobuf 메시지가 IDL에 정의 되 고 c #에서 생성 되는 방법에 대해 알아봅니다.'
ms.date: 12/15/2020
ms.openlocfilehash: c1f2a3071d45dcbe4b98d747f19fed508bad102f
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938106"
---
# <a name="protobuf-messages"></a>Protobuf 메시지

이 섹션에서는 Protobuf (프로토콜 버퍼) 메시지를 파일에 선언 하는 방법에 대해 설명 `.proto` 합니다. 이 예에서는 필드 번호 및 형식의 기본적인 개념을 설명 하 고 컴파일러가 생성 하는 c # 코드를 살펴봅니다 `protoc` .

이 장의 나머지 부분에서는 Protobuf에서 다양 한 유형의 데이터가 표시 되는 방식에 대해 자세히 살펴봅니다.

## <a name="declaring-a-message"></a>메시지 선언

WCF (Windows Communication Foundation)에서 `Stock` 시장 거래 응용 프로그램에 대 한 클래스는 다음 예제와 같이 정의 될 수 있습니다.

```csharp
namespace TraderSys
{
    [DataContract]
    public class Stock
    {
        [DataMember]
        public int Id { get; set;}
        [DataMember]
        public string Symbol { get; set;}
        [DataMember]
        public string DisplayName { get; set;}
        [DataMember]
        public int MarketId { get; set; }
    }
}
```

Protobuf에서 동일한 클래스를 구현 하려면 파일에서 선언 해야 합니다 `.proto` . `protoc`그런 다음 컴파일러는 빌드 프로세스의 일부로 .net 클래스를 생성 합니다.

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

첫 번째 줄은 사용 중인 구문 버전을 선언 합니다. 이 언어 버전 3은 2016에서 릴리스 되었습니다. GRPC 서비스에 권장 되는 버전입니다.

`option csharp_namespace`줄은 생성 된 c # 형식에 사용할 네임 스페이스를 지정 합니다. 파일이 다른 언어로 컴파일될 때이 옵션은 무시 됩니다 `.proto` . Protobuf 파일은 종종 여러 언어에 대 한 언어별 옵션을 포함 합니다.

`Stock`메시지 정의는 네 개의 필드를 지정 합니다. 각에는 형식, 이름 및 필드 번호가 있습니다.

## <a name="field-numbers"></a>필드 번호

필드 번호는 Protobuf의 중요 한 부분입니다. 이진 인코딩 데이터의 필드를 식별 하는 데 사용 됩니다. 즉, 버전에서 서비스 버전으로 변경할 수 없습니다. 이는 이전 버전과의 호환성 및 앞으로의 호환성이 가능 하기 때문입니다. 클라이언트 및 서비스는 누락 값이 처리 되는 경우에는 알 수 없는 필드 번호를 무시 합니다.

이진 형식에서 필드 번호는 형식 식별자와 결합 됩니다. 1에서 15 사이의 필드 번호는 해당 형식을 단일 바이트로 인코딩할 수 있습니다. 16에서 2047 사이의 숫자는 2 바이트를 차지 합니다. 어떤 이유로 든 메시지에서 필드가 2047 개를 초과 해야 하는 경우 더 높은 수준으로 이동할 수 있습니다. 필드 번호 1에서 15 까지의 단일 바이트 식별자는 더 나은 성능을 제공 하므로 자주 사용 되는 가장 기본적인 필드에 사용 해야 합니다.

## <a name="types"></a>형식

형식 선언은 Protobuf의 네이티브 스칼라 데이터 형식을 사용 하며, [다음 섹션](protobuf-data-types.md)에서 자세히 설명 합니다. 이 장의 나머지 부분에서는 Protobuf의 기본 제공 형식에 대해 설명 하 고 일반적인 .NET 형식과의 관계를 보여 줍니다.

> [!NOTE]
> Protobuf는 기본적 `decimal` 으로 형식을 지원 하지 않으므로 `double` 대신가 사용 됩니다. 전체 자릿수가 전체 자릿수가 필요한 응용 프로그램의 경우이 챕터의 다음 부분에 있는 [10 진수에 대 한 섹션](protobuf-data-types.md#decimals) 을 참조 하세요.

## <a name="the-generated-code"></a>생성된 코드

응용 프로그램을 빌드할 때 Protobuf는 각 메시지에 대 한 클래스를 만들어 네이티브 형식을 c # 형식에 매핑합니다. 생성 된 `Stock` 형식에는 다음과 같은 시그니처가 있습니다.

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

실제로 생성 되는 코드는 이보다 훨씬 더 복잡 합니다. 그 이유는 각 클래스에 이진 통신 형식으로 serialize 및 deserialize 하는 데 필요한 모든 코드가 포함 되어 있기 때문입니다.

### <a name="property-names"></a>속성 이름

Protobuf 컴파일러는 `PascalCase` 파일에 있었지만 속성 이름에 적용 `snake_case` `.proto` 됩니다. [Protobuf 스타일 가이드](https://developers.google.com/protocol-buffers/docs/style) 는 `snake_case` 다른 플랫폼에 대 한 코드 생성이 해당 규칙에 대해 예상 되는 대/소문자를 생성 하도록 메시지 정의에서를 사용 하는 것을 권장 합니다.

>[!div class="step-by-step"]
>[이전](protocol-buffers.md)
>[다음](protobuf-data-types.md)
