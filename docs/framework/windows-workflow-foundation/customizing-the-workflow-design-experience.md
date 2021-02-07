---
description: '자세한 정보: 워크플로 디자인 환경 사용자 지정'
title: 워크플로 디자인 환경 사용자 지정
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: 02049f8b42de3de6e4dfdfe8a4151be1500bcca9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742656"
---
# <a name="customizing-the-workflow-design-experience"></a>워크플로 디자인 환경 사용자 지정

사용자 지정 활동을 디자인 하 고 Windows 워크플로 디자이너를 재호스팅 하기 위한 시나리오는 .NET Framework 4에서 크게 간소화 되었습니다. 따라서 개발과 배포를 더 쉽고 유연하게 수행할 수 있습니다. 인프라의 주요 변경 내용으로, 새 activity designer 프로그래밍 모델은 Windows Presentation Foundation (WPF)를 기반으로 빌드됩니다. 이렇게 하면 활동 디자이너를 선언적으로 정의 하 고 비교를 사용 하 여 다른 응용 프로그램의 워크플로 디자이너을 쉽게 rehost 수 있습니다. Workflow Designer를 다시 호스트하면 IntelliSense 또는 간소화된 식 도메인을 지원하는 사용자 지정 식 편집기를 개발할 수 있습니다. WCF (Windows Communication Foundation)와의 통합은 워크플로 서비스를 사용 하 여 더욱 원활 하 게 진행 됩니다. 사용자 지정 활동 디자이너와 모델 항목 트리를 사용하여 다시 호스트된 Workflow Designer의 디자인 타임 환경을 향상시킬 수 있습니다.

## <a name="in-this-section"></a>섹션 내용

 [사용자 지정 활동 디자이너 및 템플릿 사용](using-custom-activity-designers-and-templates.md)

 새로운 사용자 지정 활동 디자이너와 템플릿을 만드는 방법을 설명합니다.

 [Workflow Designer 재호스팅](rehosting-the-workflow-designer.md)

 Visual Studio 외부에서 Windows 워크플로 디자이너를 다시 호스팅하는 방법 및 유효성 검사 오류를 표시 하는 방법에 대해 설명 합니다.

 [사용자 지정 식 편집기 사용](using-a-custom-expression-editor.md)

 Visual Studio 2010 외부에서 다시 호스트 되는 워크플로 디자이너에서 사용할 사용자 지정 식 편집기를 구현 하는 방법을 설명 합니다.

## <a name="reference"></a>참고

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a>참조

- [Windows Workflow Foundation 확장](extend.md)
- [Designer](./samples/designer.md)
- [사용자 지정 활동 디자이너](./samples/custom-activity-designers.md)
- [디자이너 재호스팅](./samples/designer-rehosting.md)
