---
description: 다음에 대해 자세히 알아보세요. <chunkedCookieHandler>
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: b0090706d3d7a9f62e17ae63ec16e4b3a869a812
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664290"
---
# \<chunkedCookieHandler>

를 구성 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 합니다. `mode` `<cookieHandler>` 요소의 특성이 "Default" 또는 "청크 분할" 인 경우에만이 요소가 있을 수 있습니다.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**  
  
## <a name="syntax"></a>구문  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  

 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|attribute|설명|  
|---------------|-----------------|  
|chunkSize|한 HTTP 쿠키에 대 한 HTTP 쿠키 데이터의 최대 크기 (문자)입니다. 청크 크기를 조정할 때 주의 해야 합니다. 웹 브라우저에는 각 도메인에 허용 되는 쿠키 크기 및 수에 대 한 제한이 다릅니다. 예를 들어 원래 Netscape 사양은 300 쿠키 합계, 쿠키 헤더 당 4096 바이트 (쿠키 값 뿐만 아니라 메타 데이터 포함) 및 도메인당 20 개의 쿠키를 규정 된 합니다. 기본값은 2000입니다. 필수 사항입니다.|  
  
### <a name="child-elements"></a>자식 요소  

 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM)에서 쿠키를 읽고 쓰는 데 사용 하는를 구성 합니다.|  
  
## <a name="remarks"></a>설명  

 <xref:System.IdentityModel.Services.ChunkedCookieHandler> `mode` 요소의 특성을 "기본" 또는 "청크 분할"으로 설정 하 여을 지정 하는 경우 `<cookieHandler>` 쿠키 처리기가 자식 요소를 포함 하 고 특성을 설정 하 여 쿠키를 읽고 쓰는 데 사용 하는 청크 크기를 지정할 수 있습니다 `<chunkedCookieHandler>` `chunkSize` . 요소가 없으면 `<chunkedCookieHandler>` 기본 청크 크기인 2000 바이트를 사용 합니다. `mode`특성이 "Custom"으로 설정 된 경우에는이 요소를 지정할 수 없습니다.  
  
 합니다 `<chunkedCookieHandler>` 에서 요소가 표시 되는 <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> 클래스입니다.  
  
## <a name="example"></a>예제  

 다음 예제에서는 쿠키를 3000 바이트 청크로 쓰는 청크 쿠키 처리기를 구성 합니다.  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a>참고 항목

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
