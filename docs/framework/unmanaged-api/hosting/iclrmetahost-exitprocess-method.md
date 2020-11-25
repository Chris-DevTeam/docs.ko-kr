---
title: ICLRMetaHost::ExitProcess 메서드
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.ExitProcess
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::ExitProcess
helpviewer_keywords:
- ICLRMetaHost::ExitProcess method [.NET Framework hosting]
- ExitProcess method, ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: b4df98cc-4e4e-407b-b8f4-e0076afef3a4
topic_type:
- apiref
ms.openlocfilehash: 6d601ac3ece801353b630c74ed852c2657f25d7f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730465"
---
# <a name="iclrmetahostexitprocess-method"></a>ICLRMetaHost::ExitProcess 메서드

로드 된 모든 런타임을 정상적으로 종료 하 고 프로세스를 종료 하려고 합니다. [Corexitprocess](corexitprocess-function.md) 함수를 대체 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
## <a name="parameters"></a>매개 변수  

 `iExitCode`  
 진행 프로세스의 종료 코드입니다.  
  
## <a name="return-value"></a>반환 값  

 이 메서드는를 반환 하지 않으므로 반환 값이 정의 되지 않습니다.  
  
## <a name="remarks"></a>설명  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** MetaHost  
  
 **라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>참조

- [ICLRMetaHost 인터페이스](iclrmetahost-interface.md)
- [호스팅](index.md)
