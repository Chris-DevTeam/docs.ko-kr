---
description: '자세히 알아보기: ICorDebugILFrame4:: GetCodeEx 메서드'
title: ICorDebugILFrame4::GetCodeEx 메서드
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetLocalVariableEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type:
- apiref
ms.openlocfilehash: 1d17dfa531354b8a4b0dd3c0d3d2eb47206900cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791233"
---
# <a name="icordebugilframe4getcodeex-method"></a>ICorDebugILFrame4::GetCodeEx 메서드

[.NET Framework 4.5.2 이상 버전에서 지원됨]  
  
 이 스택 프레임에서 실행 중인 코드에 대한 포인터를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `flags`  
 진행 프로파일러에서 ReJIT 요청에 의해 정의 된 IL (중간 언어)이 프레임에 포함 되는지 여부를 지정 하는 [Ilcodekind](ilcodekind-enumeration.md) 열거형 멤버입니다.  
  
 `ppCode`  
 제한이 이 스택 프레임이 실행 되는 코드를 나타내는 "ICorDebugCode" 개체의 주소에 대 한 포인터입니다.  
  
## <a name="remarks"></a>설명  

 이 메서드는 선택적으로 프로파일러의 ReJIT 요청으로 정의 된 코드에 액세스 한다는 점을 제외 하 고 [ICorDebugFrame:: GetCode](icordebugframe-getcode-method.md) 메서드와 비슷합니다. 값을 사용 하 여이 메서드를 호출 `flags` `ILCODE_ORIGINAL_IL` 하는 것은 [getcode](icordebugframe-getcode-method.md)를 호출 하는 것과 같습니다. 메서드가 계측 되는 경우 해당 IL에 액세스할 수 없습니다. `ILCODE_REJIT_IL`을 사용하는 경우 디버거가 프로파일러 ReJIT 요청에 의해 정의된 IL에 액세스할 수 있습니다. IL이 계측 되지 않는 경우 `ppCode` 가 **null** 이 고 메서드는를 반환 합니다 `S_OK` .  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [ICorDebugILFrame4 인터페이스](icordebugilframe4-interface.md)
- [디버깅 인터페이스](debugging-interfaces.md)
- [ReJIT: How-To 가이드](/archive/blogs/davbr/rejit-a-how-to-guide)
