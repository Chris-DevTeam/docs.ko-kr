---
title: IMetaDataImport2::GetGenericParamConstraintProps 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamConstraintProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps method [.NET Framework metadata]
- GetGenericParamConstraintProps method [.NET Framework metadata]
ms.assetid: c5fee4a0-b132-4e5e-8730-e586ce314b9a
topic_type:
- apiref
ms.openlocfilehash: 8beaea0b7493b7cea76466bb15355cfc5c6d5c7d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702708"
---
# <a name="imetadataimport2getgenericparamconstraintprops-method"></a>IMetaDataImport2::GetGenericParamConstraintProps 메서드

지정 된 제약 조건 토큰이 나타내는 제네릭 매개 변수 제약 조건과 연결 된 메타 데이터를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetGenericParamConstraintProps (  
   [in]  mdGenericParamConstraint  gpc,  
   [out] mdGenericParam            *ptGenericParam,  
   [out] mdToken                   *ptkConstraintType  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `gpc`  
 진행 메타 데이터를 반환할 제네릭 매개 변수 제약 조건에 대 한 토큰입니다.  
  
 `ptGenericParam`  
 제한이 제약 조건이 있는 제네릭 매개 변수를 나타내는 토큰에 대 한 포인터입니다.  
  
 `ptkConstraintType`  
 제한이 에 대 한 제약 조건을 나타내는 TypeDef, TypeRef 또는 TypeSpec 토큰에 대 한 포인터입니다 `ptGenericParam` .  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Cor  
  
 **라이브러리:** MsCorEE.dll에서 리소스로 사용 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참조

- [IMetaDataImport2 인터페이스](imetadataimport2-interface.md)
- [IMetaDataImport 인터페이스](imetadataimport-interface.md)
