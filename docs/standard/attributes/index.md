---
title: 특성을 사용하여 메타데이터 확장
description: .NET에서 특성을 사용하여 메타데이터를 확장하는 방법을 알아보세요. 특성은 형식, 필드 등의 프로그래밍 요소에 주석을 추가하기 위한, 키워드 방식의 설명적 선언입니다.
ms.date: 10/14/2020
helpviewer_keywords:
- metadata, extending
- attributes [.NET], metadata
- elements [.NET], attributes
- common language runtime, attributes
- annotating programming elements
- keyword-like descriptive declarations
- runtime, attributes
- extending metadata
ms.assetid: 30386922-1e00-4602-9ebf-526b271a8b87
ms.openlocfilehash: e41299b83ae451117ab6829eee928b0d2306be19
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829078"
---
# <a name="extend-metadata-using-attributes"></a>특성을 사용하여 메타데이터 확장

공용 언어 런타임에서는 형식, 필드, 메서드 및 속성과 같은 프로그래밍 요소에 주석을 달기 위해 특성이라는 키워드 방식의 설명적 선언을 추가할 수 있습니다. 런타임용으로 코드를 컴파일하는 경우 MSIL(Microsoft Intermediate Language)로 변환되고 컴파일러에서 생성된 메타데이터와 함께 PE(이식 가능한 실행) 파일 내에 배치됩니다. 특성을 사용하여 런타임 리플렉션 서비스를 통해 추출할 수 있는 메타데이터에 추가 설명 정보를 배치할 수 있습니다. <xref:System.Attribute?displayProperty=nameWithType>에서 파생되는 특수 클래스 인스턴스를 선언하면 컴파일러에서 특성을 만듭니다.

.NET은 다양한 이유로, 그리고 많은 문제를 해결하기 위해 특성을 사용합니다. 특성은 데이터를 직렬화하고, 보안을 적용하는 데 사용되는 특징을 지정하고, 코드를 쉽게 디버그할 수 있도록 JIT(Just-In-Time) 컴파일러에 의한 최적화를 제한하는 방법을 설명합니다. 또한 특성은 폼을 개발하는 동안 파일 이름 또는 코드 작성자를 기록하거나 컨트롤과 멤버의 표시 유형을 제어할 수 있습니다.

## <a name="related-articles"></a>관련 문서

|제목|설명|
|-----------|-----------------|
|[특성 적용](applying-attributes.md)|코드의 요소에 특성을 적용하는 방법을 설명합니다.|
|[사용자 지정 특성 작성](writing-custom-attributes.md)|사용자 지정 특성 클래스를 디자인하는 방법을 설명합니다.|
|[특성에 저장된 정보 검색](retrieving-information-stored-in-attributes.md)|실행 컨텍스트에 로드된 코드에 대한 사용자 지정 특성을 검색하는 방법을 설명합니다.|
|[메타데이터 및 자동 기술 구성 요소](../metadata-and-self-describing-components.md)|메타데이터를 개괄적으로 설명하고 .NET PE(이식 가능한 실행) 파일에서 구현하는 방법을 설명합니다.|
|[방법: 리플렉션 전용 컨텍스트에 어셈블리 로드](../../framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|리플렉션 전용 컨텍스트에서 사용자 지정 특성 정보를 검색하는 방법을 설명합니다.|

## <a name="reference"></a>참고

- <xref:System.Attribute?displayProperty=nameWithType>
