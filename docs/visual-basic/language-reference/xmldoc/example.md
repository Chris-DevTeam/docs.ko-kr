---
description: 다음에 대해 자세히 알아보세요. <example> (Visual Basic)
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 643e06fd24e38123dd2693d671b9ab33da5b413e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787489"
---
# <a name="example-visual-basic"></a>\<example>(Visual Basic)

멤버에 대 한 예제를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a>매개 변수  

 `description`  
 코드 샘플에 대한 설명입니다.  
  
## <a name="remarks"></a>설명  

 `<example>` 태그를 사용하면 메서드 또는 기타 라이브러리 멤버를 사용하는 방법의 예제를 지정할 수 있습니다. 여기에는 일반적으로 [\<code>](code.md) 태그를 같이 사용합니다.  
  
 [-doc](../../reference/command-line-compiler/doc.md)로 컴파일하여 문서 주석을 파일로 처리합니다.  
  
## <a name="example"></a>예제  

 이 예제에서는 태그를 사용 하 여 `<example>` 필드 사용에 대 한 예제를 포함 합니다 `ID` .  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>참고 항목

- [XML 주석 태그](index.md)
