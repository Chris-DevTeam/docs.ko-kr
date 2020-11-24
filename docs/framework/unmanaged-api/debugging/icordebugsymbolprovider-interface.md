---
title: ICorDebugSymbolProvider 인터페이스
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
ms.openlocfilehash: ff1f39be3d3db43f70cfa4a0711a3f42c180bc1a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672086"
---
# <a name="icordebugsymbolprovider-interface"></a>ICorDebugSymbolProvider 인터페이스

디버그 기호 정보를 검색하는 데 사용할 수 있는 메서드를 제공합니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[GetAssemblyImageBytes 메서드](icordebugsymbolprovider-getassemblyimagebytes-method.md)|병합된 어셈블리의 RVA(상대 가상 주소)가 지정된 경우 병합된 어셈블리에서 데이터를 읽습니다.|  
|[GetAssemblyImageMetadata 메서드](icordebugsymbolprovider-getassemblyimagemetadata-method.md)|병합된 어셈블리에서 메타데이터를 반환합니다.|  
|[GetCodeRange 메서드](icordebugsymbolprovider-getcoderange-method.md)|메서드의 RVA(상대 가상 주소)가 지정된 경우 메서드 시작 주소와 크기를 가져옵니다.|  
|[GetInstanceFieldSymbols 메서드](icordebugsymbolprovider-getinstancefieldsymbols-method.md)|typespec 서명에 해당하는 인스턴스 필드 기호를 가져옵니다.|  
|[GetMergedAssemblyRecords 메서드](icordebugsymbolprovider-getmergedassemblyrecords-method.md)|모든 병합된 어셈블리에 대한 기호 레코드를 가져옵니다.|  
|[GetMethodLocalSymbols 메서드](icordebugsymbolprovider-getmethodlocalsymbols-method.md)|메서드의 RVA(상대 가상 주소)가 지정된 경우 해당 메서드의 로컬 기호를 가져옵니다.|  
|[GetMethodParameterSymbols 메서드](icordebugsymbolprovider-getmethodparametersymbols-method.md)|메서드의 RVA(상대 가상 주소)가 지정된 경우 해당 메서드의 매개 변수 기호를 가져옵니다.|  
|[GetMethodProps 메서드](icordebugsymbolprovider-getmethodprops-method.md)|해당 메서드에 RVA(상대 가상 주소)가 제공된 경우 메서드의 메타데이터 토큰 및 제네릭 매개 변수 정보와 같은 메서드 속성 정보를 반환합니다.|  
|[GetObjectSize 메서드](icordebugsymbolprovider-getobjectsize-method.md)|typespec 서명을 기준으로 개체의 개체 크기를 반환합니다.|  
|[GetStaticFieldSymbols 메서드](icordebugsymbolprovider-getstaticfieldsymbols-method.md)|typespec 서명에 해당하는 정적 필드 기호를 가져옵니다.|  
|[GetTypeProps 메서드](icordebugsymbolprovider-gettypeprops-method.md)|vtable에 RVA(상대 가상 주소)가 제공된 경우 해당 제네릭 매개 변수의 서명 수와 같은 형식의 속성 정보를 반환합니다.|  
  
## <a name="remarks"></a>설명  
  
> [!NOTE]
> 이 인터페이스는 .NET 네이티브에서만 사용할 수 있습니다. .NET 네이티브 외부의 ICorDebug 시나리오에 대해 이 인터페이스를 구현하는 경우 공용 언어 런타임에서 이 인터페이스를 무시합니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>참조

- [디버깅 인터페이스](debugging-interfaces.md)
- [디버깅](index.md)
