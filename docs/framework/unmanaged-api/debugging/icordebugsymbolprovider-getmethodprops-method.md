---
title: ICorDebugSymbolProvider::GetMethodProps 메서드
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
ms.openlocfilehash: 5412b2f06445627c1240d6c8f4efb3ce6bbbec54
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730827"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a>ICorDebugSymbolProvider::GetMethodProps 메서드

해당 메서드에 RVA(상대 가상 주소)가 제공된 경우 메서드의 메타데이터 토큰 및 제네릭 매개 변수 정보와 같은 메서드 속성 정보를 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetMethodProps(  
   [in]  ULONG32 codeRva,  
   [out] mdToken *pMethodToken,  
   [out] ULONG32 *pcGenericParams,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a>매개 변수  

 `codeRVA`  
 [in] 정보를 검색할 메서드의 상대 가상 주소입니다.  
  
 `pMethodToken`  
 [out] 메서드의 메타데이터 토큰에 대한 포인터입니다.  
  
 `pcGenericParams`  
 [out] 이 메서드와 연결된 제네릭 매개 변수 개수에 대한 포인터입니다.  
  
 `cbSignature`  
 [in] `signature` 배열의 크기입니다. 주의 섹션을 참조하십시오.  
  
 `pcbSignature`  
 [out] 반환된 `signature` 배열의 크기에 대한 포인터입니다.  
  
 `signature`  
 [out] 모든 제네릭 매개 변수의 typespec 서명을 보유하는 버퍼입니다.  
  
## <a name="remarks"></a>설명  

 메서드의 배열에 필요한 크기를 가져오려면 인수를 `signature` 0으로 설정 하 `cbSignature` 고 `signature` 를 **null** 로 설정 합니다. 메서드가 반환되면 `signature` 배열에 필요한 바이트 수가 `pcbSignature`에 포함됩니다.  
  
> [!NOTE]
> 이 메서드는 .NET 네이티브에서만 사용할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>참조

- [GetTypeProps 메서드](icordebugsymbolprovider-gettypeprops-method.md)
- [ICorDebugSymbolProvider 인터페이스](icordebugsymbolprovider-interface.md)
- [디버깅 인터페이스](debugging-interfaces.md)
