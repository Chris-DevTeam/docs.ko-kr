---
description: '자세히 알아보기: ICorDebugEval:: NewObject 메서드'
title: ICorDebugEval::NewObject 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type:
- apiref
ms.openlocfilehash: 0f7feb53d061e5dbc453015772b97f2a5a59bbb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693956"
---
# <a name="icordebugevalnewobject-method"></a>ICorDebugEval::NewObject 메서드

새 개체 인스턴스를 할당 하 고 지정 된 생성자 메서드를 호출 합니다.  
  
 이 메서드는 .NET Framework 버전 2.0에서 사용 되지 않습니다. 대신 [ICorDebugEval2:: NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) 를 사용 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `pConstructor`  
 진행 호출할 생성자입니다.  
  
 `nArgs`  
 [in] `ppArgs` 배열의 크기입니다.  
  
 `ppArgs`  
 진행 각각 생성자에 전달 되는 인수를 나타내는 ICorDebugValue 개체의 배열입니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:** 1.1, 1.0  
  
## <a name="see-also"></a>참고 항목

- [NewParameterizedObject 메서드](icordebugeval2-newparameterizedobject-method.md)
