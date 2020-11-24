---
title: ISymUnmanagedReader 인터페이스
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader
helpviewer_keywords:
- ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type:
- apiref
ms.openlocfilehash: bca84fdba575ed9bfe572b9fd7a5869620962de6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675869"
---
# <a name="isymunmanagedreader-interface"></a>ISymUnmanagedReader 인터페이스

기호 저장소 내의 문서, 메서드 및 변수에 대한 액세스를 제공하는 기호 판독기를 나타냅니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[GetDocument 메서드](isymunmanagedreader-getdocument-method.md)|문서를 찾습니다.|  
|[GetDocuments 메서드](isymunmanagedreader-getdocuments-method.md)|기호 저장소에 정의 된 모든 문서의 배열을 반환 합니다.|  
|[GetDocumentVersion 메서드](isymunmanagedreader-getdocumentversion-method.md)|지정 된 문서의 지정 된 버전을 가져옵니다.|  
|[GetGlobalVariables 메서드](isymunmanagedreader-getglobalvariables-method.md)|모든 전역 변수를 반환 합니다.|  
|[GetMethod 메서드](isymunmanagedreader-getmethod-method.md)|메서드 토큰이 지정 된 경우 기호 판독기 메서드를 가져옵니다.|  
|[GetMethodByVersion 메서드](isymunmanagedreader-getmethodbyversion-method.md)|메서드 토큰과 편집 및 복사 버전 번호가 지정 된 경우 기호 판독기 메서드를 가져옵니다.|  
|[GetMethodFromDocumentPosition 메서드](isymunmanagedreader-getmethodfromdocumentposition-method.md)|문서의 지정 된 위치에 중단점을 포함 하는 메서드를 반환 합니다.|  
|[GetMethodsFromDocumentPosition 메서드](isymunmanagedreader-getmethodsfromdocumentposition-method.md)|각각 문서의 지정 된 위치에 중단점을 포함 하는 메서드의 배열을 반환 합니다.|  
|[GetMethodVersion 메서드](isymunmanagedreader-getmethodversion-method.md)|메서드 버전을 가져옵니다.|  
|[GetNamespaces 메서드](isymunmanagedreader-getnamespaces-method.md)|이 기호 저장소의 전역 범위에서 정의 된 네임 스페이스를 가져옵니다.|  
|[GetSymAttribute 메서드](isymunmanagedreader-getsymattribute-method.md)|이름에 따라 사용자 지정 특성을 가져옵니다.|  
|[GetSymbolStoreFileName 메서드](isymunmanagedreader-getsymbolstorefilename-method.md)|기호 저장소의 디스크에 있는 파일 이름을 제공 합니다.|  
|[GetUserEntryPoint 메서드](isymunmanagedreader-getuserentrypoint-method.md)|모듈에 대 한 사용자 진입점으로 지정 된 메서드를 반환 합니다 (있는 경우).|  
|[GetVariables 메서드](isymunmanagedreader-getvariables-method.md)|부모 및 이름이 지정 된 경우 지역 변수가 아닌 변수를 반환 합니다.|  
|[Initialize 메서드](isymunmanagedreader-initialize-method.md)|이 판독기가 연결 될 메타 데이터 가져오기 인터페이스를 사용 하 여 기호 판독기를 모듈의 파일 이름과 함께 초기화 합니다.|  
|[ReplaceSymbolStore 메서드](isymunmanagedreader-replacesymbolstore-method.md)|기존 기호 저장소를 델타 기호 저장소로 바꿉니다.|  
|[UpdateSymbolStore 메서드](isymunmanagedreader-updatesymbolstore-method.md)|기존 기호 저장소를 델타 기호 저장소로 업데이트합니다.|  
  
## <a name="requirements"></a>요구 사항  

 **헤더:** CorSym, CorSym  
  
## <a name="see-also"></a>참조

- [진단 기호 저장소 인터페이스](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader2 인터페이스](isymunmanagedreader2-interface.md)
