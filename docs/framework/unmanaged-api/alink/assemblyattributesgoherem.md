---
description: '자세히 알아보기: AssemblyAttributesGoHereM 클래스'
title: AssemblyAttributesGoHereM 클래스 (System.runtime.compilerservices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereM
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereM
helpviewer_keywords:
- AssemblyAttributesGoHereM type
- Alink API, AssemblyAttributesGoHereM type
ms.assetid: caaa8ba9-b4bb-4dd6-934d-57e436b2f3e5
topic_type:
- apiref
ms.openlocfilehash: 9afa72e5adbd539acaf8dfe45b446a61862df49e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638576"
---
# <a name="assemblyattributesgoherem-class"></a>AssemblyAttributesGoHereM 클래스

ALink에서 사용자 지정 특성 정보를 저장하는 자리 표시자로 사용됩니다.

## <a name="syntax"></a>구문

```csharp
internal sealed class AssemblyAttributesGoHereM
```

## <a name="remarks"></a>설명

이 형식에 대한 참조는 소스에 어셈블리 사용자 지정 특성이 들어 있는 netmodule 내부에 포함될 수 있습니다. 이러한 유형에 대한 참조가 포함된 netmodule 하나 이상에서 어셈블리 매니페스트를 빌드할 때 ALink에서는 이들 참조에 연결된 정보를 사용하여 실제 사용자 지정 특성을 내보냅니다. 따라서 이 형식은 인스턴스화되지 않으며, 이에 대한 참조는 빌드 프로세스 부분으로만 사용되고 최종 어셈블리에서 도움이 되지 않습니다.

이 형식에 대한 참조는 보관과 관련되지 않지만 다양한 용도가 있는 사용자 지정 특성을 나타냅니다.

이러한 형식은 .NET Framework 내에서 "내부"로 표시 되 고 <xref:System.Runtime.CompilerServices> 네임 스페이스에 있습니다.

## <a name="requirements"></a>요구 사항

mscorlib.dll

## <a name="see-also"></a>참고 항목

- [AssemblyAttributesGoHere](assemblyattributesgohere.md)
- [AssemblyAttributesGoHereS](assemblyattributesgoheres.md)
- [AssemblyAttributesGoHereSM](assemblyattributesgoheresm.md)
