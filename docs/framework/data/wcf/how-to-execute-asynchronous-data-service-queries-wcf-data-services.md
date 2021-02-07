---
description: '자세한 정보: 방법: 비동기 데이터 서비스 쿼리 실행 (WCF Data Services)'
title: '방법: 비동기 데이터 서비스 쿼리 실행 (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
ms.assetid: 902a2dc1-d0e9-4b00-90a8-becc4cb1f6a7
ms.openlocfilehash: 35300de319673b29484dc981b5d6d51c964ad908
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765349"
---
# <a name="how-to-execute-asynchronous-data-service-queries-wcf-data-services"></a>방법: 비동기 데이터 서비스 쿼리 실행 (WCF Data Services)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

WCF Data Services 클라이언트 라이브러리를 사용 하 여 쿼리 실행, 변경 내용 저장 등의 클라이언트-서버 작업을 비동기식으로 수행할 수 있습니다. 자세한 내용은 [비동기 작업](asynchronous-operations-wcf-data-services.md)합니다.  
  
> [!NOTE]
> 지정된 스레드에 대해 콜백을 호출해야 하는 애플리케이션에서는 <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> 메서드 실행을 명시적으로 마샬링해야 합니다. 자세한 내용은 [비동기 작업](asynchronous-operations-wcf-data-services.md)합니다.  
  
 이 항목의 예제에서는 Northwind 샘플 데이터 서비스 및 자동 생성된 클라이언트 데이터 서비스 클래스를 사용합니다. 이 서비스 및 클라이언트 데이터 클래스는 [WCF Data Services 빠른](quickstart-wcf-data-services.md)시작을 완료 하면 생성 됩니다.  
  
## <a name="example"></a>예제  

 다음 예제에서는 메서드를 호출 하 여 쿼리를 시작 함으로써 비동기 쿼리를 실행 하는 방법을 보여 줍니다 <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> . 인라인 대리자는 메서드를 호출 <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> 하 여 쿼리 결과를 표시 합니다.  
  
 [!code-csharp[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#executequeryasync)]
 [!code-vb[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#executequeryasync)]  
  
## <a name="see-also"></a>참고 항목

- [WCF Data Services 클라이언트 라이브러리](wcf-data-services-client-library.md)
