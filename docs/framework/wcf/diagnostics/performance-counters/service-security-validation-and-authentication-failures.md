---
description: '자세한 정보: 서비스: 보안 유효성 검사 및 인증 실패'
title: '서비스: Security Validation and Authentication Failures'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: 8938c74e706526a02bf2ea5885951d067d6ebae9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759486"
---
# <a name="service-security-validation-and-authentication-failures"></a>서비스: Security Validation and Authentication Failures

카운터 이름: Security Validation and Authentication Failures  
  
## <a name="description"></a>설명  

 이 카운터는 "Security Calls Not Authorized" 카운터로 처리되지 않는 보안 문제 때문에 메시지가 거부될 때마다 증가합니다. 이러한 문제는 다음과 같습니다.  
  
- 클라이언트 토큰을 메시지에서 읽을 수 없습니다.  
  
- 클라이언트 토큰에서 인증에 실패했습니다(예: 잘못된 암호).  
  
- 서명 확인에 실패했습니다(예: 메시지 변조).  
  
- 메시지가 이전 메시지와 중복됩니다. 이러한 현상은 재생 공격 중에 나타날 수 있습니다.  
  
- 해독 오류가 발생했습니다.  
  
- 일부 필수 요소(예: 타임스탬프 또는 암호화된 데이터 블록)가 메시지에 없습니다.  
  
- TLSNEGO/SPNEGO 핸드셰이크 중에 오류가 발생했습니다.
