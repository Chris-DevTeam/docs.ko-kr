---
description: '자세히 알아보기: IXCLRDataProcess:: EnumModule 메서드'
title: 'IXCLRDataProcess:: EnumModule 메서드'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumModule Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumModule Method
helpviewer.keywords:
- IXCLRDataProcess::EnumModule Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 33b15da6939a0fb78a4eeafcf75e1a2b2f0d0ab1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800684"
---
# <a name="ixclrdataprocessenummodule-method"></a>IXCLRDataProcess:: EnumModule 메서드

이 프로세스의 모듈을 열거 합니다.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>구문

```cpp
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

## <a name="parameters"></a>매개 변수

`handle`\
[in, out] 모듈을 열거 하는 핸들입니다.

`mod`\
제한이 열거 된 모듈입니다.

## <a name="remarks"></a>설명

제공 된 메서드는 인터페이스의 일부 `IXCLRDataProcess` 이며 가상 메서드 테이블의 25 번째 슬롯에 해당 합니다.

## <a name="requirements"></a>요구 사항

**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
**헤더:** 없음을  
**라이브러리:** 없음을  
**.NET Framework 버전:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>참고 항목

- [CLRDataSourceType 열거형](clrdatasourcetype-enumeration.md)
- [디버깅](index.md)
- [IXCLRDataModule 인터페이스](ixclrdatamodule-interface.md)
- [IXCLRDataProcess 인터페이스](ixclrdataprocess-interface.md)
