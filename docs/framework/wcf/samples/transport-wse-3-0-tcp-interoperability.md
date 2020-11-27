---
title: '전송: WSE 3.0 TCP 상호 운용성'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: c268043a9d5c3f6a48b7b66dc807e4e30f029f61
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96292508"
---
# <a name="transport-wse-30-tcp-interoperability"></a>전송: WSE 3.0 TCP 상호 운용성

WSE 3.0 TCP 상호 운용성 전송 샘플에서는 TCP 이중 세션을 WCF (사용자 지정 Windows Communication Foundation) 전송으로 구현 하는 방법을 보여 줍니다. 또한 채널 계층의 확장성을 사용하여 연결을 통해 기존에 배포된 시스템과 상호 작용할 수 있는 방법도 보여 줍니다. 다음 단계에서는이 사용자 지정 WCF 전송을 빌드하는 방법을 보여 줍니다.  
  
1. TCP 소켓에서 시작하여 DIME 프레이밍을 사용하여 메시지 경계를 나타내는 <xref:System.ServiceModel.Channels.IDuplexSessionChannel>의 클라이언트 및 서버 구현을 만듭니다.  
  
2. WSE TCP 서비스에 연결되고 클라이언트 <xref:System.ServiceModel.Channels.IDuplexSessionChannel>을 통해 프레임 메시지를 보내는 채널 팩터리를 만듭니다.  
  
3. 들어오는 TCP 연결을 수락하고 해당하는 채널을 생성하도록 채널 수신기를 만듭니다.  
  
4. 네트워크 관련 예외가 <xref:System.ServiceModel.CommunicationException>의 적절한 파생 클래스로 정규화되는지 확인합니다.  
  
5. 사용자 지정 전송을 채널 스택에 추가하는 바인딩 요소를 추가합니다. 자세한 내용은 [바인딩 요소 추가]를 참조 하세요.  
  
## <a name="creating-iduplexsessionchannel"></a>IDuplexSessionChannel 만들기  

 WSE 3.0 TCP 상호 운용성 전송을 작성하는 첫 번째 단계는 <xref:System.ServiceModel.Channels.IDuplexSessionChannel> 위에 <xref:System.Net.Sockets.Socket>의 구현을 만드는 것입니다. `WseTcpDuplexSessionChannel`은 <xref:System.ServiceModel.Channels.ChannelBase>로부터 파생됩니다. 메시지를 보내는 논리는 (1) 메시지를 바이트로 인코딩한 다음 (2) 이러한 바이트를 프레이밍하여 연결을 통해 보내는 두 가지 주요 작업으로 구성됩니다.  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 또한 Send() 호출이 IDuplexSessionChannel을 순서대로 유지하고 기본 소켓에 대한 호출이 올바르게 동기화되도록 잠금을 설정합니다.  
  
 `WseTcpDuplexSessionChannel`은 <xref:System.ServiceModel.Channels.MessageEncoder>와 byte[] 간의 변환에 <xref:System.ServiceModel.Channels.Message>를 사용합니다. 이는 전송이기 때문에 `WseTcpDuplexSessionChannel`은 채널이 구성된 원격 주소를 적용하는 작업도 담당합니다. `EncodeMessage`는 이 변환을 위한 논리를 캡슐화합니다.  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 <xref:System.ServiceModel.Channels.Message>를 바이트로 인코딩한 다음에는 연결을 통해 전송해야 합니다. 이렇게 하려면 메시지 경계를 정의하기 위한 시스템이 필요합니다. WSE 3.0에서는 프레이밍 프로토콜로 [DIME](/archive/msdn-magazine/2002/december/sending-files-attachments-and-soap-messages-via-dime) 버전을 사용 합니다. `WriteData`는 프레이밍 논리를 캡슐화하여 byte[]를 DIME 레코드의 집합으로 래핑합니다.  
  
 메시지를 수신 하는 논리는 유사 합니다. 주요 복잡성은 소켓 읽기가 요청 된 것 보다 더 짧은 바이트를 반환할 수 있다는 사실을 처리 하는 것입니다. 메시지를 수신하기 위해 `WseTcpDuplexSessionChannel`은 연결이 끊긴 상태에서 바이트를 읽고 DIME 프레이밍을 디코딩한 다음 byte[]를 <xref:System.ServiceModel.Channels.MessageEncoder>로 변환하는 데 <xref:System.ServiceModel.Channels.Message>를 사용합니다.  
  
 기본 `WseTcpDuplexSessionChannel`은 연결된 소켓을 수신하는 것으로 가정합니다. 기본 클래스는 소켓 종료를 처리합니다. 소켓 닫기를 처리하는 세 위치는 다음과 같습니다.  
  
