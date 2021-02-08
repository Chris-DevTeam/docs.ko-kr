---
description: '자세한 정보: Visual Basic의 오류 메시지'
title: Visual Basic 오류 메시지
titleSuffix: ''
ms.date: 10/13/2020
helpviewer_keywords:
- errors [Visual Basic]
- error messages
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
ms.openlocfilehash: 28e59a47c47ff7905dfec93b057f7cb534842b91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796069"
---
# <a name="error-messages-in-visual-basic"></a>Visual Basic의 오류 메시지

Visual Basic 응용 프로그램을 컴파일하거나 실행할 때 다음과 같은 유형의 오류가 발생할 수 있습니다.

- 응용 프로그램을 컴파일할 때 발생 하는 컴파일 타임 오류입니다.

- 응용 프로그램이 실행 중일 때 발생 하는 런타임 오류입니다.

특정 오류를 해결하는 방법에 대한 자세한 내용은 [Visual Basic 프로그래머를 위한 추가 리소스](../../getting-started/additional-resources.md)를 참조하세요.

## <a name="run-time-errors"></a>런타임 오류

Visual Basic 응용 프로그램이 시스템에서 실행할 수 없는 작업을 수행 하려고 하면 런타임 오류가 발생 하 고 Visual Basic에서 개체를 throw <xref:System.Exception> 합니다. `Exception`문을 사용 하 여 개체를 비롯 한 모든 데이터 형식의 사용자 지정 오류를 생성할 수 Visual Basic `Throw` . 애플리케이션은 catch한 예외의 오류 번호 및 메시지를 표시하여 오류를 식별할 수 있습니다. 오류가 catch되지 않으면 애플리케이션이 종료됩니다.

코드는 런타임 오류를 트래핑하고 검사할 수 있습니다. 오류를 생성하는 코드를 `Try` 블록에 포함할 경우 일치 하는 `Catch` 블록 내에서 throw된 오류를 catch할 수 있습니다. 런타임 시 오류를 트래핑하고 코드에 응답하는 방법에 대한 자세한 내용은 [Try...Catch...Finally 문](../statements/try-catch-finally-statement.md)을 참조하세요.

## <a name="compile-time-errors"></a>컴파일 타임 오류

Visual Basic 컴파일러를 사용하는 동안 코드에서 문제가 발생하는 경우 컴파일 타임 오류가 발생합니다. Visual Studio 코드 편집기에서 코드 줄 아래에 물결선이 표시 되기 때문에 오류가 발생 한 코드 줄을 쉽게 식별할 수 있습니다. 물결 무늬 밑줄을 가리키거나 **오류 목록** 을 열어도 오류 메시지가 표시됩니다. 오류 목록을 열면 다른 메시지도 볼 수 있습니다.

식별자에 물결선 밑줄이 있고 가장 오른쪽 문자 아래에 짧은 밑줄이 표시 되는 경우 클래스, 생성자, 메서드, 속성, 필드 또는 열거형에 대 한 스텁을 생성할 수 있습니다. 자세한 내용은 관례 [에서 생성 (Visual Studio)](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage)을 참조 하세요.

Visual Basic 컴파일러에서 경고를 확인하면 버그 수를 줄이고 코드를 더 빠르게 실행할 수 있습니다. 이러한 경고는 애플리케이션이 실행될 때 오류를 유발할 수 있는 코드를 식별합니다. 예를 들어 컴파일러에서는 사용자가 할당되지 않은 개체 변수의 멤버를 호출하거나, 반환 값을 설정하지 않고 함수에서 반환되거나, 예외를 catch하기 위한 논리에서 오류가 있는 `Try` 블록을 실행하려고 시도할 경우 경고합니다. 경고를 켜고 끄는 방법을 비롯하여 경고에 대한 자세한 내용은 [Visual Basic에서 경고 구성](/visualstudio/ide/configuring-warnings-in-visual-basic)을 참조하세요.
