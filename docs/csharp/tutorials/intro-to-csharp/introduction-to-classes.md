---
title: 클래스 및 개체 - C# 소개 자습서
description: 첫 번째 C# 프로그램을 만들고 개체 지향 개념을 살펴봅니다.
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 3da445e6c656628fffdb9ef9384fb1a1c556a2cd
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255420"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a>클래스 및 개체를 사용한 개체 지향 프로그래밍 살펴보기

이 자습서에서는 콘솔 애플리케이션을 빌드하고 C# 언어의 일부인 기본 개체 지향 기능을 확인합니다.

## <a name="prerequisites"></a>사전 준비 사항

이 자습서에서는 컴퓨터가 로컬 개발용으로 설정되어 있다고 가정합니다. Windows, Linux 또는 macOS에서 .NET CLI를 사용하여 애플리케이션을 만들고, 빌드하고, 실행할 수 있습니다. Windows에서 Visual Studio 2019를 사용할 수 있습니다. 설정 지침은 [로컬 환경 설정](../../tour-of-csharp/tutorials/local-environment.md)을 참조하세요.

## <a name="create-your-application"></a>애플리케이션 만들기

터미널 창을 사용하여 *클래스* 라는 디렉터리를 만듭니다. 거기에 애플리케이션을 빌드할 것입니다. 해당 디렉터리로 변경하고 콘솔 창에 `dotnet new console`을 입력합니다. 이 명령은 애플리케이션을 만듭니다. *Program.cs* 를 엽니다. 다음과 같이 표시됩니다.

```csharp
using System;

namespace classes
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

이 자습서에서는 은행 계좌를 나타내는 새로운 형식을 만듭니다. 일반적으로 개발자는 여러 텍스트 파일에 각 클래스를 정의합니다. 그러면 프로그램의 크기가 커질 때 쉽게 관리할 수 있습니다. *클래스* 디렉터리에 *BankAccount.cs* 라는 새 파일을 만듭니다.

이 파일에는 ***은행 계좌** _의 정의가 포함됩니다. 개체 지향 프로그래밍은 클래스 형태로 형식을 생성하여 코드를 구성합니다. 이러한 클래스에는 특정 엔티티를 나타내는 코드가 포함됩니다. `BankAccount` 클래스는 은행 계좌를 나타냅니다. 코드는 메서드 및 속성을 통해 특정 작업을 구현합니다. 이 자습서에서 은행 계좌는 다음 동작을 지원합니다.

1. 은행 계좌를 고유하게 식별하는 10자리 숫자가 있습니다.
1. 소유자의 이름을 저장하는 문자열이 있습니다.
1. 잔액을 검색할 수 있습니다.
1. 예금을 허용합니다.
1. 인출을 허용합니다.
1. 초기 잔액은 양수여야 합니다.
1. 인출로 인해 음의 잔액이 발생할 수 없습니다.

## <a name="define-the-bank-account-type"></a>은행 계좌 형식 정의

동작을 정의하는 클래스의 기본 사항을 만들어 시작할 수 있습니다. **File:New** 명령을 사용하여 새 파일을 만듭니다. 파일의 이름을 *BankAccount.cs* 로 지정합니다. *BankAccount.cs* 파일에 다음 코드를 추가합니다.

```csharp
using System;

namespace classes
{
    public class BankAccount
    {
        public string Number { get; }
        public string Owner { get; set; }
        public decimal Balance { get; }

        public void MakeDeposit(decimal amount, DateTime date, string note)
        {
        }

