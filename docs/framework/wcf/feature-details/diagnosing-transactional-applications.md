---
title: 트랜잭션 애플리케이션 진단
ms.date: 03/30/2017
ms.assetid: 4a993492-1088-4d10-871b-0c09916af05f
ms.openlocfilehash: 696ebe7249a8388eaaf38a678581e28d472e821a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96290246"
---
# <a name="diagnosing-transactional-applications"></a>트랜잭션 애플리케이션 진단

이 항목에서는 WCF (Windows Communication Foundation) 관리 및 진단 기능을 사용 하 여 트랜잭션 응용 프로그램의 문제를 해결 하는 방법에 대해 설명 합니다.  
  
## <a name="performance-counters"></a>성능 카운터  

 WCF는 트랜잭션 응용 프로그램의 성능을 측정 하는 데 사용할 수 있는 표준 성능 카운터 집합을 제공 합니다. 자세한 내용은 [성능 카운터](../diagnostics/performance-counters/index.md)를 참조하세요.  
  
 성능 카운터는 다음 표의 설명과 같이 서비스, 엔드포인트 및 작업의 세 가지 수준으로 구분됩니다.  
  
### <a name="service-performance-counters"></a>서비스 성능 카운터  
  
|성능 카운터|Description|  
|-------------------------|-----------------|  
|Transactions Flowed|이 서비스에서 작업에 적용된 트랜잭션의 수입니다. 서비스에 전송된 메시지에 트랜잭션이 있을 때마다 이 카운터가 증가합니다.|  
|Transactions Flowed Per Second|이 서비스에서 작업에 적용된 초당 트랜잭션의 수입니다. 서비스에 전송된 메시지에 트랜잭션이 있을 때마다 이 카운터가 증가합니다.|  
|Transacted Operations Committed|이 서비스에 커밋된 결과로 트랜잭션이 완료된 트랜잭션 처리 작업 수행 수입니다. 해당 작업에 대해 수행된 작업이 완전히 커밋됩니다. 작업에서 수행된 작업에 따라 리소스가 업데이트됩니다.|  
|Transacted Operations Committed Per Second|이 서비스에서 커밋된 결과로 트랜잭션이 완료된 초당 트랜잭션 처리 작업 수행 수입니다. 해당 작업에 대해 수행된 작업이 완전히 커밋됩니다. 작업에서 수행된 작업에 따라 리소스가 업데이트됩니다.|  
|Transacted Operations Aborted|이 서비스에서 중단된 결과로 트랜잭션이 완료된 트랜잭션 처리 작업 수행 수입니다. 해당 작업에 대해 수행된 작업이 롤백됩니다. 리소스가 이전 상태로 되돌아갑니다.|  
|Transacted Operations Aborted Per Second|이 서비스에서 중단된 결과로 트랜잭션이 완료된 초당 트랜잭션 처리 작업 수행 수입니다. 해당 작업에 대해 수행된 작업이 롤백됩니다. 리소스가 이전 상태로 되돌아갑니다.|  
|Transacted Operations In Doubt|이 서비스에서 불확실한 상태의 결과로 트랜잭션이 완료된 트랜잭션 처리 작업 수행 수입니다. 불확실한 상태의 결과로 수행된 작업은 결정할 수 없는 상태입니다. 리소스가 보류된 결과를 보관합니다.|  
|Transacted Operations In Doubt Per Second|이 서비스에서 불확실한 상태의 결과로 트랜잭션이 완료된 초당 트랜잭션 처리 작업 수행 수입니다. 불확실한 상태의 결과로 수행된 작업은 결정할 수 없는 상태입니다. 리소스가 보류된 결과를 보관합니다.|  
  
### <a name="endpoint-performance-counters"></a>엔드포인트 성능 카운터  
  
|성능 카운터|Description|  
|-------------------------|-----------------|  
|Transactions Flowed|이 엔드포인트에서 작업에 적용된 트랜잭션의 수입니다. 엔드포인트에 전송된 메시지에 트랜잭션이 있을 때마다 이 카운터가 증가합니다.|  
|Transactions Flowed Per Second|이 엔드포인트에서 작업에 적용된 초당 트랜잭션의 수입니다. 엔드포인트에 전송된 메시지에 트랜잭션이 있을 때마다 이 카운터가 증가합니다.|  
  
### <a name="operation-performance-counters"></a>작업 성능 카운터  
  
|성능 카운터|Description|  
|-------------------------|-----------------|  
|Transactions Flowed|이 엔드포인트에서 작업에 적용된 트랜잭션의 수입니다. 엔드포인트에 전송된 메시지에 트랜잭션이 있을 때마다 이 카운터가 증가합니다.|  
|Transactions Flowed Per Second|이 엔드포인트에서 작업에 적용된 초당 트랜잭션의 수입니다. 엔드포인트에 전송된 메시지에 트랜잭션이 있을 때마다 이 카운터가 증가합니다.|  
  
## <a name="windows-management-instrumentation"></a>Windows Management Instrumentation  

 WCF는 WCF WMI(Windows Management Instrumentation) (WMI) 공급자를 통해 런타임에 서비스의 검사 데이터를 노출 합니다. WMI 데이터에 액세스 하는 방법에 대 한 자세한 내용은 [진단에 WMI(Windows Management Instrumentation) 사용](../diagnostics/wmi/index.md)을 참조 하세요.  
  
 다양한 읽기 전용 WMI 속성이 서비스에 대해 적용된 트랜잭션 설정을 나타냅니다. 다음 표에서는 이러한 모든 설정을 보여 줍니다.  
  
 서비스에서 `ServiceBehaviorAttribute`에는 다음 속성이 있습니다.  
  
