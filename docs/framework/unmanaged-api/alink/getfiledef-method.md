---
description: '자세히 알아보기: GetFileDef 메서드'
title: GetFileDef 메서드
ms.date: 03/30/2017
api_name:
- IALink2.GetFileDef
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetFileDef
helpviewer_keywords:
- GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type:
- apiref
ms.openlocfilehash: 5d44336e686ca565f468fb95ce5290ee41d5e16e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718449"
---
# <a name="getfiledef-method"></a>GetFileDef 메서드

ALink에서 할당 된 토큰과는 반대로 메타 데이터에 사용 되는 실제 FileDef 토큰을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a>매개 변수  

 `AssemblyID`  
 어셈블리의 ID입니다.  
  
 `TargetFile`  
 AddFile Method 또는 AddImport 메서드에서 검색 된 추가 된 파일의 토큰입니다.  
  
 `pScope`  
 FileDef 토큰을 받습니다.  
  
## <a name="return-value"></a>Return Value  

 메서드가 성공 하면 S_OK을 반환 합니다.  
  
## <a name="requirements"></a>요구 사항  

 Alink 필요  
  
## <a name="see-also"></a>참고 항목

- [IALink2 인터페이스](ialink2-interface.md)
- [IALink 인터페이스](ialink-interface.md)
- [ALink API](index.md)
