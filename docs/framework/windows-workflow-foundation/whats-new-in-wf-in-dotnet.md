---
title: .NET Framework 4.5에 Windows Workflow Foundation의 새로운 기능
description: .NET Framework 4.5의 Windows Workflow Foundation에는 새로운 작업, 디자이너 기능, 워크플로 개발 모델 등의 많은 새로운 기능이 도입 되었습니다.
ms.date: 03/30/2017
ms.assetid: 195c43a8-e0a8-43d9-aead-d65a9e6751ec
ms.openlocfilehash: 0d7086fd5ff9bfa410568a74092be3e29f732e23
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697911"
---
# <a name="whats-new-in-windows-workflow-foundation-in-net-framework-45"></a>.NET Framework 4.5에 Windows Workflow Foundation의 새로운 기능

.NET Framework 4.5의 WF (Windows Workflow Foundation)에는 새로운 작업, 디자이너 기능, 워크플로 개발 모델 등의 많은 새로운 기능이 도입 되었습니다. .NET Framework 4.5에 도입 된 새로운 워크플로 기능 중 상당수는 다시 호스트 된 workflow designer에서 지원 됩니다. 지원 되는 새로운 기능에 대 한 자세한 내용은 [Rehosted 워크플로 디자이너의 새로운 Workflow Foundation 4.5 기능 지원](wf-features-in-the-rehosted-workflow-designer.md)을 참조 하세요. 최신 버전을 사용 하도록 .NET Framework 3.0 및 .NET Framework 3.5 워크플로 응용 프로그램을 마이그레이션하는 방법에 대 한 자세한 내용은 [마이그레이션 지침](migration-guidance.md)을 참조 하세요. 이 문서에서는 .NET Framework 4.5에 도입 된 새로운 워크플로 기능에 대 한 개요를 제공 합니다.

> [!WARNING]
> 이전 버전의 프레임 워크를 대상으로 하는 프로젝트에서는 4.5 .NET Framework에 도입 된 새로운 Windows Workflow Foundation 기능을 사용할 수 없습니다. .NET Framework 4.5를 대상으로 하는 프로젝트가 이전 버전의 Framework로 대상이 변경 되는 경우 여러 가지 문제가 발생할 수 있습니다.
>
> - C # 식은 디자이너에서 메시지 **값이 XAML로 설정 되었습니다**.로 대체 됩니다.
> - 다음 오류를 포함하여 여러 빌드 오류가 발생합니다.
>
> **파일 형식이 현재 대상 프레임 워크와 호환 되지 않습니다. 파일 형식을 변환 하려면 파일을 명시적으로 저장 하세요. 이 오류 메시지는 파일을 저장 하 고 디자이너를 다시 열 때 사라집니다.**

## <a name="workflow-versioning"></a><a name="BKMK_Versioning"></a> 워크플로 버전 관리

.NET Framework 4.5에는 새 클래스를 기반으로 몇 가지 새로운 버전 관리 기능이 도입 <xref:System.Activities.WorkflowIdentity> 되었습니다. <xref:System.Activities.WorkflowIdentity>는 워크플로 애플리케이션 작성자에게 지속형 워크플로 인스턴스를 해당 정의와 매핑하는 메커니즘을 제공합니다.

- <xref:System.Activities.WorkflowApplication> 호스팅을 사용하는 개발자는 <xref:System.Activities.WorkflowIdentity>를 사용하여 여러 버전의 워크플로를 함께 호스트할 수 있습니다. 새로운 <xref:System.Activities.WorkflowApplicationInstance> 클래스를 사용하여 지속형 워크플로 인스턴스를 로드할 수 있으며, 그런 다음 호스트에서는 <xref:System.Activities.WorkflowApplicationInstance.DefinitionIdentity%2A>를 사용하여 <xref:System.Activities.WorkflowApplication>을 인스턴스화할 때 올바른 버전의 워크플로 정의를 제공할 수 있습니다. 자세한 내용은 [WorkflowIdentity 및 버전 사용](using-workflowidentity-and-versioning.md) 및 [방법: 여러 버전의 워크플로](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)를 함께 호스트를 참조 하세요.

