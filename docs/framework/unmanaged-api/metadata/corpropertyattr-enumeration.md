---
title: CorPropertyAttr 열거형
ms.date: 03/30/2017
api_name:
- CorPropertyAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPropertyAttr
helpviewer_keywords:
- CorPropertyAttr enumeration [.NET Framework metadata]
ms.assetid: 58ac8202-854d-4efd-acfb-d2da8b446e12
topic_type:
- apiref
ms.openlocfilehash: d76de80f87a8e5a63eac9f6a413f2efb0e394b0a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706127"
---
# <a name="corpropertyattr-enumeration"></a>CorPropertyAttr 열거형

속성의 메타데이터를 설명하는 값을 포함합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a>멤버  
  
|멤버|설명|  
|------------|-----------------|  
|`prSpecialName`|속성을 특수 하 게 지정 하 고 해당 이름에서 방법을 설명 합니다.|  
|`prReservedMask`|공용 언어 런타임에서 내부용으로 사용 하도록 예약 되어 있습니다.|  
|`prRTSpecialName`|공용 언어 런타임 메타 데이터 내부 Api가 속성 이름의 인코딩을 확인 하도록 지정 합니다.|  
|`prHasDefault`|속성이 기본값을 갖도록 지정합니다.|  
|`prUnused`|사용되지 않습니다.|  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorHdr .h  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참조

- [메타데이터 열거형](metadata-enumerations.md)
