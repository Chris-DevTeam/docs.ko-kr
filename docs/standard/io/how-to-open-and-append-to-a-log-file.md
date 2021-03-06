---
title: '방법: 열기 및 로그 파일에 추가'
description: .NET에서 스트림에 문자를 쓰고 스트림에서 문자를 읽는 StreamWriter 및 StreamReader 클래스를 사용하여 로그 파일을 열고 로그 파일에 추가합니다.
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
ms.openlocfilehash: ed8345901dc5f44e947bd076944d7e61eac561da
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188174"
---
# <a name="how-to-open-and-append-to-a-log-file"></a>방법: 열기 및 로그 파일에 추가

<xref:System.IO.StreamWriter> 및 <xref:System.IO.StreamReader>는 스트림에서 문자를 쓰고 문자를 읽습니다. 다음 코드 예제는 입력을 위해 *log.txt* 파일을 열거나, 파일이 존재하지 않는 경우 파일을 만들고 파일의 끝에 로그 정보를 추가합니다. 이 예제는 파일의 콘텐츠를 디스플레이의 표준 출력에 씁니다.

이 예제의 대안으로, 정보를 단일 문자열 또는 문자열 배열로 저장하고, <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> 또는 <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> 메서드를 사용하여 동일한 기능을 수행할 수도 있습니다.  
  
> [!NOTE]
> Visual Basic 사용자는 로그 파일을 생성하거나 로그 파일에 쓰기 위해 <xref:Microsoft.VisualBasic.Logging.Log> 클래스 또는 <xref:Microsoft.VisualBasic.FileIO.FileSystem> 클래스에서 제공하는 메서드 및 속성을 사용하도록 선택할 수 있습니다.  
  
## <a name="example"></a>예제  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a>참조

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [방법: 디렉터리 및 파일 열거](how-to-enumerate-directories-and-files.md)  
- [방법: 새로 만든 데이터 파일 읽기 및 쓰기](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [방법: 파일에서 텍스트 읽기](how-to-read-text-from-a-file.md)  
- [방법: 파일에 텍스트 쓰기](how-to-write-text-to-a-file.md)  
- [방법: 문자열에서 문자 읽기](how-to-read-characters-from-a-string.md)  
- [방법: 문자열에 문자 쓰기](how-to-write-characters-to-a-string.md)  
- [파일 및 스트림 I/O](index.md)
