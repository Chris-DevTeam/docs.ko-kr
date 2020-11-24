---
title: ICorDebugAppDomain 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
ms.openlocfilehash: 98273a5d4602c023863758045bdb2a6a502ba7a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687231"
---
# <a name="icordebugappdomain-interface"></a>ICorDebugAppDomain 인터페이스

애플리케이션 도메인 디버깅에 사용하는 메서드를 제공합니다. 이 인터페이스는 ICorDebugController의 서브 클래스입니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[Attach 메서드](icordebugappdomain-attach-method.md)|응용 프로그램 도메인에 디버거를 연결 합니다.|  
|[EnumerateAssemblies 메서드](icordebugappdomain-enumerateassemblies-method.md)|응용 프로그램 도메인의 어셈블리에 대 한 열거자를 가져옵니다.|  
|[EnumerateBreakpoints 메서드](icordebugappdomain-enumeratebreakpoints-method.md)|응용 프로그램 도메인의 모든 활성 중단점에 대 한 열거자를 가져옵니다.|  
|[EnumerateSteppers 메서드](icordebugappdomain-enumeratesteppers-method.md)|응용 프로그램 도메인의 모든 활성 steppers에 대 한 열거자를 가져옵니다.|  
|[GetId 메서드](icordebugappdomain-getid-method.md)|응용 프로그램 도메인의 고유 ID를 가져옵니다.|  
|[GetModuleFromMetaDataInterface 메서드](icordebugappdomain-getmodulefrommetadatainterface-method.md)|지정 된 메타 데이터 인터페이스를 사용 하 여 ICorDebugModule 개체를 가져옵니다.|  
|[GetName 메서드](icordebugappdomain-getname-method.md)|응용 프로그램 도메인의 이름을 가져옵니다.|  
|[GetObject 메서드](icordebugappdomain-getobject-method.md)|CLR (공용 언어 런타임) 응용 프로그램 도메인에 대 한 인터페이스 포인터를 가져옵니다.|  
|[GetProcess 메서드](icordebugappdomain-getprocess-method.md)|응용 프로그램 도메인을 포함 하는 프로세스를 가져옵니다.|  
|[IsAttached 메서드](icordebugappdomain-isattached-method.md)|디버거가 응용 프로그램 도메인에 연결 되어 있는지 여부를 확인 합니다.|  
  
## <a name="remarks"></a>설명  
  
> [!NOTE]
> 이 인터페이스는 크로스 시스템 또는 크로스 프로세스 원격 호출을 지원하지 않습니다.  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** CorDebug.idl, CorDebug.h  
  
 **라이브러리:** CorGuids.lib  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참조

- [디버깅 인터페이스](debugging-interfaces.md)
