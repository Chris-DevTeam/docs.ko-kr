---
description: '다음에 대 한 자세한 정보: IAssemblyCacheItem:: CreateStream 메서드'
title: IAssemblyCacheItem::CreateStream 메서드
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
ms.openlocfilehash: 89592d8fe1a7f43a7da20dd10883881c3339f088
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760875"
---
# <a name="iassemblycacheitemcreatestream-method"></a>IAssemblyCacheItem::CreateStream 메서드

지정 된 이름 및 형식을 사용 하 여 스트림을 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CreateStream (
    [in]  DWORD dwFlags,
    [in]  LPCWSTR pszStreamName,
    [in]  DWORD dwFormat,
    [in]  DWORD dwFormatFlags,
    [out] IStream **ppIStream,
    [in, optional] ULARGE_INTEGER *puliMaxSize
);
```

## <a name="parameters"></a>매개 변수

`dwFlags`\
진행 Fusion에 정의 된 플래그입니다.

`pszStreamName`\
진행 만들 스트림의 이름입니다.

`dwFormat`\
진행 스트리밍할 파일의 형식입니다.

`dwFormatFlags`\
진행 Fusion에 정의 된 형식별 플래그입니다.

`ppIStream`\
제한이 반환 된 [IStream](/windows/desktop/api/objidl/nn-objidl-istream) 인스턴스의 주소에 대 한 포인터입니다.

`puliMaxSize`\
[in, 선택 사항] 에서 참조 하는 스트림의 최대 크기 `ppIStream` 입니다.

## <a name="requirements"></a>요구 사항

**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.

**헤더:** Fusion. h

**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>참고 항목

- [IAssemblyCacheItem 인터페이스](iassemblycacheitem-interface.md)
