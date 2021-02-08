---
description: '자세히 알아보기: IMetaDataImport:: GetFieldProps 메서드'
title: IMetaDataImport::GetFieldProps 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
ms.openlocfilehash: 76735f837ff53b46b35cdf8c39990ed8689cc69c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789205"
---
# <a name="imetadataimportgetfieldprops-method"></a>IMetaDataImport::GetFieldProps 메서드

지정한 FieldDef 토큰이 참조하는 필드와 연결된 메타데이터를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pcbSigBlob,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `mb`  
 진행 연결 된 메타 데이터를 가져올 필드를 나타내는 FieldDef 토큰입니다.  
  
 `pClass`  
 제한이 필드가 속한 클래스의 형식을 나타내는 TypeDef 토큰에 대 한 포인터입니다.  
  
 `szField`  
 제한이 필드의 이름입니다.  
  
 `cchField`  
 진행 *Szfield* 에 대 한 버퍼의 와이드 문자 크기입니다.  
  
 `pchField`  
 제한이 반환 된 버퍼의 실제 크기입니다.  
  
 `pdwAttr`  
 제한이 필드의 메타 데이터와 연결 된 플래그입니다.  
  
 `ppvSigBlob`  
 진행 필드를 설명 하는 이진 메타 데이터 값에 대 한 포인터입니다.  
  
 `pcbSigBlob`  
 제한이 의 크기 (바이트) `ppvSigBlob` 입니다.  
  
 `pdwCPlusTypeFlag`  
 제한이 필드의 값 형식을 지정 하는 플래그입니다.  
  
 `ppValue`  
 제한이 필드에 대 한 상수 값입니다.  
  
 `pcchValue`  
 제한이 의 문자 크기 `ppValue` 이거나, 문자열이 없는 경우 0입니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Cor  
  
 **라이브러리:** MsCorEE.dll의 리소스로 포함 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [IMetaDataImport 인터페이스](imetadataimport-interface.md)
- [IMetaDataImport2 인터페이스](imetadataimport2-interface.md)
