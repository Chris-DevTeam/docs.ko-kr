---
title: COINITICOR 열거형
ms.date: 03/30/2017
api_name:
- COINITICOR
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COINITICOR
helpviewer_keywords:
- COINITICOR enumeration [.NET Framework metadata]
ms.assetid: 67fefd89-28d6-4588-84ea-dc7a5870e014
topic_type:
- apiref
ms.openlocfilehash: 4d5bc66cdc292d390cb4ea187277fda8b8a071fc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724210"
---
# <a name="coiniticor-enumeration"></a>COINITICOR 열거형

공용 언어 런타임을 초기화할 때 [CoInitializeCor](../hosting/coinitializecor-function.md) 에서 사용 하는 상수를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef enum tagCOINITCOR  
{  
    COINITCOR = 0x0  
} COINITICOR;  
```  
  
## <a name="members"></a>멤버  
  
|멤버|설명|  
|------------|-----------------|  
|`COINITCOR`|기본 초기화 모드를 나타냅니다.|  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Cor  
  
 **라이브러리:** MsCorEE.dll의 리소스로 포함 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참조

- [메타데이터 열거형](metadata-enumerations.md)
