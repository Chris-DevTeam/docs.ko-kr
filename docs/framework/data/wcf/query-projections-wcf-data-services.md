---
description: '자세한 정보: 쿼리 프로젝션 (WCF Data Services)'
title: 쿼리 프로젝션(WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: a09f4985-9f0d-48c8-b183-83d67a3dfe5f
ms.openlocfilehash: 35427a4bc74691f366711c30cfa7af23de1caa35
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794964"
---
# <a name="query-projections-wcf-data-services"></a>쿼리 프로젝션(WCF Data Services)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

프로젝션은 엔터티의 특정 속성만 응답에서 반환 되도록 지정 하 여 쿼리에서 반환 되는 피드의 데이터 양을 줄이도록 OData (Open Data Protocol)의 메커니즘을 제공 합니다. 자세한 내용은 섹션 4.8을 참조 하세요. [URI 규칙 (OData 버전 2.0)](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/)에서 시스템 쿼리 옵션 ($select)을 선택 합니다.

이 항목에서는 쿼리 프로젝션을 정의하는 방법, 엔터티 및 비 엔터티 형식에 대한 요구 사항, 프로젝션된 결과 업데이트 및 프로젝션된 형식 만들기에 대해 설명하고 몇 가지 프로젝션 고려 사항을 제시합니다.

## <a name="defining-a-query-projection"></a>쿼리 프로젝션 정의

`$select`URI에서 쿼리 옵션을 사용 하거나 LINQ 쿼리에서 [select](../../../csharp/language-reference/keywords/select-clause.md) 절 (Visual Basic에서[선택](../../../visual-basic/language-reference/queries/select-clause.md) )을 사용 하 여 쿼리에 프로젝션 절을 추가할 수 있습니다. 반환된 엔터티 데이터는 클라이언트에서 엔터티 형식이나 비 엔터티 형식으로 프로젝션될 수 있습니다. 이 항목의 예제에서는 LINQ 쿼리에서 `select` 절을 사용하는 방법을 보여 줍니다.

> [!IMPORTANT]
> 프로젝션된 형식을 업데이트한 내용을 저장할 때 데이터 서비스에서 데이터가 손실될 수 있습니다. 자세한 내용은 [프로젝션 고려 사항](#considerations)을 참조 하세요.

## <a name="requirements-for-entity-and-non-entity-types"></a>엔터티 및 비 엔터티 형식에 대한 요구 사항

엔터티 형식에는 엔터티 키를 구성하는 하나 이상의 ID 속성이 있어야 합니다. 엔터티 형식은 클라이언트에서 다음 중 한 가지 방법으로 정의됩니다.

- <xref:System.Data.Services.Common.DataServiceKeyAttribute> 또는 <xref:System.Data.Services.Common.DataServiceEntityAttribute>를 형식에 적용하여

- 형식에 `ID`라는 속성이 있는 경우

- 형식에 형식이 인 속성이 있는 경우  `ID` . 여기서 *type* 은 형식의 이름입니다.

기본적으로 쿼리 결과를 클라이언트에서 정의된 형식으로 프로젝션하는 경우 프로젝션에서 요청된 속성이 클라이언트 형식에 있어야 합니다. 그러나 `true`의 <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> 속성에 <xref:System.Data.Services.Client.DataServiceContext> 값을 지정하는 경우에는 프로젝션에 지정된 속성이 클라이언트 형식에 있을 필요가 없습니다.

### <a name="making-updates-to-projected-results"></a>프로젝션된 결과 업데이트

쿼리 결과를 클라이언트에서 엔터티 형식으로 프로젝션하는 경우 <xref:System.Data.Services.Client.DataServiceContext>는 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 메서드를 호출할 때 데이터 서비스로 다시 전송되는 업데이트를 통해 이러한 개체를 추적할 수 있습니다. 그러나 클라이언트에서 비 엔터티 형식으로 프로젝션된 데이터를 업데이트한 내용은 데이터 서비스로 다시 전송될 수 없습니다. 이는 엔터티 인스턴스를 식별하는 키가 없는 경우 데이터 서비스가 데이터 소스에서 올바른 엔터티를 업데이트할 수 없기 때문입니다. 비 엔터티 형식은 <xref:System.Data.Services.Client.DataServiceContext>에 연결되지 않습니다.

데이터 서비스에 정의된 엔터티 형식의 속성 중 하나 이상이 엔터티가 프로젝션되는 클라이언트 형식에 없는 경우 새 엔터티를 삽입할 때 이러한 없는 속성이 포함되지 않습니다. 이 경우 기존 엔터티에 대 한 업데이트에 **도** 이러한 누락 된 속성이 포함 되지 않습니다. 이러한 속성의 값이 있는 경우 업데이트를 수행하면 속성의 값이 데이터 소스에 정의된 속성의 기본값으로 다시 설정됩니다.

### <a name="creating-projected-types"></a>프로젝션된 형식 만들기

다음 예제에서는 `Customers` 형식의 주소 관련 속성을 새 `CustomerAddress` 형식으로 프로젝션하는 익명 LINQ 쿼리를 사용합니다. 새 형식은 클라이언트에서 정의되며 엔터티 형식으로 특성이 지정됩니다.

[!code-csharp[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddressspecific)]
[!code-vb[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddressspecific)]

이 예제에서 개체 이니셜라이저 패턴은 생성자를 호출하는 대신 `CustomerAddress` 형식의 새 인스턴스를 만드는 데 사용됩니다. 생성자는 엔터티 형식으로 프로젝션할 때 지원되지 않지만 비 엔터티 및 익명 형식으로 프로젝션할 때 사용할 수 있습니다. `CustomerAddress`가 엔터티 형식이기 때문에 변경 후 데이터 서비스로 다시 전송될 수 있습니다.

또한 `Customer` 형식의 데이터가 익명 형식 대신 `CustomerAddress` 엔터티 형식의 인스턴스로 프로젝션됩니다. 익명 형식으로 프로젝션할 수 있지만 익명 형식이 비 엔터티 형식으로 처리되기 때문에 데이터가 읽기 전용입니다.

<xref:System.Data.Services.Client.MergeOption>의 <xref:System.Data.Services.Client.DataServiceContext> 설정은 쿼리 프로젝션 중에 ID 확인에 사용됩니다. 이는 `Customer` 형식의 인스턴스가 이미 <xref:System.Data.Services.Client.DataServiceContext>에 있는 경우 ID가 동일한 `CustomerAddress`의 인스턴스가 <xref:System.Data.Services.Client.MergeOption>에 의해 설정된 ID 확인 규칙을 따름을 의미합니다.

다음에서는 결과를 엔터티 및 비 엔터티 형식으로 프로젝션 하는 경우의 동작에 대해 설명 합니다.

**이니셜라이저를 사용 하 여 새 프로젝션 인스턴스 만들기**

- 예제:

   [!code-csharp[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithinitializer)]
   [!code-vb[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithinitializer)]

- 엔터티 형식: 지원 됨

- 비 엔터티 형식: 지원 됨

**생성자를 사용 하 여 새 프로젝션 인스턴스 만들기**

- 예제:

   [!code-csharp[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithconstructor)]
   [!code-vb[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithconstructor)]

- 엔터티 형식: <xref:System.NotSupportedException> 이 발생 합니다.

- 비 엔터티 형식: 지원 됨

**프로젝션을 사용 하 여 속성 값 변환**

- 예제:

   [!code-csharp[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithtransform)]
   [!code-vb[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithtransform)]

- 엔터티 형식: 혼동을 야기 하 고 잠재적으로 다른 엔터티에 속한 데이터 소스의 데이터를 덮어쓸 수 있기 때문에이 변환은 엔터티 형식에 대해 지원 되지 않습니다. <xref:System.NotSupportedException>이 발생함

- 비 엔터티 형식: 지원 됨

<a name="considerations"></a>

## <a name="projection-considerations"></a>프로젝션 고려 사항

쿼리 프로젝션을 정의할 때 다음 사항을 추가로 고려해야 합니다.

- Atom 형식에 대한 사용자 지정 피드를 정의하는 경우 사용자 지정 매핑이 정의되어 있는 모든 엔터티 속성이 프로젝션에 포함되도록 해야 합니다. 매핑된 엔터티 속성이 프로젝션에 포함되지 않는 경우 데이터가 손실될 수 있습니다. 자세한 내용은 [피드 사용자 지정](feed-customization-wcf-data-services.md)을 참조 하세요.

- 데이터 서비스의 데이터 모델에서 엔터티의 모든 속성을 포함하지 않는 프로젝션된 형식에 삽입이 수행되는 경우 클라이언트에서 프로젝션에 포함되지 않은 속성이 기본값으로 설정됩니다.

- 데이터 서비스의 데이터 모델에서 엔터티의 모든 속성을 포함하지 않는 프로젝션된 형식을 업데이트하는 경우 클라이언트에서 프로젝션에 포함되지 않은 기존 값이 초기화되지 않은 기본값으로 덮어쓰입니다.

- 프로젝션에 복합 속성이 포함된 경우 전체 복합 개체가 반환되어야 합니다.

- 프로젝션에 탐색 속성이 포함된 경우 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 메서드를 호출하지 않고도 관련 개체가 암시적으로 로드됩니다. <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 메서드는 프로젝션된 쿼리에서 사용할 수 없습니다.

- 클라이언트의 쿼리 프로젝션 쿼리는 요청 URI에서 `$select` 쿼리 옵션을 사용하도록 변환됩니다. 프로젝션을 포함 하는 쿼리가 쿼리 옵션을 지원 하지 않는 이전 버전의 WCF Data Services에 대해 실행 되는 경우 `$select` 오류가 반환 됩니다. 이러한 문제는 데이터 서비스에 대한 <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A>의 <xref:System.Data.Services.DataServiceBehavior>이 <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1> 값으로 설정된 경우에도 발생할 수 있습니다. 자세한 내용은 [데이터 서비스 버전 관리](data-service-versioning-wcf-data-services.md)를 참조 하세요.

자세한 내용은 [방법: 쿼리 결과 프로젝트](how-to-project-query-results-wcf-data-services.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

- [데이터 서비스 쿼리](querying-the-data-service-wcf-data-services.md)
