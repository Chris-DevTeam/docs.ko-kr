---
title: Storeadm.exe(격리된 스토리지 도구)
description: 격리된 스토리지 도구인 Storeadm.exe에 대해 알아봅니다. 이 도구를 사용하여 현재 사용자의 기존 저장소를 모두 표시하거나 제거할 수 있습니다.
ms.date: 03/30/2017
helpviewer_keywords:
- Storeadm.exe
- listing stores for current user
- Isolated Storage tool
- stores, current user
- removing stores
ms.assetid: b81202b8-d91d-4b23-9c53-4a112f74a44a
ms.openlocfilehash: 1bd7aee54af8ec78454d9c9023856966beb91174
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653610"
---
# <a name="storeadmexe-isolated-storage-tool"></a>Storeadm.exe(격리된 스토리지 도구)

격리된 스토리지 도구를 사용하면 현재 사용자의 기존 저장소를 모두 표시하거나 제거할 수 있습니다.  
  
 이 도구는 자동으로 Visual Studio와 함께 설치됩니다. 도구를 실행하려면 [Visual Studio 개발자 명령 프롬프트 또는 Visual Studio 개발자 PowerShell](/visualstudio/ide/reference/command-prompt-powershell)을 사용합니다.
  
 명령 프롬프트에 다음을 입력합니다.  
  
## <a name="syntax"></a>구문  
  
```console  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a>매개 변수  
  
|옵션|설명|  
|------------|-----------------|  
|**/h**[**elp**]|이 도구의 명령 구문 및 옵션을 표시합니다.|  
|**/list**|현재 사용자의 기존 저장소를 모두 표시합니다. 여기에는 해당 사용자가 실행한 모든 애플리케이션 또는 어셈블리의 저장소가 포함됩니다.|  
|**/machine**|컴퓨터 저장소를 선택합니다. 이 옵션을 **/list** 또는 **/remove** 옵션과 함께 사용하면 해당 작업이 컴퓨터 저장소에 적용되도록 지정할 수 있습니다.<br /><br /> .NET Framework 2.0에 새로 추가된 옵션입니다.|  
|**/quiet**|자동 모드를 지정합니다. 오류 메시지만 표시되도록 자세한 정보는 출력하지 않습니다.|  
|**/remove**|현재 사용자의 기존 저장소를 모두 영구 제거합니다.|  
|**/roaming**|로밍 저장소를 선택합니다. 이 옵션을 **/list** 또는 **/remove** 옵션과 함께 사용하면 해당 작업이 로밍 저장소에 적용되도록 지정할 수 있습니다.|  
|**/?**|이 도구의 명령 구문 및 옵션을 표시합니다.|  
  
## <a name="remarks"></a>설명  

 아무 옵션도 지정하지 않고 명령줄에서 Storeadm.exe를 실행하면 이 도구의 구문 및 옵션이 표시됩니다.  
  
 **/list** 옵션 및 **/remove** 옵션은 일반적으로 한 번에 하나만 사용되지만 둘 이상의 옵션을 지정한 경우에는 명령줄에 표시된 순서대로 수행됩니다.  
  
 애플리케이션에서는 두 개의 사용자용 저장소 중 하나 또는 컴퓨터 저장소를 선택하여 저장할 수 있습니다.  
  
- 로컬 저장소는 해당 사용자에 대해 사용자 데이터 로밍이 사용되는 경우에도 로밍되지 않는 위치에 있습니다(Windows 2000 이상의 경우).  
  
- 로밍 저장소는 로밍할 수 있는 위치에 있지만 Windows NT 관리를 통해 해당 사용자에 대해 로밍이 사용되는 경우에만 로밍할 수 있습니다.  
  
- 컴퓨터 저장소는 컴퓨터의 모든 사용자에게 공통적이며 해당 컴퓨터의 공용 디렉터리에 저장됩니다.  
  
    > [!NOTE]
    > 컴퓨터 저장소는 .NET Framework 버전 2.0에서 새로 도입되었습니다.  
  
 사용자에 대해 로밍이 실제로 사용되는지 여부는 Storeadm.exe의 관리에 영향을 주지 않습니다. 옵션 없이 이 도구를 실행하면 모든 작업이 로컬 저장소에 적용됩니다. **/roaming** 옵션을 지정하여 이 도구를 실행하면 모든 작업이 로밍 가능한 저장소에 적용됩니다. **/machine** 옵션을 지정하여 이 도구를 실행하면 모든 작업이 컴퓨터 저장소에 적용됩니다.  
  
## <a name="see-also"></a>참조

- [도구](index.md)
- [격리된 스토리지](../../standard/io/isolated-storage.md)
- [개발자 명령줄 셸](/visualstudio/ide/reference/command-prompt-powershell)
