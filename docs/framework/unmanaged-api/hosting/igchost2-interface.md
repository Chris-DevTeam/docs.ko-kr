---
description: '자세히 알아보기: IGCHost2 인터페이스'
title: IGCHost2 인터페이스
ms.date: 03/30/2017
api_name:
- IGCHost2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2
helpviewer_keywords:
- IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type:
- apiref
ms.openlocfilehash: e32a4894fcff3600c9385f0f559443e23b2bc307
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709323"
---
# <a name="igchost2-interface"></a>IGCHost2 인터페이스

가비지 컬렉션 시스템에 대 한 정보를 가져오고 가비지 수집의 일부 측면을 제어 하기 위한 메서드를 제공 합니다.  
  
> [!NOTE]
> 새 개발을 위해 [ICLRGCManager2](iclrgcmanager2-interface.md) 인터페이스를 대신 사용 하는 것이 좋습니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[SetGCStartupLimitsEx 메서드](igchost2-setgcstartuplimitsex-method.md)|0 세대의 세그먼트 크기와 최대 크기를 설정 합니다. 0 세대 및 세그먼트 크기를 보다 크게 설정 `DWORD` 합니다.|  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** GCHost, GCHost  
  
 **라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [호스팅 인터페이스](hosting-interfaces.md)
- [CLR 호스팅 인터페이스](clr-hosting-interfaces.md)
- [CorRuntimeHost Coclass](corruntimehost-coclass.md)
