---
description: '자세히 알아보기: ICorDebugLoadedModule 인터페이스'
title: ICorDebugLoadedModule 인터페이스
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
ms.openlocfilehash: 6a1b466a9d2d7781fad7ac2bc8c24f0b2a5c23e0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801230"
---
# <a name="icordebugloadedmodule-interface"></a>ICorDebugLoadedModule 인터페이스

로드된 모듈에 대한 정보를 제공합니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[GetBaseAddress 메서드](icordebugloadedmodule-getbaseaddress-method.md)|로드된 모듈의 기본 주소를 가져옵니다.|  
|[GetName 메서드](icordebugloadedmodule-getname-method.md)|로드된 모듈의 이름을 가져옵니다.|  
|[GetSize 메서드](icordebugloadedmodule-getsize-method.md)|로드된 모듈의 크기(바이트)를 가져옵니다.|  
  
## <a name="remarks"></a>설명  

 `ICorDebugLoadedModule` 인터페이스는 디버거에서 구현되며 CLR 디버깅 인터페이스가 디버거에서 로드된 모듈에 대한 정보를 가져오는 데 사용됩니다.  
  
> [!NOTE]
> 이 인터페이스는 .NET 네이티브에서만 사용할 수 있습니다. .NET 네이티브 외부의 ICorDebug 시나리오에 대해 이 인터페이스를 구현하는 경우 공용 언어 런타임에서 이 인터페이스를 무시합니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [디버깅 인터페이스](debugging-interfaces.md)
- [디버깅](index.md)