- OnAbort -- 소켓을 강제로 닫습니다(강제 닫기).  
  
- On[Begin]Close -- 소켓을 정상적으로 닫습니다(정상 닫기).  
  
- 세션별. CloseOutputSession--아웃 바운드 데이터 스트림 (절반 닫기)을 종료 합니다.  
  
## <a name="channel-factory"></a>채널 팩터리  

 TCP 전송을 작성하는 다음 단계는 클라이언트 채널을 위한 <xref:System.ServiceModel.Channels.IChannelFactory>의 구현을 만드는 것입니다.  
  
- `WseTcpChannelFactory`에서 파생 <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel> 됩니다. 이는 `OnCreateChannel`을 재정의하여 클라이언트 채널을 생성하는 팩터리입니다.  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
- `ClientWseTcpDuplexSessionChannel` 기본에 논리를 추가 `WseTcpDuplexSessionChannel` 하 여 시간에 TCP 서버에 연결 `channel.Open` 합니다. 다음 코드에 나온 것처럼 먼저 호스트 이름이 IP 주소로 확인됩니다.  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
- 그런 다음에는 다음 코드에 나온 것처럼 호스트 이름이 루프의 사용 가능한 첫 번째 IP 주소에 연결됩니다.  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
- 채널 계약의 일부로 도메인 관련 예외를 래핑합니다(예: `SocketException`의 <xref:System.ServiceModel.CommunicationException>).  
  
## <a name="channel-listener"></a>채널 수신기  

 TCP 전송을 작성하는 다음 단계는 서버 채널을 수락하기 위한 <xref:System.ServiceModel.Channels.IChannelListener>의 구현을 만드는 것입니다.  
  
- `WseTcpChannelListener`에서 파생 되 <xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel> 고 [Begin] Open 및 On [Begin] Close에서를 재정의 하 여 수신 소켓의 수명을 제어 합니다. OnOpen에서는 IP_ANY를 수신 대기하는 소켓이 만들어집니다. 더 고급 구현에서는 IPv6을 수신 대기하는 두 번째 소켓도 만들 수 있습니다. 또한 호스트 이름에 IP 주소를 지정할 수도 있습니다.  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 새 소켓을 수락하면 이 소켓으로 서버 채널이 초기화됩니다. 모든 입력 및 출력은 기본 클래스에서 이미 구현되었으므로 이 채널은 소켓의 초기화를 담당합니다.  
  
## <a name="adding-a-binding-element"></a>바인딩 요소 추가  

 팩터리와 채널이 빌드되었으므로 이제 바인딩을 통해 ServiceModel 런타임에 노출해야 합니다. 바인딩은 서비스 주소와 연결된 통신 스택을 나타내는 바인딩 요소의 컬렉션입니다. 스택의 각 요소는 바인딩 요소로 표현됩니다.  
  
 이 샘플에서 바인딩 요소는 `WseTcpTransportBindingElement`에서 파생된 <xref:System.ServiceModel.Channels.TransportBindingElement>로, <xref:System.ServiceModel.Channels.IDuplexSessionChannel>을 지원하고 다음 메서드를 재정의하여 바인딩과 연결된 팩터리를 빌드합니다.  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 또한 `BindingElement`를 복제하고 체계(wse.tcp)를 반환하기 위한 멤버를 포함합니다.  
  
