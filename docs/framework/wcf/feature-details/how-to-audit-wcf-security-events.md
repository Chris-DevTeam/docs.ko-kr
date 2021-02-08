---
description: '자세한 정보: 방법: 보안 이벤트 감사 Windows Communication Foundation'
title: '방법: Windows Communication Foundation 보안 이벤트 감사'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
ms.openlocfilehash: b9cd258f51dbc726108fef0bbf173c7ee26c1d0f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780208"
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a>방법: Windows Communication Foundation 보안 이벤트 감사

WCF (Windows Communication Foundation)를 사용 하면 windows 이벤트 뷰어를 사용 하 여 볼 수 있는 Windows 이벤트 로그에 보안 이벤트를 기록할 수 있습니다. 이 항목에서는 보안 이벤트를 기록하도록 애플리케이션을 설정하는 방법에 대해 설명합니다. WCF 감사에 대 한 자세한 내용은 [감사](auditing-security-events.md)를 참조 하세요.  
  
### <a name="to-audit-security-events-in-code"></a>코드에서 보안 이벤트를 감사하려면  
  
1. 감사 로그 위치를 지정합니다. 이렇게 하려면 다음 코드와 같이 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> 클래스의 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> 속성을 <xref:System.ServiceModel.AuditLogLocation> 열거형 값 중 하나로 설정합니다.  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     열거형에는 <xref:System.ServiceModel.AuditLogLocation> `Application` , 또는의 세 가지 값이 `Security` `Default` 있습니다. 이 값은 이벤트 뷰어에서 볼 수 있는 로그(보안 로그 또는 애플리케이션 로그) 중 하나를 지정합니다. `Default` 값을 사용하는 경우 실제 로그는 애플리케이션을 실행하는 운영 체제에 따라 달라집니다. 감사를 사용하지만 로그 위치가 지정되지 않은 경우 기본값은 보안 로그에 쓰기를 지원하는 플랫폼의 `Security` 로그입니다. 그렇지 않으면 `Application` 로그에 씁니다. Windows Server 2003 및 Windows Vista 에서만 기본적으로 보안 로그에 쓰기를 지원 합니다.  
  
2. 감사할 이벤트 형식을 설정합니다. 서비스 수준 이벤트나 메시지 수준 권한 부여 이벤트를 동시에 감사할 수 있습니다. 이렇게 하려면 다음 코드와 같이 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> 속성이나 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> 속성을 <xref:System.ServiceModel.AuditLevel> 열거형 값 중 하나로 설정합니다.  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3. 로그 감사 이벤트에 대해 오류를 애플리케이션에 노출할지 또는 표시하지 않을지 지정합니다. 다음 코드와 같이 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> 속성을 `true` 또는 `false`로 설정합니다.  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     기본 `SuppressAuditFailure` 속성이 `true`이므로 감사하지 못해도 애플리케이션에 영향을 주지 않습니다. 그러지 않으면 예외가 throw됩니다. 성공한 모든 감사에 대해 자세한 추적이 기록됩니다. 감사하지 못하면 오류 수준에서 추적이 기록됩니다.  
  
4. <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>의 설명에 있는 동작 컬렉션에서 기존 <xref:System.ServiceModel.ServiceHost>를 삭제합니다. 동작 컬렉션은 <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> 컬렉션에서 액세스되는 <xref:System.ServiceModel.ServiceHostBase.Description%2A> 속성으로 액세스됩니다. 다음 코드와 같이 동일한 컬렉션에 새 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>를 추가합니다.  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a>구성에서 감사를 설정하려면  
  
1. 구성에서 감사를 설정 하려면 [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) web.config 파일의 섹션에 요소를 추가 합니다. 그런 다음 [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) , 다음 예제와 같이 요소를 추가 하 고 다양 한 특성을 설정 합니다.  
  
    ```xml  
    <behaviors>  
       <behavior name="myAuditBehavior">  
          <serviceSecurityAudit auditLogLocation="Application"  
                suppressAuditFailure="false"
                serviceAuthorizationAuditLevel="None"
                messageAuthenticationAuditLevel="SuccessOrFailure" />  
          </behavior>  
    </behaviors>  
    ```  
  
2. 다음 예제와 같이 서비스의 동작을 지정해야 합니다.  
  
    ```xml  
    <services>  
        <service type="WCS.Samples.Service.Echo"
        behaviorConfiguration=" myAuditBehavior">  
           <endpoint address=""  
                    binding="wsHttpBinding"  
                    bindingConfiguration="CertificateDefault"
                    contract="WCS.Samples.Service.IEcho" />  
        </service>  
    </services>  
    ```  
  
## <a name="example"></a>예제  

 다음 코드에서는 <xref:System.ServiceModel.ServiceHost> 클래스의 인스턴스를 만들고 동작 컬렉션에 새 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>를 추가합니다.  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a>.NET Framework 보안  

 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> 속성을 `true`로 설정하면 보안 감사 생성 오류가 표시되지 않습니다. `false`로 설정하면 예외가 throw됩니다. 그러나 다음 Windows **로컬 보안 설정** 속성을 사용 하도록 설정 하면 감사 이벤트를 생성 하는 데 실패 하면 Windows가 즉시 종료 됩니다.  
  
 **감사: 보안 감사를 로그할 수 없는 경우 즉시 시스템 종료**  
  
 속성을 설정 하려면 **로컬 보안 설정** 대화 상자를 엽니다. **보안 설정** 에서 **로컬 정책** 을 클릭 합니다. 그런 다음 **보안 옵션** 을 클릭 합니다.  
  
 <xref:System.ServiceModel.AuditLogLocation>속성이로 설정 되 <xref:System.ServiceModel.AuditLogLocation.Security> 고 **감사 개체 액세스가** **로컬 보안 정책** 에 설정 되어 있지 않은 경우 감사 이벤트는 보안 로그에 기록 되지 않습니다. 오류가 반환되지는 않지만 감사 항목이 보안 로그에 기록되지 않습니다.  
  
## <a name="see-also"></a>참고 항목

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [감사](auditing-security-events.md)
