---
description: '자세한 정보: CLRRuntimeHost Coclass'
title: CLRRuntimeHost Coclass
ms.date: 03/30/2017
api_name:
- CLRRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLRRuntimeHost
helpviewer_keywords:
- CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type:
- apiref
ms.openlocfilehash: a371b9b7263f8bb58b5c513de6647320f000beed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799891"
---
# <a name="clrruntimehost-coclass"></a>CLRRuntimeHost Coclass

런타임에의 한 코드 실행을 관리 하기 위한 인터페이스를 제공 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a>인터페이스  
  
|인터페이스|설명|  
|---------------|-----------------|  
|[ICLRRuntimeHost 인터페이스](iclrruntimehost-interface.md)|런타임에의 한 응용 프로그램 실행을 제어 하는 메서드를 제공 합니다.|  
|[ICLRValidator 인터페이스](iclrvalidator-interface.md)|이식 가능한 실행 이미지의 유효성을 검사 하 고 유효성 검사 오류에 대 한 자세한 보고를 위한 메서드를 제공 합니다.|  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Mscoree.dll  
  
 **라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [호스팅 Coclass](hosting-coclasses.md)
