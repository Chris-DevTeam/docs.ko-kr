---
description: "자세한 정보: ' Dir ' 함수는 먼저 ' PathName ' 인수를 사용 하 여 호출 해야 합니다."
title: "'Dir' 함수는 처음에 'Pathname' 인수를 사용하여 호출해야 합니다."
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 076828978b27911a97a4767cde1b1d7b04317a31
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100479974"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a>'Dir' 함수는 처음에 'Pathname' 인수를 사용하여 호출해야 합니다.

함수에 대 한 초기 호출에는 `Dir` 인수가 포함 되지 않습니다 `PathName` . 에 대 한 첫 번째 호출에 `Dir` 는를 포함 해야 `PathName` 하지만에 대 한 후속 호출에서는 `Dir` 다음 항목을 검색 하기 위한 매개 변수를 포함할 필요가 없습니다.

## <a name="to-correct-this-error"></a>이 오류를 해결하려면

- `PathName`함수 호출에 인수를 제공 합니다.

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
