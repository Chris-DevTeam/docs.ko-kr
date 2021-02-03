---
description: '#pragma warning - C# 참조'
title: '#pragma warning - C# 참조'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 16582a74bd34f2c0d89950280f1d5fde25435eea
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99215994"
---
# <a name="pragma-warning-c-reference"></a>#pragma warning(C# 참조)

`#pragma warning`은 특정 경고를 사용하거나 사용하지 않도록 설정합니다.

## <a name="syntax"></a>구문

```csharp
#pragma warning disable warning-list
#pragma warning restore warning-list
```

## <a name="parameters"></a>매개 변수

 `warning-list` 쉼표로 구분된 경고 번호 목록입니다. "CS" 접두사는 선택 사항입니다.

 경고 번호를 지정하지 않은 경우 `disable`은 모든 경고를 사용하지 않도록 설정하고 `restore`는 모든 경고를 사용하도록 설정합니다.

> [!NOTE]
> Visual Studio에서 경고 번호를 찾으려면 프로젝트를 빌드하고 **출력** 창에서 경고 번호를 찾습니다.

## <a name="example"></a>예제

```csharp
// pragma_warning.cs
using System;

#pragma warning disable 414, CS3021
[CLSCompliant(false)]
public class C
{
    int i = 1;
    static void Main()
    {
    }
}
#pragma warning restore CS3021
[CLSCompliant(false)]  // CS3021
public class D
{
    int i = 1;
    public static void F()
    {
    }
}
```

## <a name="see-also"></a>참고 항목

- [C# 참조](../index.md)
- [C# 프로그래밍 가이드](../../programming-guide/index.md)
- [C# 전처리기 지시문](./index.md)
- [C# 컴파일러 오류](../compiler-messages/index.md)
- [코드 분석 경고를 표시하지 않는 방법](../../../fundamentals/code-analysis/suppress-warnings.md)
