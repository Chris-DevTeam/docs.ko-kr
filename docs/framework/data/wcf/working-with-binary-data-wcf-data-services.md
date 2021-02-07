---
description: '자세한 정보: 이진 데이터 작업 (WCF Data Services)'
title: 이진 데이터 작업(WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, binary data
- WCF Data Services, streams
ms.assetid: aeccc45c-d5c5-4671-ad63-a492ac8043ac
ms.openlocfilehash: dfcc5f03376d2f84267d8648acf55fb1aa96e318
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748104"
---
# <a name="working-with-binary-data-wcf-data-services"></a>이진 데이터 작업(WCF Data Services)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

WCF Data Services 클라이언트 라이브러리를 사용 하면 다음 방법 중 하나를 사용 하 여 OData (Open Data Protocol) 피드에서 이진 데이터를 검색 하 고 업데이트할 수 있습니다.

- 엔터티의 기본 형식 속성으로. 이 방법은 메모리에 쉽게 로드할 수 있는 작은 이진 데이터 개체로 작업하는 경우 권장됩니다. 이 경우 이진 속성은 데이터 모델에서 노출하는 엔터티 속성이며, 데이터 서비스는 이진 데이터를 응답 메시지에서 base-64 이진 인코딩 XML로 serialize합니다.

- 별도의 이진 리소스 스트림으로. 이 방법은 사진, 비디오 또는 다른 형식의 이진 인코딩 데이터를 나타낼 수 있는 BLOB(Binary Large Object) 데이터에 액세스하고 변경하는 경우 권장됩니다.

WCF Data Services는 OData에 정의 된 대로 HTTP를 사용 하 여 이진 데이터의 스트리밍을 구현 합니다. 이 메커니즘에서 이진 데이터는 미디어 링크 항목이라고 하는 엔터티와 관련되어 있지만 별도로 존재하는 미디어 리소스로 처리됩니다. 자세한 내용은 [스트리밍 공급자](streaming-provider-wcf-data-services.md)합니다.

> [!TIP]
> 사진을 저장 하는 OData 서비스에서 이진 이미지 파일을 다운로드 하는 Windows Presentation Foundation (WPF) 클라이언트 응용 프로그램을 만드는 방법에 대 한 단계별 예제는 [스트리밍 공급자 Series-Part 2: 클라이언트에서 미디어 리소스 스트림에 액세스 게시물 Data Services](/archive/blogs/astoriateam/data-services-streaming-provider-series-part-2-accessing-a-media-resource-stream-from-the-client)을 참조 하세요. 블로그 게시물에 제공 되는 stream photo data service에 대 한 샘플 코드를 다운로드 하려면 GitHub의 [스트리밍 사진 데이터 서비스 샘플](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/Streaming%20Photo%20OData%20Service%20Sample) 을 참조 하세요.

## <a name="entity-metadata"></a>엔터티 메타데이터

관련 미디어 리소스 스트림이 있는 엔터티는 미디어 링크 항목인 엔터티 형식에 적용된 `HasStream` 특성을 통해 데이터 서비스 메타데이터에 표시됩니다. 다음 예제에서 `PhotoInfo` 엔터티는 특성으로 표시 되는 관련 미디어 리소스가 있는 미디어 링크 항목입니다 `HasStream` .

[!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_photo_streaming_service/xml/photodata.edmx#hasstream)]

이 항목의 나머지 예제에서는 미디어 리소스 스트림에 액세스하고 변경하는 방법을 보여 줍니다. WCF Data Services 클라이언트 라이브러리를 사용 하 여 .NET Framework 클라이언트 응용 프로그램에서 미디어 리소스 스트림을 사용 하는 방법에 대 한 전체 예제는 [클라이언트에서 미디어 리소스 스트림에 액세스](/archive/blogs/astoriateam/data-services-streaming-provider-series-part-2-accessing-a-media-resource-stream-from-the-client)게시물을 참조 하세요.

## <a name="accessing-the-binary-resource-stream"></a>이진 리소스 스트림 액세스

WCF Data Services 클라이언트 라이브러리는 OData 기반 데이터 서비스에서 이진 리소스 스트림에 액세스 하는 메서드를 제공 합니다. 미디어 리소스를 다운로드할 때 미디어 리소스의 URI를 사용하거나 미디어 리소스 데이터 자체가 포함된 이진 스트림을 가져올 수 있습니다. 또한 미디어 리소스 데이터를 이진 스트림으로 업로드할 수도 있습니다.

> [!TIP]
> 사진을 저장 하는 OData 서비스에서 이진 이미지 파일을 다운로드 하는 Windows Presentation Foundation (WPF) 클라이언트 응용 프로그램을 만드는 방법에 대 한 단계별 예제는 [스트리밍 공급자 Series-Part 2: 클라이언트에서 미디어 리소스 스트림에 액세스 게시물 Data Services](/archive/blogs/astoriateam/data-services-streaming-provider-series-part-2-accessing-a-media-resource-stream-from-the-client)을 참조 하세요. 블로그 게시물에 제공 되는 stream photo data service에 대 한 샘플 코드를 다운로드 하려면 GitHub의 [스트리밍 사진 데이터 서비스 샘플](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/Streaming%20Photo%20OData%20Service%20Sample) 을 참조 하세요.

### <a name="getting-the-uri-of-the-binary-stream"></a>이진 스트림의 URI 가져오기

이미지 및 기타 미디어 파일과 같은 특정 유형의 미디어 리소스를 검색할 때 이진 데이터 스트림 자체를 처리하는 것보다 애플리케이션에 있는 미디어 리소스의 URI를 사용하는 것이 쉬운 경우가 많습니다. 특정 미디어 링크 항목과 연결된 리소스 스트림의 URI를 가져오려면 엔터티를 추적하는 <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> 인스턴스에서 <xref:System.Data.Services.Client.DataServiceContext> 메서드를 호출해야 합니다. 다음 예제에서는 <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> 메서드를 호출하여 클라이언트에서 새 이미지를 만드는 데 사용되는 미디어 리소스 스트림의 URI를 가져오는 방법을 보여 줍니다.

[!code-csharp[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_client/cs/photowindow.xaml.cs#getreadstreamuri)]
[!code-vb[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_client/vb/photowindow.xaml.vb#getreadstreamuri)]

### <a name="downloading-the-binary-resource-stream"></a>이진 리소스 스트림 다운로드

이진 리소스 스트림을 검색할 때 미디어 링크 항목을 추적하는 <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> 인스턴스에서 <xref:System.Data.Services.Client.DataServiceContext> 메서드를 호출해야 합니다. 이 메서드는 리소스가 포함된 스트림에 대한 참조가 있는 <xref:System.Data.Services.Client.DataServiceStreamResponse> 개체를 반환하는 데이터 서비스에 요청을 보냅니다. 애플리케이션에 <xref:System.IO.Stream>으로 이진 리소스가 필요한 경우 이 메서드를 사용하세요. 다음 예제에서는 <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> 메서드를 호출하여 클라이언트에서 새 이미지를 만드는 데 사용되는 스트림을 검색하는 방법을 보여 줍니다.

[!code-csharp[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_streaming_client/cs/customerphotowindow.xaml.cs#getreadstreamclient)]
[!code-vb[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_streaming_client/vb/customerphotowindow.xaml.vb#getreadstreamclient)]

> [!NOTE]
> 이진 스트림이 포함된 응답 메시지의 Content-Length 헤더는 데이터 서비스에서 설정되지 않습니다. 이 값은 이진 데이터 스트림의 실제 길이를 나타내지 않을 수 있습니다.

### <a name="uploading-a-media-resource-as-a-stream"></a>미디어 리소스를 스트림으로 업로드

미디어 리소스를 삽입하거나 업데이트하려면 엔터티를 추적하는 <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> 인스턴스에서 <xref:System.Data.Services.Client.DataServiceContext> 메서드를 호출합니다. 이 메서드는 제공된 스트림에서 읽은 미디어 리소스가 포함된 요청을 데이터 서비스에 보냅니다. 다음 예제에서는 <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> 메서드를 호출하여 이미지를 데이터 서비스에 보내는 방법을 보여 줍니다.

[!code-csharp[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_client/cs/photodetailswindow.xaml.cs#setsavestream)]
[!code-vb[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_client/vb/photodetailswindow.xaml.vb#setsavestream)]

이 예제에서 <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> 메서드는 `true` 매개 변수에 `closeStream` 값을 제공하여 호출됩니다. 이렇게 하면 이진 데이터가 데이터 서비스로 업로드된 후 <xref:System.Data.Services.Client.DataServiceContext>가 스트림을 닫습니다.

> [!NOTE]
> <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A>을 호출하면 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>를 호출할 때까지 데이터 서비스로 스트림이 전송되지 않습니다.

## <a name="see-also"></a>참고 항목

- [WCF Data Services 클라이언트 라이브러리](wcf-data-services-client-library.md)
- [컨트롤에 데이터 바인딩](binding-data-to-controls-wcf-data-services.md)
