---
title: ICorDebugMDA::GetXML 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetXML
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type:
- apiref
ms.openlocfilehash: 9a088c7e4e9c72c8247ccdd384bc724587210c37
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710872"
---
# <a name="icordebugmdagetxml-method"></a>ICorDebugMDA::GetXML 메서드

[ICorDebugMDA](icordebugmda-interface.md)로 표시 된 MDA (관리 디버깅 도우미)와 연결 된 전체 XML 스트림을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `cchName`  
 [in] `szName` 배열의 크기입니다.  
  
 `pcchName`  
 제한이 XML 스트림의 길이에 대 한 포인터입니다.  
  
 `szName`  
 제한이 XML 스트림을 저장할 배열입니다. 배열은 비어 있을 수 있습니다.  
  
## <a name="remarks"></a>설명  

 `GetXML`메서드는 연결 된 XML 스트림의 크기에 따라 성능에 잠재적으로 영향을 줄 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참조

- [ICorDebugMDA 인터페이스](icordebugmda-interface.md)
- [관리 디버깅 도우미를 사용하여 오류 진단](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
