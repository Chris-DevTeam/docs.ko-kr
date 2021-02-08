---
description: IMetaDataEmit::D efineSecurityAttributeSet 메서드에 대해 자세히 알아보세요.
title: IMetaDataEmit::DefineSecurityAttributeSet 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineSecurityAttributeSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet
helpviewer_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet method [.NET Framework metadata]
- DefineSecurityAttributeSet method [.NET Framework metadata]
ms.assetid: 27064ca2-4186-4433-90a7-3b297785e891
topic_type:
- apiref
ms.openlocfilehash: 3512857ca23d65389b0e150bd24234d272ddd9b6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784056"
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a>IMetaDataEmit::DefineSecurityAttributeSet 메서드

지정 된 토큰이 참조 하는 개체에 연결할 보안 권한 집합을 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT DefineSecurityAttributeSet (
    [in]  mdToken       tkObj,
    [in]  COR_SECATTR   rSecAttrs[],
    [in]  ULONG         cSecAttrs,
    [out] ULONG         *pulErrorAttr
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `tkObj`  
 진행 보안 정보가 연결 된 토큰입니다.  
  
 `rSecAttrs`  
 진행 구조체의 배열 `COR_SECATTR` 입니다.  
  
 `cSecAttrs`  
 진행 의 요소 수 `rSecAttrs` 입니다.  
  
 `pulErrorAttr`  
 제한이 메서드가 실패 하는 경우 문제를 일으킨 요소의 인덱스를 지정 합니다 `rSecAttrs` .  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Cor  
  
 **라이브러리:** MSCorEE.dll에서 리소스로 사용 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [IMetaDataEmit 인터페이스](imetadataemit-interface.md)
- [IMetaDataEmit2 인터페이스](imetadataemit2-interface.md)
