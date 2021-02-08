---
description: '자세히 알아보기: ISOSDacInterface:: GetMethodDescPtrFromIP 메서드'
title: 'ISOSDacInterface:: GetMethodDescPtrFromIP 메서드'
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 8d7c7071b7b3fc520faea71c8d7792317745cfde
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790414"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a>ISOSDacInterface:: GetMethodDescPtrFromIP 메서드

지정 된 기본 명령 주소를 포함 하는 메서드에 해당 하는 MethodDesc의 포인터를 검색 합니다.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>구문

```cpp
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a>매개 변수

`ip`\
진행 런타임에 메서드 내의 주소입니다.

`ppMD`\
제한이 `MethodDesc` 특정 메서드에 대 한의 주소입니다.

## <a name="remarks"></a>설명

제공 된 메서드는 [ `ISOSDacInterface` 인터페이스](isosdacinterface-interface.md) 의 일부 이며 가상 메서드 테이블의 2 번째 슬롯에 해당 합니다.

## <a name="requirements"></a>요구 사항

**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
**헤더:** 없음을  
**라이브러리:** 없음을  
**.NET Framework 버전:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>참고 항목

- [디버깅](index.md)
- [ISOSDacInterface 인터페이스](isosdacinterface-interface.md)
