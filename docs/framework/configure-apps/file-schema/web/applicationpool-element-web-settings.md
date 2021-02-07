---
description: '다음에 대 한 자세한 정보: <applicationPool> 요소 (웹 설정)'
title: <applicationPool> 요소(웹 설정)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: e70b804fbad506f98d5356828843208e5ef9e515
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681996"
---
# <a name="applicationpool-element-web-settings"></a>\<applicationPool> 요소(웹 설정)

ASP.NET 응용 프로그램이 IIS 7.0 이상 버전에서 통합 모드로 실행 되는 경우 프로세스 전체 동작을 관리 하기 위해 ASP.NET에서 사용 하는 구성 설정을 지정 합니다.  
  
> [!IMPORTANT]
> 이 요소와이 요소는 ASP.NET 응용 프로그램이 IIS 7.0 이상 버전에서 호스팅되는 경우에만 작동 합니다.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<applicationPool>**  
  
## <a name="syntax"></a>구문  
  
```xml  
<applicationPool
    maxConcurrentRequestsPerCPU="5000"
    maxConcurrentThreadsPerCPU="0"
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  

다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|attribute|설명|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|ASP.NET에서 CPU 당 허용 하는 동시 요청 수를 지정 합니다.|  
|`maxConcurrentThreadsPerCPU`|각 CPU의 응용 프로그램 풀에 대해 실행 될 수 있는 동시 스레드 수를 지정 합니다. 이는 CPU 당 사용 하 여 요청을 처리할 수 있는 관리 되는 스레드 수를 제한할 수 있으므로 ASP.NET 동시성을 제어 하는 대체 방법을 제공 합니다. 기본적으로이 설정은 0입니다. 즉, ASP.NET는 CPU 당 만들 수 있는 스레드 수를 제한 하지 않습니다 .이는 CLR 스레드 풀도 만들 수 있는 스레드 수를 제한 합니다.|  
|`requestQueueLimit`|단일 프로세스에서 ASP.NET에 대해 큐에 대기할 수 있는 최대 요청 수를 지정 합니다. ASP.NET 응용 프로그램을 둘 이상 단일 응용 프로그램 풀에서 실행 하는 경우 응용 프로그램 풀의 응용 프로그램에 대 한 누적 요청 집합은이 설정이 적용 됩니다.|  
  
### <a name="child-elements"></a>자식 요소  

 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|ASP.NET가 호스트 응용 프로그램과 상호 작용 하는 방법에 대 한 정보를 포함 합니다.|  
  
## <a name="remarks"></a>설명  

통합 모드에서 IIS 7.0 이상 버전을 실행 하는 경우이 요소 조합을 사용 하면 응용 프로그램이 IIS 응용 프로그램 풀에서 호스팅될 때 ASP.NET에서 스레드를 관리 하 고 요청을 큐에 대기 하는 방법을 구성할 수 있습니다. IIS 6을 실행 하거나 클래식 모드나 ISAPI 모드에서 IIS 7.0를 실행 하는 경우 이러한 설정은 무시 됩니다.  
  
`applicationPool`설정은 특정 버전의 .NET Framework에서 실행 되는 모든 응용 프로그램 풀에 적용 됩니다. 설정은 aspnet.config 파일에 포함 되어 있습니다. .NET Framework 버전 2.0 및 4.0에 대 한이 파일 버전이 있습니다. .NET Framework 버전 3.0 및 3.5은 버전 2.0와 aspnet.config 파일을 공유 합니다.  
  
> [!IMPORTANT]
> Windows 7에서 IIS 7.0를 실행 하는 경우 모든 응용 프로그램 풀에 대해 별도의 aspnet.config 파일을 구성할 수 있습니다. 이렇게 하면 각 응용 프로그램 풀에 대 한 스레드의 성능을 조정할 수 있습니다.  
  
설정의 경우 `maxConcurrentRequestsPerCPU` .NET Framework 4에서 "5000"의 기본 설정은 실제로 CPU 당 5000 이상의 요청이 있는 경우를 제외 하 고 ASP.NET에 의해 제어 되는 요청 제한을 효과적으로 해제 합니다. 기본 설정은 CPU 당 동시성을 자동으로 관리 하기 위해 CLR 스레드 풀에 대신 종속 됩니다. 비동기 요청 처리를 광범위 하 게 사용 하는 응용 프로그램이 나 네트워크 i/o에서 차단 된 많은 장기 실행 요청이 있는 응용 프로그램은 .NET Framework 4의 기본 제한 값을 높입니다. `maxConcurrentRequestsPerCPU`를 0으로 설정 하면 ASP.NET 요청을 처리 하기 위해 관리 되는 스레드를 사용 하지 않습니다. 응용 프로그램이 IIS 응용 프로그램 풀에서 실행 되는 경우 요청은 IIS i/o 스레드에 남아 있으므로 동시성이 IIS 스레드 설정에 의해 제한 됩니다.  
  
`requestQueueLimit`설정은 ASP.NET 응용 프로그램의 web.config 파일에 설정된 [processModel](/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) 요소의 `requestQueueLimit`특성과 동일한 방식으로 작동합니다. 그러나 `requestQueueLimit` aspnet.config 파일의 설정은 `requestQueueLimit` Web.config 파일의 설정을 재정의 합니다. 즉, 두 특성이 모두 설정 되 면 (기본적으로 true 임) `requestQueueLimit` aspnet.config 파일의 설정이 우선적으로 적용 됩니다.  
  
## <a name="example"></a>예제  

다음 예제에서는 다음과 같은 경우 aspnet.config 파일에서 ASP.NET 프로세스 전체 동작을 구성 하는 방법을 보여 줍니다.  
  
- 응용 프로그램은 IIS 7.0 응용 프로그램 풀에서 호스팅됩니다.  
  
- IIS 7.0가 통합 모드로 실행 되 고 있습니다.  
  
- 응용 프로그램에서 .NET Framework 3.5 SP1 이상 버전을 사용 하 고 있습니다.  
  
이 예제의 값은 기본값입니다.  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool
        maxConcurrentRequestsPerCPU="5000"  
        maxConcurrentThreadsPerCPU="0"
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a>요소 정보  
  
|||  
|-|-|  
|네임스페이스||  
|Schema Name||  
|유효성 검사 파일||  
|비워 둘 수 있음||  
  
## <a name="see-also"></a>참고 항목

- [\<system.web> 요소 (웹 설정)](system-web-element-web-settings.md)
