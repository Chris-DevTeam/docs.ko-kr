---
description: '자세히 알아보기: IMetaDataAssemblyEmit 인터페이스'
title: IMetaDataAssemblyEmit 인터페이스
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit
helpviewer_keywords:
- IMetaDataAssemblyEmit interface [.NET Framework metadata]
ms.assetid: 34fb03cc-2285-4a45-ac48-ad993b7a921a
topic_type:
- apiref
ms.openlocfilehash: bcfca4eedc14f2292c40874d86c4984b4c1948f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678213"
---
# <a name="imetadataassemblyemit-interface"></a>IMetaDataAssemblyEmit 인터페이스

공용 언어 런타임에서 리소스를 확인하고 소비하는 데 사용되는 자체 설명 모델을 지원하는 메서드를 제공합니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[DefineAssembly 메서드](imetadataassemblyemit-defineassembly-method.md)|지정된 어셈블리에 대한 메타데이터를 포함하는 어셈블리 데이터 구조를 만들고 연결된 메타데이터 토큰을 반환합니다.|  
|[DefineAssemblyRef 메서드](imetadataassemblyemit-defineassemblyref-method.md)|이 어셈블리가 참조하는 어셈블리에 대한 메타데이터를 포함하는 `AssemblyRef` 구조를 만들고 연결된 메타데이터 토큰을 반환합니다.|  
|[DefineExportedType 메서드](imetadataassemblyemit-defineexportedtype-method.md)|지정된 내보낸 형식에 대한 메타데이터를 포함하는 `ExportedType` 구조를 만들고 연결된 메타데이터 토큰을 반환합니다.|  
|[DefineFile 메서드](imetadataassemblyemit-definefile-method.md)|이 어셈블리가 참조하는 어셈블리에 대한 메타데이터를 포함하는 `File` 메타데이터 구조를 만들고 연결된 메타데이터 토큰을 반환합니다.|  
|[DefineManifestResource 메서드](imetadataassemblyemit-definemanifestresource-method.md)|지정된 매니페스트 리소스에 대한 메타데이터를 포함하는 `ManifestResource` 구조를 만들고 연결된 메타데이터 토큰을 반환합니다.|  
|[SetAssemblyProps 메서드](imetadataassemblyemit-setassemblyprops-method.md)|지정된 `Assembly` 메타데이터 구조를 수정합니다.|  
|[SetAssemblyRefProps 메서드](imetadataassemblyemit-setassemblyrefprops-method.md)|지정된 `AssemblyRef` 메타데이터 구조를 수정합니다.|  
|[SetExportedTypeProps 메서드](imetadataassemblyemit-setexportedtypeprops-method.md)|지정된 `ExportedType` 메타데이터 구조를 수정합니다.|  
|[SetFileProps 메서드](imetadataassemblyemit-setfileprops-method.md)|지정된 `File` 메타데이터 구조를 수정합니다.|  
|[SetManifestResourceProps 메서드](imetadataassemblyemit-setmanifestresourceprops-method.md)|지정된 `ManifestResource` 메타데이터 구조를 수정합니다.|  
  
## <a name="remarks"></a>설명  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** Cor  
  
 **라이브러리:** MsCorEE.dll에서 리소스로 사용 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>참고 항목

- [메타데이터 인터페이스](metadata-interfaces.md)
- [IMetaDataAssemblyImport 인터페이스](imetadataassemblyimport-interface.md)
