---
description: IMetaDataEmit::D efineModuleRef 메서드에 대해 자세히 알아보세요.
title: IMetaDataEmit::DefineModuleRef 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineModuleRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineModuleRef
helpviewer_keywords:
- DefineModuleRef method [.NET Framework metadata]
- IMetaDataEmit::DefineModuleRef method [.NET Framework metadata]
ms.assetid: f2833594-d90b-4a71-9a53-34b12470c64a
topic_type:
- apiref
ms.openlocfilehash: b5af5e458f749d2315612bbe9419f037331f8c46
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753395"
---
# <a name="imetadataemitdefinemoduleref-method"></a>IMetaDataEmit::DefineModuleRef 메서드

지정 된 이름을 사용 하 여 모듈에 대 한 메타 데이터 서명을 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT DefineModuleRef (
    [in]  LPCWSTR           szName,
    [out] mdModuleRef       *pmur
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `szName`  
 진행 다른 메타 데이터 파일의 이름입니다 (일반적으로 DLL). 이는 파일 이름입니다. 전체 경로 이름을 사용 하지 마십시오.  
  
 `pmur`  
 제한이 할당 된 `mdModuleRef` 토큰입니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Cor  
  
 **라이브러리:** MSCorEE.dll에서 리소스로 사용 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [IMetaDataEmit 인터페이스](imetadataemit-interface.md)
- [IMetaDataEmit2 인터페이스](imetadataemit2-interface.md)