        public void MakeWithdrawal(decimal amount, DateTime date, string note)
        {
        }
    }
}
```

계속하기 전에 빌드한 내용을 살펴보겠습니다.  `namespace` 선언은 코드를 논리적으로 구성하는 방법을 제공합니다. 이 자습서는 비교적 작으므로 하나의 네임스페이스에 모든 코드를 넣습니다.

`public class BankAccount`는 생성하는 클래스 또는 형식을 정의합니다. 클래스 선언 뒤에 오는 `{` 및 `}`의 모든 항목은 클래스의 상태와 동작을 정의합니다. `BankAccount` 클래스의 ***멤버** _가 다섯 개 있습니다. 처음 세 개는 ‘속성’입니다. 속성은 데이터 요소이며 유효성 검사 또는 기타 규칙을 적용하는 코드가 있을 수 있습니다. 마지막 두 개는 메서드입니다. 메서드는 단일 함수를 수행하는 코드 블록입니다. 각 멤버의 이름을 읽으면 사용자 또는 다른 개발자가 클래스가 수행하는 작업을 이해하기에 충분한 정보를 제공해야 합니다.

## <a name="open-a-new-account"></a>새 계좌 개설

구현할 첫 번째 기능은 은행 계좌 개설 기능입니다. 고객이 계좌를 개설할 때 초기 잔액과 해당 계좌 소유자에 대한 정보를 제공해야 합니다.

`BankAccount` 형식의 새 개체를 생성하는 것은 해당 값을 할당하는 **생성자** 를 정의하는 것입니다. 생성자는 클래스와 이름이 같은 멤버입니다. 생성자는 해당 클래스 형식의 개체를 초기화하는 데 사용됩니다. `BankAccount` 형식에 다음 생성자를 추가합니다. `MakeDeposit` 선언 위에 다음 코드를 배치합니다.

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

생성자는 [`new`](../../language-reference/operators/new-operator.md)를 사용하여 개체를 만들 때 호출됩니다. *Program.cs* 의 `Console.WriteLine("Hello World!");` 줄을 다음 코드로 바꿉니다(`<name>`을 사용자의 이름으로 바꿈).

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

지금까지 빌드한 코드를 실행해 보겠습니다. Visual Studio를 사용하는 경우 **실행** 메뉴에서 **디버깅하지 않고 시작** 을 선택합니다. 명령줄을 사용하는 경우 프로젝트를 만든 디렉터리에 `dotnet run`을 입력합니다.

계좌 번호가 공백인가요? 이를 수정해 보겠습니다. 개체가 생성될 때 계좌 번호를 지정해야 합니다. 그러나 계좌 번호 생성은 호출자의 책임이 아닙니다. `BankAccount` 클래스 코드는 새 계좌 번호를 지정하는 방법을 알아야 합니다.  이를 수행하는 간단한 방법은 10자리 숫자로 시작하는 것입니다. 새 계좌가 생성될 때마다 숫자가 늘어납니다. 마지막으로, 개체가 생성될 때 현재 계좌 번호를 저장합니다.

`BankAccount` 클래스에 멤버 선언을 추가합니다. `BankAccount` 클래스의 시작 부분에서 여는 중괄호 `{` 뒤에 다음 코드 줄을 배치합니다.

```csharp
private static int accountNumberSeed = 1234567890;
```

이는 데이터 멤버입니다. 이것은 `private`입니다. 즉 `BankAccount` 클래스 내의 코드로만 액세스할 수 있습니다. 이는 전용 구현(계좌 번호가 생성되는 방법)과 공공 책임(계좌 번호를 가지는 것 등)을 구분하는 방법입니다. 모든 `BankAccount` 개체에서 공유됨을 의미하는 `static`이기도 합니다. 비정적 변수의 값은 `BankAccount` 개체의 각 인스턴스에 고유합니다. 생성자에 다음 두 줄을 추가하여 계좌 번호를 지정합니다. `this.Balance = initialBalance` 줄 뒤에 배치합니다.

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

`dotnet run`을 입력하여 결과를 확인합니다.

## <a name="create-deposits-and-withdrawals"></a>예금 및 인출 만들기

은행 계좌 클래스는 제대로 작동하려면 예금과 인출을 허용해야 합니다. 계좌의 모든 트랜잭션에 대한 저널을 만들어 예금과 인출을 구현하겠습니다. 단순히 각 트랜잭션의 잔액을 업데이트하는 것보다 많은 장점이 있습니다. 기록을 사용하여 모든 트랜잭션을 감사하고 일별 잔액을 관리할 수 있습니다. 필요한 경우 모든 트랜잭션의 기록에서 잔액을 계산함으로써, 수정된 단일 트랜잭션의 오류가 다음 계산의 잔액에 올바르게 반영됩니다.

트랜잭션을 나타내는 새 형식을 생성해 보겠습니다. 이는 책임이 없는 단순 형식입니다. 몇 가지 속성이 필요합니다. *Transaction.cs* 라는 새 파일을 만듭니다. 파일에 다음 코드를 추가합니다.

:::code language="csharp" source="./snippets/introduction-to-classes/Transaction.cs":::

이제 `Transaction` 개체의 <xref:System.Collections.Generic.List%601>를 `BankAccount` 클래스에 추가하겠습니다. *BankAccount.cs* 파일의 생성자 뒤에 다음 선언을 추가합니다.

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="TransactionDeclaration":::

<xref:System.Collections.Generic.List%601> 클래스를 사용하려면 다른 네임스페이스를 가져와야 합니다. *BankAccount.cs* 의 시작 부분에 다음을 추가합니다.

```csharp
using System.Collections.Generic;
```

이제 `Balance`를 올바르게 계산해 보겠습니다. 모든 트랜잭션의 값을 합하여 현재 잔액을 찾을 수 있습니다. 코드가 현재 상태이기 때문에 계정의 초기 잔액만 가져올 수 있으므로 `Balance` 속성을 업데이트해야 합니다. *BankAccount.cs* 의 `public decimal Balance { get; }` 줄을 다음 코드로 바꿉니다.

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="BalanceComputation":::

이 예제에서는 ***속성*** 의 중요한 측면을 보여 줍니다. 이제 다른 프로그래머가 값을 요청할 때 잔액을 계산합니다. 계산은 모든 트랜잭션을 열거하고 합계를 현재 잔액으로 제공합니다.

다음으로 `MakeDeposit` 및 `MakeWithdrawal` 메서드를 구현합니다. 이러한 메서드는 최종 두 규칙을 적용합니다. 초기 잔액은 양수여야 하고 인출로 인해 음수의 잔액이 발생되어서는 안 됩니다.

이는 ***예외*** 의 개념을 소개합니다. 메서드가 작업을 성공적으로 완료할 수 없음을 나타내는 일반적인 방법은 예외를 throw하는 것입니다. 예외 형식 및 관련 메시지는 오류를 설명합니다. 여기에서 `MakeDeposit` 메서드는 인출 금액이 음수인 경우 예외를 throw합니다. 인출 금액이 음수이거나 인출 적용 후 잔액이 음수인 경우 `MakeWithdrawal` 메서드는 예외를 throw합니다. `allTransactions` 목록의 선언 뒤에 다음 코드를 추가합니다.

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="DepositAndWithdrawal":::

[`throw`](../../language-reference/keywords/throw.md) 문은 예외를 **throw** 합니다. 현재 블록의 실행이 종료되고 제어가 호출 스택에 있는 처음 일치하는 `catch` 블록으로 전달됩니다. `catch` 블록을 추가하여 나중에 이 코드를 테스트합니다.

생성자는 잔액을 직접 업데이트하지 않고 초기 트랜잭션을 추가하도록 변경해야 합니다. `MakeDeposit` 메서드를 이미 작성했으므로 생성자에서 호출합니다. 완성된 생성자는 다음과 같아야 합니다.

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="Constructor":::

<xref:System.DateTime.Now?displayProperty=nameWithType>은 현재 날짜 및 시간을 반환하는 속성입니다. 새 `BankAccount`를 만드는 코드를 따라 `Main` 메서드에서 몇 가지 예금 및 인출을 추가하여 테스트합니다.

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

다음으로 음수 잔액을 사용하여 계정을 생성하여 오류 조건을 알아보는 테스트를 수행합니다. 방금 추가한 이전 코드 뒤에 다음 코드를 추가합니다.

```csharp
// Test that the initial balances must be positive.
try
{
    var invalidAccount = new BankAccount("invalid", -55);
}
catch (ArgumentOutOfRangeException e)
{
    Console.WriteLine("Exception caught creating account with negative balance");
    Console.WriteLine(e.ToString());
}
```

[`try` 및 `catch` 문](../../language-reference/keywords/try-catch.md)을 사용하여 예외를 throw할 수 있는 코드 블록을 표시하고 예상한 오류를 catch합니다. 동일한 기술을 사용하여 음수 잔액에 대한 예외를 throw하는 코드를 테스트할 수 있습니다. `Main` 메서드의 끝에 다음 코드를 추가합니다.

```csharp
// Test for a negative balance.
try
{
    account.MakeWithdrawal(750, DateTime.Now, "Attempt to overdraw");
}
catch (InvalidOperationException e)
{
    Console.WriteLine("Exception caught trying to overdraw");
    Console.WriteLine(e.ToString());
}
```

파일을 저장하고 `dotnet run`을 입력하여 시도해 보세요.

## <a name="challenge---log-all-transactions"></a>과제 - 모든 트랜잭션 기록

이 자습서를 완료하기 위해 트랜잭션 기록에 대해 `string`을 생성하는 `GetAccountHistory` 메서드를 작성할 수 있습니다. `BankAccount` 형식에 이 메서드를 추가합니다.

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="History":::

<xref:System.Text.StringBuilder> 클래스를 사용하여 각 트랜잭션에 대해 한 줄을 포함하는 문자열의 형식을 지정합니다. 이러한 자습서의 앞부분에서 문자열 형식 지정 코드를 살펴보았습니다. 새 문자는 `\t`입니다. 이 새 문자는 탭을 삽입하여 출력 형식을 지정합니다.

*Program.cs* 에서 테스트하려면 이 줄을 추가합니다.

```csharp
Console.WriteLine(account.GetAccountHistory());
```

프로그램을 실행하여 결과를 확인합니다.

## <a name="next-steps"></a>다음 단계

잘 알 수 없는 경우 [GitHub 리포지토리](https://github.com/dotnet/docs/tree/main/docs/csharp/tutorials/intro-to-csharp/snippets/introduction-to-classes)에서 이 자습서의 소스를 확인할 수 있습니다.

[개체 지향 프로그래밍](object-oriented-programming.md) 자습서를 계속 진행할 수 있습니다.

다음 문서에서 이러한 개념을 더 자세히 알아볼 수 있습니다.

- [If 및 else 문](../../language-reference/keywords/if-else.md)
- [While 문](../../language-reference/keywords/while.md)
- [Do 문](../../language-reference/keywords/do.md)
- [For 문](../../language-reference/keywords/for.md)
