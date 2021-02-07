---
description: '자세한 정보: CorTypeAttr 열거형'
title: CorTypeAttr 열거형
ms.date: 03/30/2017
api_name:
- CorTypeAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTypeAttr
helpviewer_keywords:
- CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type:
- apiref
ms.openlocfilehash: d4f7d25ce8ead945790defae800b7a45dc88bc38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721168"
---
# <a name="cortypeattr-enumeration"></a>CorTypeAttr 열거형

형식 메타데이터를 나타내는 값을 포함합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef enum CorTypeAttr {  
  
    tdVisibilityMask        =   0x00000007,  
    tdNotPublic             =   0x00000000,  
    tdPublic                =   0x00000001,  
    tdNestedPublic          =   0x00000002,  
    tdNestedPrivate         =   0x00000003,  
    tdNestedFamily          =   0x00000004,  
    tdNestedAssembly        =   0x00000005,  
    tdNestedFamANDAssem     =   0x00000006,  
    tdNestedFamORAssem      =   0x00000007,  
  
    tdLayoutMask            =   0x00000018,  
    tdAutoLayout            =   0x00000000,  
    tdSequentialLayout      =   0x00000008,  
    tdExplicitLayout        =   0x00000010,  
  
    tdClassSemanticsMask    =   0x00000020,  
    tdClass                 =   0x00000000,  
    tdInterface             =   0x00000020,  
  
    tdAbstract              =   0x00000080,  
    tdSealed                =   0x00000100,  
    tdSpecialName           =   0x00000400,  
  
    tdImport                =   0x00001000,  
    tdSerializable          =   0x00002000,  
    tdWindowsRuntime        =   0x00004000,  
  
    tdStringFormatMask      =   0x00030000,  
    tdAnsiClass             =   0x00000000,  
    tdUnicodeClass          =   0x00010000,  
    tdAutoClass             =   0x00020000,  
    tdCustomFormatClass     =   0x00030000,  
    tdCustomFormatMask      =   0x00C00000,  
  
    tdBeforeFieldInit       =   0x00100000,  
    tdForwarder             =   0x00200000,  
  
    tdReservedMask          =   0x00040800,  
    tdRTSpecialName         =   0x00000800,  
    tdHasSecurity           =   0x00040000,  
  
} CorTypeAttr;  
```  
  
## <a name="members"></a>구성원  
  
|멤버|설명|  
|------------|-----------------|  
|`tdVisibilityMask`|형식 표시 유형 정보에 사용 됩니다.|  
|`tdNotPublic`|형식이 공용 범위에 있지 않도록 지정 합니다.|  
|`tdPublic`|형식이 공용 범위에 있음을 지정 합니다.|  
|`tdNestedPublic`|형식이 공용 표시 유형으로 중첩 되도록 지정 합니다.|  
|`tdNestedPrivate`|형식이 전용 표시 유형으로 중첩 되도록 지정 합니다.|  
|`tdNestedFamily`|형식이 패밀리 표시 유형으로 중첩 되도록 지정 합니다.|  
|`tdNestedAssembly`|형식이 어셈블리 표시 유형으로 중첩 되도록 지정 합니다.|  
|`tdNestedFamANDAssem`|형식이 패밀리 및 어셈블리 표시 유형으로 중첩 되도록 지정 합니다.|  
|`tdNestedFamORAssem`|형식이 패밀리 또는 어셈블리 표시 유형으로 중첩 되도록 지정 합니다.|  
|`tdLayoutMask`|형식에 대 한 레이아웃 정보를 가져옵니다.|  
|`tdAutoLayout`|이 형식의 필드를 자동으로 배치 하도록 지정 합니다.|  
|`tdSequentialLayout`|이 형식의 필드를 순차적으로 배치 하도록 지정 합니다.|  
|`tdExplicitLayout`|필드 레이아웃이 명시적으로 제공 되도록 지정 합니다.|  
|`tdClassSemanticsMask`|형식에 대 한 의미 체계 정보를 가져옵니다.|  
|`tdClass`|형식을 클래스로 지정합니다.|  
|`tdInterface`|형식을 인터페이스로 지정합니다.|  
|`tdAbstract`|형식을 추상으로 지정합니다.|  
|`tdSealed`|형식을 확장할 수 없도록 지정 합니다.|  
|`tdSpecialName`|클래스 이름을 특수 하도록 지정 합니다. 해당 이름에서 방법을 설명 합니다.|  
|`tdImport`|형식을 가져오도록 지정 합니다.|  
|`tdSerializable`|형식을 serialize 할 수 있도록 지정 합니다.|  
|`tdWindowsRuntime`|이 형식이 Windows 런타임 형식이 되도록 지정 합니다.|  
|`tdStringFormatMask`|문자열을 인코딩하고 형식을 지정 하는 방법에 대 한 정보를 가져옵니다.|  
|`tdAnsiClass`|이 형식이 LPTSTR를 ANSI로 해석 하도록 지정 합니다.|  
|`tdUnicodeClass`|이 형식이 LPTSTR를 유니코드로 해석 하도록 지정 합니다.|  
|`tdAutoClass`|이 형식이 LPTSTR를 자동으로 해석 하도록 지정 합니다.|  
|`tdCustomFormatClass`|에 지정 된 대로 형식이 비표준 인코딩을 포함 하도록 지정 합니다 `CustomFormatMask` .|  
|`tdCustomFormatMask`|네이티브 interop에 대 한 비표준 인코딩 정보를 가져오려면이 마스크를 사용 합니다. 이러한 두 비트 값의 의미는 지정 되지 않습니다.|  
|`tdBeforeFieldInit`|정적 필드에 대 한 첫 번째 액세스를 시도 하기 전에 형식을 초기화 하도록 지정 합니다.|  
|`tdForwarder`|형식을 내보내도록 지정 하 고 형식 전달자를 지정 합니다.|  
|`tdReservedMask`|이 플래그와 아래 플래그는 공용 언어 런타임에서 내부적으로 사용 됩니다.|  
|`tdRTSpecialName`|공용 언어 런타임에서 이름 인코딩을 확인 하도록 지정 합니다.|  
|`tdHasSecurity`|형식에 연결 된 보안이 있음을 지정 합니다.|  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorHdr .h  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [메타데이터 열거형](metadata-enumerations.md)
