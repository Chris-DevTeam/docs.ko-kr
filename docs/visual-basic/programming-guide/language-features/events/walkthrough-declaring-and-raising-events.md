---
description: '자세한 정보: 연습: 이벤트 선언 및 발생 (Visual Basic)'
title: 이벤트 선언 및 발생
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 98e9d2eabd1ace06de9f8cc7931013093d864e7a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466382"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>연습: 이벤트 선언 및 발생(Visual Basic)

이 연습에서는 라는 클래스에 대 한 이벤트를 선언 하 고 발생 시키는 방법을 보여 줍니다 `Widget` . 단계를 완료 한 후에는 개체의 이벤트를 사용 하 여 응용 프로그램에서 상태 정보를 제공 하는 방법을 보여 주는 [연습: 이벤트 처리](walkthrough-handling-events.md)항목을 읽어 볼 수 있습니다 `Widget` .  
  
## <a name="the-widget-class"></a>Widget 클래스  

 클래스가 있는 순간을 가정 합니다 `Widget` . 클래스에는 `Widget` 실행 하는 데 시간이 오래 걸릴 수 있는 메서드가 있으며 응용 프로그램에서 일종의 완성 표시기를 배치할 수 있도록 하려고 합니다.  
  
 물론 `Widget` 개체에 완료율 대화 상자를 표시 하 고 클래스를 사용한 모든 프로젝트에서 해당 대화 상자를 사용 하 여 작업을 수행할 수 있습니다 `Widget` . 개체를 사용 하는 응용 프로그램은 폼 이나 대화 상자를 관리 하는 것이 아니라 개체를 사용 하는 응용 프로그램에서 사용자 인터페이스를 처리 하도록 하는 것이 좋습니다.  
  
 의 목적은 `Widget` 다른 작업을 수행 하는 것 이므로 이벤트를 추가 하 `PercentDone` 고 메서드를 호출 하는 프로시저에서 `Widget` 해당 이벤트를 처리 하 고 상태 업데이트를 표시 하는 것이 좋습니다. `PercentDone`또한 이벤트는 태스크를 취소 하는 메커니즘을 제공할 수 있습니다.  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>이 항목에 대 한 코드 예제를 빌드하려면  
  
1. 새 Visual Basic Windows 응용 프로그램 프로젝트를 열고 이라는 폼을 만듭니다 `Form1` .  
  
2. 에 두 개의 단추와 레이블을 추가 `Form1` 합니다.  
  
3. 다음 표에 나와 있는 것처럼 개체의 이름을 지정합니다.  
  
    |Object|속성|설정|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|시작 태스크|  
    |`Button2`|`Text`|취소|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4. **프로젝트** 메뉴에서 **클래스 추가** 를 선택 하 여 라는 클래스를 `Widget.vb` 프로젝트에 추가 합니다.  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>Widget 클래스의 이벤트를 선언 하려면  
  
- `Event`클래스에서 이벤트를 선언 하려면 키워드를 사용 `Widget` 합니다. 이벤트는 `ByVal` 및 인수를 가질 수 있으며 `ByRef` , 이벤트 `Widget` 는 `PercentDone` 다음과 같습니다.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 호출 하는 개체가 이벤트를 수신 하면 `PercentDone` `Percent` 인수에 완료 된 작업의 백분율이 포함 됩니다. `Cancel`이벤트를 발생 시킨 메서드를 취소 하려면 인수를로 설정할 수 있습니다 `True` .  
  
> [!NOTE]
> 프로시저의 인수를 사용 하는 것과 같은 방법으로 이벤트 인수를 선언할 수 있습니다. 단, 이벤트에 `Optional` 또는 인수를 사용할 수 없고 `ParamArray` 이벤트에 반환 값이 없습니다.  
  
 `PercentDone`이벤트는 `LongTask` 클래스의 메서드에 의해 발생 합니다 `Widget` . `LongTask`는 두 개의 인수, 즉 메서드가 작업을 수행 하는 데 걸리는 시간 및 `LongTask` 이벤트를 발생 시키기 위해 일시 중지 되기 전의 최소 시간 간격을 lie 합니다. `PercentDone`  
  
#### <a name="to-raise-the-percentdone-event"></a>PercentDone 이벤트를 발생 시키려면  
  
1. 이 클래스에서 사용 하는 속성에 대 한 액세스를 간소화 하려면 문 `Timer` `Imports` 위의 클래스 모듈의 선언 섹션 맨 위에 문을 추가 `Class Widget` 합니다.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. `Widget` 클래스에 다음 코드를 추가합니다.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 응용 프로그램에서 메서드를 호출 하는 경우 `LongTask` `Widget` 클래스는 `PercentDone` 초 마다 이벤트를 발생 시킵니다 `MinimumInterval` . 이벤트가 반환 되 면는 `LongTask` `Cancel` 인수가로 설정 되었는지 확인 `True` 합니다.  
  
 여기에 몇 가지 법적 사항이 필요 합니다. 간단 하 게 하기 위해이 `LongTask` 절차에서는 작업에 소요 되는 시간을 미리 알고 있다고 가정 합니다. 거의 그렇지 않습니다. 작업을 짝수의 청크로 분할 하는 것은 어려울 수 있으며, 대부분의 경우 사용자에 게 가장 중요 한 것은 문제가 발생 했음을 표시 하기 전에 경과 하는 시간입니다.  
  
 이 샘플에서 다른 결함을 발견 했을 수 있습니다. `Timer`속성은 자정 이후 경과 된 시간 (초)을 반환 하므로 응용 프로그램이 자정 직전에 시작 되 면 중지 됩니다. 보다 신중 하 게 시간을 측정 하는 방법은와 같은 속성을 사용 하 여 이러한 상황을 고려 하거나 함께 사용 하지 않도록 하는 것 `Now` 입니다.  
  
 이제 `Widget` 클래스가 이벤트를 발생 시킬 수 있으므로 다음 연습으로 이동할 수 있습니다. [연습: 이벤트 처리](walkthrough-handling-events.md) 는를 사용 하 여 이벤트 `WithEvents` 처리기를 이벤트와 연결 하는 방법을 보여 줍니다 `PercentDone` .  
  
## <a name="see-also"></a>추가 정보

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [연습: 이벤트 처리](walkthrough-handling-events.md)
- [이벤트](index.md)
