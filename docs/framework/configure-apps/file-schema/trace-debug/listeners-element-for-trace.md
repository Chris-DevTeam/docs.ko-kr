---
description: '에 대 한 자세한 정보: <listeners> 요소 <trace>'
title: <trace>에 대한 <listeners> 요소
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: 25f6d4b49eeb57b25b4afbbdfdba484d6d7eea3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639629"
---
# <a name="listeners-element-for-trace"></a>\<trace>에 대한 \<listeners> 요소

메시지를 수집, 저장 및 라우팅하는 수신기를 지정 합니다. 수신기는 추적 출력을 적절 한 대상으로 보냅니다.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**

## <a name="syntax"></a>구문  
  
```xml  
<listeners>
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  

 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  

 없음  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-trace.md)|`Listeners` 컬렉션에 수신기를 추가합니다.|  
|[\<clear>](clear-element-for-listeners-for-trace.md)|추적의 `Listeners` 컬렉션을 지웁니다.|  
|[\<remove>](remove-element-for-listeners-for-trace.md)|컬렉션에서 수신기를 제거 합니다 `Listeners` .|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|`configuration`|공용 언어 런타임 및 .NET Framework 애플리케이션에서 사용하는 모든 구성 파일의 루트 요소입니다.|  
|`system.diagnostics`|ASP.NET 구성 섹션의 루트 요소를 지정합니다.|  
|`trace`|추적 메시지를 수집하고 저장하고 라우팅하는 수신기가 포함되어 있습니다.|  
  
## <a name="remarks"></a>설명  

 <xref:System.Diagnostics.Debug>및 <xref:System.Diagnostics.Trace> 클래스는 동일한 **Listeners** 컬렉션을 공유 합니다. 이러한 클래스 중 하나에서 컬렉션에 수신기 개체를 추가 하는 경우 다른 클래스는 동일한 수신기를 사용 합니다. .NET Framework와 함께 제공 되는 수신기 클래스는 클래스에서 파생 <xref:System.Diagnostics.TraceListener> 됩니다.  
  
## <a name="configuration-file"></a>구성 파일  

 이 요소는 컴퓨터 구성 파일 (Machine.config) 및 응용 프로그램 구성 파일에서 사용할 수 있습니다.  
  
## <a name="example"></a>예제  

 다음 예제에서는 요소를 사용 하 여 수신기 **\<listeners>** `MyListener` 및 수신기 `MyEventListener` 컬렉션에  를 추가 하는 방법을 보여 줍니다. `MyListener` 이라는 파일을 만들고 `MyListener.log` 출력을 파일에 씁니다. `MyEventListener` 이벤트 로그에 항목을 만듭니다.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"
          type="System.Diagnostics.TextWriterTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>참고 항목

- <xref:System.Diagnostics.TraceListener>
- [추적 및 디버그 설정 스키마](index.md)