- <xref:System.ServiceModel.WorkflowServiceHost>는 이제 다중 버전 호스트입니다. 워크플로 서비스의 새 버전을 배포할 경우 새 인스턴스는 새 서비스를 사용하여 만들어지지만 기존 인스턴스는 이전 버전을 사용하여 완료됩니다. 자세한 내용은 [WorkflowServiceHost의 Side-by-side 버전 관리](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md)를 참조 하세요.

- 지속형 워크플로 인스턴스의 정의를 업데이트하는 메커니즘을 제공하는 동적 업데이트가 도입되었습니다. 자세한 내용은 [동적 업데이트](dynamic-update.md) 및 [방법: 실행 중인 워크플로 인스턴스의 정의 업데이트](how-to-update-the-definition-of-a-running-workflow-instance.md)를 참조 하세요.

- .NET Framework 4 데이터베이스 스크립트를 사용 하 여 만든 지 속성 데이터베이스를 업그레이드 하는 Sqlworkflowinstancestoreschemaupgrade.sql 데이터베이스 스크립트가 제공 됩니다. 이 스크립트는 .NET Framework 4.5에 도입 된 새 버전 관리 기능을 지원 하도록 .NET Framework 4 지 속성 데이터베이스를 업데이트 합니다. 데이터베이스의 지속형 워크플로 인스턴스는 기본 버전 관리 값을 제공 받으며, side-by-side 실행 및 동적 업데이트에 참여할 수 있습니다. 자세한 내용은 [워크플로 버전 관리를 지원 하도록 .NET Framework 4 지 속성 데이터베이스 업그레이드](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)를 참조 하세요.

## <a name="activities"></a><a name="BKMK_NewActivities"></a> 내용

기본 제공 활동 라이브러리에는 새로운 활동과 기존 활동의 새로운 기능이 들어 있습니다.

### <a name="nopersist-scope"></a><a name="BKMK_NoPersistScope"></a> NoPersist 범위

<xref:System.Activities.Statements.NoPersistScope>는 NoPersistScope의 자식 활동이 실행될 때 워크플로가 지속되지 않도록 하는 새로운 컨테이너 활동입니다. 이는 워크플로가 파일 핸들과 같은 시스템별 리소스를 사용하고 있거나 데이터베이스 트랜잭션 중일 때와 같이 워크플로가 지속되는 것이 적합하지 않은 시나리오에서 유용합니다. 이전에는 활동이 실행되는 동안 지속성을 방지하기 위해 <xref:System.Activities.NativeActivity>을 사용하는 사용자 지정 <xref:System.Activities.NoPersistHandle>가 필요했습니다.

### <a name="new-flowchart-capabilities"></a><a name="BKMK_NewFlowchartCapabilities"></a> 새 순서도 기능

순서도는 .NET Framework 4.5에 대해 업데이트 되며 다음과 같은 새 기능을 제공 합니다.

- `DisplayName` 또는 <xref:System.Activities.Statements.FlowSwitch%601> 활동의 <xref:System.Activities.Statements.FlowDecision> 속성을 편집할 수 있습니다. 따라서 활동 디자이너에 활동의 목적에 대한 자세한 내용을 표시할 수 있습니다.

- 순서도에는 <xref:System.Activities.Statements.Flowchart.ValidateUnconnectedNodes%2A>라는 새로운 속성이 있으며, 이 속성의 기본값은 `False`입니다. 이 속성이 `True`로 설정된 경우 연결되지 않은 순서도 노드에 유효성 검사 오류가 발생합니다.

## <a name="support-for-partial-trust"></a>부분 신뢰에 대한 지원

.NET Framework 4의 워크플로에는 완전히 신뢰할 수 있는 응용 프로그램 도메인이 필요 합니다. .NET Framework 4.5에서 워크플로는 부분 신뢰 환경에서 작동할 수 있습니다. 부분 신뢰 환경에서는 호스트 리소스에 대한 전체 액세스 권한을 부여하지 않고 타사 구성 요소를 사용할 수 있습니다. 워크플로를 부분 신뢰 상태로 실행할 때는 다음과 같은 몇 가지 사항을 고려해야 합니다.

1. <xref:System.Activities.Statements.Interop> 활동에 포함된 규칙 등의 레거시 구성 요소는 부분 신뢰 상태로 사용할 수 없습니다.

