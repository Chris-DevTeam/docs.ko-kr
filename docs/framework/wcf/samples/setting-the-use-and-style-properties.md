---
description: '자세히 알아보기: 사용 및 스타일 속성 설정'
title: 사용 및 스타일 속성 샘플 설정
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: 435ea23e4a34ec91ea764ae9435487c1e1313afd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793001"
---
# <a name="setting-the-use-and-style-properties"></a>속성의 사용 및 스타일 설정

이 샘플에서는 <xref:System.ServiceModel.XmlSerializerFormatAttribute> 및 <xref:System.ServiceModel.DataContractFormatAttribute>에서 Use 및 Style 속성을 사용하는 방법을 보여 줍니다. 이러한 속성은 메시지 형식을 지정하는 방법에 영향을 줍니다. 기본적으로 메시지 본문 형식은 <xref:System.ServiceModel.OperationFormatStyle.Document>로 설정된 스타일을 사용하여 지정됩니다. 이러한 설정은 서비스 계약 수준이나 작업 계약 수준에서 지정할 수 있습니다.

> [!NOTE]
> 이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.

<xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> 스타일 속성은 서비스의 WSDL 메타데이터 형식이 지정되는 방법을 결정합니다. 가능한 값은 <xref:System.ServiceModel.OperationFormatStyle.Document> 및 <xref:System.ServiceModel.OperationFormatStyle.Rpc>입니다. RPC는 작업에 대해 교환된 메시지의 WSDL 표현에는 원격 프로시저 호출인 것처럼 매개 변수가 포함되어 있음을 의미합니다. 다음은 이에 대한 예입니다.

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="n1" type="xsd:double"/>
  <wsdl:part name="n2" type="xsd:double"/>
</wsdl:message>
```

스타일을로 설정 하면 <xref:System.ServiceModel.OperationFormatStyle.Document> 다음 예제와 같이 WSDL 표현에 작업에 대해 교환 되는 문서를 나타내는 단일 요소가 포함 됩니다.

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="parameters" element="tns:Add"/>
</wsdl:message>
```

<xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> 속성은 메시지의 형식을 결정합니다. 가능한 값은 <xref:System.ServiceModel.OperationFormatUse.Literal> 및 <xref:System.ServiceModel.OperationFormatUse.Encoded>이고 기본값은 <xref:System.ServiceModel.OperationFormatUse.Literal>입니다. Literal은 다음 Document/Literal 예제에서처럼 메시지가 WSDL에 있는 스키마의 리터럴 인스턴스임을 의미합니다.

```xml
<Add xmlns="http://Microsoft.ServiceModel.Samples">
  <n1>100</n1>
  <n2>15.99</n2>
</Add>
```

인코딩된은 WSDL의 스키마가 SOAP 1.1 섹션 5에 있는 규칙에 따라 인코딩된 추상 사양 임을 의미 합니다. 다음은 RPC/Encoded 예제입니다.

```xml
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">
  <n1 xsi:type="xsd:double" xmlns="">100</n1>
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>
</q1:Add>
```

WS-I Basic Profile 1.0에서 <xref:System.ServiceModel.OperationFormatUse.Encoded> 사용을 금지하므로 레거시 서비스에 필요한 경우에만 이를 사용해야 합니다. `Encoded` 메시지 형식은 XmlSerializer를 사용할 경우에만 사용할 수 있습니다.

보내고 받는 메시지를 볼 수 있도록이 샘플은 [추적 및 메시지 로깅을](tracing-and-message-logging.md)기반으로 합니다. 추적 및 메시지 로깅을 설정하고 사용할 수 있도록 서비스 구성과 소스 코드가 수정되었습니다. 또한 <xref:System.ServiceModel.WSHttpBinding>이 보안 없이 구성되었으므로 기록된 메시지를 암호화되지 않은 형식으로 볼 수 있습니다. 결과 추적 로그 (e2e 및 .log)는 [서비스 추적 뷰어 도구 (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)를 사용 하 여 보아야 합니다. 추적은 C:\LOGS 폴더에 만들어지도록 구성됩니다. 샘플을 실행하기 전에 이 폴더를 만듭니다. 추적 뷰어 도구에서 메시지 내용을 보려면 도구의 왼쪽 창과 오른쪽 창 모두에서 **메시지** 를 선택 합니다.

다음 코드에서는 기본 <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A>에서 <xref:System.ServiceModel.OperationFormatUse>로 변경된 메시지 본문의 형식과  <xref:System.ServiceModel.OperationFormatStyle>로 설정된 <xref:System.ServiceModel.OperationFormatStyle.Document> 속성이 있는 서비스 계약을 보여 줍니다.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),
XmlSerializerFormat(Style = OperationFormatStyle.Rpc,
                                 Use = OperationFormatUse.Encoded)]
public interface IUseAndStyleCalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

다른 <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> 및 <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> 설정 간의 차이를 보려면 서비스에서 해당 설정을 수정하고 클라이언트를 다시 생성한 다음 샘플을 실행하고 Service Trace Viewer 도구에서 c:\logs\message.logs 파일을 검사합니다. 또한를 확인 하 여 메타 데이터에 미치는 영향을 관찰 합니다 `http://localhost/ServiceModelSamples/service.svc?wsdl` . 서비스의 메타데이터는 일반적으로 여러 페이지로 분리됩니다. 기본 wsdl 페이지에는 WSDL 바인딩이 포함 되어 있지만 메시지 정의를 관찰 하는 뷰가 포함 되어 있습니다 `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` .

## <a name="to-set-up-build-and-run-the-sample"></a>샘플을 설치, 빌드 및 실행하려면

1. [Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.

2. 메시지를 기록할 C:\LOGS 디렉터리를 만듭니다. 사용자에게 이 디렉터리에 대한 네트워크 서비스 쓰기 권한을 부여합니다.

3. C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.

4. 단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.

> [!IMPORTANT]
> 컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다. 계속하기 전에 다음(기본) 디렉터리를 확인하세요.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> 이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다. 이 샘플은 다음 디렉터리에 있습니다.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`
