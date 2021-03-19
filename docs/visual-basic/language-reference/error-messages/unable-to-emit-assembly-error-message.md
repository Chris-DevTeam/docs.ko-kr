---
description: '다음에 대해 자세히 알아보세요. BC30145: 어셈블리를 내보낼 수 없습니다. <error message>'
title: 어셈블리를 생성할 수 없습니다. <error message>
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 2ba476b39b6aa441d8778ee0618dcc3dcf3f7ac8
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653284"
---
# <a name="bc30145-unable-to-emit-assembly-error-message"></a>BC30145: 어셈블리를 내보낼 수 없습니다. \<error message>

Visual Basic 컴파일러는 어셈블리 링커 *Al.exe*(Alink 라고도 함)를 호출 하 여 매니페스트를 사용 하 여 어셈블리를 생성 하 고, 링커가 어셈블리 만들기의 내보내기 단계에서 오류를 보고 합니다.

**오류 ID:** BC30145

## <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. 따옴표 붙은 오류 메시지를 검사 하 고 자세한 설명과 조언을 보려면 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) 항목을 참조 하세요.

2. [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) 또는 [Sn.exe (강력한 이름 도구)](../../../framework/tools/sn-exe-strong-name-tool.md)중 하나를 사용 하 여 어셈블리에 수동으로 서명 하세요.

3. 오류가 계속 발생하면 해당 상황에 대한 정보를 수집하여 Microsoft 기술 지원 서비스에 알립니다.

### <a name="to-sign-the-assembly-manually"></a>어셈블리에 수동으로 서명하려면

1. [Sn.exe (강력한 이름 도구)](../../../framework/tools/sn-exe-strong-name-tool.md))를 사용 하 여 공개/개인 키 쌍 파일을 만듭니다.

   이 파일의 확장명은 *.snk* 입니다.

2. 프로젝트에서 오류를 생성하는 COM 참조를 삭제합니다.

3. [Visual studio 개발자 명령 프롬프트 또는 Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell)을 엽니다.

4. 어셈블리 래퍼를 저장 하려는 디렉터리로 디렉터리를 변경 합니다.

5. 다음 명령을 입력합니다.

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   입력할 수 있는 실제 명령의 예는 다음과 같습니다.

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > 경로 또는 파일에 공백이 있는 경우 큰따옴표를 사용 합니다.

6. Visual Studio에서 방금 만든 파일에 .NET 어셈블리 참조를 추가 합니다.

## <a name="see-also"></a>참고 항목

- [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)
- [Sn.exe(강력한 이름 도구)](../../../framework/tools/sn-exe-strong-name-tool.md)
- [방법: 퍼블릭/프라이빗 키 쌍 만들기](../../../standard/assembly/create-public-private-key-pair.md)
- [Visual Studio 피드백 옵션](/visualstudio/ide/feedback-options)
