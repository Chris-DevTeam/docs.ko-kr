---
description: '자세한 정보: 방법: Visual Basic에서 COM 개체 참조'
title: '방법: Visual Basic에서 COM 개체 참조'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
ms.openlocfilehash: f0c08e5be9144bdefc3fe0b4609bad2421889d52
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100477569"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a>방법: Visual Basic에서 COM 개체 참조

Visual Basic에서 형식 라이브러리가 있는 COM 개체에 대 한 참조를 추가 하려면 COM 라이브러리에 대 한 interop 어셈블리를 만들어야 합니다. COM 개체의 멤버에 대 한 참조는 interop 어셈블리로 라우팅되고 실제 COM 개체로 전달 됩니다. COM 개체의 응답이 interop 어셈블리로 라우팅되고 .NET Framework 응용 프로그램으로 전달 됩니다.  
  
 COM 개체에 대 한 형식 정보를 .NET 어셈블리에 포함 하 여 interop 어셈블리를 사용 하지 않고 COM 개체를 참조할 수 있습니다. 형식 정보를 포함 하려면 `Embed Interop Types` `True` COM 개체에 대 한 참조에 대 한 속성을로 설정 합니다. 명령줄 컴파일러를 사용 하 여 컴파일하는 경우 옵션을 사용 하 여 `/link` COM 라이브러리를 참조 합니다. 자세한 내용은 [링크 (Visual Basic)](../../reference/command-line-compiler/link.md)를 참조 하세요.  
  
 IDE (통합 개발 환경)에서 형식 라이브러리에 대 한 참조를 추가 하면 Visual Basic에서 자동으로 interop 어셈블리를 만듭니다. 명령줄에서 작업할 때 Tlbimp 유틸리티를 사용 하 여 interop 어셈블리를 수동으로 만들 수 있습니다.  
  
### <a name="to-add-references-to-com-objects"></a>COM 개체에 대 한 참조를 추가 하려면  
  
1. **프로젝트** 메뉴에서 **참조 추가** 를 선택한 다음 대화 상자에서 **COM** 탭을 클릭 합니다.  
  
2. COM 개체 목록에서 사용 하려는 구성 요소를 선택 합니다.  
  
3. Interop 어셈블리에 대 한 액세스를 간소화 하려면 `Imports` COM 개체를 사용 하는 클래스 또는 모듈의 맨 위에 문을 추가 합니다. 예를 들어 다음 코드 예제에서는 `INKEDLib` 라이브러리에서 참조 되는 개체에 대 한 네임 스페이스를 가져옵니다 `Microsoft InkEdit Control 1.0` .  
  
     [!code-vb[VbVbalrInterop#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#40)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a>Tlbimp를 사용 하 여 interop 어셈블리를 만들려면  
  
1. 검색 경로에 아직 없는 경우 Tlbimp의 위치를 검색 경로에 추가 하 고 현재 디렉터리가 있는 디렉터리에 있지 않은 경우에는 해당 위치를 검색 경로에 추가 합니다.  
  
2. 명령 프롬프트에서 Tlbimp를 호출 하 여 다음 정보를 제공 합니다.  
  
    - 형식 라이브러리를 포함 하는 DLL의 이름 및 위치  
  
    - 정보를 배치할 네임 스페이스의 이름 및 위치  
  
    - 대상 interop 어셈블리의 이름 및 위치  
  
     다음 코드는 예제를 제공합니다.  
  
    ```console  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     Tlbimp를 사용 하 여 등록 되지 않은 COM 개체의 경우에도 형식 라이브러리에 대 한 interop 어셈블리를 만들 수 있습니다. 그러나 interop 어셈블리에서 참조 하는 COM 개체를 사용 하려는 컴퓨터에 올바르게 등록 해야 합니다. Windows 운영 체제에 포함 된 Regsvr32 유틸리티를 사용 하 여 COM 개체를 등록할 수 있습니다.  
  
## <a name="see-also"></a>추가 정보

- [COM Interop](index.md)
- [Tlbimp.exe(형식 라이브러리 가져오기)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe(형식 라이브러리 내보내기)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [연습: COM 개체를 사용한 상속 구현](walkthrough-implementing-inheritance-with-com-objects.md)
- [상호 운용성 문제 해결](troubleshooting-interoperability.md)
- [Imports 문(.NET 네임스페이스 및 형식)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
