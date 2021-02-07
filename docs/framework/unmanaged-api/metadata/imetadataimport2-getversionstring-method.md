---
description: '자세히 알아보기: IMetaDataImport2:: GetVersionString 메서드'
title: IMetaDataImport2::GetVersionString 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type:
- apiref
ms.openlocfilehash: 6f7e296607dc3167936c69d52a8baae4f5555b88
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688561"
---
# <a name="imetadataimport2getversionstring-method"></a>IMetaDataImport2::GetVersionString 메서드

어셈블리를 빌드하는 데 사용 된 런타임의 버전 번호를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `pwzBuf`  
 제한이 버전을 지정 하는 문자열을 저장할 배열입니다.  
  
 `ccBufSize`  
 진행 배열의 크기 (와이드 문자) `pwzBuf` 입니다.  
  
 `pccBufSize`  
 제한이 배열에 반환 된 null 종결자를 포함 하는 와이드 문자 수입니다 `pwzBuf` .  
  
## <a name="remarks"></a>설명  

 `GetVersionString`메서드는 현재 메타 데이터 범위의 기본 제공 버전을 가져옵니다. 범위를 저장 하지 않은 경우에는 기본 제공 버전이 없으며 빈 문자열이 반환 됩니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Cor  
  
 **라이브러리:** MsCorEE.dll에서 리소스로 사용 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [IMetaDataImport2 인터페이스](imetadataimport2-interface.md)
- [IMetaDataImport 인터페이스](imetadataimport-interface.md)
