---
title: IsFrameworkAssembly 함수
ms.date: 03/30/2017
api_name:
- IsFrameworkAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IsFrameworkAssembly
helpviewer_keywords:
- IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type:
- apiref
ms.openlocfilehash: 828c7660d6c006e700302d119ce4caf7d76e5d84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728565"
---
# <a name="isframeworkassembly-function"></a>IsFrameworkAssembly 함수

지정 된 어셈블리가 관리 되는지 여부를 나타내는 값을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a>매개 변수  

 `pwzAssemblyReference`  
 진행 확인할 어셈블리의 이름입니다.  
  
 `pbIsFrameworkAssembly`  
 제한이 어셈블리가 관리 되는지 여부를 나타내는 부울 값입니다.  
  
 `pwzFrameworkAssemblyIdentity`  
 진행 어셈블리의 고유 id를 포함 하는 정규화 되지 않은 문자열입니다.  
  
 `pccSize`  
 [in] `pwzFrameworkAssemblyIdentity`의 크기입니다.  
  
## <a name="remarks"></a>설명  

 `pwzAssemblyReference`매개 변수는 어셈블리 이름을 포함 하는 문자열에 대 한 포인터입니다.  
  
 이 어셈블리가 .NET Framework의 일부인 경우 `pbIsFrameworkAssembly` 매개 변수에 부울 값이 포함 됩니다 `true` .  
  
 명명 된 어셈블리가 .NET Framework의 일부가 아니거나 `pwzAssemblyReference` 매개 변수가 어셈블리의 이름을 지정 하지 않는 경우에는 `pbIsFrameworkAssembly` 부울 값이 포함 됩니다 `false` .  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
## <a name="see-also"></a>참조

- [Fusion 전역 정적 함수](fusion-global-static-functions.md)
