---
title: EClrFailure 열거형
ms.date: 03/30/2017
api_name:
- EClrFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrFailure
helpviewer_keywords:
- EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type:
- apiref
ms.openlocfilehash: d2794b53ed17640413928b3af0d1ed3656e25f22
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675765"
---
# <a name="eclrfailure-enumeration"></a>EClrFailure 열거형

호스트에서 정책 작업을 설정할 수 있는 오류 집합을 설명 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef enum {  
    FAIL_NonCriticalResource,  
    FAIL_CriticalResource,  
    FAIL_FatalRuntime,  
    FAIL_OrphanedLock  
    FAIL_StackOverflow  
    FAIL_AccessViolation  
    FAIL_CodeContract  
} EClrFailure;  
```  
  
## <a name="members"></a>멤버  
  
|멤버|설명|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|중요 하지 않은 코드 영역에서 리소스 (예: 스레드, 메모리 블록 또는 잠금)를 할당 하는 동안 오류가 발생 했습니다.|  
|`FAIL_CriticalResource`|중요 한 코드 영역에서 리소스 (예: 스레드, 메모리 블록 또는 잠금)를 할당 하려고 시도 하는 동안 오류가 발생 했습니다.|  
|`FAIL_FatalRuntime`|CLR (공용 언어 런타임)은 더 이상 프로세스에서 관리 코드를 실행할 수 없습니다. 예측이 모든 호스팅 함수를 호출 하면 HRESULT 값 HOST_E_CLRNOTAVAILABLE 반환 됩니다.|  
|`FAIL_OrphanedLock`|스레드가 개체에서 반환 될 때 잠금을 해제 하지 못했습니다 <xref:System.AppDomain> . 호스트에서이 오류를 설정 하 여 스레드를 중단 시킬 수 없습니다.|  
|`FAIL_StackOverflow`|스택 오버플로가 발생 했습니다.|  
|`FAIL_AccessViolation`|보호 된 메모리를 읽거나 쓰려고 했습니다. .NET Framework 4에서는 지원 되지 않습니다.|  
|`FAIL_CodeContract`|코드 계약 오류가 발생 했습니다. [코드 계약](../../debug-trace-profile/code-contracts.md)을 참조 하세요.|  
  
## <a name="remarks"></a>설명  

 호스트에서 오류 조건에 대 한 정책 작업을 지정 하는 데 사용할 수 있는 [EPolicyAction](epolicyaction-enumeration.md) 값 목록은 [ICLRPolicyManager:: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) 메서드를 참조 하세요. 중요 하 고 중요 하지 않은 코드 영역에 대 한 자세한 내용은 [EClrOperation](eclroperation-enumeration.md)를 참조 하세요.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Mscoree.dll  
  
 **라이브러리:** MSCorEE.dll  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참조

- [ICLRPolicyManager 인터페이스](iclrpolicymanager-interface.md)
- [SetActionOnFailure 메서드](iclrpolicymanager-setactiononfailure-method.md)
- [IHostPolicyManager 인터페이스](ihostpolicymanager-interface.md)
- [호스팅 열거형](hosting-enumerations.md)
