---
description: '자세히 알아보기: IMetaDataImport:: EnumProperties 메서드'
title: IMetaDataImport::EnumProperties 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumProperties
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumProperties
helpviewer_keywords:
- IMetaDataImport::EnumProperties method [.NET Framework metadata]
- EnumProperties method [.NET Framework metadata]
ms.assetid: 60573ad7-8821-4721-a068-3f7a6d25926a
topic_type:
- apiref
ms.openlocfilehash: 7503dd14668e8ea4ccf8939e67b91a41db187105
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799358"
---
# <a name="imetadataimportenumproperties-method"></a>IMetaDataImport::EnumProperties 메서드

지정한 TypeDef 토큰이 참조하는 형식의 속성을 나타내는 PropertyDef 토큰을 열거합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `phEnum`  
 [in, out] 열거자에 대 한 포인터입니다. 이 메서드의 첫 번째 호출에서는 NULL 이어야 합니다.  
  
 `td`  
 진행 열거할 속성이 있는 형식을 나타내는 TypeDef 토큰입니다.  
  
 `rProperties`  
 제한이 PropertyDef 토큰을 저장 하는 데 사용 되는 배열입니다.  
  
 `cMax`  
 [in] `rProperties` 배열의 최대 크기입니다.  
  
 `pcProperties`  
 제한이 에서 반환 된 PropertyDef 토큰의 수입니다 `rProperties` .  
  
## <a name="return-value"></a>Return Value  
  
|HRESULT|설명|  
|-------------|-----------------|  
|`S_OK`|`EnumProperties` 성공적으로 반환 되었습니다.|  
|`S_FALSE`|열거할 토큰이 없습니다. 이 경우는 `pcProperties` 0입니다.|  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Cor  
  
 **라이브러리:** MsCorEE.dll의 리소스로 포함 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [IMetaDataImport 인터페이스](imetadataimport-interface.md)
- [IMetaDataImport2 인터페이스](imetadataimport2-interface.md)