2. <xref:System.ServiceModel.WorkflowServiceHost>에서 부분 신뢰 상태로 워크플로를 실행할 수 없습니다.

3. 부분 신뢰 시나리오에서 예외를 지속하는 것은 잠재적 보안 위협입니다. 예외 지속성을 사용하지 않으려면 프로젝트에 <xref:System.Activities.ExceptionPersistenceExtension> 형식의 확장을 추가하여 예외 지속성을 해제해야 합니다. 다음 코드 예제에서는 이 형식을 구현하는 방법을 보여 줍니다.

    ```csharp
    public class ExceptionPersistenceExtension
    {
        public ExceptionPersistenceExtension()
        {
            this.PersistExceptions = false;
        }
        public bool PersistExceptions { get; set; }
    }
    ```

     예외가 serialize되지 않는 경우에는 예외가 <xref:System.Activities.Statements.NoPersistScope> 내에서 사용되도록 합니다.

4. 활동 작성자는 <xref:System.Activities.Activity.CacheMetadata%2A>를 재정의하여 워크플로 런타임이 자동으로 해당 형식에 대해 리플렉션을 실행하지 않도록 해야 합니다. 인수 및 자식 활동은 null이 아니어야 하며, <xref:System.Activities.ActivityMetadata.Bind%2A>는 명시적으로 호출되어 합니다. 재정의에 대 한 자세한 내용은 <xref:System.Activities.Activity.CacheMetadata%2A> [CacheMetadata를 사용 하 여 데이터 노출](exposing-data-with-cachemetadata.md)을 참조 하세요. 또한 또는 private 형식의 인수 인스턴스는 `internal` 리플렉션에서 생성 되지 않도록에서 명시적 **private** 으로 만들어야 합니다 <xref:System.Activities.Activity.CacheMetadata%2A> .

5. 형식은 serialization에 <xref:System.Runtime.Serialization.ISerializable> 또는 <xref:System.SerializableAttribute>를 사용하지 않으며, serialize되는 형식은 <xref:System.Runtime.Serialization.DataContractSerializer>를 지원해야 합니다.

6. <xref:System.Activities.Expressions.LambdaValue%601>를 사용하는 식은 <xref:System.Security.Permissions.ReflectionPermissionAttribute.RestrictedMemberAccess%2A>를 필요로 하므로 부분 신뢰 상태로 작동하지 않습니다. <xref:System.Activities.Expressions.LambdaValue%601>를 사용하는 워크플로에서는 해당 식을 <xref:System.Activities.CodeActivity%601>에서 파생된 활동으로 바꿔야 합니다. .

7. 부분 신뢰 상태에서는 <xref:System.Activities.XamlIntegration.TextExpressionCompiler>나 Visual Basic에서 호스트되는 컴파일러를 사용하여 식을 컴파일할 수 없지만, 이전에 컴파일된 식은 실행할 수 있습니다.

8. [수준 2 투명도](../misc/security-transparent-code-level-2.md) 를 사용 하는 단일 어셈블리는 .NET Framework 4, [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 완전 신뢰 및 부분 신뢰에서 사용할 수 없습니다 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] .

## <a name="new-designer-capabilities"></a><a name="BKMK_NewDesignerCapabilites"></a> 새 디자이너 기능

### <a name="designer-search"></a><a name="BKMK_DesignerSearch"></a> 디자이너 검색

이제 대규모 워크플로를 보다 효율적으로 관리하기 위해 워크플로를 키워드로 검색할 수 있습니다. 이 기능은 Visual Studio 에서만 사용할 수 있습니다. 이 기능은 재 호스트 된 디자이너에서 사용할 수 없습니다. 사용 가능한 검색 종류는 다음 두 가지입니다.

- 빠른 찾기- **Ctrl + F** 나 **편집**, **찾기 및 바꾸기**, **빠른 찾기** 를 사용 하 여 시작 합니다.

- 파일에서 찾기- **Ctrl + Shift + F** 나 **편집**, **찾기 및 바꾸기**, **파일에서 찾기** 로 시작 합니다.

바꾸기는 지원되지 않습니다.

#### <a name="quick-find"></a><a name="BKMK_QuickFind"></a> 빠른 찾기