|이름|유형|Description|  
|----------|----------|-----------------|  
|ReleaseServiceInstanceOnTransactionComplete|부울|현재 트랜잭션이 완료되면 서비스 개체를 재활용할지 여부를 지정합니다.|  
|TransactionAutoCompleteOnSessionClose|부울|현재 세션이 닫히면 보류 중인 트랜잭션을 완료할지 여부를 지정합니다.|  
|TransactionIsolationLevel|유효한 <xref:System.Transactions.IsolationLevel> 열거형 값이 들어 있는 문자열입니다.|이 서비스가 지원하는 트랜잭션 격리 수준을 지정합니다.|  
|TransactionTimeout|<xref:System.DateTime>|트랜잭션을 완료해야 하는 기간을 지정합니다.|  
  
 `ServiceTimeoutsBehavior`에는 다음 속성이 있습니다.  
  
|이름|유형|Description|  
|----------|----------|-----------------|  
|TransactionTimeout|<xref:System.DateTime>|트랜잭션을 완료해야 하는 기간을 지정합니다.|  
  
 바인딩에서 `TransactionFlowBindingElement`에는 다음 속성이 있습니다.  
  
|이름|유형|Description|  
|----------|----------|-----------------|  
|TransactionProtocol|<xref:System.ServiceModel.TransactionProtocol> 형식에 대해 유효한 값이 들어 있는 문자열입니다.|트랜잭션을 이동하는 데 사용할 트랜잭션 프로토콜을 지정합니다.|  
|TransactionFlow|부울|들어오는 트랜잭션 흐름을 사용할 수 있는지 여부를 지정합니다.|  
  
 작업에서 `OperationBehaviorAttribute`에는 다음 속성이 있습니다.  
  
|이름|유형|Description|  
|----------|----------|-----------------|  
|TransactionAutoComplete|부울|처리되지 않은 예외가 발생하지 않을 때 현재 트랜잭션을 자동으로 커밋할지 여부를 지정합니다.|  
|TransactionScopeRequired|부울|작업에서 트랜잭션이 필요한지 여부를 지정합니다.|  
  
 작업에서 `TransactionFlowAttribute`에는 다음 속성이 있습니다.  
  
|이름|유형|Description|  
|----------|----------|-----------------|  
|TransactionFlowOption|유효한 <xref:System.ServiceModel.TransactionFlowOption> 열거형 값이 들어 있는 문자열입니다.|트랜잭션 이동이 필요한 범위를 지정합니다.|  
  
## <a name="tracing"></a>추적  

 추적을 사용하면 트랜잭션 애플리케이션의 오류를 모니터링하고 분석할 수 있습니다. 다음 방법을 사용하여 추적을 사용할 수 있습니다.  
  
- 표준 WCF 추적  
  
     이 추적 유형은 모든 WCF 응용 프로그램을 추적 하는 것과 같습니다. 자세한 내용은 [Configuring Tracing](../diagnostics/tracing/configuring-tracing.md)을 참조하세요.  
  
- WS-AtomicTransaction 추적  
  
     Ws-atomictransaction [구성 유틸리티 (wsatConfig.exe)](../ws-atomictransaction-configuration-utility-wsatconfig-exe.md)를 사용 하 여 WS-AtomicTransaction 추적을 사용 하도록 설정할 수 있습니다. 이러한 추적을 통해 시스템 내의 트랜잭션 및 참여 상태를 정확하게 판단할 수 있습니다. 또한 내부 서비스 모델 추적을 사용하기 위해 `HKLM\SOFTWARE\Microsoft\WSAT\3.0\ServiceModelDiagnosticTracing` 레지스트리 키를 유효한 <xref:System.Diagnostics.SourceLevels> 열거형 값으로 설정할 수 있습니다. 다른 WCF 응용 프로그램과 동일한 방식으로 메시지 로깅을 사용 하도록 설정할 수 있습니다.  
  
- `System.Transactions` 추적  
  
     OleTransactions 프로토콜을 사용하는 경우 프로토콜 메시지를 추적할 수 없습니다. <xref:System.Transactions> 인프라가 제공하는 추적 지원(OleTransactions 사용)을 통해 사용자는 트랜잭션에 발생된 이벤트를 확인할 수 있습니다. <xref:System.Transactions> 애플리케이션에 대한 추적을 사용하기 위해 다음 코드를 `App.config` 구성 파일에 포함합니다.  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
         <sources>  
            <source name="System.Transactions" switchValue="Verbose, ActivityTracing">  
               <listeners>  
                  <add name="Text"  
                     type="System.Diagnostics.XmlWriterTraceListener"  
                     initializeData="SysTx.log"  
                     traceOutputOptions="Callstack" />  
               </listeners>  
            </source>  
         </sources>  
         <trace autoflush="true" indentsize="4">  
         </trace>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
     또한 WCF는 인프라를 활용 하므로 WCF 추적을 사용 하도록 설정 <xref:System.Transactions> 합니다.  
  
## <a name="see-also"></a>참고 항목

- [관리 및 진단](../diagnostics/index.md)
- [추적 구성](../diagnostics/tracing/configuring-tracing.md)
- [WS-AtomicTransaction 구성 유틸리티(wsatConfig.exe)](../ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
