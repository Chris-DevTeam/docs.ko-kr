---
description: '자세히 알아보기: IMetaDataEmit:: SaveToMemory 메서드'
title: IMetaDataEmit::SaveToMemory 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToMemory
helpviewer_keywords:
- IMetaDataEmit::SaveToMemory method [.NET Framework metadata]
- SaveToMemory method [.NET Framework metadata]
ms.assetid: d5237628-2675-45ed-a39e-65c0731b6a56
topic_type:
- apiref
ms.openlocfilehash: b5fbca2c3ce06398de72bf2690108077545fef9c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745803"
---
# <a name="imetadataemitsavetomemory-method"></a>IMetaDataEmit::SaveToMemory 메서드

현재 범위에 있는 모든 메타 데이터를 지정 된 메모리 영역에 저장 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT SaveToMemory (
    [out]  void        *pbData,
    [in]   ULONG       cbData
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `pbData`  
 제한이 메타 데이터 작성을 시작할 주소입니다.  
  
 `cbData`  
 진행 할당 된 메모리의 크기 (바이트)입니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Cor  
  
 **라이브러리:** MSCorEE.dll에서 리소스로 사용 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [IMetaDataEmit 인터페이스](imetadataemit-interface.md)
- [IMetaDataEmit2 인터페이스](imetadataemit2-interface.md)
