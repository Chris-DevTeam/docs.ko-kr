---
description: '자세히 알아보기: CorFileMapping 열거형'
title: CorFileMapping 열거형
ms.date: 03/30/2017
api_name:
- CorFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileMapping
helpviewer_keywords:
- CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type:
- apiref
ms.openlocfilehash: 0fc3916e75c576a6b133ba8a49c00eec6c9bac19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784472"
---
# <a name="corfilemapping-enumeration"></a>CorFileMapping 열거형

[IMetaDataInfo:: GetFileMapping](imetadatainfo-getfilemapping-method.md) 메서드 호출에서 반환 되는 파일 매핑의 유형을 설명 하는 값을 포함 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a>구성원  
  
|멤버|설명|  
|------------|-----------------|  
|`fmFlat`|파일은 데이터 파일로 매핑됩니다. 즉, `SEC_IMAGE` 플래그가 Microsoft Win32 함수에 전달 되지 않았습니다 `CreateFileMapping` .|  
|`fmExecutableImage`|파일은 플래그를 사용 하 여 함수 또는 함수를 사용 하 여 실행을 위해 매핑됩니다 `LoadLibrary` `CreateFileMapping` `SEC_IMAGE` .|  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorHdr .h  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [메타데이터 열거형](metadata-enumerations.md)
- [GetFileMapping 메서드](imetadatainfo-getfilemapping-method.md)
