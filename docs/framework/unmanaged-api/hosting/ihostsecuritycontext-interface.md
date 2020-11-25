---
title: IHostSecurityContext 인터페이스
ms.date: 03/30/2017
api_name:
- IHostSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext
helpviewer_keywords:
- IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type:
- apiref
ms.openlocfilehash: aafaa1d648396ddaa76193fa15cf7f74394777a9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724808"
---
# <a name="ihostsecuritycontext-interface"></a>IHostSecurityContext 인터페이스

CLR (공용 언어 런타임)이 호스트에서 구현 하는 보안 컨텍스트 정보를 유지 관리할 수 있도록 합니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[Capture 메서드](ihostsecuritycontext-capture-method.md)|`IHostSecurityContext` [IHostSecurityManager:: GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md)에 대 한 호출에서 반환 된 인스턴스의 복제본을 가져옵니다.|  
  
## <a name="remarks"></a>설명  

 호스트는 CLR 및 사용자 코드를 모두 사용 하 여 스레드 토큰에 대 한 모든 코드 액세스를 제어할 수 있습니다. 또한 코드 액세스가 제한 된 비동기 작업 또는 코드 포인트로 전체 보안 컨텍스트 정보를 전달 하도록 할 수 있습니다. `IHostSecurityContext` 런타임에 불투명 한이 보안 컨텍스트 정보를 캡슐화 합니다. 런타임은를 사용 하 여이 정보 `Capture` 를 캡처하여 스레드 풀 작업자 항목 디스패치, 종료자 실행 및 모듈 및 클래스 생성자 간에 이동 합니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Mscoree.dll  
  
 **라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참조

- [ICLRHostProtectionManager 인터페이스](iclrhostprotectionmanager-interface.md)
- [IHostSecurityManager 인터페이스](ihostsecuritymanager-interface.md)
- [호스팅 인터페이스](hosting-interfaces.md)
