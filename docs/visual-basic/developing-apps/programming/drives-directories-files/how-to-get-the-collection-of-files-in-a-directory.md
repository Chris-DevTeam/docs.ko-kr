---
description: '자세한 정보: 방법: Visual Basic에서 디렉터리의 파일 컬렉션 가져오기'
title: '방법: 디렉터리의 파일 컬렉션 가져오기'
ms.date: 07/20/2015
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
ms.openlocfilehash: bd799390c0ad0868f51387ba12e8612fe8948297
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797538"
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a>방법: Visual Basic에서 디렉터리의 파일 컬렉션 가져오기

<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> 메서드의 오버로드는 디렉터리 내의 파일 이름을 나타내는 문자열의 읽기 전용 컬렉션을 반환합니다.  
  
- 하위 디렉터리를 검색하지 않고 지정된 디렉터리에서 단순 파일 검색을 수행하려면 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> 오버로드를 사용합니다.  
  
- 검색을 위한 추가 옵션을 지정하려면 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> 오버로드를 사용합니다. `wildCards` 매개 변수를 사용하면 검색 패턴을 지정할 수 있습니다. 검색에 하위 디렉터리를 포함하려면 `searchType` 매개 변수를 <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>로 설정합니다.  
  
 지정한 패턴과 일치하는 파일이 없으면 빈 컬렉션이 반환됩니다.  
  
### <a name="to-list-files-in-a-directory"></a>디렉터리의 파일을 나열하려면  
  
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> 메서드 오버로드 중 하나를 사용하고 `directory` 매개 변수에서 검색할 디렉터리의 이름과 경로를 제공합니다. 다음 예제에서는 디렉터리의 모든 파일을 반환하여 `ListBox1`에 추가합니다.  
  
     [!code-vb[VbVbcnMyFileSystem#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#32)]  
  
## <a name="robust-programming"></a>강력한 프로그래밍  

 다음 조건에서 예외가 발생합니다.  
  
- 길이가 0인 문자열이거나, 공백만 포함하거나, 잘못된 문자를 포함하거나, 경로가 디바이스 경로인 경우(\\\\.\\로 시작됨)와 같은 여러 가지 이유 중 하나로 경로가 올바르지 않은 경우(<xref:System.ArgumentException>)  
  
- 경로가 `Nothing` 이기 때문에 올바르지 않은 경우(<xref:System.ArgumentNullException>)  
  
- `directory`가 없는 경우(<xref:System.IO.DirectoryNotFoundException>)  
  
- `directory`가 기존 파일을 가리키는 경우(<xref:System.IO.IOException>)  
  
- 경로가 시스템 정의 최대 길이를 초과하는 경우(<xref:System.IO.PathTooLongException>)  
  
- 경로의 파일 이름이나 디렉터리 이름에 콜론(:)이 있거나 이름의 형식이 잘못된 경우(<xref:System.NotSupportedException>)  
  
- 경로를 보는 데 필요한 권한이 사용자에게 없는 경우(<xref:System.Security.SecurityException>)  
  
- 사용자에게 필요한 권한이 없는 경우(<xref:System.UnauthorizedAccessException>)  
  
## <a name="see-also"></a>참고 항목

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>
- [방법: 특정 패턴의 파일 찾기](how-to-find-files-with-a-specific-pattern.md)
- [방법: 특정 패턴의 하위 디렉터리 찾기](how-to-find-subdirectories-with-a-specific-pattern.md)