워크플로에서 검색되는 키워드는 다음 디자이너 항목과 일치합니다.

- <xref:System.Activities.Activity> 개체, <xref:System.Activities.Statements.FlowNode> 개체, <xref:System.Activities.Statements.State> 개체, <xref:System.Activities.Statements.Transition> 개체 및 기타 사용자 지정 흐름 제어 항목의 속성

- 변수

- 인수

- 식

빠른 찾기는 디자이너의 <xref:System.Activities.Presentation.Model.ModelItem> 트리에서 수행됩니다. 워크플로 정의로 가져온 네임스페이스는 빠른 찾기로 찾을 수 없습니다.

#### <a name="find-in-files"></a><a name="BKMK_FindInFiles"></a> 파일에서 찾기

워크플로에서 검색되는 키워드는 워크플로 파일의 실제 내용과 일치합니다. 검색 결과는 Visual Studio 찾기 결과 뷰 창에 표시됩니다. 결과 항목을 두 번 클릭하면 워크플로 디자이너의 일치 항목이 포함된 활동으로 이동됩니다.

### <a name="delete-context-menu-item-in-variable-and-argument-designer"></a><a name="BKMK_VariableDeleteContextMenu"></a> 변수 및 인수 디자이너에서 상황에 맞는 메뉴 항목 삭제

.NET Framework 4에서는 키보드를 사용 하 여 디자이너에서 변수와 인수를 삭제할 수 있었습니다. .NET Framework 4.5부터 변수 및 인수는 상황에 맞는 메뉴를 사용 하 여 삭제할 수 있습니다.

다음 스크린 샷에서는 변수 및 인수 디자이너의 상황에 맞는 메뉴를 보여 줍니다.

![변수 및 인수 디자이너 상황에 맞는 메뉴](./media/whats-new-in-wf-in-dotnet/designer-context-menu.png)

### <a name="auto-surround-with-sequence"></a><a name="BKMK_AutoSurround"></a> 시퀀스를 사용 하 여 자동 감싸기

워크플로 또는 특정 컨테이너 활동(예: <xref:System.Activities.Statements.NoPersistScope>)에는 단일 본문 활동만 포함할 수 있으므로 두 번째 활동을 추가하려면 개발자가 첫 번째 활동을 삭제하고 <xref:System.Activities.Statements.Sequence> 활동을 추가한 후 두 활동을 모두 시퀀스 활동에 추가해야 했습니다. .NET Framework 4.5부터 디자이너 화면에 두 번째 활동을 추가할 때 `Sequence` 두 활동을 래핑하는 활동이 자동으로 생성 됩니다.

다음 스크린 샷에서는 `WriteLine`의 `Body`에 있는 `NoPersistScope` 활동을 보여 줍니다.

![NoPersistScope 활동 본문의 WriteLine 활동입니다.](./media/whats-new-in-wf-in-dotnet/auto-surround-write-line-activity.png)

다음 스크린 샷에서는 두 번째 `Sequence`이 첫 번째 항목 아래에 놓였을 때 `Body`에 자동으로 만들어진 `WriteLine` 활동을 보여 줍니다.

![NoPersistScope의 본문에서 자동으로 생성 된 시퀀스입니다.](./media/whats-new-in-wf-in-dotnet/auto-surround-sequence-activity.png)

### <a name="pan-mode"></a><a name="BKMK_PanMode"></a> 이동 모드

디자이너에서 큰 워크플로를 더욱 쉽게 이동하기 위해 이동 모드를 사용할 수 있습니다. 이동 모드에서 개발자는 스크롤 바를 사용할 필요 없이 워크플로의 보이는 부분을 클릭하여 끌 수 있습니다. 이동 모드를 활성화하는 단추는 디자이너의 오른쪽 아래 모퉁이에 있습니다.

다음 스크린 샷에서는 Workflow Designer의 오른쪽 아래 모퉁이에 있는 이동 단추를 보여 줍니다.

![Workflow designer에 강조 표시 된 이동 단추입니다.](./media/whats-new-in-wf-in-dotnet/pan-button-workflow-designer.png)

마우스 가운데 단추 또는 스페이스바를 사용하여 워크플로 디자이너를 이동할 수도 있습니다.

### <a name="multi-select"></a><a name="BKMK_MultiSelect"></a> 다중 선택