## <a name="the-wse-tcp-test-console"></a>WSE TCP 테스트 콘솔  

 이 샘플 전송을 사용하기 위한 테스트 코드는 TestCode.cs에서 제공합니다. 다음 지침은 WSE `TcpSyncStockService` 샘플을 설치하는 방법을 보여 줍니다.  
  
 이 테스트 코드는 인코딩으로 MTOM을 사용하고 전송으로 `WseTcpTransport`를 사용하는 사용자 지정 바인딩을 만듭니다. 또한 다음 코드에 나온 것처럼 WSE 3.0을 준수하도록 AddressingVersion을 설정합니다.  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 이 테스트 코드는 두 개의 테스트로 구성됩니다. 첫 번째 테스트에서는 WSE 3.0 WSDL에서 생성된 코드를 사용하여 형식화된 클라이언트를 설정합니다. 두 번째 테스트는 채널 Api 위에서 직접 메시지를 전송 하 여 WCF를 클라이언트와 서버로 모두 사용 합니다.  
  
 샘플을 실행할 경우의 예상 출력은 다음과 같습니다.  
  
 클라이언트:  
  
```console  
Calling soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Symbol: FABRIKAM  
        Name: Fabrikam, Inc.  
        Last Price: 120  
  
Symbol: CONTOSO  
        Name: Contoso Corp.  
        Last Price: 50.07  
Press enter.  
  
Received Action: http://SayHello  
Received Body: to you.  
Hello to you.  
Press enter.  
  
Received Action: http://NotHello  
Received Body: to me.  
Press enter.  
```  
  
 서버:  
  
```console  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
## <a name="set-up-build-and-run-the-sample"></a>샘플 설정, 빌드 및 실행  
  
1. 이 샘플을 실행 하려면 Microsoft .NET 및 WSE 샘플 [에 대 한 wse (웹 서비스 향상) 3.0](https://www.microsoft.com/download/details.aspx?id=14089) 이 설치 되어 있어야 합니다 `TcpSyncStockService` .
  
> [!NOTE]
> WSE 3.0은 Windows Server 2008에서 지원 되지 않으므로 `TcpSyncStockService` 해당 운영 체제에서 예제를 설치 하거나 실행할 수 없습니다.  
  
1. `TcpSyncStockService` 샘플을 설치했으면 다음 작업을 수행합니다.  
  
    1. `TcpSyncStockService`Visual Studio에서를 엽니다. TcpSyncStockService 샘플은 WSE 3.0와 함께 설치 됩니다. 이 샘플 코드에 포함 되지 않습니다.  
  
    2. StockService 프로젝트를 시작 프로젝트로 설정 합니다.  
  
    3. StockService 프로젝트에서 StockService.cs를 열고 `StockService` 클래스의 [Policy] 특성을 주석으로 처리합니다. 이렇게 하면 샘플에서 보안을 사용하지 않습니다. WCF는 WSE 3.0 보안 끝점과 상호 운용할 수 있지만 보안을 사용 하지 않도록 설정 하 여이 샘플이 사용자 지정 TCP 전송에 집중 되도록 합니다.  
  
    4. F5 키를 눌러 `TcpSyncStockService`를 시작합니다. 새 콘솔 창에서 서비스가 시작됩니다.  
  
    5. Visual Studio에서 이 TCP 전송 샘플을 엽니다.  
  
    6. `TcpSyncStockService`를 실행하는 컴퓨터 이름과 일치하도록 TestCode.cs의 "hostname" 변수를 업데이트합니다.  
  
    7. F5 키를 눌러 TCP 전송 샘플을 시작합니다.  
  
    8. TCP 전송 테스트 클라이언트가 새 콘솔에서 시작됩니다. 클라이언트는 서비스에서 스톡 할당량을 요청한 다음 콘솔 창에 결과를 표시합니다.
