---
description: '자세한 정보: 방법: Visual Basic에서 애플리케이션 설정 읽기'
title: '방법: 애플리케이션 설정 읽기'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 30b5a3b0cdf3565fc8c1f0dfa19e7717a714c350
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797824"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a>방법: Visual Basic에서 애플리케이션 설정 읽기

`My.Settings` 개체에서 설정의 속성에 액세스하여 사용자 설정을 읽을 수 있습니다.  
  
 `My.Settings` 개체는 각 설정을 속성으로 표시합니다. 속성 이름은 설정 이름과 같고 속성 형식은 설정 형식과 같습니다. 설정의 **범위** 는 속성이 읽기 전용인지 여부를 나타냅니다. **애플리케이션** 범위 설정의 속성은 읽기 전용이지만 **사용자** 범위 설정의 속성은 읽기-쓰기입니다. 자세한 내용은 [My.Settings 개체](../../../language-reference/objects/my-settings-object.md)를 참조하세요.  
  
## <a name="example"></a>예제  

 이 예제에서는 `Nickname` 설정의 값을 표시합니다.  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 이 예제가 작동하려면 애플리케이션에 `String` 형식의 `Nickname` 설정이 있어야 합니다. 자세한 내용은 [애플리케이션 설정 관리(.NET)](/visualstudio/ide/managing-application-settings-dotnet)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목

- [My.Settings 개체](../../../language-reference/objects/my-settings-object.md)
- [방법: Visual Basic에서 사용자 설정 변경](how-to-change-user-settings.md)
- [방법: Visual Basic에서 사용자 설정 유지](how-to-persist-user-settings.md)
- [방법: Visual Basic에서 사용자 설정의 속성 표 만들기](how-to-create-property-grids-for-user-settings.md)
- [애플리케이션 설정 관리(.NET)](/visualstudio/ide/managing-application-settings-dotnet)
