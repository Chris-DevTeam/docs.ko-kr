---
description: '자세히 알아보기: StrongNameGetBlobFromImage 함수'
title: StrongNameGetBlobFromImage 함수
ms.date: 03/30/2017
api_name:
- StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type:
- apiref
ms.openlocfilehash: c68d6914d47fbb711c49c1e8432cae1bf33e771f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636353"
---
# <a name="strongnamegetblobfromimage-function"></a>StrongNameGetBlobFromImage 함수

지정된 메모리 주소에 있는 어셈블리 이미지의 이진 표현을 가져옵니다.  
  
 이 함수는 더 이상 사용 되지 않습니다. 대신 [ICLRStrongName:: StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) 메서드를 사용 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `pbBase`  
 진행 매핑된 어셈블리 매니페스트의 메모리 주소입니다.  
  
 `dwLength`  
 진행 에 있는 이미지의 크기 (바이트)입니다 `pbBase` .  
  
 `pbBlob`  
 진행 이미지의 이진 표현을 포함 하는 버퍼입니다.  
  
 `pcbBlob`  
 [in, out] 요청 된 최대 크기 (바이트)입니다 `pbBlob` . 반환 시의 실제 크기 (바이트)입니다 `pbBlob` .  
  
## <a name="return-value"></a>Return Value  

 `true` 성공적으로 완료 되 면 그렇지 않으면 `false` 입니다.  
  
## <a name="remarks"></a>설명  

 `StrongNameGetBlobFromImage`함수가 성공적으로 완료되지 않으면 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 함수를 호출하여 마지막으로 생성된 오류를 검색합니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** StrongName  
  
 **라이브러리:** MsCorEE.dll의 리소스로 포함 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [StrongNameGetBlobFromImage 메서드](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [StrongNameGetBlob 메서드](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [ICLRStrongName 인터페이스](../hosting/iclrstrongname-interface.md)
