---
description: '다음에 대 한 자세한 정보: <performanceCounters> 요소'
title: <performanceCounters> 요소
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <performanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
ms.openlocfilehash: 3a9a6c42575be3fc7fb5c5d80ffecd940894e164
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639577"
---
# <a name="performancecounters-element"></a>\<performanceCounters> 요소

성능 카운터에서 공유하는 전역 메모리의 크기를 지정합니다.

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**  

## <a name="syntax"></a>구문

```xml
<performanceCounters filemappingsize="524288" />
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|filemappingsize|필수 특성입니다.<br /><br /> 성능 카운터에서 공유하는 전역 메모리의 크기(바이트)를 지정합니다. 기본값은 524288입니다.|

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|`Configuration`|공용 언어 런타임 및 .NET Framework 애플리케이션에서 사용하는 모든 구성 파일의 루트 요소입니다.|
|`system.diagnostics`|ASP.NET 구성 섹션의 루트 요소를 지정합니다.|

## <a name="remarks"></a>설명

성능 카운터는 메모리 매핑된 파일 또는 공유 메모리를 사용 하 여 성능 데이터를 게시 합니다.  공유 메모리의 크기에 따라 한 번에 사용할 수 있는 인스턴스 수가 결정 됩니다.  공유 메모리에는 전역 공유 메모리와 별도의 공유 메모리의 두 가지 유형이 있습니다.  전역 공유 메모리는 .NET Framework 버전 1.0 또는 1.1과 함께 설치 된 모든 성능 카운터 범주에서 사용 됩니다.  .NET Framework 버전 2.0와 함께 설치 되는 성능 카운터 범주는 별도의 메모리를 포함 하는 각 성능 카운터 범주와 함께 별도의 공유 메모리를 사용 합니다.

전역 공유 메모리의 크기는 구성 파일을 사용 하는 경우에만 설정할 수 있습니다.  기본 크기는 524288이 고, 최대 크기는 33554432 바이트이 고, 최소 크기는 32768 바이트입니다.  전역 공유 메모리는 모든 프로세스와 범주에서 공유 되기 때문에 첫 번째 작성자는 크기를 지정 합니다.  응용 프로그램 구성 파일에서 크기를 정의 하는 경우 해당 크기는 응용 프로그램이 성능 카운터를 실행 하는 첫 번째 응용 프로그램 인 경우에만 사용 됩니다.  따라서 값을 지정 하는 올바른 위치는 `filemappingsize` Machine.config 파일입니다.  전역 공유 메모리의 메모리는 개별 성능 카운터에 의해 해제 될 수 없으므로 다른 이름을 사용 하는 많은 수의 성능 카운터 인스턴스를 만든 경우에는 결과적으로 전역 공유 메모리가 모두 사용 됩니다.

별도의 공유 메모리 크기에 대해 레지스트리 키 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Performance의 DWORD FileMappingSize 값을 \\ *\<category name>* 먼저 참조 한 다음 구성 파일의 전역 공유 메모리에 대해 지정 된 값을 참조 합니다. FileMappingSize 값이 없는 경우 별도의 공유 메모리 크기가 구성 파일에서 4 개의 4 (1/4) 전역 설정으로 설정 됩니다.

## <a name="see-also"></a>참고 항목

- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
