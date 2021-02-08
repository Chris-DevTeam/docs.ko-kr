---
description: '자세한 정보: My를 사용한 개발(Visual Basic)'
title: My를 사용한 개발
ms.date: 07/20/2015
f1_keywords:
- My.MyWpfExtension.Windows
helpviewer_keywords:
- My object
- My namespace
- My feature
- Visual Basic, programming in
ms.assetid: f1d04509-5e46-4551-9f9f-94334a121fca
ms.openlocfilehash: f19365471dab5fa30b565a9dd93c40a2f5795118
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666565"
---
# <a name="development-with-my-visual-basic"></a>My를 사용한 개발(Visual Basic)

Visual Basic은 강력한 기능을 지원하며 생산성 및 사용 편의성을 향상시키는 애플리케이션을 신속하게 개발할 수 있는 새로운 기능을 제공합니다. 이러한 기능 중 하나인 `My`는 애플리케이션 및 해당 런타임 환경과 관련된 정보와 기본 개체 인스턴스에 대한 액세스를 제공합니다. 이 정보는 IntelliSense를 통해 검색할 수 있는 형식으로 구성되고 용도에 따라 논리적으로 설명됩니다.  
  
 `My`의 최상위 멤버는 개체로 노출됩니다. 각 개체는 `Shared` 멤버가 있는 네임스페이스 또는 클래스와 비슷하게 동작하며 관련 멤버의 집합을 노출합니다.  
  
 다음 표에서는 최상위 `My` 개체와 서로 간의 관계를 보여 줍니다.  
  
 ![다이어그램은 My의 개체 모델을 보여 줍니다.](./media/index/my-object-model-relationships.gif)  
  
## <a name="in-this-section"></a>섹션 내용  

 [My.Application, My.Computer 및 My.User를 사용한 작업 수행](performing-tasks-with-my-application-my-computer-and-my-user.md)  
 정보 및 기능에 액세스할 수 있도록 하는 세 개의 핵심 `My` 개체 `My.Application`, `My.Computer` 및 `My.User`에 대해 설명합니다.  
  
 [My.Forms 및 My.WebServices에서 제공하는 기본 개체 인스턴스](default-object-instances-provided-by-my-forms-and-my-webservices.md)  
 애플리케이션에서 사용되는 폼, 데이터 소스 및 XML Web services에 액세스할 수 있도록 하는 `My.Forms` 및 `My.WebServices` 개체에 대해 설명합니다.  
  
 [My.Resources 및 My.Settings를 사용한 신속한 애플리케이션 개발](rapid-application-development-with-my-resources-and-my-settings.md)  
 애플리케이션의 리소스 및 설정에 액세스할 수 있도록 하는 `My.Resources` 및 `My.Settings` 개체에 대해 설명합니다.  
  
 [Visual Basic 애플리케이션 모델 개요](overview-of-the-visual-basic-application-model.md)  
 Visual Basic 애플리케이션 시작/종료 모델에 관해 설명합니다.  
  
 [My가 프로젝트 형식에 의존하는 방식](how-my-depends-on-project-type.md)  
 여러 다른 프로젝트 형식에서 사용할 수 있는 `My` 기능에 대해 자세히 설명합니다.  
  
## <a name="see-also"></a>참조

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [My.Forms 개체](../../language-reference/objects/my-forms-object.md)
- [My.WebServices 개체](../../language-reference/objects/my-webservices-object.md)
- [My가 프로젝트 형식에 의존하는 방식](how-my-depends-on-project-type.md)
