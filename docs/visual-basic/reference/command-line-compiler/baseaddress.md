---
description: '자세한 정보: -baseaddress'
title: -baseaddress
ms.date: 08/09/2018
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
ms.openlocfilehash: eaa2992c126ebb83b20cfdbef3ab995a30ee25fd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468319"
---
# <a name="-baseaddress"></a>-baseaddress

DLL을 만들 때 기본 기준 주소를 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a>인수  
  
|용어|정의|  
|---|---|  
|`address`|필수 요소. DLL의 기준 주소입니다. 이 주소는 16진수 숫자로 지정해야 합니다.|  
  
## <a name="remarks"></a>설명  

 DLL에 대한 기본 기준 주소는 .NET Framework에 의해 설정됩니다.  
  
 이 주소의 하위 단어는 반올림됩니다. 예를 들어 0x11110001을 지정하면 0x11110000으로 반올림됩니다.  
  
 DLL에 대한 서명 프로세스를 완료하려면 강력한 이름 지정 도구(Sn.exe)의 `–R` 옵션을 사용합니다.  
  
 대상이 DLL이 아닌 경우이 옵션은 무시됩니다.  
  
|Visual Studio IDE에서 -baseaddress를 설정하려면|  
|---|  
|1.  **솔루션 탐색기** 에서 프로젝트를 선택합니다. **프로젝트** 메뉴에서 **속성** 을 클릭합니다. <br />2.  **컴파일** 탭을 클릭합니다.<br />3.  **고급** 을 클릭합니다.<br />4.  **DLL 기준 주소:** 상자에서 값을 수정합니다. **참고:**      대상이 DLL이 아닌 한 **DLL 기준 주소:** 상자는 읽기 전용입니다.|  
  
## <a name="see-also"></a>참조

- [Visual Basic 명령줄 컴파일러](index.md)
- [-target(Visual Basic)](target.md)
- [샘플 컴파일 명령줄](sample-compilation-command-lines.md)
- [Sn.exe(강력한 이름 도구)](../../../framework/tools/sn-exe-strong-name-tool.md)
