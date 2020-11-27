---
title: ClaimSet에서 클레임 찾기
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], finding in a claimset
- claims [WCF]
ms.assetid: a76ce107-aeb3-47d0-bfa9-134c53664e20
ms.openlocfilehash: c43a47b32a2a3c15d1a51b8b6931ebb021722a64
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268458"
---
# <a name="finding-claims-in-a-claimset"></a>ClaimSet에서 클레임 찾기

<xref:System.IdentityModel.Claims.ClaimSet>클레임 기반 권한 부여를 사용 하는 경우 특정 유형의 클레임에 대 한의 콘텐츠를 검사 하는 것은 일반적인 작업입니다. <xref:System.IdentityModel.Claims.ClaimSet>특정 클레임이 있는지 확인 하려면 메서드를 사용 합니다 <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> . 이 메서드가 <xref:System.IdentityModel.Claims.ClaimSet>을 직접 반복하는 것보다 더 성능이 좋습니다. 다음은 이렇게 사용하는 경우의 예입니다. `claimType` 및 `claimRight` 매개 변수는 `null`일 수 있습니다. 이 경우 매개 변수에서는 모든 클레임 형식과 클레임 권한을 일치시킵니다.  
  
## <a name="example"></a>예제  

 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a>참고 항목

- [ID 모델을 사용하여 클레임 및 권한 부여 관리](managing-claims-and-authorization-with-the-identity-model.md)
