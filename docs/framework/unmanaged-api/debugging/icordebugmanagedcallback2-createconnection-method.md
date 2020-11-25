---
title: ICorDebugManagedCallback2::CreateConnection 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.CreateConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type:
- apiref
ms.openlocfilehash: 5a4ebf65dfaaa487e87f3fd78e54c468c7e24a89
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697248"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a>ICorDebugManagedCallback2::CreateConnection 메서드

새 연결이 생성 되었음을 디버거에 알립니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `pProcess`  
 진행 연결이 생성 된 프로세스를 나타내는 "ICorDebugProcess" 개체에 대 한 포인터입니다.  
  
 `dwConnectionId`  
 진행 새 연결의 ID입니다.  
  
 `pConnName`  
 진행 새 연결의 이름에 대 한 포인터입니다.  
  
## <a name="remarks"></a>설명  

 `CreateConnection`콜백은 다음 중 한 가지 경우에 발생 합니다.  
  
- 디버거가 연결을 포함 하는 프로세스에 연결 하는 경우 이 경우 런타임은 `CreateConnection` 프로세스의 각 연결에 대해 이벤트 및 [ICorDebugManagedCallback2:: ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md) 이벤트를 생성 하 고 디스패치합니다.  
  
- 호스트가 [호스팅 API](../hosting/index.md)에서 [ICLRDebugManager:: beginconnection](../hosting/iclrdebugmanager-beginconnection-method.md) 을 호출 하는 경우  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참조

- [ICorDebugManagedCallback2 인터페이스](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback 인터페이스](icordebugmanagedcallback-interface.md)
