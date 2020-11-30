---
title: <schemaImporterExtensions>에 대한 <add> 요소
description: <add> 요소는 XmlSchemaImporter 클래스가 XSD 형식을 .NET 형식에 매핑하기 위해 사용하는 형식을 추가합니다.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: b8a0775e9d33d59606b1150aa9a1b3b1026d4b0b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726446"
---
# <a name="add-element-for-schemaimporterextensions"></a>\<schemaImporterExtensions>에 대한 \<add> 요소

<xref:System.Xml.Serialization.XmlSchemaImporter>에서 XSD 형식을 .NET 형식에 매핑하는 데 사용하는 형식을 추가합니다. 구성 파일에 대한 자세한 내용은 [구성 파일 스키마](../../framework/configure-apps/file-schema/index.md)를 참조하세요.  
  
\<configuration>  
\<system.xml.serialization>  
\<schemaImporterExtensions>  
\<add>  
  
## <a name="syntax"></a>구문  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  

 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|**name**|인스턴스를 찾는 데 사용되는 단순한 이름입니다.|  
|**type**|필수 요소. 추가할 스키마 확장 클래스를 지정합니다. **type** 특성 값은 한 줄로 표시되어야 하며 정규화된 형식 이름을 포함해야 합니다. GAC(전역 어셈블리 캐시)에 추가되는 어셈블리에는 서명된 어셈블리의 버전, 문화권 및 공개 키 토큰도 포함되어 있어야 합니다.|  
  
### <a name="child-elements"></a>자식 요소  

 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|\<schemaImporterExtensions>|<xref:System.Xml.Serialization.XmlSchemaImporter>에서 사용하는 형식을 포함합니다.|  
  
## <a name="example"></a>예제  

 다음 코드 예제에서는 XmlSchemaImporter가 형식을 매핑할 때 사용할 수 있는 확장 형식을 추가합니다.  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <schemaImporterExtensions>  
       <add name="contoso" type="System.Web.Mobile.MobileCapabilities,
       System.Web.Mobile, Version=2.0.0.0, Culture=neutral,
       PublicKeyToken=b03f5f7f11d50a3a" />
    </schemaImporterExtensions>  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a>참조

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [\<system.xml.serialization> 요소](system-xml-serialization-element.md)
- [\<schemaImporterExtensions> 요소](schemaimporterextensions-element.md)
