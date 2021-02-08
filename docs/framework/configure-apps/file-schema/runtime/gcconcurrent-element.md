---
description: '다음에 대 한 자세한 정보: <gcConcurrent> 요소'
title: gcConcurrent 요소
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: dff8b073977c007a132cfbd685724a02ba37684b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787008"
---
# <a name="gcconcurrent-element"></a>\<gcConcurrent> 요소

공용 언어 런타임이 별도 스레드에서 가비지 수집을 실행하는지 여부를 지정합니다.

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent>

## <a name="syntax"></a>구문

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|`enabled`|필수 특성입니다.<br /><br />런타임이 동시에 가비지 컬렉션을 실행하는지 여부를 지정합니다.|

#### <a name="enabled-attribute"></a>enabled 특성

|값|설명|
|-----------|-----------------|
|`false`|가비지 수집을 동시에 실행 하지 않습니다.|
|`true`|동시에 가비지 컬렉션을 실행합니다. 기본값입니다.|

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|`configuration`|공용 언어 런타임 및 .NET Framework 애플리케이션에서 사용하는 모든 구성 파일의 루트 요소입니다.|
|`runtime`|어셈블리 바인딩 및 가비지 컬렉션에 대한 정보를 포함합니다.|

## <a name="remarks"></a>설명

.NET Framework 4 이전에는 워크스테이션 가비지 수집에서 별도 스레드의 백그라운드에서 가비지 수집을 수행 하는 동시 가비지 수집을 지원 했습니다. .NET Framework 4에서는 동시 가비지 수집이 백그라운드 GC로 대체 되었으며,이는 별도의 스레드에서 백그라운드에서 가비지 수집을 수행 하기도 합니다. .NET Framework 4.5부터 백그라운드 수집은 서버 가비지 컬렉션에서 사용할 수 있게 되었습니다. **GcConcurrent** 요소는 런타임이 동시 또는 백그라운드 가비지 수집을 수행 하는지 (사용할 수 있는 경우) 아니면 포그라운드에서 가비지 수집을 수행 하는지 여부를 제어 합니다.

### <a name="to-disable-background-garbage-collection"></a>백그라운드 가비지 수집을 사용 하지 않도록 설정 하려면

> [!WARNING]
> .NET Framework 4부터 동시 가비지 수집이 백그라운드 가비지 수집으로 대체 됩니다. .NET Framework 설명서에서는 *동시* 및 *배경* 이라는 용어를 교대로 사용 합니다. 백그라운드 가비지 수집을 사용 하지 않도록 설정 하려면이 문서에서 설명 하는 대로 **gcConcurrent** 요소를 사용 합니다.

기본적으로 런타임은 대기 시간에 최적화된 동시 또는 백그라운드 가비지 컬렉션을 사용합니다. 사용자 상호 작용이 많이 필요한 애플리케이션인 경우에는 가비지 컬렉션을 수행할 때 애플리케이션의 일시 중지를 최소화하도록 동시 가비지 컬렉션 기능을 사용하는 것이 좋습니다. `enabled` **GcConcurrent** 요소의 특성을로 설정 하면 `false` 런타임에서는 처리량에 최적화 된 비 동시 가비지 수집을 사용 합니다.

다음 구성 파일은 백그라운드 가비지 수집을 사용 하지 않도록 설정 합니다.

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

**GcConcurrentSetting** 설정이 컴퓨터 구성 파일에 있는 경우 모든 .NET Framework 응용 프로그램에 대 한 기본값을 정의 합니다. 컴퓨터 구성 파일 설정은 애플리케이션 구성 파일 설정을 재정의합니다.

동시 및 백그라운드 가비지 수집에 대 한 자세한 내용은 [백그라운드 가비지 수집](../../../../standard/garbage-collection/background-gc.md)을 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 백그라운드 가비지 수집을 사용 하도록 설정 합니다.

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>참고 항목

- [런타임 설정 스키마](index.md)
- [구성 파일 스키마](../index.md)
- [가비지 수집 기본 사항](../../../../standard/garbage-collection/fundamentals.md)
