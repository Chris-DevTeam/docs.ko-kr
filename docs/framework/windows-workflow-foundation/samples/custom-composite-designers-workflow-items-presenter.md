---
description: '자세한 정보: 사용자 지정 복합 디자이너-워크플로 항목 프레 젠 터'
title: 사용자 지정 복합 디자이너 - 워크플로 항목 프리젠터
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
ms.openlocfilehash: 07970763e12eccd981370f1241642cc28f675824
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792585"
---
# <a name="custom-composite-designers---workflow-items-presenter"></a>사용자 지정 복합 디자이너 - 워크플로 항목 프리젠터

<xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> 는 포함된 요소의 컬렉션을 편집할 수 있도록 하는 WF 디자이너 프로그래밍 모델의 키 형식입니다. 이 샘플에서는 이러한 편집 가능한 컬렉션을 표시하는 활동 디자이너를 빌드하는 방법을 보여 줍니다.

이 샘플에서 설명하는 방법은 다음과 같습니다.

- <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>를 사용하여 사용자 지정 활동 디자이너 만들기

- "축소" 및 "확장" 보기를 사용 하 여 활동 디자이너 만들기

- 다시 호스트된 애플리케이션에서 기본 디자이너 재정의

## <a name="set-up-build-and-run-the-sample"></a>샘플 설정, 빌드 및 실행

1. C #에 대 한 **usingworkflowitemspresenter.sln** 샘플 솔루션 또는 Visual Studio 2010의 Visual Basic을 엽니다.

2. 솔루션을 빌드하고 실행합니다.

   다시 호스트 된 워크플로 디자이너 응용 프로그램이 열리고 작업을 캔버스로 끌어 올 수 있습니다.

## <a name="sample-highlights"></a>샘플의 중요 사항

이 샘플의 코드는 다음 내용을 보여 줍니다.

- 디자이너가 빌드되는 활동:  `Parallel`

- <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>를 사용하여 사용자 지정 활동 디자이너를 만드는 방법 고려해야 할 몇 가지 사항은 다음과 같습니다.

  - WPF 데이터 바인딩을 사용하여 `ModelItem.Branches`에 바인딩합니다. `ModelItem`은 디자이너가 사용될 기본 개체(이 경우 `WorkflowElementDesigner`)를 참조하는 `Parallel`의 속성입니다.

  - <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType>을 사용하여 컬렉션의 개별 항목을 시각적으로 표시할 수 있습니다.

  - <xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType>은 컬렉션에 있는 항목의 레이아웃을 결정하는 데 제공할 수 있는 템플릿입니다. 이 경우에는 가로 스택 패널이 사용됩니다.

  다음 코드 예제에서는 이를 보여 줍니다.

  ```xaml
  <sad:WorkflowItemsPresenter HintText="Drop Activities Here"
                                Items="{Binding Path=ModelItem.Branches}">
      <sad:WorkflowItemsPresenter.SpacerTemplate>
        <DataTemplate>
          <Ellipse Width="10" Height="10" Fill="Black"/>
        </DataTemplate>
      </sad:WorkflowItemsPresenter.SpacerTemplate>
      <sad:WorkflowItemsPresenter.ItemsPanel>
        <ItemsPanelTemplate>
          <StackPanel Orientation="Horizontal"/>
        </ItemsPanelTemplate>
      </sad:WorkflowItemsPresenter.ItemsPanel>
    </sad:WorkflowItemsPresenter>
  ```

- `DesignerAttribute` 형식에 `Parallel`를 연결한 다음 보고되는 특성을 출력합니다.

  - 먼저 모든 기본 디자이너를 등록합니다.

    다음은 코드 예제입니다.

    ```csharp
    // register metadata
    (new DesignerMetadata()).Register();
    RegisterCustomMetadata();
    ```

    ```vb
    ' register metadata
    Dim metadata = New DesignerMetadata()
    metadata.Register()
    ' register custom metadata
    RegisterCustomMetadata()
    ```

  - 그런 다음 `RegisterCustomMetadata` 메서드에서 병렬을 재정의합니다.

    다음 코드에서는 C# 및 Visual Basic으로 이를 보여 줍니다.

    ```csharp
    void RegisterCustomMetadata()
    {
          AttributeTableBuilder builder = new AttributeTableBuilder();
          builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));
          MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

    ```vb
    Sub RegisterCustomMetadata()
       Dim builder As New AttributeTableBuilder()
       builder.AddCustomAttributes(GetType(Parallel), New DesignerAttribute(GetType(CustomParallelDesigner)))
       MetadataStore.AddAttributeTable(builder.CreateTable())
    End Sub
    ```

- 마지막으로, 다양한 데이터 템플릿과 트리거를 사용하여 `IsRootDesigner` 속성을 기반으로 적절한 템플릿을 선택합니다.

  다음은 코드 예제입니다.

  ```xaml
  <sad:ActivityDesigner x:Class="Microsoft.Samples.CustomParallelDesigner"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:sad="clr-namespace:System.Activities.Design;assembly=System.Activities.Design"
      xmlns:sadv="clr-namespace:System.Activities.Design.View;assembly=System.Activities.Design">
    <sad:ActivityDesigner.Resources>
      <DataTemplate x:Key="Expanded">
        <StackPanel>
          <TextBlock>This is the Expanded View</TextBlock>
          <sad:WorkflowItemsPresenter HintText="Drop Activities Here"
                                      Items="{Binding Path=ModelItem.Branches}">
            <sad:WorkflowItemsPresenter.SpacerTemplate>
              <DataTemplate>
                <Ellipse Width="10" Height="10" Fill="Black"/>
              </DataTemplate>
            </sad:WorkflowItemsPresenter.SpacerTemplate>
            <sad:WorkflowItemsPresenter.ItemsPanel>
              <ItemsPanelTemplate>
                <StackPanel Orientation="Horizontal"/>
              </ItemsPanelTemplate>
            </sad:WorkflowItemsPresenter.ItemsPanel>
          </sad:WorkflowItemsPresenter>
        </StackPanel>
      </DataTemplate>
      <DataTemplate x:Key="Collapsed">
        <TextBlock>This is the Collapsed View</TextBlock>
      </DataTemplate>
      <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
        <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
        <Style.Triggers>
          <DataTrigger Binding="{Binding Path=IsRootDesigner}" Value="true">
            <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
          </DataTrigger>
        </Style.Triggers>
      </Style>
    </sad: ActivityDesigner.Resources>
    <Grid>
      <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>
    </Grid>
  </sad: ActivityDesigner>
  ```

> [!IMPORTANT]
> 컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다. 계속하기 전에 다음(기본) 디렉터리를 확인하세요.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> 이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다. 이 샘플은 다음 디렉터리에 있습니다.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`

## <a name="see-also"></a>참고 항목

- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- [워크플로 디자이너로 애플리케이션 개발](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
