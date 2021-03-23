---
title: HttpWebRequest._CoreResponse 필드
description: .NET의 HttpWebRequest._CoreResponse 필드에 대해 읽어 보십시오. 이 필드는 HTTP 응답 구문 분석의 결과를 포함 하는 CoreResponseData 또는 Exception 개체입니다.
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.HttpWebRequest._CoreResponse
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: f5fb71c21922285c0e18c2d1f28eeaf2353dcaee
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873837"
---
# <a name="httpwebrequest_coreresponse-field"></a>HttpWebRequest. \_ CoreResponse 필드

`HttpWebRequest._CoreResponse`는 [](coreresponsedata.md) <xref:System.Exception> HTTP 응답 구문 분석의 결과를 포함 하는 개체 (CoreResponseData 또는)입니다.

## <a name="syntax"></a>Syntax
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> 이 API는 코드에서 직접 사용할 수 없습니다. 대신를 사용 <xref:System.Diagnostics.DiagnosticSource> 하 여 네트워킹 코드를 후크 해야 합니다. [DiagnosticSource 사용자 가이드](https://github.com/dotnet/runtime/blob/main/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)를 참조 하세요.
>
> Microsoft는 어떤 경우에도 프로덕션 응용 프로그램에서이 클래스를 사용 하는 것을 지원 하지 않습니다.

## <a name="requirements"></a>요구 사항

**네임스페이스:** <xref:System.Net>

**어셈블리:** 시스템 (System.dll)

**.NET Framework 버전:** 2.0부터 사용할 수 있습니다.
