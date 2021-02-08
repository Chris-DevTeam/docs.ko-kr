---
description: '자세히 알아보기: IActionOnCLREvent 인터페이스'
title: IActionOnCLREvent 인터페이스
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent
helpviewer_keywords:
- IActionOnCLREvent interface [.NET Framework hosting]
ms.assetid: b5f9b41e-7301-429c-911f-21d5422292b3
topic_type:
- apiref
ms.openlocfilehash: 9d762635247f897663f4c6f2badf67edf98bd5d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785174"
---
# <a name="iactiononclrevent-interface"></a>IActionOnCLREvent 인터페이스

[ICLROnEventManager:: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) 메서드를 호출 하 여 등록 된 이벤트에 대해 콜백을 수행 하는 [IActionOnCLREvent:: OnEvent](iactiononclrevent-onevent-method.md) 메서드를 제공 합니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[OnEvent 메서드](iactiononclrevent-onevent-method.md)|등록 된 이벤트에 대 한 콜백을 수행 합니다.|  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Mscoree.dll  
  
 **라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [EClrEvent 열거형](eclrevent-enumeration.md)
- [ICLRControl 인터페이스](iclrcontrol-interface.md)
- [ICLROnEventManager 인터페이스](iclroneventmanager-interface.md)
- [호스팅 인터페이스](hosting-interfaces.md)
