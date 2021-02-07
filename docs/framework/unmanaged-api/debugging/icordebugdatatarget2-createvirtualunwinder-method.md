---
description: '자세히 알아보기: ICorDebugDataTarget2:: CreateVirtualUnwinder 메서드'
title: ICorDebugDataTarget2::CreateVirtualUnwinder Method
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
ms.openlocfilehash: 0646c85000f42b303769d6587354b3105e2deabd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764413"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a>ICorDebugDataTarget2::CreateVirtualUnwinder Method

초기 컨텍스트(반드시 스레드의 리프일 필요는 없음)에서 해제를 시작하는 새 스택 해제기를 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
## <a name="parameters"></a>매개 변수  

 nativeThreadID  
 [in] 스택을 해제할 스레드의 네이티브 스레드 ID입니다.  
  
 contextFlags  
 [in] `initialContext`에 정의된 컨텍스트 부분을 지정하는 플래그입니다.  
  
 cbContext  
 [in] `initialContext`의 크기입니다.  
  
 initialContext  
 [in] 컨텍스트의 데이터입니다.  
  
 ppUnwinder  
 [out] ICorDebugVirtualUnwinder 인터페이스 개체의 주소에 대한 포인터입니다.  
  
## <a name="return-value"></a>Return Value  

 성공하는 경우 `S_OK`입니다. 기타 `HRESULT`는 오류를 나타냅니다. `HRESULT`Mscordbi.dll에서 수신 하는 모든 오류는 치명적인 것으로 간주 되 고 [ICorDebug](icordebug-interface.md) 메서드는를 반환 `CORDBG_E_DATA_TARGET_ERROR` 합니다.  
  
## <a name="remarks"></a>설명  
  
> [!NOTE]
> 이 메서드는 .NET 네이티브에서만 사용할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [ICorDebugDataTarget2 인터페이스](icordebugdatatarget2-interface.md)
- [디버깅 인터페이스](debugging-interfaces.md)
