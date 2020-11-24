---
title: ISymUnmanagedWriter::GetDebugInfo 메서드
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.GetDebugInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type:
- apiref
ms.openlocfilehash: dcab63b603d4a9a8e1430228043d2a5e597bbf4f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678294"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a>ISymUnmanagedWriter::GetDebugInfo 메서드

컴파일러가 PE (이식 가능한 실행) 파일 헤더에 디버그 디렉터리 항목을 쓰는 데 필요한 정보를 반환 합니다. 기호 작성기는 및를 제외한 모든 필드를 `TimeDateStamp` 채웁니다 `PointerToRawData` . 컴파일러는 이러한 두 필드를 적절 하 게 설정 해야 합니다.  
  
 컴파일러는이 메서드를 호출 하 고, 데이터 blob을 PE 파일로 내보내고, `PointerToRawData` IMAGE_DEBUG_DIRECTORY의 필드를 내보낸 데이터를 가리키도록 설정 하 고, IMAGE_DEBUG_DIRECTORY를 pe 파일에 씁니다. 또한 컴파일러는 `TimeDateStamp` `TimeDateStamp` 생성 되는 PE 파일의와 같도록 필드를 설정 해야 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a>매개 변수  

 `pIDD`  
 [in, out] 기호 작성기가 채울 IMAGE_DEBUG_DIRECTORY에 대 한 포인터입니다.  
  
 `cData`  
 진행 `DWORD` 디버그 데이터의 크기를 포함 하는입니다.  
  
 `pcData`  
 제한이 `DWORD` 디버그 데이터를 포함 하는 데 필요한 버퍼의 크기를 수신 하는에 대 한 포인터입니다.  
  
 `data`  
 제한이 기호 저장소에 대 한 디버그 데이터를 저장 하기에 충분 한 크기의 버퍼에 대 한 포인터입니다.  
  
## <a name="return-value"></a>반환 값  

 메서드가 성공 하면이 고, 그렇지 않으면 S_OK입니다. 그렇지 않으면 E_FAIL 또는 일부 다른 오류 코드입니다.  
  
## <a name="requirements"></a>요구 사항  

 **헤더:** CorSym, CorSym  
  
## <a name="see-also"></a>참조

- [ISymUnmanagedWriter 인터페이스](isymunmanagedwriter-interface.md)
