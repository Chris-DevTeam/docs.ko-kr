---
title: ICLRRuntimeInfo 인터페이스
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo
helpviewer_keywords:
- ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 287e5ede-b3a7-4ef8-a756-4fca3f285a82
topic_type:
- apiref
ms.openlocfilehash: 9f485728ddb050abf815bf8ba26c69be9c909785
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714978"
---
# <a name="iclrruntimeinfo-interface"></a>ICLRRuntimeInfo 인터페이스

버전, 디렉터리 및 로드 상태를 포함 하 여 특정 CLR (공용 언어 런타임)에 대 한 정보를 반환 하는 메서드를 제공 합니다. 또한이 인터페이스는 런타임을 초기화 하지 않고 런타임 관련 기능을 제공 합니다. 이 메서드에는 [Getinterface](iclrruntimeinfo-getinterface-method.md) 메서드를 통해 런타임 관련 [LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) 메서드, 런타임 모듈 관련 [GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) 메서드 및 런타임 제공 인터페이스가 포함 됩니다.  
  
## <a name="methods"></a>메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[BindAsLegacyV2Runtime 메서드](iclrruntimeinfo-bindaslegacyv2runtime-method.md)|모든 레거시 CLR 버전 2 활성화 정책 결정에 대해이 런타임을 바인딩합니다.|  
|[GetDefaultStartupFlags 메서드](iclrruntimeinfo-getdefaultstartupflags-method.md)|CLR 시작 플래그 및 호스트 구성 파일을 가져옵니다.|  
|[GetInterface 메서드](iclrruntimeinfo-getinterface-method.md)|CLR을 현재 프로세스로 로드 하 고 [ICLRRuntimeHost](iclrruntimehost-interface.md), [ICLRStrongName](iclrstrongname-interface.md) 및 [IMetaDataDispenser](../metadata/imetadatadispenser-interface.md)와 같은 런타임 인터페이스 포인터를 반환 합니다. 이 메서드는 모든 함수를 대체 `CorBindTo*` 합니다.|  
|[GetProcAddress 메서드](iclrruntimeinfo-getprocaddress-method.md)|이 인터페이스와 연결 된 CLR에서 내보낸 지정 된 함수의 주소를 가져옵니다. 이 메서드는 [GetRealProcAddress](getrealprocaddress-function.md) 메서드를 대체 합니다.|  
|[GetRuntimeDirectory 메서드](iclrruntimeinfo-getruntimedirectory-method.md)|이 인터페이스와 연결 된 CLR의 설치 디렉터리를 가져옵니다. 이 메서드는 [GetCORSystemDirectory](getcorsystemdirectory-function.md) 메서드를 대체 합니다.|  
|[GetVersionString 메서드](iclrruntimeinfo-getversionstring-method.md)|지정 된 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 인터페이스와 연결 된 CLR (공용 언어 런타임) 버전 정보를 가져옵니다. 이 메서드는 [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md) 및 [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) 메서드를 대체 합니다.|  
|[IsLoadable 메서드](iclrruntimeinfo-isloadable-method.md)|프로세스에 이미 로드 되어 있을 수 있는 다른 런타임을 고려 하 여이 인터페이스와 연결 된 런타임을 현재 프로세스에 로드할 수 있는지 여부를 나타냅니다.|  
|[IsLoaded 메서드](iclrruntimeinfo-isloaded-method.md)|[ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 인터페이스와 연결 된 CLR이 프로세스에 로드 되는지 여부를 나타냅니다.|  
|[IsStarted 메서드](iclrruntimeinfo-isstarted-method.md)|[ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 인터페이스와 연결 된 CLR이 시작 되었는지 여부를 나타냅니다.|  
|[LoadErrorString 메서드](iclrruntimeinfo-loaderrorstring-method.md)|HRESULT 값을 지정 된 문화권에 대 한 적절 한 오류 메시지로 변환 합니다. 이 메서드는 [LoadStringRC](loadstringrc-function.md) 및 [LoadStringRCEx](loadstringrcex-function.md) 메서드를 대체 합니다.|  
|[LoadLibrary 메서드](iclrruntimeinfo-loadlibrary-method.md)|[ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 인터페이스로 표시 되는 CLR의 프레임 워크 디렉터리에서 라이브러리를 로드 합니다. 이 메서드는 [LoadLibraryShim](loadlibraryshim-function.md) 메서드를 대체 합니다.|  
|[SetDefaultStartupFlags 메서드](iclrruntimeinfo-setdefaultstartupflags-method.md)|CLR 시작 플래그 및 호스트 구성 파일을 설정 합니다.|  
  
## <a name="requirements"></a>요구 사항  

 **플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.  
  
 **헤더:** MetaHost  
  
 **라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.  
  
 **.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>참조

- [호스팅 인터페이스](hosting-interfaces.md)
- [호스팅](index.md)
