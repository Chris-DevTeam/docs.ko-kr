---
description: -target:appcontainerexe(C# 컴파일러 옵션)
title: -target:appcontainerexe(C# 컴파일러 옵션)
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: e4aa60ebc9dcc1a63b63863385b0ee9f13d6d78d
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "91193740"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a>-target:appcontainerexe(C# 컴파일러 옵션)

**-target:appcontainerexe** 컴파일러 옵션을 사용하면 컴파일러는 앱 컨테이너에서 실행해야 하는 Windows 실행 파일(.exe)을 만듭니다. 이 옵션은 [-target:winexe](./target-winexe-compiler-option.md)와 같지만, Windows 8.x 스토어 앱을 위해 설계되었습니다.  
  
## <a name="syntax"></a>구문  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a>설명  

 이 옵션은 앱이 앱 컨테이너에서 실행되도록 하기 위해 PE([이식 가능 파일](/windows/desktop/Debug/pe-format))에 비트를 설정합니다. 해당 비트가 설정된 경우 CreateProcess 메서드가 응용 프로그램 밖에서 실행 파일을 실행하려고 시도하면 오류가 발생합니다.  
  
 [-out](./out-compiler-option.md) 옵션을 사용하지 않으면 [Main](../../programming-guide/main-and-command-args/index.md) 메서드가 포함된 입력 파일의 이름이 출력 파일의 이름으로 사용됩니다.  
  
 이 옵션을 명령 프롬프트에서 지정하면 실행 파일을 만드는 데 다음 **-out** 또는 **-target** 옵션까지의 모든 파일이 사용됩니다.  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a>IDE에서 이 컴파일러 옵션을 설정하려면  
  
1. **솔루션 탐색기** 에서 프로젝트의 바로 가기 메뉴를 열고 **속성** 을 선택합니다.  
  
2. **애플리케이션** 탭의 **출력 형식** 목록에서 **Windows 스토어 앱** 을 선택합니다.  
  
     이 옵션은 Windows 8.x 스토어 앱 템플릿에만 사용할 수 있습니다.  
  
 이 컴파일러 옵션을 프로그래밍 방식으로 설정하는 방법에 대한 자세한 내용은 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>을 참조하십시오.  
  
## <a name="example"></a>예제  

 다음 명령은 `filename.cs`를 응용 프로그램 컨테이너에서만 실행할 수 있는 Windows 실행 파일로 컴파일합니다.  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a>참고 항목

- [-target(C# 컴파일러 옵션)](./target-compiler-option.md)
- [-target:winexe(C# 컴파일러 옵션)](./target-winexe-compiler-option.md)
- [C# 컴파일러 옵션](./index.md)
