---
description: '자세한 정보: ClickOnce를 사용 하 여 WCF 응용 프로그램 배포'
title: ClickOnce를 사용하여 WCF 애플리케이션 배포
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: f0a78bab6bbe7ddfd431e8e12bfe1ca9c9143143
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646090"
---
# <a name="deploying-wcf-applications-with-clickonce"></a>ClickOnce를 사용하여 WCF 애플리케이션 배포

WCF (Windows Communication Foundation)를 사용 하는 클라이언트 응용 프로그램은 ClickOnce 기술을 사용 하 여 배포할 수 있습니다. 클라이언트 응용 프로그램이 신뢰할 수 있는 인증서를 사용하여 디지털 방식으로 서명되는 경우, 이 기술을 통해 클라이언트 응용 프로그램은 코드 액세스 보안에서 제공하는 런타임 보안 보호의 이점을 활용할 수 있습니다. ClickOnce 애플리케이션 서명에 사용되는 인증서는 신뢰할 수 있는 게시자 스토리지에 있어야 하며, 클라이언트 컴퓨터의 로컬 보안 정책은 게시자의 인증서를 사용하여 서명된 애플리케이션에 완전 신뢰 권한을 부여하도록 구성되어야 합니다.  
  
 ClickOnce 응용 프로그램 및 신뢰할 수 있는 게시자 구성에 대 한 자세한 내용은 [clickonce의 신뢰할 수 있는 게시자 구성](/previous-versions/dotnet/articles/ms996418(v=msdn.10))을 참조 하세요.  
  
## <a name="see-also"></a>참고 항목

- [신뢰할 수 있는 애플리케이션 배포 개요](/visualstudio/deployment/trusted-application-deployment-overview)
- [Windows Forms 응용 프로그램에 대 한 ClickOnce 배포](/previous-versions/visualstudio/visual-studio-2008/wh45kb66(v=vs.90))
