---
description: '자세히 알아보기: 방법: 재 호스트 된 디자이너에서 유효성 검사 오류 표시'
title: '방법: 다시 호스트된 디자이너에서 유효성 검사 오류 표시'
ms.date: 03/30/2017
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
ms.openlocfilehash: 75ff45e6e9a81df96a9940ce21d1b160cab1000e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777738"
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a>방법: 다시 호스트된 디자이너에서 유효성 검사 오류 표시

이 항목에서는 재 호스트 된 Windows 워크플로 디자이너에서 유효성 검사 오류를 검색 하 고 게시 하는 방법에 대해 설명 합니다. 또한 다시 호스트된 디자이너의 워크플로가 유효한지 확인하는 절차도 제공합니다.  
  
 이 작업은 두 부분으로 구성되어 있습니다. 첫 번째 부분은 <xref:System.Activities.Presentation.Validation.IValidationErrorService> 구현을 제공하는 것입니다.  이 인터페이스에서 구현할 중요한 메서드인 <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>가 있습니다. 이 메서드는 디버그 로그 오류에 대한 정보가 들어 있는 <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> 개체 목록을 전달합니다.  인터페이스를 구현한 후 해당 구현의 인스턴스를 편집 컨텍스트에 게시하여 오류 정보를 검색합니다.  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a>IValidationErrorService 인터페이스 구현  
  
1. 다음은 유효성 검사 오류를 디버그 로그에 쓰는 간단한 구현을 위한 코드 샘플입니다.  
  
    ```csharp  
    using System.Activities.Presentation.Validation;  
    using System.Collections.Generic;  
    using System.Diagnostics;  
    using System.Linq;  
  
    namespace VariableFinderShell  
    {  
        class DebugValidationErrorService : IValidationErrorService  
        {  
            public void ShowValidationErrors(IList<ValidationErrorInfo> errors)  
            {  
                errors.ToList().ForEach(vei => Debug.WriteLine($"Error: {vei.Message}"));  
            }  
        }  
    }  
    ```  
  
### <a name="publishing-to-the-editing-context"></a>편집 컨텍스트에 게시  
  
1. 다음은 이 인스턴스를 편집 컨텍스트에 게시하는 코드입니다.  
  
    ```csharp  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
