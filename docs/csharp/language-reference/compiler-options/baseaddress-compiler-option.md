---
description: -baseaddress(C# 컴파일러 옵션)
title: -baseaddress(C# 컴파일러 옵션)
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: 76da496f7045f12778bba273947b913be1b94e3e
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "91196847"
---
# <a name="-baseaddress-c-compiler-options"></a>-baseaddress(C# 컴파일러 옵션)

**-baseaddress** 옵션을 사용하면 DLL을 로드할 기본 기준 주소를 지정할 수 있습니다. 이 옵션을 사용하는 시기와 이유에 대한 자세한 내용은 [Larry Osterman's WebLog](/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system)를 참조하세요.  
  
## <a name="syntax"></a>구문  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a>인수  

 `address`  
 DLL의 기준 주소입니다. 이 주소는 10진수, 16진수 또는 8진수 숫자로 지정할 수 있습니다.  
  
## <a name="remarks"></a>설명  

 DLL의 기본 기준 주소는 .NET 공용 언어 런타임에서 설정됩니다.  
  
 이 주소의 하위 단어는 반올림됩니다. 예를 들어 0x11110001을 지정하면 0x11110000으로 반올림됩니다.  
  
 DLL에 대한 서명 프로세스를 완료하려면 SN.EXE에 -R 옵션을 사용합니다.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면  
  
1. 프로젝트 **속성** 페이지를 엽니다.  
  
2. **빌드** 속성 페이지를 클릭합니다.  
  
3. **고급** 단추를 클릭합니다.  
  
4. **DLL 기준 주소** 속성을 수정합니다.  
  
     프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>를 참조하세요.  
  
## <a name="see-also"></a>참고 항목

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [C# 컴파일러 옵션](./index.md)
- [프로젝트 및 솔루션 속성 관리](/visualstudio/ide/managing-project-and-solution-properties)