이동 모드를 사용하지 않을 경우 활동 주위의 사각형을 끌거나, Ctrl 키를 누른 채 원하는 활동을 하나씩 클릭하여 여러 활동을 한 번에 선택할 수 있습니다.

디자이너 내에서 선택된 여러 활동을 끌어다 놓을 수도 있으며 상황에 맞는 메뉴를 사용하여 상호 작용할 수도 있습니다.

### <a name="outline-view-of-workflow-items"></a><a name="BKMK_DocumentOutline"></a> 워크플로 항목의 개요 보기

계층적 워크플로를 쉽게 탐색할 수 있도록 워크플로의 구성 요소는 트리 스타일 개요 뷰로 표시됩니다. 개요 뷰가 **문서 개요** 보기에 표시 됩니다. 이 보기를 열려면 맨 위 메뉴에서 **보기**, **다른 창**, **문서 개요** 를 차례로 선택 하거나 ctrl + W, U를 누릅니다. 개요 뷰의 노드를 클릭하면 워크플로 디자이너의 해당 활동으로 이동되고 개요 뷰가 업데이트되어 디자이너에서 선택된 활동이 표시됩니다.

[시작 자습서](getting-started-tutorial.md) 에서 완료 된 워크플로의 다음 스크린샷은 순차 워크플로를 사용 하는 개요 보기를 보여 줍니다.

![Visual Studio의 순차 워크플로를 사용 하는 개요 보기의 스크린샷](./media/whats-new-in-wf-in-dotnet/outline-view-in-workflow-designer.jpg)

### <a name="c-expressions"></a><a name="BKMK_CSharpExpressions"></a> C # 식

.NET Framework 4.5 이전에는 워크플로의 모든 식을 Visual Basic 으로만 작성할 수 있었습니다. .NET Framework 4.5에서 Visual Basic 식은 Visual Basic를 사용 하 여 만든 프로젝트에만 사용 됩니다. Visual C# 프로젝트는 이제 식에 C#을 사용합니다. 문법 강조 표시 및 IntelliSense와 같은 기능이 포함된 완전한 기능의 C# 식 편집기가 제공됩니다. 이전 버전에서 만들어졌으며 Visual Basic 식을 사용하는 C# 워크플로 프로젝트는 계속 작동합니다.

디자인 타임에 C# 식의 유효성이 검사됩니다. C# 식의 오류는 빨간색 물결선으로 표시됩니다.

C # 식에 대 한 자세한 내용은 [c # 식](csharp-expressions.md)을 참조 하세요.

### <a name="more-control-of-visibility-of-shell-bar-and-header-items"></a><a name="BKMK_Visibility"></a> 셸 표시줄 및 머리글 항목의 표시 유형 추가

재호스트된 디자이너에서 특정 워크플로에 대해 의미가 없는 일부 표준 UI 컨트롤은 해제할 수 있습니다. .NET Framework 4에서이 사용자 지정은 디자이너 하단의 셸 표시줄 에서만 지원 됩니다. .NET Framework 4.5에서를 <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> 적절 한 값으로 설정 하 여 디자이너 맨 위에 있는 셸 헤더 항목의 표시 유형을 조정할 수 있습니다 <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> .

### <a name="auto-connect-and-auto-insert-in-flowchart-and-state-machine-workflows"></a><a name="BKMK_AutoConnect"></a> 순서도 및 상태 시스템 워크플로의 자동 연결 및 자동 삽입

.NET Framework 4에서는 순서도 워크플로의 노드 간 연결을 수동으로 추가 해야 했습니다. .NET Framework 4.5에서 순서도 및 상태 시스템 노드에는 활동을 도구 상자에서 디자이너 화면으로 끌 때 표시 되는 자동 연결 지점이 있습니다. 이러한 지점 중 하나에 활동을 놓으면 필요한 연결과 함께 활동이 자동으로 추가됩니다.

다음 스크린 샷에서는 도구 상자에서 디자이너 화면으로 활동을 끌어 올 때 표시되는 연결 지점을 보여 줍니다.

![자동 연결 요소를 보여 주는 순서도 시작 노드](./media/whats-new-in-wf-in-dotnet/auto-connect-points-start-node.png)

