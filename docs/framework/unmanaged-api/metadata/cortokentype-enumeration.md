---
description: '다음에 대 한 자세한 정보: CorTokenType 열거형'
title: CorTokenType 열거형
ms.date: 03/30/2017
api_name:
- CorTokenType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTokenType
helpviewer_keywords:
- CorTokenType enumeration [.NET Framework metadata]
ms.assetid: 93c9a369-225f-4eff-9b78-3fbee4902cf1
topic_type:
- apiref
ms.openlocfilehash: 954bddccd8fe20be46080f8843bcf754e0cf1bbb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678408"
---
# <a name="cortokentype-enumeration"></a>CorTokenType 열거형

메타 데이터 토큰의 형식을 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef enum CorTokenType {  
  
    mdtModule                       = 0x00000000,  
    mdtTypeRef                      = 0x01000000,  
    mdtTypeDef                      = 0x02000000,  
    mdtFieldDef                     = 0x04000000,  
    mdtMethodDef                    = 0x06000000,  
    mdtParamDef                     = 0x08000000,  
    mdtInterfaceImpl                = 0x09000000,  
    mdtMemberRef                    = 0x0a000000,  
    mdtCustomAttribute              = 0x0c000000,  
    mdtPermission                   = 0x0e000000,  
    mdtSignature                    = 0x11000000,  
    mdtEvent                        = 0x14000000,  
    mdtProperty                     = 0x17000000,  
    mdtModuleRef                    = 0x1a000000,  
    mdtTypeSpec                     = 0x1b000000,  
    mdtAssembly                     = 0x20000000,  
    mdtAssemblyRef                  = 0x23000000,  
    mdtFile                         = 0x26000000,  
    mdtExportedType                 = 0x27000000,  
    mdtManifestResource             = 0x28000000,  
    mdtGenericParam                 = 0x2a000000,  
    mdtMethodSpec                   = 0x2b000000,  
    mdtGenericParamConstraint       = 0x2c000000,  
    mdtString                       = 0x70000000,  
    mdtName                         = 0x71000000,  
    mdtBaseType                     = 0x72000000  
  
} CorTokenType;  
```  
  
## <a name="members"></a>구성원  
  
|멤버|설명|  
|------------|-----------------|  
|`mdtModule`|`mdModule`토큰입니다.|  
|`mdtTypeRef`|`mdTypeRef`토큰입니다.|  
|`mdtTypeDef`|`mdTypeDef`토큰입니다.|  
|`mdtFieldDef`|`mdFieldDef`토큰입니다.|  
|`mdtMethodDef`|`mdMethodDef`토큰입니다.|  
|`mdtParamDef`|`mdParamDef`토큰입니다.|  
|`mdtInterfaceImpl`|`mdInterfaceImpl`토큰입니다.|  
|`mdtMemberRef`|`mdMemberRef`토큰입니다.|  
|`mdtCustomAttribute`|`mdCustomAttribute`토큰입니다.|  
|`mdtPermission`|`mdPermission`토큰입니다.|  
|`mdtSignature`|`mdSignature`토큰입니다.|  
|`mdtEvent`|`mdEvent`토큰입니다.|  
|`mdtProperty`|`mdProperty`토큰입니다.|  
|`mdtModuleRef`|`mdModuleRef`토큰입니다.|  
|`mdtTypeSpec`|`mdTypeSpec`토큰입니다.|  
|`mdtAssembly`|`mdAssembly`토큰입니다.|  
|`mdtAssemblyRef`|`mdAssemblyRef`토큰입니다.|  
|`mdtFile`|`mdFile`토큰입니다.|  
|`mdtExportedType`|`mdExportedType`토큰입니다.|  
|`mdtManifestResource`|`mdManifestResource`토큰입니다.|  
|`mdtGenericParam`|`mdGenericParam`토큰입니다.|  
|`mdtMethodSpec`|`mdMethodSpec`토큰입니다.|  
|`mdtGenericParamConstraint`|`mdGenericParamConstraint`토큰입니다.|  
|`mdtString`|`mdString`토큰입니다.|  
|`mdtName`|`mdName`토큰입니다.|  
|`mdtBaseType`|사용되지 않습니다.|  
  
## <a name="remarks"></a>설명  

 각 값은 해당 하는 메타 데이터 토큰에서 최상위 바이트의 값과 같습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorHdr .h  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [메타데이터 열거형](metadata-enumerations.md)
