---
description: '다음에 대 한 자세한 정보: System.web 메서드'
title: System.Math 메서드
ms.date: 03/30/2017
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
ms.openlocfilehash: e97e0a16b6eafdb57f4aaf72d62788e6657afbdc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681346"
---
# <a name="systemmath-methods"></a>System.Math 메서드

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]에서는 다음 <xref:System.Math> 메서드를 지원하지 않습니다.  
  
- <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a>.NET과의 차이점  

 .NET Framework의 반올림 구문은 SQL Server와 다릅니다. <xref:System.Math.Round%2A>.NET Framework의 메서드는 *은행원의 반올림* 을 수행 합니다. 여기서 0.5로 끝나는 숫자는 다음으로 큰 숫자가 아닌 가장 가까운 짝수로 반올림 됩니다. 예를 들어 2.5는 2가 되고 3.5는 4가 됩니다. 이 방법은 많은 데이터 트랜잭션에서 값이 높아질수록 발생할 수 있는 체계적 오차를 방지할 수 있습니다.  
  
 SQL에서 `ROUND` 함수는 항상 0 이상의 정수 값으로 반올림됩니다. 따라서 2.5의 경우 .NET Framework에서는 2가 되는데 반해 SQL에서는 3이 됩니다.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]은 SQL `ROUND` 구문을 따르며 은행원의 반올림을 사용하지 않습니다.  
  
## <a name="see-also"></a>참고 항목

- [데이터 형식 및 함수](data-types-and-functions.md)