활동을 순서도 노드와 상태 간 연결로 끌어 와 다른 두 노드 사이에 노드를 자동으로 삽입할 수도 있습니다. 다음 스크린 샷에서는 도구 상자의 활동을 끌어다 놓을 수 있는 강조 표시된 연결선을 보여 줍니다.

![활동을 끌기 위한 자동 삽입 핸들](./media/whats-new-in-wf-in-dotnet/auto-insert-connecting-line.png)

### <a name="designer-annotations"></a><a name="BKMK_Annotations"></a> 디자이너 주석

이제 대규모 워크플로를 손쉽게 개발할 수 있도록 디자이너에서 주석을 추가하여 디자인 프로세스를 추적할 수 있습니다. 주석은 활동, 상태, 순서도 노드, 변수 및 인수에 추가할 수 있습니다. 다음 스크린 샷에서는 디자이너에 주석을 추가하는 데 사용되는 상황에 맞는 메뉴를 보여 줍니다.

![주석을 추가 하는 메뉴를 보여 주는 스크린샷](./media/whats-new-in-wf-in-dotnet/designer-annotations-context-menu.png)

### <a name="debugging-states"></a>상태 디버깅

.NET Framework 4에서 활동이 아닌 요소는 실행 단위가 아니기 때문에 디버그 중단점을 지원할 수 없습니다. 이 릴리스에서는 <xref:System.Activities.Statements.State> 개체에 중단점을 추가하는 메커니즘을 제공합니다. <xref:System.Activities.Statements.State>에서 중단점을 설정하면 해당 진입 활동 또는 트리거가 예약되기 전에 상태 전환 시점에서 실행이 중단됩니다.

### <a name="define-and-consume-activitydelegate-objects-in-the-designer"></a><a name="BKMK_ActivityDelegates"></a> 디자이너에서 ActivityDelegate 개체 정의 및 사용

.NET Framework 4의 활동을 사용 <xref:System.Activities.ActivityDelegate> 하 여 워크플로의 다른 부분이 워크플로의 실행과 상호 작용할 수 있는 실행 지점을 노출 하지만 이러한 실행 지점을 사용 하려면 일반적으로 상당한 양의 코드가 필요 합니다. 이 릴리스에서는 개발자가 워크플로 디자이너를 사용하여 활동 대리자를 정의하고 사용할 수 있습니다. 자세한 내용은 [방법: 워크플로 디자이너에서 작업 대리자 정의 및 사용](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer)을 참조 하세요.

### <a name="build-time-validation"></a><a name="BKMK_BuildTimeValidation"></a> 빌드 타임 유효성 검사

.NET Framework 4에서는 워크플로 프로젝트를 빌드하는 동안 워크플로 유효성 검사 오류가 빌드 오류로 계산 되지 않았습니다. 따라서 워크플로 유효성 검사 오류가 있더라도 워크플로 프로젝트를 성공적으로 빌드할 수 있었습니다. .NET Framework 4.5에서 워크플로 유효성 검사 오류로 인해 빌드가 실패 합니다.

### <a name="design-time-background-validation"></a><a name="BKMK_DesignTimeValidation"></a> 디자인 타임 백그라운드 유효성 검사

.NET Framework 4에서 워크플로는 포그라운드 프로세스로 유효성이 검사 되어 복잡 하거나 시간이 많이 걸리는 유효성 검사 프로세스 중에 UI를 차단할 수 있습니다. 이제는 백그라운드 스레드에서 워크플로 유효성 검사를 수행하므로 UI가 차단되지 않습니다.

### <a name="view-state-located-in-a-separate-location-in-xaml-files"></a><a name="BKMK_ViewState"></a> XAML 파일의 별도 위치에 있는 뷰 상태

.NET Framework 4에서 워크플로의 뷰 상태 정보는 다양 한 위치에 있는 XAML 파일을 통해 저장 됩니다. 따라서 개발자가 XAML을 직접 읽거나 뷰 상태 정보를 제거하는 코드를 작성하기에 불편했습니다. .NET Framework 4.5에서 XAML 파일의 뷰 상태 정보는 XAML 파일에서 별도의 요소로 serialize 됩니다. 개발자는 활동의 뷰 상태 정보를 쉽게 찾아 편집 하거나 뷰 상태를 완전히 제거할 수 있습니다.

