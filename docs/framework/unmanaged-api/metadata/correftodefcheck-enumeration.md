---
description: '자세한 정보: CorRefToDefCheck 열거형'
title: CorRefToDefCheck 열거형
ms.date: 03/30/2017
api_name:
- CorRefToDefCheck
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRefToDefCheck
helpviewer_keywords:
- CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type:
- apiref
ms.openlocfilehash: ca9d1c7ceb3d9f82ef8d5f1f54d869db64053e69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784251"
---
# <a name="correftodefcheck-enumeration"></a>CorRefToDefCheck 열거형

코드를 최적화하기 위해 해당 정의로 변환되는 참조된 항목을 제어하는 플래그를 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a>구성원  
  
|멤버|설명|  
|------------|-----------------|  
|`MDRefToDefDefault`|형식 참조 및 멤버 참조를 정의로 변환 하도록 지정 합니다. 이 값은 기본값 ( `MDTypeRefToDef` &#124; `MDMemberRefToDef` )입니다.|  
|`MDRefToDefAll`|참조 되는 모든 항목을 정의로 변환 하도록 지정 합니다.|  
|`MDRefToDefNone`|참조 되는 항목을 정의로 변환 하지 않도록 지정 합니다.|  
|`MDTypeRefToDef`|형식 참조만 형식 정의로 변환 하도록 지정 합니다.|  
|`MDMemberRefToDef`|멤버 참조만 정의로 변환 하도록 지정 합니다. 즉, 멤버 참조는 메서드 정의 또는 필드 정의 중 하나로 변환 되어야 합니다.|  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorHdr .h  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [메타데이터 열거형](metadata-enumerations.md)
