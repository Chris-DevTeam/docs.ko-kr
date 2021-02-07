---
description: '자세히 알아보기: IMetaDataEmit2 인터페이스'
title: IMetaDataEmit2 인터페이스
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2
helpviewer_keywords:
- IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type:
- apiref
ms.openlocfilehash: db1880d64bf3b1e9084d6745251c174788a4afe7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745686"
---
# <a name="imetadataemit2-interface"></a>IMetaDataEmit2 인터페이스

[IMetaDataEmit](imetadataemit-interface.md) 인터페이스를 주로 확장 하 여 제네릭 형식으로 작업 하는 기능을 제공 합니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[DefineGenericParam 메서드](imetadataemit2-definegenericparam-method.md)|제네릭 형식 매개 변수에 대 한 정의를 만들고 해당 제네릭 형식 매개 변수에 대 한 토큰을 가져옵니다.|  
|[DefineMethodSpec 메서드](imetadataemit2-definemethodspec-method.md)|메서드의 제네릭 인스턴스를 만들고 해당 정의에 대 한 토큰을 가져옵니다.|  
|[GetDeltaSaveSize 메서드](imetadataemit2-getdeltasavesize-method.md)|현재 편집 하며 계속 하기 세션의 변경 내용을 표현 하는 데 필요한 데이터 크기의 차이를 나타내는 값을 가져옵니다.|  
|[ResetENCLog 메서드](imetadataemit2-resetenclog-method.md)|편집 하며 계속 하기 로그를 다시 설정 하 고 새 세션을 시작 합니다.|  
|[SaveDelta 메서드](imetadataemit2-savedelta-method.md)|현재 편집 하며 계속 하기 세션의 변경 내용을 지정 된 파일에 저장 합니다.|  
|[SaveDeltaToMemory 메서드](imetadataemit2-savedeltatomemory-method.md)|현재 편집 하며 계속 하기 세션의 변경 내용을 메모리로 저장 합니다.|  
|[SaveDeltaToStream 메서드](imetadataemit2-savedeltatostream-method.md)|현재 편집 하며 계속 하기 세션의 변경 내용을 지정 된 스트림에 저장 합니다.|  
|[SetGenericParamProps 메서드](imetadataemit2-setgenericparamprops-method.md)|지정 된 토큰이 참조 하는 제네릭 매개 변수 정의에 대 한 속성 값을 설정 합니다.|  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Cor  
  
 **라이브러리:** MsCorEE.dll에서 리소스로 사용 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [메타데이터 인터페이스](metadata-interfaces.md)
- [IMetaDataEmit 인터페이스](imetadataemit-interface.md)
