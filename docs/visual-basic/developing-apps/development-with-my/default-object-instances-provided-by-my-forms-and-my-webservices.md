---
description: '자세한 정보: My.Forms 및 My.WebServices에서 제공하는 기본 개체 인스턴스(Visual Basic)'
title: My.Forms 및 My.WebServices에서 제공하는 기본 개체 인스턴스
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: 34363a56577ca0fafb839e782a8066bd8a8c5a14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775359"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>My.Forms 및 My.WebServices에서 제공하는 기본 개체 인스턴스(Visual Basic)

[My.Forms](../../language-reference/objects/my-forms-object.md) 및 [My.WebServices](../../language-reference/objects/my-webservices-object.md) 개체는 애플리케이션에서 사용되는 폼, 데이터 원본 및 XML Web services에 대한 액세스를 제공합니다. 이들 각 개체의 ‘기본 인스턴스’ 컬렉션을 통해 액세스를 제공합니다.  
  
## <a name="default-instances"></a>기본 인스턴스  

 기본 인스턴스는 런타임이 제공하는 클래스의 인스턴스이고 `Dim` 및 `New` 문을 사용하여 선언하고 인스턴스화할 필요가 없습니다. 다음 예제에서는 `Form1`이라는 <xref:System.Windows.Forms.Form> 클래스의 인스턴스를 선언하고 인스턴스화한 후 `My.Forms`를 통해 이 <xref:System.Windows.Forms.Form> 클래스의 기본 인스턴스를 가져오는 방법을 보여 줍니다.  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 `My.Forms` 개체는 프로젝트에 있는 모든 `Form` 클래스의 기본 인스턴스 컬렉션을 반환합니다. 마찬가지로 `My.WebServices`는 애플리케이션에서 참조를 만든 모든 웹 서비스에 대한 프록시 클래스의 기본 인스턴스를 제공합니다.  
  
## <a name="see-also"></a>참조

- [My.Forms 개체](../../language-reference/objects/my-forms-object.md)
- [My.WebServices 개체](../../language-reference/objects/my-webservices-object.md)
- [My가 프로젝트 형식에 의존하는 방식](how-my-depends-on-project-type.md)
