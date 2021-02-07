---
description: '자세한 정보: ImportTypes 메서드'
title: ImportTypes 메서드
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
ms.openlocfilehash: 9a30c735ca2c9ad0f945628c3de1eb1bb56efe2c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662626"
---
# <a name="importtypes-method"></a>ImportTypes 메서드

[Importfile 메서드](importfile-method.md)를 통해 가져온 각 범위에서 형식의 가져오기를 시작 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a>매개 변수  

 `AssemblyID`  
 가져올 어셈블리의 ID입니다.  
  
 `FileToken`  
 가져올 파일의 ID입니다.  
  
 `dwScope`  
 가져올 범위 (0부터 시작)입니다.  
  
 `phEnum`  
 이 범위에 있는 형식에 대 한 열거자 핸들을 받습니다.  
  
 `ppImportScope`  
 선택적으로 [IMetaDataImport 인터페이스](../metadata/imetadataimport-interface.md) 인터페이스를 수신 합니다.  
  
 `pdwCountOfTypes`  
 지정 된 범위에서 필요에 따라 형식의 수를 받습니다.  
  
## <a name="return-value"></a>Return Value  

 메서드가 성공 하면 S_OK을 반환 합니다.  
  
## <a name="requirements"></a>요구 사항  

 Alink 필요  
  
## <a name="see-also"></a>참고 항목

- [IALink 인터페이스](ialink-interface.md)
- [IALink2 인터페이스](ialink2-interface.md)
- [ALink API](index.md)
