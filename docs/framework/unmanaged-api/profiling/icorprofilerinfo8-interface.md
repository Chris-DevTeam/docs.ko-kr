---
description: '자세히 알아보기: ICorProfilerInfo8 인터페이스'
title: ICorProfilerInfo8 인터페이스
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 4538c9d314283c67ab0bfe6af3f3768062cffda4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646545"
---
# <a name="icorprofilerinfo8-interface"></a>ICorProfilerInfo8 인터페이스

동적 메서드에 대 한 정보를 쿼리 하는 메서드를 제공 하는 [ICorProfilerInfo7](icorprofilerinfo7-interface.md) 의 서브 클래스입니다.

## <a name="methods"></a>메서드  

| 메서드|설명|  
| ------------|-----------------|  
|[IsFunctionDynamic 메서드](icorprofilerinfo8-isfunctiondynamic-method.md)| 함수에 연결 된 메타 데이터가 있는지 여부를 확인 합니다.|
|[GetFunctionFromIP3 메서드](icorprofilerinfo8-getfunctionfromip3-method.md)| 관리 코드 명령 포인터를 FunctionID에 매핑합니다. 이 메서드는 동적 메서드와 비동적 메서드 모두에 대해 작동 합니다. |
|[GetDynamicFunctionInfo 메서드](icorprofilerinfo8-getdynamicfunctioninfo-method.md)| 동적 메서드에 대 한 정보를 검색 합니다. |

## <a name="requirements"></a>요구 사항  

**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
**헤더:** CorProf.idl, CorProf.h  
**.NET Framework 버전:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>참고 항목

- [프로파일링 인터페이스](profiling-interfaces.md)
