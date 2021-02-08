---
description: '자세한 정보: CorEventAttr 열거형'
title: CorEventAttr 열거형
ms.date: 03/30/2017
api_name:
- CorEventAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorEventAttr
helpviewer_keywords:
- CorEventAttr enumeration [.NET Framework metadata]
ms.assetid: dc2b3281-3820-487e-930d-350b66dc6417
topic_type:
- apiref
ms.openlocfilehash: 70f05eacf2cc7c7975b9b52d402cceb60bbea426
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784511"
---
# <a name="coreventattr-enumeration"></a>CorEventAttr 열거형

이벤트의 메타데이터를 설명하는 값을 포함합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a>구성원  
  
|멤버|설명|  
|------------|-----------------|  
|`evSpecialName`|이벤트를 특수 하 게 지정 하 고 해당 이름에서 방법을 설명 합니다.|  
|`evReservedMask`|공용 언어 런타임에서 내부용으로 사용 하도록 예약 되어 있습니다.|  
|`evRTSpecialName`|공용 언어 런타임에서 이벤트 이름의 인코딩을 확인 하도록 지정 합니다.|  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorHdr .h  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [메타데이터 열거형](metadata-enumerations.md)
