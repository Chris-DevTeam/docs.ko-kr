---
title: CorSymAddrKind 열거형
ms.date: 03/30/2017
api_name:
- CorSymAddrKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymAddrKind
helpviewer_keywords:
- CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type:
- apiref
ms.openlocfilehash: f71d8956e8706cdc71b94b6e6e2e8210e5b9161e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725237"
---
# <a name="corsymaddrkind-enumeration"></a>CorSymAddrKind 열거형

메모리 주소의 유형을 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef enum CorSymAddrKind  
{  
    ADDR_IL_OFFSET          = 1,  
    ADDR_NATIVE_RVA         = 2,  
    ADDR_NATIVE_REGISTER    = 3,  
    ADDR_NATIVE_REGREL      = 4,  
    ADDR_NATIVE_OFFSET      = 5,  
    ADDR_NATIVE_REGREG      = 6,  
    ADDR_NATIVE_REGSTK      = 7,  
    ADDR_NATIVE_STKREG      = 8,  
    ADDR_BITFIELD           = 9,  
    ADDR_NATIVE_ISECTOFFSET = 10  
} CorSymAddrKind;  
```  
  
## <a name="members"></a>멤버  
  
|멤버|설명|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|MSIL (Microsoft 중간 언어) 지역 변수 또는 매개 변수 인덱스를 나타냅니다.|  
|`ADDR_NATIVE_RVA`|모듈에 대 한 상대 가상 주소를 나타냅니다.|  
|`ADDR_NATIVE_REGISTER`|CPU 레지스터를 나타냅니다.|  
|`ADDR_NATIVE_REGREL`|첫 번째 주소가 레지스터가 고 두 번째 주소가 오프셋 임을 나타냅니다.|  
|`ADDR_NATIVE_OFFSET`|기본 주소에서 오프셋을 나타냅니다.|  
|`ADDR_NATIVE_REGREG`|첫 번째 주소가 레지스터의 하위 부분이 고 두 번째 주소가 높은 부분 임을 나타냅니다.|  
|`ADDR_NATIVE_REGSTK`|첫 번째 주소가 레지스터의 하위 부분이 고 두 번째 주소가 상위 부분이 며 세 번째 주소가 오프셋 임을 나타냅니다.|  
|`ADDR_NATIVE_STKREG`|첫 번째 주소가 레지스터이 고, 두 번째 주소가 오프셋 임을 나타내며, 세 번째 주소가 레지스터의 상위 부분 임을 나타냅니다.|  
|`ADDR_BITFIELD`|첫 번째 주소는 필드의 시작이 고 두 번째 주소는 필드 길이 임을 나타냅니다.|  
|`ADDR_NATIVE_ISECTOFFSET`|첫 번째 주소는 섹션이 고 두 번째 주소는 오프셋 임을 나타냅니다.|  
  
## <a name="requirements"></a>요구 사항  

 **헤더:** CorSym, CorSym  
  
## <a name="see-also"></a>참조

- [진단 기호 저장소 열거형](diagnostics-symbol-store-enumerations.md)
