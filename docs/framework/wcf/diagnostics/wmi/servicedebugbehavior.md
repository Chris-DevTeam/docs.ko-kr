---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: dba4abd74cdddeb2b641feec5902413fe0704b1f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262296"
---
# <a name="servicedebugbehavior"></a>ServiceDebugBehavior

ServiceDebugBehavior  
  
## <a name="syntax"></a>구문  
  
```csharp
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a>메서드  

 ServiceDebugBehavior 클래스는 메서드를 정의하지 않습니다.  
  
## <a name="properties"></a>속성  

 ServiceDebugBehavior 클래스에는 다음 속성이 포함되어 있습니다.  
  
### <a name="httphelppageenabled"></a>HttpHelpPageEnabled  

 데이터 형식: boolean  
  
 액세스 형식: 읽기 전용  
  
 `HttpGetUrl` 특성으로 제어되는 주소에서 서비스가 WSDL을 게시할지 여부를 제어합니다.  
  
### <a name="httphelppageurl"></a>HttpHelpPageUrl  

 데이터 형식: 문자열  
  
 액세스 형식: 읽기 전용  
  
 HTTP를 사용한 검색을 위해 서비스 WSDL이 게시되는 위치를 설정합니다.  
  
### <a name="httpshelppageenabled"></a>HttpsHelpPageEnabled  

 데이터 형식: boolean  
  
 액세스 형식: 읽기 전용  
  
 `HttpsGetUrl` 특성으로 제어되는 주소에서 서비스가 HTTPS를 통해 WSDL을 게시할지 여부를 제어합니다.  
  
### <a name="httpshelppageurl"></a>HttpsHelpPageUrl  

 데이터 형식: 문자열  
  
 액세스 형식: 읽기 전용  
  
 HTTPS를 사용한 검색을 위해 서비스 WSDL이 게시되는 위치를 설정합니다.  
  
### <a name="includeexceptiondetailinfaults"></a>IncludeExceptionDetailInFaults  

 데이터 형식: boolean  
  
 액세스 형식: 읽기 전용  
  
 디버깅 목적으로 클라이언트에 반환되는 SOAP 오류 정보에 관리되는 예외 정보를 포함할지 여부를 지정합니다.  
  
## <a name="requirements"></a>요구 사항  
  
|MOF|Servicemodel.mof에 선언되어 있습니다.|  
|---------|-----------------------------------|  
|네임스페이스|root\ServiceModel에 정의되어 있습니다.|  
  
## <a name="see-also"></a>참고 항목

- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
