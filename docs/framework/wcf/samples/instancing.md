---
description: '방법에 대 한 자세한 정보: 인스턴스'
title: 인스턴싱
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, instancing sample
- Instancing Sample [Windows Communication Foundation]
ms.assetid: c290fa54-f6ae-45a1-9186-d9504ebc6ee6
ms.openlocfilehash: 88cff6912e3285370a456d5d8575c995ff15ef57
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726457"
---
# <a name="instancing"></a>인스턴싱

Instancing 샘플에서는 클라이언트 요청에 응답하여 서비스 클래스의 인스턴스가 만들어지는 방법을 제어하는 인스턴스 만들기 동작 설정을 보여 줍니다. 이 샘플은 서비스 계약을 구현 하는 [시작](getting-started-sample.md)을 기반으로 합니다 `ICalculator` . 이 샘플은 `ICalculatorInstance`에서 상속되는 새 계약 `ICalculator`를 정의합니다. `ICalculatorInstance`에 의해 지정된 계약은 서비스 인스턴스의 상태를 검사하기 위한 세 개의 추가 작업을 제공합니다. 인스턴스 만들기 설정을 변경하여 클라이언트를 실행하면 동작의 변화를 확인할 수 있습니다.  
  
 이 샘플에서 클라이언트는 콘솔 애플리케이션(.exe)이고 서비스는 IIS(인터넷 정보 서비스)를 통해 호스트됩니다.  
  
> [!NOTE]
> 이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.  
  
 사용할 수 있는 인스턴스 만들기 모드는 다음과 같습니다.  
  
- <xref:System.ServiceModel.InstanceContextMode.PerCall>: 새 서비스 인스턴스가 각 클라이언트 요청에 대해 만들어집니다.  
  
- <xref:System.ServiceModel.InstanceContextMode.PerSession>: 새 인스턴스가 각각의 새 클라이언트 세션에 대해 만들어지고 해당 세션의 수명이 유지 관리됩니다. 이를 수행하려면 세션을 지원하는 바인딩이 필요합니다.  
  
- <xref:System.ServiceModel.InstanceContextMode.Single>: 서비스 클래스의 단일 인스턴스가 애플리케이션의 수명에 대한 모든 클라이언트 요청을 처리합니다.  
  
 다음 코드 샘플과 같이 서비스 클래스는 `[ServiceBehavior(InstanceContextMode=<setting>)]` 특성을 사용하여 인스턴스 만들기 동작을 지정합니다. 주석 처리되는 줄을 변경하여 각 인스턴스 모드의 동작을 확인할 수 있습니다. 인스턴스 만들기 모드를 변경한 후 서비스를 다시 빌드해야 합니다. 클라이언트에서 인스턴스 만들기와 관련하여 지정해야 할 설정은 없습니다.  
  
```csharp
// Enable one of the following instance modes to compare instancing behaviors.  
 [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
  
// PerCall creates a new instance for each operation.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerCall)]  
  
// Singleton creates a single instance for application lifetime.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class CalculatorService : ICalculatorInstance  
{  
    static Object syncObject = new object();  
    static int instanceCount;  
    int instanceId;  
    int operationCount;  
  
    public CalculatorService()  
    {  
        lock (syncObject)  
        {  
            instanceCount++;  
            instanceId = instanceCount;  
        }  
    }  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 / n2;  
    }  
  
    public string GetInstanceContextMode()  
    {   // Return the InstanceContextMode of the service  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.InstanceContextMode.ToString();  
    }  
  
    public int GetInstanceId()  
    {   // Return the id for this instance  
        return instanceId;  
    }  
  
    public int GetOperationCount()  
    {   // Return the number of ICalculator operations performed
        // on this instance  
        lock (syncObject)  
        {  
            return operationCount;  
        }  
    }  
}  
  
static void Main()  
{  
    // Create a client.  
    CalculatorInstanceClient client = new CalculatorInstanceClient();  
    string instanceMode = client.GetInstanceContextMode();  
    Console.WriteLine("InstanceContextMode: {0}", instanceMode);  
    DoCalculations(client);  
  
    // Create a second client.  
    CalculatorInstanceClient client2 = new CalculatorInstanceClient();  
  
    DoCalculations(client2);  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
 샘플을 실행하면 작업 요청 및 응답이 클라이언트 콘솔 창에 표시됩니다. 실행 중인 서비스가 해당하는 인스턴스 모드가 표시됩니다. 인스턴스 만들기 모드의 동작을 반영하기 위해 각 작업 후에 인스턴스 ID와 작업 카운트가 표시됩니다. 클라이언트를 종료하려면 클라이언트 창에서 Enter 키를 누릅니다.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>샘플을 설치, 빌드 및 실행하려면  
  
1. [Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.  
  
2. C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.  
  
3. 단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.  
  
> [!IMPORTANT]
> 컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다. 계속하기 전에 다음(기본) 디렉터리를 확인하세요.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다. 이 샘플은 다음 디렉터리에 있습니다.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Instancing`  
