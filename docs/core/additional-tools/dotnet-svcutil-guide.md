---
title: WCF svcutil 도구 개요
description: .NET Framework 프로젝트용 WCF svcutil 도구와 유사하게, .NET Core 및 ASP.NET Core 프로젝트 기능을 추가하는 Microsoft WCF dotnet-svcutil 도구에 대한 개요입니다.
author: honggit
ms.date: 02/22/2019
ms.openlocfilehash: 9468a881fe3850b53d48945340127ac2c2d4c6c8
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957925"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a>.NET Core용 WCF dotnet-svcutil 도구

WCF(Windows Communication Foundation) **dotnet-svcutil** 도구는 네트워크 위치의 웹 서비스 또는 WSDL 파일에서 메타데이터를 검색하고, 해당 웹 서비스 작업에 액세스하는 클라이언트 프록시 메서드가 포함된 WCF 클래스를 생성하는 .NET 도구입니다.

.NET Framework 프로젝트용 [**서비스 모델 메타데이터 - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 도구와 비슷하게, **dotnet-svcutil** 은 .NET Core 및 .NET Standard 프로젝트와 호환되는 웹 서비스 참조를 생성하기 위한 명령줄 도구입니다.

**dotnet-svcutil** 도구는 Visual Studio 2017 버전 15.5에서 처음 제공된 [**WCF Web Service Reference Provider 도구 사용**](wcf-web-service-reference-guide.md) Visual Studio 연결된 서비스 공급자의 대체 옵션입니다. .NET 도구인 **dotnet-svcutil** 도구는 Linux, macOS, Windows와 같은 여러 플랫폼에서 사용할 수 있습니다.

> [!IMPORTANT]
> 신뢰할 수 있는 원본의 서비스만 참조해야 합니다. 신뢰할 수 없는 원본에서 참조를 추가하면 보안이 손상될 수 있습니다.

## <a name="prerequisites"></a>사전 요구 사항

<!-- markdownlint-disable MD025 -->

# <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

- [.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) 이상 버전
- 선호하는 코드 편집기

# <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

- [.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) 이상 버전
- 선호하는 코드 편집기

---

## <a name="getting-started"></a>시작

다음 예제에서는 .NET Core 웹 프로젝트에 웹 서비스 참조를 추가하고 서비스를 호출하는 데 필요한 단계를 안내합니다. *HelloSvcutil* 이라는 .NET Core 웹 애플리케이션을 만들고 다음 계약을 구현하는 웹 서비스에 대한 참조를 추가합니다.

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

이 예제에서는 웹 서비스가 `http://contoso.com/SayHello.svc` 주소에서 호스트되는 것으로 가정합니다.

Windows, macOS 또는 Linux 명령 창에서 다음 단계를 수행합니다.

1. 프로젝트에 대해 _HelloSvcutil_ 디렉터리를 만들고 다음 예제와 같이 현재 디렉터리로 설정합니다.

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. 다음과 같이 [`dotnet new`](../tools/dotnet-new.md) 명령을 사용하여 이 디렉터리에서 새 C# 웹 프로젝트를 만듭니다.

    ```dotnetcli
    dotnet new web
    ```

3. [`dotnet-svcutil` NuGet 패키지](https://nuget.org/packages/dotnet-svcutil)를 CLI 도구( )로 설치합니다.<!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

    편집기에서 `HelloSvcutil.csproj` 프로젝트 파일을 열고, `Project` 요소를 편집하고, 다음 코드를 사용하여 [`dotnet-svcutil` NuGet 패키지](https://nuget.org/packages/dotnet-svcutil)를 CLI 도구 참조로 추가합니다.

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    그리고 다음과 같이 [`dotnet restore`](../tools/dotnet-restore.md) 명령을 사용하여 _dotnet-svcutil_ 패키지를 복원합니다.

    ```dotnetcli
    dotnet restore
    ```

    ---

4. 다음과 같이 _dotnet-svcutil_ 명령을 실행하여 웹 서비스 참조 파일을 생성합니다.

    # <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

    ```dotnetcli
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

생성된 파일은 _HelloSvcutil/ServiceReference/Reference.cs_ 로 저장됩니다. 또한 _dotnet-svcutil_ 도구는 프록시 코드에 필요한 적절한 WCF 패키지를 프로젝트에 패키지 참조로 추가합니다.

## <a name="using-the-service-reference"></a>서비스 참조 사용

1. 다음과 같이 [`dotnet restore`](../tools/dotnet-restore.md) 명령을 사용하여 WCF 패키지를 복원합니다.

    ```dotnetcli
    dotnet restore
    ```

2. 사용하려는 클라이언트 클래스 및 작업의 이름을 찾습니다. `Reference.cs`는 `System.ServiceModel.ClientBase`에서 상속되는 클래스와 서비스에서 작업을 호출하는 데 사용할 수 있는 메서드를 포함합니다. 이 예제에서는 _SayHello_ 서비스의 _Hello_ 작업을 호출합니다. `ServiceReference.SayHelloClient`는 클라이언트 클래스의 이름이고, 작업을 호출하는 데 사용할 수 있는 `HelloAsync`라는 메서드를 갖습니다.

3. 편집기에서 `Startup.cs` 파일을 열고 상단에 서비스 참조 네임스페이스를 위한 `using` 지시문을 추가합니다.

    ```csharp
    using ServiceReference;
    ```

4. `Configure` 메서드가 웹 서비스를 호출하도록 편집합니다. 이렇게 하려면 `ClientBase`에서 상속되는 클래스의 인스턴스를 만들고 클라이언트 개체에서 메서드를 호출합니다.

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }

        app.Run(async (context) =>
        {
            var client = new SayHelloClient();
            var response = await client.HelloAsync();
            await context.Response.WriteAsync(response);
        });
    }

    ```

5. 다음과 같이 [`dotnet run`](../tools/dotnet-run.md) 명령을 사용하여 애플리케이션을 실행합니다.

    ```dotnetcli
    dotnet run
    ```

6. 웹 브라우저에서, 콘솔에 나열된 URL(예: `http://localhost:5000`)로 이동합니다.

다음과 같은 내용이 출력됩니다. "Hello dotnet-svcutil!"

`dotnet-svcutil` 도구 매개 변수에 대한 자세한 설명을 보려면 다음과 같이 help 매개 변수를 전달하는 도구를 호출합니다.

# <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

```dotnetcli
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

```dotnetcli
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a>사용자 의견 및 질문

질문이나 의견이 있는 경우 [GitHub에서 문제를 엽니다](https://github.com/dotnet/wcf/issues/new). 또한 [GitHub의 WCF 리포지토리에서](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling) 기존 질문이나 문제를 검토할 수 있습니다.

## <a name="release-notes"></a>릴리스 정보

- 알려진 문제를 비롯한 업데이트된 릴리스 정보는 [릴리스 정보](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md)를 참조하세요.

## <a name="information"></a>정보

- [dotnet-svcutil NuGet 패키지](https://nuget.org/packages/dotnet-svcutil)
