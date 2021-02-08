---
description: '자세히 알아보기: 파일이 너무 커서 바이트 배열로 읽어 올 수 없습니다.'
title: 파일이 너무 커서 바이트 배열로 읽어 들일 수 없습니다.
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: 8b2eb7bcbbea42c56d607147e55d6c02695c5670
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796290"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a>파일이 너무 커서 바이트 배열로 읽어 들일 수 없습니다.

바이트 배열로 읽으려고 하는 파일 크기가 4gb를 초과 합니다. `My.Computer.FileSystem.ReadAllBytes`메서드가이 크기를 초과 하는 파일을 읽을 수 없습니다.  
  
## <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 을 사용 <xref:System.IO.StreamReader> 하 여 파일을 읽습니다. 자세한 내용은 [.NET Framework 파일 i/o 및 파일 시스템의 기본 사항 (Visual Basic)](../../developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)을 참조 하세요.  
  
## <a name="see-also"></a>참고 항목

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [Visual Basic을 사용한 파일 액세스](../../developing-apps/programming/drives-directories-files/file-access.md)
- [방법: StreamReader를 사용하여 파일에서 텍스트 읽기](../../developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
