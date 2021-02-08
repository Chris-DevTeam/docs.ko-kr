---
description: '자세한 정보: Operation 클래스'
title: 작업 클래스
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: 035c02bc05b7a64c5d15538001dbdcf2ec0b135b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803076"
---
# <a name="operation-class"></a>작업 클래스

작업  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class Operation  
{  
  string Action;  
  boolean AsyncPattern;  
  Behavior Behaviors[];  
  boolean IsCallback;  
  boolean IsInitiating;  
  boolean IsOneWay;  
  boolean IsTerminating;  
  string MethodSignature;  
  string Name;  
  string ParameterTypes[];  
  string ReplyAction;  
  string ReturnType;  
};  
```  
  
## <a name="methods"></a>메서드  

 Operation 클래스는 메서드를 정의하지 않습니다.  
  
## <a name="properties"></a>속성  

 Operation 클래스에는 다음 속성이 있습니다.  
  
### <a name="action"></a>작업  

 데이터 형식: 문자열  
  
 액세스 형식: 읽기 전용  
  
 요청 메시지의 WS-Addressing 동작입니다.  
  
### <a name="asyncpattern"></a>AsyncPattern  

 데이터 형식: boolean  
  
 액세스 형식: 읽기 전용  
  
 `Begin`서비스 계약에서 [열기/닫기 꺾쇠 괄호]와 `End` [open/close 꺾쇠 괄호] 메서드 쌍을 사용 하 여 작업이 비동기적으로 구현 됨을 나타냅니다.  
  
### <a name="behaviors"></a>동작  

 데이터 형식: Behavior array  
  
 액세스 형식: 읽기 전용  
  
 이 작업과 연관된 동작입니다.  
  
### <a name="iscallback"></a>IsCallback  

 데이터 형식: boolean  
  
 액세스 형식: 읽기 전용  
  
 작업이 콜백 작업인 경우 true입니다.  
  
### <a name="isinitiating"></a>IsInitiating  

 데이터 형식: boolean  
  
 액세스 형식: 읽기 전용  
  
 서버에서 세션을 시작할 수 있는 작업을 메서드에서 구현하는지 여부를 나타냅니다.  
  
### <a name="isoneway"></a>IsOneWay  

 데이터 형식: boolean  
  
 액세스 형식: 읽기 전용  
  
 작업에서 회신 메시지를 반환하는지 여부를 나타냅니다.  
  
### <a name="isterminating"></a>IsTerminating  

 데이터 형식: boolean  
  
 액세스 형식: 읽기 전용  
  
 작업에서 회신 메시지를 반환하는지 여부를 나타냅니다.  
  
### <a name="methodsignature"></a>MethodSignature  

 데이터 형식: 문자열  
  
 액세스 형식: 읽기 전용  
  
 작업의 메서드 서명입니다.  
  
### <a name="name"></a>Name  

 데이터 형식: 문자열  
  
 액세스 형식: 읽기 전용  
  
 작업의 이름입니다.  
  
### <a name="parametertypes"></a>ParameterTypes  

 데이터 형식: string array  
  
 액세스 형식: 읽기 전용  
  
 작업의 매개 변수 형식입니다.  
  
### <a name="replyaction"></a>ReplyAction  

 데이터 형식: 문자열  
  
 액세스 형식: 읽기 전용  
  
 작업의 회신 메시지에 대한 SOAP 동작 값입니다.  
  
### <a name="returntype"></a>ReturnType  

 데이터 형식: 문자열  
  
 액세스 형식: 읽기 전용  
  
 작업의 반환 형식입니다.  
  
## <a name="requirements"></a>요구 사항  
  
|MOF|Servicemodel.mof에 선언되어 있습니다.|  
|---------|-----------------------------------|  
|네임스페이스|root\ServiceModel에 정의되어 있습니다.|  
  
## <a name="see-also"></a>참고 항목

- <xref:System.ServiceModel.Description.OperationDescription>
