---
description: '자세히 알아보기: IXCLRDataProcess:: EndEnumModules 메서드'
title: 'IXCLRDataProcess:: EndEnumModules 메서드'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 454d4fa3616f9ba8312dc3d1ac02c228625aa488
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800710"
---
# <a name="ixclrdataprocessendenummodules-method"></a>IXCLRDataProcess:: EndEnumModules 메서드

모듈 열거 중 사용 되는 내부 반복기에서 사용 하는 리소스를 해제 합니다.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>구문

```cpp
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a>매개 변수

`handle`\
제한이 모듈을 열거 하는 핸들입니다.

## <a name="remarks"></a>설명

제공 된 메서드는 인터페이스의 일부 이며 `IXCLRDataProcess` 가상 메서드 테이블의 26 일 슬롯에 해당 합니다.

## <a name="requirements"></a>요구 사항

**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.
**헤더:** None **라이브러리:** 없음 **.NET Framework 버전:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>참고 항목

- [디버깅](index.md)
- [IXCLRDataProcess 인터페이스](ixclrdataprocess-interface.md)
