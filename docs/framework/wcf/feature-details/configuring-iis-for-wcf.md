---
description: '자세한 정보: Windows Communication Foundation에 대 한 인터넷 정보 서비스 7.0 구성'
title: Windows Communication Foundation에 대해 Internet Information Services 7.0 구성
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: e76918d70a922cb32c9bbacd5779aa4f8e991b2c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743267"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a>Windows Communication Foundation에 대해 Internet Information Services 7.0 구성

IIS(인터넷 정보 서비스) 7.0은 필요한 구성 요소를 선택적으로 설치할 수 있는 모듈형 디자인입니다. 이 디자인은 Windows Vista에 도입 된 새로운 매니페스트 기반 구성 요소화 기술을 기반으로 합니다. IIS 7.0에는 독립적으로 설치할 수 있는 40 개의 독립 실행형 기능 구성 요소가 있습니다. 따라서 IT 전문가는 필요에 따라 편리하게 설치를 사용자 지정할 수 있습니다. 이 항목에서는 Windows Communication Foundation (WCF)와 함께 사용 하도록 IIS 7.0를 구성 하 고 필요한 구성 요소를 확인 하는 방법에 대해 설명 합니다.

## <a name="minimal-installation-installing-was"></a>최소 설치: WAS 설치

 전체 IIS 7.0 패키지의 최소 설치는 WAS (Windows Process Activation Service)를 설치 하는 것입니다. WAS는 독립 실행형 기능이 며, 모든 Windows Vista 운영 체제 (Home Basic, Home Premium, Business, Ultimate 및 Enterprise)에서 사용할 수 있는 IIS 7.0의 유일한 기능입니다.

 제어판에서 **프로그램** 을 클릭 한 다음 **프로그램 및 기능** 아래에 나열 된 **Windows 기능 사용/사용 안 함** 을 클릭 합니다. 다음 그림과 같이 WAS 구성 요소가 목록에 표시 됩니다.

 ![Windows 기능 사용/사용 안 함 대화 상자](media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")

 이 기능에는 다음과 같은 하위 구성 요소가 있습니다.

- .NET 환경

- 구성 API

- 프로세스 모델

 WAS의 루트 노드를 선택 하면 **프로세스 모델** 하위 노드만 기본적으로 선택 됩니다. 이 설치에서는 웹 서버에 대한 지원이 없으므로 WAS만 설치됩니다.

 WCF 또는 ASP.NET 응용 프로그램을 작동 시키려면 **.Net 환경** 확인란을 선택 합니다. 즉, WCF 및 ASP.NET가 제대로 작동 하도록 하기 위해서는 모든 WAS 구성 요소가 필요 합니다. 이러한 구성 요소는 일단 설치되면 자동으로 선택됩니다.

## <a name="iis-70-default-installation"></a>IIS 7.0: 기본 설치

 **인터넷 정보 서비스** 기능을 확인 하면 다음 그림과 같이 일부 하위 노드가 자동으로 선택 됩니다.

 ![IIS 7.0 기능에 대한 기본 설정](media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")

 이는 IIS 7.0의 기본 설치입니다. 이 설치에서는 IIS 7.0를 사용 하 여 정적 콘텐츠 (예: HTML 페이지 및 기타 콘텐츠)를 서비스 할 수 있습니다. 그러나 ASP.NET 또는 CGI 응용 프로그램을 실행 하거나 WCF 서비스를 호스트할 수는 없습니다.

## <a name="iis-70-installation-with-aspnet-support"></a>IIS 7.0: ASP.NET 지원과 함께 설치

 IIS 7.0에서 ASP.NET 작업을 수행 하려면 ASP.NET를 설치 해야 합니다. **ASP.NET** 를 확인 한 후 화면은 다음 그림과 같이 표시 됩니다.

 ![ASP.NET 필수 설정](media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")

 이는 IIS 7.0에서 WCF 및 ASP.NET 응용 프로그램이 작동 하는 최소 환경입니다.

## <a name="iis-70-installation-with-iis-60-compatibility-components"></a>IIS 7.0: IIS 6.0 호환성 구성 요소와 함께 설치

 Visual Studio 2005를 사용 하는 시스템 또는 iis 6.0 메타 베이스 API를 사용 하는 가상 응용 프로그램을 구성 하는 기타 자동화 스크립트나 도구 (예: Adsutil.vbs)에 IIS 7.0를 설치할 경우 IIS 6.0 **스크립팅 도구** 를 선택 해야 합니다. 그러면 IIS 6.0 **관리 호환성** 의 다른 하위 노드가 자동으로 확인 됩니다. 다음 그림에서는이 작업을 수행한 후의 화면을 보여 줍니다.

 ![IIS 6.0 관리 호환성 설정](media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")

 이 설치에서는 웹에서 사용할 수 있는 IIS 7.0, ASP.NET 및 WCF 기능과 샘플을 사용 하는 데 필요한 모든 것이 있습니다.

## <a name="request-limits"></a>요청 제한

 Windows Vista with IIS 7에서는 `maxUri` 및 설정의 기본값이 `maxQueryStringSize` 변경 되었습니다. 기본적으로 IIS 7.0의 요청 필터링은 URL 길이로 4096자를 허용하며 쿼리 문자열 길이로 2048자를 허용합니다. 이러한 기본값을 변경하려면 다음 XML을 App.config 파일에 추가합니다.

```xml
 <system.webServer>
    <security>
        <requestFiltering>
            <requestLimits maxUrl="8192" maxQueryString="8192" />
        </requestFiltering>
    </security>
 </system.webServer>
 ```

## <a name="see-also"></a>참고 항목

- [WAS Activation 아키텍처](was-activation-architecture.md)
- [WCF에서 사용하도록 WAS 구성](configuring-the-wpa--service-for-use-with-wcf.md)
- [방법: WCF 활성화 구성 요소 설치 및 구성](how-to-install-and-configure-wcf-activation-components.md)
- [Windows Server App Fabric 호스팅 기능](/previous-versions/appfabric/ee677189(v=azure.10))
