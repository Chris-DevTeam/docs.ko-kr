---
title: IMetaDataImport::CountEnum 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CountEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CountEnum
helpviewer_keywords:
- CountEnum method [.NET Framework metadata]
- IMetaDataImport::CountEnum method [.NET Framework metadata]
ms.assetid: d1de53ad-9435-4b5f-9df7-07f21210e5b5
topic_type:
- apiref
ms.openlocfilehash: f2470cd7112adff35ef49c21a155072fcd4008be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727291"
---
# <a name="imetadataimportcountenum-method"></a>IMetaDataImport::CountEnum 메서드

지정 된 열거자에 의해 검색 된 열거형의 요소 수를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `hEnum`  
 진행 열거자에 대 한 핸들입니다.  
  
 `pulCount`  
 제한이 열거 된 요소의 수입니다.  
  
## <a name="remarks"></a>설명  

 로 지정 된 핸들은 `hEnum` 이전 `Enum` *이름* 호출에서 가져옵니다 (예 [: IMetaDataImport:: enumtypedefs](imetadataimport-enumtypedefs-method.md)).  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Cor  
  
 **라이브러리:** MsCorEE.dll의 리소스로 포함 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참조

- [IMetaDataImport 인터페이스](imetadataimport-interface.md)
- [IMetaDataImport2 인터페이스](imetadataimport2-interface.md)
