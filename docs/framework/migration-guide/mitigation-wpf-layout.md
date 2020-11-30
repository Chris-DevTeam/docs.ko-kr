---
title: '완화: WPF 레이아웃'
description: 한 픽셀씩 이동하는 개체의 배치와 같이 WPF 컨트롤 레이아웃을 변경하여 발생하는 문제를 완화하는 방법에 대해 알아봅니다.
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: caed758f6e86a1e2bee255c2f29ca3160b327e17
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244082"
---
# <a name="mitigation-wpf-layout"></a>완화: WPF 레이아웃

WPF 컨트롤의 레이아웃은 약간 변경될 수 있습니다.  
  
## <a name="impact"></a>영향  

 레이아웃을 변경한 결과는 다음과 같습니다.  
  
- 요소의 너비나 높이가 최대 1픽셀씩 늘어나거나 줄어들 수 있습니다.  
  
- 개체의 배치가 최대 1픽셀씩 이동할 수 있습니다.  
  
- 가운데 맞춤 요소가 가로 또는 세로로 최대 1픽셀씩 가운데에서 벗어날 수 있습니다.  
  
 기본적으로 이 새 레이아웃은 .NET Framework 4.6을 대상으로 하는 앱에 대해서만 사용할 수 있습니다.  
  
## <a name="mitigation"></a>완화  

 이 수정은 높은 DPI에서 WPF 컨트롤의 오른쪽 또는 아래쪽의 클리핑을 제거하는 경향이 있으므로 이전 버전의 .NET Framework를 대상으로 하지만 NET Framework 4.6에서 실행되는 앱은 다음 줄을 app.config 파일의 `<runtime>` 섹션에 추가하여 이 새 동작을 옵트인(opt in)할 수 있습니다.  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 .NET Framework 4.6을 대상으로 하지만 이전 레이아웃 알고리즘을 사용하여 WPF 컨트롤을 렌더링하려는 앱은 다음 줄을 app.config 파일의 `<runtime>` 섹션에 추가하여 수행할 수 있습니다.  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a>참조

- [애플리케이션 호환성](application-compatibility.md)
