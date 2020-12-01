---
title: '완화: 경로 콜론 검사'
description: 적절한 드라이브 구분 기호 구문(콜론)에 대한 검사를 지원하도록 .NET Framework 4.6.2에서 변경된 사항에 대해 알아봅니다.
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: 03f1c7249549aae7e3bef986c97fb5f320fbeb2f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283460"
---
# <a name="mitigation-path-colon-checks"></a>완화: 경로 콜론 검사

.NET Framework 4.6.2를 대상으로 하는 앱부터 이전에 지원되지 않던 경로를 지원하도록 여러 가지 변경이 수행되었습니다(길이 및 형식 측면에서). 특히 적절한 드라이브 구분 기호 구문(콜론)에 대한 확인이 좀 더 정확해졌습니다.  
  
## <a name="impact"></a>영향  

 이러한 변경으로 인해 <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> 및 <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> 메서드에서 이전에 지원했던 일부 URI 경로가 차단됩니다.  
  
## <a name="mitigation"></a>완화  

 전에는 허용되었지만 <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> 및 <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> 메서드로 더 이상 지원되지 않는 경로 문제를 해결하려면 다음을 수행할 수 있습니다.  
  
- URL에서 스키마를 수동으로 제거합니다. 예를 들어 URL에서 `file://`을 제거합니다.  
  
- URI를 <xref:System.Uri> 생성자에 전달하고 <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> 속성 값을 검색합니다.  
  
- `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> 스위치를 `true`로 설정하여 새 경로 정규화를 취소합니다.  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
    </runtime>  
    ```  
  
## <a name="see-also"></a>참조

- [애플리케이션 호환성](application-compatibility.md)
