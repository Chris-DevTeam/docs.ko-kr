---
description: '자세한 정보: 요소 텍스트 유추'
title: 요소 텍스트 유추
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: 5d0d9b1b3bb6164cd3cf26b429a4c7d658ee4128
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652213"
---
# <a name="inferring-element-text"></a>요소 텍스트 유추

요소가 텍스트를 포함 하 고 테이블 (특성 또는 반복 요소가 포함 된 요소)로 유추 될 자식 요소가 없는 경우 **TableName_Text** 이름이 인 새 열이 요소에 대해 유추 되는 테이블에 추가 됩니다. 이 요소에 포함된 텍스트는 테이블의 행에 추가되어 새 열에 저장됩니다. 새 열의 **ColumnMapping** 속성은 **mappingtype.attribute** 로 설정 됩니다.  
  
 예를 들어, 다음과 같은 XML을 가정해 봅시다.  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 유추 프로세스에서는 두 개의 열 ( **attr1** 및 **Element1_Text**)이 포함 된 **Element1** 라는 테이블을 생성 합니다. **Attr1** 열의 **ColumnMapping** 속성은 **mappingtype.attribute** 로 설정 됩니다. **Element1_Text** 열의 **ColumnMapping** 속성은 **mappingtype.attribute** 로 설정 됩니다.  
  
 **데이터 집합:** DocumentElement  
  
 **테이블:** Element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|value1|Text1|  
  
 요소에 텍스트뿐만 아니라 텍스트가 포함된 자식 요소도 있는 경우에는 해당 요소에 포함된 텍스트를 저장할 열이 테이블에 추가되지 않습니다. 따라서 이 요소에 포함된 텍스트는 무시되지만 자식 요소에 있는 텍스트는 해당 테이블의 행에 저장됩니다. 예를 들어, 다음과 같은 XML을 가정해 봅시다.  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 유추 프로세스는 **ChildElement1** 라는 열이 있는 **Element1** 이라는 테이블을 생성 합니다. **ChildElement1** 요소의 텍스트는 테이블의 행에 포함 됩니다. 다른 텍스트는 무시됩니다. **ChildElement1** 열의 **ColumnMapping** 속성은 **mappingtype.attribute** 로 설정 됩니다.  
  
 **데이터 집합:** DocumentElement  
  
 **테이블:** Element1  
  
|ChildElement1|  
|-------------------|  
|Text2|  
  
## <a name="see-also"></a>참고 항목

- [XML에서 데이터 세트 관계형 구조 유추](inferring-dataset-relational-structure-from-xml.md)
- [XML에서 데이터 세트 로드](loading-a-dataset-from-xml.md)
- [XML에서 데이터 세트 스키마 정보 로드](loading-dataset-schema-information-from-xml.md)
- [데이터 세트에서 XML 사용](using-xml-in-a-dataset.md)
- [DataSets, DataTables 및 DataViews](index.md)
- [ADO.NET 개요](../ado-net-overview.md)
