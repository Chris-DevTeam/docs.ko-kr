---
description: '다음에 대 한 자세한 정보: TcpConnectionPoolSettings'
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: 927fcba7f94bcbfa80e06479e79bf20986a661e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715199"
---
# <a name="tcpconnectionpoolsettings"></a>TcpConnectionPoolSettings

TcpConnectionPoolSettings  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>메서드  

 TcpConnectionPoolSettings 클래스는 메서드를 정의하지 않습니다.  
  
## <a name="properties"></a>속성  

 TcpConnectionPoolSettings 클래스에는 다음과 같은 속성이 있습니다.  
  
### <a name="groupname"></a>GroupName  

 데이터 형식: 문자열  
  
 액세스 형식: 읽기 전용  
  
 바인딩 요소가 사용하는 연결 풀의 그룹 이름입니다.  
  
### <a name="idletimeout"></a>IdleTimeout  

 데이터 형식: datetime  
  
 액세스 형식: 읽기 전용  
  
 연결이 끊어지기 전에 유휴 상태일 수 있는 최대 시간입니다.  
  
### <a name="leasetimeout"></a>LeaseTimeout  

 데이터 형식: datetime  
  
 액세스 형식: 읽기 전용  
  
 제한 시간을 초과하기 전에 대여 작업을 완료하기 위한 최대 시간입니다.  
  
### <a name="maxoutboundconnectionsperendpoint"></a>MaxOutboundConnectionsPerEndpoint  

 데이터 형식: sint32  
  
 액세스 형식: 읽기 전용  
  
 각 엔드포인트에 대한 최대 아웃바운드 연결 수입니다.  
  
## <a name="requirements"></a>요구 사항  
  
|MOF|Servicemodel.mof에 선언되어 있습니다.|  
|---------|-----------------------------------|  
|네임스페이스|root\ServiceModel에 정의되어 있습니다.|  
  
## <a name="see-also"></a>참고 항목

- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
