---
description: '자세한 정보: GetXmlNamespace 연산자 (Visual Basic)'
title: GetXmlNamespace 연산자
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: 704ac22493a0d6ce1255d171ae3b418313b74f09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665915"
---
# <a name="getxmlnamespace-operator-visual-basic"></a>GetXmlNamespace 연산자(Visual Basic)

지정 된 <xref:System.Xml.Linq.XNamespace> XML 네임 스페이스 접두사에 해당 하는 개체를 가져옵니다.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>부분  

 `xmlNamespacePrefix`  
 선택 사항입니다. XML 네임 스페이스 접두사를 식별 하는 문자열입니다. 제공 되는 경우이 문자열은 올바른 XML 식별자 여야 합니다. 자세한 내용은 [선언 된 XML 요소 및 특성의 이름](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)을 참조 하세요. 접두사가 지정 되지 않은 경우에는 기본 네임 스페이스가 반환 됩니다. 기본 네임 스페이스를 지정 하지 않으면 빈 네임 스페이스가 반환 됩니다.  
  
## <a name="return-value"></a>Return Value  

 <xref:System.Xml.Linq.XNamespace>XML 네임 스페이스 접두사에 해당 하는 개체입니다.  
  
## <a name="remarks"></a>설명  

 `GetXmlNamespace`연산자는 <xref:System.Xml.Linq.XNamespace> XML 네임 스페이스 접두사에 해당 하는 개체를 가져옵니다 `xmlNamespacePrefix` .  
  
 Xml 리터럴 및 XML 축 속성에 XML 네임 스페이스 접두사를 직접 사용할 수 있습니다. 그러나 `GetXmlNamespace` <xref:System.Xml.Linq.XNamespace> 코드에서 사용할 수 있으려면 먼저 연산자를 사용 하 여 네임 스페이스 접두사를 개체로 변환 해야 합니다. 정규화 되지 않은 요소 이름을 개체에 추가 <xref:System.Xml.Linq.XNamespace> 하 여 <xref:System.Xml.Linq.XName> 많은 메서드에 필요한 정규화 된 개체를 가져올 수 있습니다 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .  
  
## <a name="example"></a>예제  

 다음 예제에서는 `ns` XML 네임 스페이스 접두사로를 가져옵니다. 그런 다음 네임 스페이스의 접두사를 사용 하 여 XML 리터럴을 만들고 정규화 된 이름을 가진 첫 번째 자식 노드에 액세스 합니다 `ns:phone` . 그런 다음 해당 자식 노드를 서브루틴에 전달 `ShowName` 합니다 .이 서브루틴은 연산자를 사용 하 여 정규화 된 이름을 생성 합니다 `GetXmlNamespace` . `ShowName`그러면 서브루틴이 정규화 된 이름을 메서드에 전달 하 여 <xref:System.Xml.Linq.XNode.Ancestors%2A> 부모 노드를 가져옵니다 `ns:contact` .  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 를 호출 하면 `TestGetXmlNamespace.RunSample()` 다음 텍스트를 포함 하는 메시지 상자가 표시 됩니다.  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>참고 항목

- [Imports 문(XML 네임스페이스)](../statements/imports-statement-xml-namespace.md)
- [Visual Basic에서 XML에 액세스](../../programming-guide/language-features/xml/accessing-xml.md)
