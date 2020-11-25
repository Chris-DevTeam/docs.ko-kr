---
title: CorErrorIfEmitOutOfOrder 열거형
ms.date: 03/30/2017
api_name:
- CorErrorIfEmitOutOfOrder
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorErrorIfEmitOutOfOrder
helpviewer_keywords:
- CorErrorIfEmitOutOfOrder enumeration [.NET Framework metadata]
ms.assetid: 6d758aad-29a7-44fe-9481-bbff5b799a32
topic_type:
- apiref
ms.openlocfilehash: 1d1b0cbb8be33f285b63e7353da973455e0fd752
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718854"
---
# <a name="corerrorifemitoutoforder-enumeration"></a>CorErrorIfEmitOutOfOrder 열거형

메타데이터를 내보내는 순서가 잘못되었을 때 오류 메시지가 생성되어야 하는 조건을 나타내는 플래그 값을 포함합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef enum CorErrorIfEmitOutOfOrder {  
  
    MDErrorOutOfOrderDefault    = 0x00000000,  
    MDErrorOutOfOrderNone       = 0x00000000,  
    MDErrorOutOfOrderAll        = 0xffffffff,  
    MDMethodOutOfOrder          = 0x00000001,  
    MDFieldOutOfOrder           = 0x00000002,  
    MDParamOutOfOrder           = 0x00000004,  
    MDPropertyOutOfOrder        = 0x00000008,  
    MDEventOutOfOrder           = 0x00000010  
  
} CorErrorIfEmitOutOfOrder;  
```  
  
## <a name="members"></a>멤버  
  
|멤버|설명|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|오류 메시지를 생성 하지 않는 기본 동작을 나타냅니다.|  
|`MDErrorOutOfOrderNone`|컴파일러가 오류 메시지를 생성 하지 않아야 함을 나타냅니다.|  
|`MDErrorOutOfOrderAll`|필드, 속성, 이벤트, 메서드 또는 매개 변수가 잘못 된 순서로 내보내지는 경우 컴파일러에서 오류 메시지를 생성 해야 함을 나타냅니다.|  
|`MDMethodOutOfOrder`|메서드가 잘못 된 순서로 내보내지는 경우 컴파일러에서 오류 메시지를 생성 해야 함을 나타냅니다.|  
|`MDFieldOutOfOrder`|필드가 잘못 된 순서로 내보내지는 경우 컴파일러에서 오류 메시지를 생성 해야 함을 나타냅니다.|  
|`MDParamOutOfOrder`|매개 변수가 잘못 된 순서로 내보내지는 경우 컴파일러가 오류 메시지를 생성 해야 함을 나타냅니다.|  
|`MDPropertyOutOfOrder`|속성이 잘못 된 순서로 내보내지는 경우 컴파일러가 오류 메시지를 생성 해야 함을 나타냅니다.|  
|`MDEventOutOfOrder`|이벤트가 잘못 된 순서로 내보내지는 경우 컴파일러에서 오류 메시지를 생성 해야 함을 나타냅니다.|  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorHdr .h  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참조

- [메타데이터 열거형](metadata-enumerations.md)
