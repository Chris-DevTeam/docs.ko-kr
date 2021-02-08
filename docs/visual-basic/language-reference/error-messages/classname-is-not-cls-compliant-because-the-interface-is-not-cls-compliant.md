---
description: "BC40029: ' ' <classname> 인터페이스가 cls 규격이 아니므로이에 대 한 자세한 정보: ' '은 (는) cls 규격이 아닙니다. <interfacename>"
title: "'<classname>' 인터페이스가 CLS 규격이 아니므로 이 인터페이스에서 상속된 '<interfacename>'은(는) CLS 규격이 아닙니다."
ms.date: 07/20/2015
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
ms.openlocfilehash: 28264dd602bd20a6b33bebd965982ca12d402d01
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796772"
---
# <a name="bc40029-classname-is-not-cls-compliant-because-the-interface-interfacename-it-implements-is-not-cls-compliant"></a>BC40029: ' ' 인터페이스가 CLS 규격이 아니므로이 인터페이스에서 구현 하는 ' ' \<classname> 인터페이스가 cls 규격이 아닙니다. \<interfacename>

클래스 또는 인터페이스가 `<CLSCompliant(True)>` 로 표시 또는 표시되지 않은 형식을 구현하거나 해당 형식에서 파생될 때 `<CLSCompliant(False)>` 로 표시되었습니다.

 클래스 또는 인터페이스가 [언어 독립성 및 CLS (Language-Independent 구성 요소](../../../standard/language-independence-and-language-independent-components.md) )를 준수 하도록 하려면 전체 상속 계층이 규정을 준수 해야 합니다. 즉, 직접이든 간접이든 상속하는 모든 형식이 규격을 준수해야 한다는 의미입니다. 마찬가지로 클래스가 하나 이상의 인터페이스를 구현하는 경우 해당 상속 계층 전체가 모두 규격을 준수해야 합니다.

 <xref:System.CLSCompliantAttribute> 를 프로그래밍 요소에 적용하는 경우 특성의 `isCompliant` 매개 변수를 `True` 또는 `False` 로 설정하여 준수 여부를 나타냅니다. 이 매개 변수에는 기본값이 없으며 값을 제공해야 합니다.

 요소에 <xref:System.CLSCompliantAttribute> 를 적용하지 않으면 비규격인 것으로 간주됩니다.

 이 메시지는 기본적으로 경고입니다. 경고를 숨기거나 오류로 처리하는 방법에 대한 자세한 내용은 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)을 참조하세요.

 **오류 ID:** BC40029

## <a name="to-correct-this-error"></a>이 오류를 해결하려면

- CLS 규격이 필요하면 다른 상속 계층 구조에서 이 형식을 정의합니다.

- 이 형식이 현재 상속 계층 구조 또는 구현 체계에 유지되어야 하는 경우 해당 정의에서 <xref:System.CLSCompliantAttribute> 를 제거하거나 `<CLSCompliant(False)>`로 표시합니다.
