---
description: '자세한 정보: 방법: Visual Basic에서 파일 이름 및 경로 유효성 검사'
title: '방법: 파일 이름 및 경로의 유효성 검사'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: 02a48ea7cbf3291cb2fe1c64c4e636a273842546
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429742"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>방법: Visual Basic에서 파일 이름 및 경로 확인

이 예에서는 `Boolean` 문자열이 파일 이름 또는 경로를 나타내는지 여부를 나타내는 값을 반환 합니다. 유효성 검사는 이름에 파일 시스템에서 허용 하지 않는 문자가 포함 되어 있는지 확인 합니다.  
  
## <a name="example"></a>예  

 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 이 예에서는 이름에 잘못 된 콜론 또는 이름이 없는 디렉터리가 있는지 여부를 확인 하지 않으며 이름의 길이가 시스템에서 정의한 최대 길이를 초과 하는지 여부를 확인 하지 않습니다. 또한 지정 된 이름을 사용 하 여 응용 프로그램에 파일 시스템 리소스에 대 한 액세스 권한이 있는지 여부는 확인 하지 않습니다.  
  
## <a name="see-also"></a>추가 정보

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [Visual Basic의 문자열 유효성 검사](validating-strings.md)