### <a name="expression-extensibility"></a><a name="BKMK_ExpressionExtensibility"></a> 식 확장성

.NET Framework 4.5에서는 개발자가 workflow designer에 연결 될 수 있는 고유한 식 및 식 작성 환경을 만들 수 있는 방법을 제공 합니다.

### <a name="opt-in-for-workflow-45-features-in-rehosted-designer"></a><a name="BKMK_BackwardCompatRehostedDesigner"></a> 재 호스트 된 디자이너의 Workflow 4.5 기능에 대 한 옵트인

이전 버전과의 호환성을 유지 하기 위해 .NET Framework 4.5에 포함 된 일부 새로운 기능은 재 호스트 된 디자이너에서 기본적으로 사용 되지 않습니다. 따라서 재호스트된 디자이너를 사용하는 기존 애플리케이션은 최신 버전으로 업데이트해도 차단되지 않습니다. 재호스트된 디자이너에서 새로운 기능을 사용하려면 <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A>을 ".NET Framework 4.5"로 설정하거나 <xref:System.Activities.Presentation.DesignerConfigurationService>의 개별 멤버를 설정하여 개별 기능을 사용하도록 설정합니다.

## <a name="new-workflow-development-models"></a><a name="BKMK_NewWFModels"></a> 새 워크플로 개발 모델

순서도 및 순차 워크플로 개발 모델 외에도 이 릴리스에는 상태 시스템 워크플로 및 계약 중심 워크플로 서비스가 포함되어 있습니다.

### <a name="state-machine-workflows"></a><a name="BKMK_StateMachine"></a> 상태 시스템 워크플로

상태 시스템 워크플로는 [Microsoft .NET Framework 4 플랫폼 업데이트 1](/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1)에서 .NET Framework 4 버전 4.0.1의 일부로 도입 되었습니다. 이 업데이트에는 여러 가지 새로운 클래스 및 활동이 포함되어 있으므로 개발자가 상태 시스템 워크플로를 만들 수 있었습니다. 이러한 클래스와 활동은 .NET Framework 4.5에 대해 업데이트 되었습니다. 업데이트에는 다음이 포함됩니다.

1. 상태에 중단점을 설정할 수 있는 기능

2. Workflow Designer에서 전환을 복사하여 붙여 넣을 수 있는 기능

3. 공유 트리거 전환 작성을 위한 디자이너 지원

4. <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State> 및 <xref:System.Activities.Statements.Transition>을 포함하여 상태 시스템 워크플로를 만드는 데 사용되는 활동

다음 스크린샷에서는 [시작 자습서](getting-started-tutorial.md) 단계 [방법: 상태 시스템 워크플로 만들기](how-to-create-a-state-machine-workflow.md)의 완료 된 상태 시스템 워크플로를 보여 줍니다.

![완료 된 상태 시스템 워크플로를 보여 주는 그림입니다.](./media/whats-new-in-wf-in-dotnet/complete-state-machine-workflow.jpg)

상태 시스템 워크플로를 만드는 방법에 대 한 자세한 내용은 [상태 시스템 워크플로](state-machine-workflows.md)를 참조 하세요.

### <a name="contract-first-workflow-development"></a><a name="BKMK_ContractFirst"></a> 계약 중심 워크플로 개발

개발자는 계약 중심 워크플로 개발 도구를 사용 하 여 코드에서 계약을 먼저 디자인 한 다음 Visual Studio에서 몇 번의 클릭으로 각 작업을 나타내는 도구 상자에 활동 템플릿을 자동으로 생성할 수 있습니다. 그런 다음 이러한 활동은 계약에서 정의한 작업을 구현하는 워크플로를 만드는 데 사용됩니다. 워크플로 디자이너는 워크플로 서비스의 유효성을 검사하여 이러한 작업을 구현하고 워크플로의 서명이 계약 서명과 일치하도록 합니다. 개발자는 워크플로 서비스와 구현된 계약 컬렉션을 연결할 수도 있습니다. 계약 중심 워크플로 서비스 개발에 대 한 자세한 내용은 [방법: 기존 서비스 계약을 사용 하는 워크플로 서비스 만들기](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)를 참조 하세요.
