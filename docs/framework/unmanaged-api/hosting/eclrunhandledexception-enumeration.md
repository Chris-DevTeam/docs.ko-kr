---
title: EClrUnhandledException 열거형
ms.date: 03/30/2017
api_name:
- EClrUnhandledException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrUnhandledException
helpviewer_keywords:
- EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type:
- apiref
ms.openlocfilehash: bccd44e1bead4feadf67929dc104557715904577
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686464"
---
# <a name="eclrunhandledexception-enumeration"></a>EClrUnhandledException 열거형

사용자 코드에서 처리 되지 않은 예외를 관리 하는 데 사용할 수 있는 옵션을 설명 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a>멤버  
  
|멤버|설명|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|기본 동작이 발생 하도록 지정 합니다. 프로세스가 중단 됩니다.|  
|`eHostDeterminedPolicy`|CLR (공용 언어 런타임)이 처리 되지 않은 예외를 무시 하 고 호스트에서 추가 작업을 확인할 수 있도록 지정 합니다.|  
  
## <a name="remarks"></a>설명  

 CLR이 이전 버전과 동일 하 게 동작 하도록 지정 하려면 멤버를 사용 `eHostDeterminedPolicy` 합니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Mscoree.dll  
  
 **라이브러리:** MSCorEE.dll  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참조

- [EClrFailure 열거형](eclrfailure-enumeration.md)
- [EClrOperation 열거형](eclroperation-enumeration.md)
- [ICLRPolicyManager 인터페이스](iclrpolicymanager-interface.md)
- [SetUnhandledExceptionPolicy 메서드](iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [IHostPolicyManager 인터페이스](ihostpolicymanager-interface.md)
- [호스팅 열거형](hosting-enumerations.md)
