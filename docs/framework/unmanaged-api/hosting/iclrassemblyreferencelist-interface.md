---
title: ICLRAssemblyReferenceList 인터페이스
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList
helpviewer_keywords:
- ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type:
- apiref
ms.openlocfilehash: a75235cd0ac0e55412f0ba58881796e3ebc801f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679240"
---
# <a name="iclrassemblyreferencelist-interface"></a>ICLRAssemblyReferenceList 인터페이스

호스트가 아닌 CLR (공용 언어 런타임)에 의해 로드 되는 어셈블리 목록을 관리 합니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IsAssemblyReferenceInList 메서드](iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|제공 된 포인터가 목록의 어셈블리를 참조 하는지 여부를 나타내는 값을 가져옵니다.|  
|[IsStringAssemblyReferenceInList 메서드](iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|제공 된 이름이 목록의 어셈블리 이름과 일치 하는지 여부를 나타내는 값을 가져옵니다.|  
  
## <a name="remarks"></a>설명  

 [ICLRAssemblyIdentityManager:: GetCLRAssemblyReferenceList](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) 메서드를 호출 하 여의 인스턴스에 대 한 포인터를 가져옵니다 `ICLRAssemblyReferenceList` .  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Mscoree.dll  
  
 **라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참조

- [ICLRAssemblyIdentityManager 인터페이스](iclrassemblyidentitymanager-interface.md)
- [IHostAssemblyStore 인터페이스](ihostassemblystore-interface.md)
- [호스팅 인터페이스](hosting-interfaces.md)
