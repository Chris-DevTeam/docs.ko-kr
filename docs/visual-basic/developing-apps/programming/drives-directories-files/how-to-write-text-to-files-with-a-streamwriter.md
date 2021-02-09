---
description: '자세한 정보: 방법: Visual Basic에서 StreamWriter를 사용하여 파일에 텍스트 쓰기'
title: '방법: StreamWriter를 사용하여 파일에 텍스트 쓰기'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: d5528d0b5e7de40062558d29c0d3bebc227583a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797356"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a>방법: Visual Basic에서 StreamWriter를 사용하여 파일에 텍스트 쓰기

이 예제에서는 `My.Computer.FileSystem.OpenTextFileWriter` 메서드를 사용하여 <xref:System.IO.StreamWriter> 개체를 열고 이 개체를 사용하여 <xref:System.IO.StreamWriter> 클래스의 <xref:System.IO.TextWriter.WriteLine%2A> 메서드로 텍스트 파일에 문자열을 씁니다.  
  
## <a name="example"></a>예제  

 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a>강력한 프로그래밍  

 다음 조건에서 예외가 발생합니다.  
  
- 파일이 있지만 읽기 전용인 경우(<xref:System.IO.IOException>)  
  
- 디스크가 꽉 찬 경우(<xref:System.IO.IOException>)  
  
- 경로 이름이 너무 긴 경우(<xref:System.IO.PathTooLongException>)  
  
## <a name="net-framework-security"></a>.NET Framework 보안  

 이 예제에서는 파일이 아직 없는 경우 새 파일을 만듭니다. 애플리케이션에서 파일을 만들어야 하는 경우 해당 애플리케이션에 폴더에 대한 `Create` 권한이 있어야 합니다. 파일이 이미 있는 경우 애플리케이션에 더 낮은 권한인 `Write` 권한만 있으면 됩니다. 가능한 경우 배포하는 동안 파일을 만들고, 폴더에 대한 `Create` 권한 대신 단일 파일에 대해 `Read` 권한만 부여하는 것이 더 안전합니다.  
  
## <a name="see-also"></a>참조

- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [방법: 텍스트 파일에서 읽기](how-to-read-from-text-files.md)
- [파일에 쓰기](writing-to-files.md)
