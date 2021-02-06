---
description: '자세히 알아보기: ICorDebugProcess2:: GetVersion 메서드'
title: ICorDebugProcess2::GetVersion 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetVersion
helpviewer_keywords:
- GetVersion method, ICorDebugProcess2 interface [.NET Framework debugging]
- ICorDebugProcess2::GetVersion method [.NET Framework debugging]
ms.assetid: e11d5a75-61d9-4548-aedf-79c26079bd17
topic_type:
- apiref
ms.openlocfilehash: 8472e811ea4df1f99fb4e27b55f3561fae0c8a21
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650103"
---
# <a name="icordebugprocess2getversion-method"></a>ICorDebugProcess2::GetVersion 메서드

이 프로세스에서 실행 되는 CLR (공용 언어 런타임)의 버전 번호를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetVersion (
    [out] COR_VERSION     *version
);
```

## <a name="parameters"></a>매개 변수

`version`\
제한이 런타임의 버전 번호를 저장 하는 COR_VERSION 구조체에 대 한 포인터입니다.

## <a name="remarks"></a>설명

`GetVersion`프로세스에서 로드 된 런타임이 없으면 메서드는 오류 코드를 반환 합니다.

## <a name="requirements"></a>요구 사항

**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.

**헤더:** CorDebug.idl, CorDebug.h

**라이브러리:** CorGuids.lib

**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
