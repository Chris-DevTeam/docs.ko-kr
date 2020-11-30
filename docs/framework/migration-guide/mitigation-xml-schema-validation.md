---
title: '완화: XML 스키마 유효성 검사'
description: .NET Framework 4.6에서 복합 키를 사용하고 한 개의 키가 비어 있는 경우 XSD 스키마 유효성 검사가 고유한 제약 조건 위반을 검색합니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
ms.openlocfilehash: 0744a703c1e9dc35a8accc448d34f1a736e77e4d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253533"
---
# <a name="mitigation-xml-schema-validation"></a>완화: XML 스키마 유효성 검사

.NET Framework 4.6에서 복합 키를 사용하고 한 개의 키가 비어 있는 경우 XSD 스키마 유효성 검사가 고유한 제약 조건 위반을 검색합니다.  
  
## <a name="impact"></a>영향  

 이 변경에 따른 영향이 최소화되어야 합니다. 빈 키가 포함된 복합 키를 사용함으로써 `xsd:unique`가 위반된 경우 스키마 사양에 따라 스키마 유효성 검사 오류가 예상됩니다.  
  
## <a name="mitigation"></a>완화  

 복합 키에 한 개의 빈 키가 있는 경우 스키마 유효성 검사 오류 검색 여부는 구성 가능한 기능입니다.  
  
- .NET Framework 4.6을 대상으로 하는 앱부터 스키마 유효성 검사 오류 검색은 기본적으로 사용하도록 설정되어 있습니다. 그러나 스키마 유효성 검사 오류가 검색되지 않도록 이 기능을 옵트아웃(opt out)할 수 있습니다.  
  
- .NET Framework 4.6에서 실행되지만 .NET Framework 4.5.2 및 이전 버전을 대상으로 하는 앱에서는 스키마 유효성 검사 오류가 기본적으로 검색되지 않습니다. 그러나 스키마 유효성 검사 오류가 검색되도록 이 기능을 옵트인(opt in)할 수 있습니다.  
  
 이 동작은 <xref:System.AppContext> 클래스를 사용하여 `System.Xml.IgnoreEmptyKeySequences` 스위치의 값을 정의하도록 구성할 수 있습니다. 스위치의 기본값은 `false`(빈 키 시퀀스가 무시되지 않음)이기 때문에 .NET Framework 4.6을 대상으로 하는 앱은 다음 코드를 사용하여 스위치의 값을 `true`로 설정하면 해당 동작을 옵트아웃(opt out)할 수 있습니다.  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 .NET Framework 4.5.2 및 이전 버전을 대상으로 하는 앱의 경우 스위치의 기본값이 `true`(빈 키 시퀀스가 무시됨)이기 때문에 다음 코드를 사용하여 스위치의 값을 `false`로 설정하면 빈 키가 포함된 복합 키가 스키마 유효성 검사 오류를 생성하도록 할 수 있습니다.  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a>참조

- [애플리케이션 호환성](application-compatibility.md)
