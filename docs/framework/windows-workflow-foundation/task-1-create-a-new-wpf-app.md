---
description: '자세한 정보: 작업 1: 새 Windows Presentation Foundation 응용 프로그램 만들기'
title: '작업 1: 새 Windows Presentation Foundation 애플리케이션 만들기'
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 7bbb49e3d663d1878b2b3e150a24f775eeca0135
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755241"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a>작업 1: 새 Windows Presentation Foundation 애플리케이션 만들기

이 작업에서는 WPF 응용 프로그램 Visual Studio 템플릿을 사용 하 여 빈 Windows Presentation Foundation (WPF) 응용 프로그램을 만들고 해당 워크플로 어셈블리에 대 한 참조를 추가 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 합니다.  
  
## <a name="to-create-the-wpf-application-project"></a>WPF 애플리케이션 프로젝트를 만들려면

1. Visual Studio를 열고 **파일** 메뉴에서 **새로 만들기** 를 가리킨 다음 **프로젝트** 를 클릭 합니다.

2. **새 프로젝트** 대화 상자의 왼쪽에 있는 **설치 된 템플릿** 창에서 **Visual c #** 또는 **Visual Basic** 를 선택 합니다. 선택한 언어가 표시 되지 않는 경우 **다른 언어** 아래를 확인 합니다.

3. **설치 된 템플릿** 창에서 **Windows** 를 선택 합니다.

4. 위쪽 창의 드롭다운 목록 상자에서 (기본값) **.NET Framework 4** 가 선택 되어 있는지 확인 한 다음 **WPF 응용 프로그램** 을 선택 합니다.

5. 창의 맨 아래에 프로젝트 이름을 **HostingApplication** 로 설정 합니다.

6. 솔루션 이름을 **RehostingTheDesigner** 로 설정 합니다.

7. **확인** 을 클릭 하 여 응용 프로그램 프로젝트를 만듭니다. Visual Studio는 응용 프로그램에 대 한 기본 WPF UI를 만들고 적절 한 XAML 및 코드 숨김이 포함 된 파일을 포함 합니다.

8. **Workflowmodel** 어셈블리에 대 한 참조를 추가 합니다. 이렇게 하려면 **솔루션 탐색기** 에서 **HostingApplication** 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **참조 추가** 를 선택 합니다.

9. **참조 추가** 대화 상자에서 **.net** 탭을 클릭 하 고 CTRL 키를 누른 채 다음 어셈블리를 선택 하 고 **확인** 을 클릭 합니다.

    - System.Activities
    - System.Activities.Presentation
    - System.Activities.Core.Presentation

10. Workflow Designer 디자인 캔버스를 호스트 하는 방법에 대 한 자세한 내용은 [작업 2: 호스트 워크플로 디자이너](task-2-host-the-workflow-designer.md) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

- [Workflow Designer 재호스팅](rehosting-the-workflow-designer.md)
- [작업 2: 워크플로 디자이너 호스트](task-2-host-the-workflow-designer.md)
