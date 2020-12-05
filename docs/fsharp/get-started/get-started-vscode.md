---
title: Visual Studio Code에서 F# 시작
description: 'Visual Studio Code와 함께 F #을 사용 하는 방법 및 충돌 하는 Ide 플러그 인 제품군에 대해 알아봅니다.'
ms.date: 12/23/2018
ms.openlocfilehash: 11fb0d443fb7c2b3f270d45bfeaa91102ba28efd
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739804"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>Visual Studio Code에서 F# 시작

리팩터링 [ide 플러그](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp) 인을 사용 하 여 F [Visual Studio Code](https://code.visualstudio.com) #을 작성 하 여 IntelliSense 및 코드를 사용 하는 뛰어난 플랫폼 간 경량 Ide (통합 개발 환경) 환경을 얻을 수 있습니다. 플러그 인에 대 한 자세한 내용은 [Ionide.io](https://ionide.io) 를 참조 하세요.

시작 하려면 [F # 및 작동 하는 ide 플러그 인이 올바르게 설치](install-fsharp.md#install-f-with-visual-studio-code)되어 있는지 확인 합니다.

## <a name="create-your-first-project-with-ionide"></a>이상 Ide를 사용 하 여 첫 번째 프로젝트 만들기

새 F # 프로젝트를 만들려면 명령줄을 열고 .NET Core CLI를 사용 하 여 새 프로젝트를 만듭니다.

```dotnetcli
dotnet new console -lang "F#" -o FirstIonideProject
```

완료 되 면 디렉터리를 프로젝트로 변경 하 고 Visual Studio Code를 엽니다.

```console
cd FirstIonideProject
code .
```

Visual Studio Code에서 프로젝트가 로드 되 면 창의 왼쪽에 F # 솔루션 탐색기 창이 표시 됩니다. 즉, 사용자가 방금 만든 프로젝트가 성공적으로 로드 된 것입니다. 이 시점 이전에 편집기에서 코드를 작성할 수 있지만이 경우 모든 것이 로드를 완료 한 것입니다.

## <a name="configure-f-interactive"></a>F # interactive 구성

먼저 .NET Core 스크립팅이 기본 스크립팅 환경 인지 확인 합니다.

1. Visual Studio Code 설정 (**코드**  >  **기본** 설정  >  **설정**)을 엽니다.
1. **F # 스크립트** 라는 용어를 검색 합니다.
1. **Fsharp.core: USE SDK scripts** 확인란을 클릭 합니다.

이는 현재 .NET Core 스크립팅을 사용 하지 않는 .NET Framework 기반 스크립팅에 사용 되는 일부 레거시 동작으로 인해 필요 하며, 현재는 이전 버전과의 호환성을 위해 현재 웹사이트를 사용 하 고 있습니다. 나중에 .NET Core 스크립팅이 기본값이 됩니다.

### <a name="write-your-first-script"></a>첫 번째 스크립트 작성

.NET Core 스크립팅을 사용 하도록 Visual Studio Code 구성 했으면 Visual Studio Code에서 탐색기 보기로 이동 하 여 새 파일을 만듭니다. 이름을 *Myfirstscript* 로 합니다.

이제 다음 코드를 추가 합니다.

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

이 함수는 단어를 [Pig 라틴어](https://en.wikipedia.org/wiki/Pig_Latin)형식으로 변환 합니다. 다음 단계는 F# 대화형 (FSI.EXE)를 사용 하 여 평가 하는 것입니다.

전체 함수를 강조 표시 합니다 (길이가 11 줄 이어야 함). 강조 표시 되 면 **Alt** 키를 누르고 **enter** 키를 누릅니다. 화면 아래쪽에 터미널 창이 표시 되 고 다음과 같이 표시 됩니다.

![충돌 Ide를 사용 하는 F# 대화형 출력의 예](./media/getting-started-vscode/vscode-fsi.png)

다음 세 가지 작업을 수행 했습니다.

1. FSI.EXE 프로세스를 시작 했습니다.
2. FSI.EXE 프로세스를 통해 강조 표시 한 코드를 전송 했습니다.
3. FSI.EXE 프로세스는 전송 된 코드를 평가 합니다.

에서 전송 된 항목은 [함수](../language-reference/functions/index.md)이기 때문에 이제 fsi.exe!를 사용 하 여 해당 함수를 호출할 수 있습니다. 대화형 창에서 다음을 입력 합니다.

```fsharp
toPigLatin "banana";;
```

다음 결과가 표시됩니다.

```fsharp
val it : string = "ananabay"
```

이제 모음을 첫 글자로 사용해 보겠습니다. 다음을 입력합니다.

```fsharp
toPigLatin "apple";;
```

다음 결과가 표시됩니다.

```fsharp
val it : string = "appleyay"
```

함수가 예상 대로 작동 하는 것 처럼 보입니다. 축 하 합니다. Visual Studio Code에 첫 번째 F # 함수를 작성 하 고 FSI.EXE를 사용 하 여 평가 했습니다.

> [!NOTE]
> FSI.EXE의 줄은로 종료 됩니다 `;;` . FSI.EXE에서 여러 줄을 입력할 수 있기 때문입니다. 끝에 있는를 `;;` 사용 하면 코드가 완료 될 때 fsi.exe 알 수 있습니다.

## <a name="explaining-the-code"></a>코드 설명

코드가 실제로 수행 하는 작업을 잘 모르는 경우에는 다음 단계를 수행 합니다.

여기서 볼 수 있듯이 `toPigLatin` 는 단어를 입력으로 사용 하 고 해당 단어의 Pig-Latin 표현으로 변환 하는 함수입니다. 이에 대 한 규칙은 다음과 같습니다.

단어의 첫 문자가 모음으로 시작 하는 경우 단어의 끝에 "yay"를 추가 합니다. 모음으로 시작 하지 않으면 첫 번째 문자를 단어의 끝으로 이동 하 여 "ay"를 추가 합니다.

FSI.EXE에서 다음을 발견할 수 있습니다.

```fsharp
val toPigLatin : word:string -> string
```

이는를 `toPigLatin` 입력으로 사용 하 고 다른를 반환 하는 함수입니다 `string` `word` `string` . 이를 f # 코드를 이해 하는 데 핵심적인 F #의 기본 부분이 [함수의 형식 서명](https://fsharpforfunandprofit.com/posts/function-signatures/)이라고 합니다. 또한 Visual Studio Code에서 함수를 가리키면이를 확인할 수 있습니다.

함수의 본문에는 다음과 같은 두 가지 요소가 있습니다.

1. `isVowel`지정 된 문자 ( `c` )가 [패턴 일치](../language-reference/pattern-matching.md)를 통해 제공 된 패턴 중 하 나와 일치 하는지 확인 하 여 해당 문자 ()가 모음 인지 여부를 확인 하는 이라는 내부 함수입니다.

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md)첫 번째 문자가 모음 인지 확인 하 고 첫 번째 문자가 모음 인지 여부를 기준으로 입력 문자에서 반환 값을 생성 하는 식입니다.

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

따라서의 흐름은 `toPigLatin` 다음과 같습니다.

입력 단어의 첫 문자가 모음 인지 확인 합니다. 이 경우 "yay"를 단어 끝에 연결 합니다. 그렇지 않으면 첫 번째 문자를 단어의 끝으로 이동 하 여 "ay"를 추가 합니다.

이에 대 한 최종 정보는 다음과 같습니다. F #에는 함수에서 반환할 명시적인 명령이 없습니다. F #은 식 기반 이며, 함수 본문에서 계산 된 마지막 식이 해당 함수의 반환 값을 결정 하기 때문입니다. `if..then..else`는 자체 식 이므로 블록의 본문이 나 블록의 본문을 계산 하면 `then` `else` 함수에서 반환 하는 값이 결정 됩니다 `toPigLatin` .

## <a name="turn-the-console-app-into-a-pig-latin-generator"></a>콘솔 앱을 Pig 라틴어 생성기로 전환 합니다.

이 문서의 이전 섹션에서는 F # 코드를 작성 하는 첫 번째 단계를 보여 주었습니다. 초기 함수를 작성 하 고 FSI.EXE를 사용 하 여 대화형으로 실행 합니다. 이를 repl 기반 개발 이라고 하며, 여기서 [repl](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) 은 "읽기-평가-인쇄 루프"를 나타냅니다. 작업을 수행할 때까지 기능을 시험해 볼 수 있는 좋은 방법입니다.

REPL 기반 개발의 다음 단계는 작업 코드를 F # 구현 파일로 이동 하는 것입니다. 그런 다음 F # 컴파일러에서 실행할 수 있는 어셈블리로 컴파일할 수 있습니다.

시작 하려면 이전에 .NET Core CLI를 사용 하 여 만든 *Program fs* 파일을 엽니다. 일부 코드는 이미 여기에 있습니다.

그런 다음 라는 새를 [`module`](../language-reference/modules.md) 만들고 `PigLatin` 앞에서 만든 함수를 다음과 같이 복사 합니다 `toPigLatin` .

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L3-L14)]

이 모듈은 `main` 함수 및 선언 아래에 있어야 합니다 `open System` . F #에서 선언 순서는 중요 하므로 파일에서 호출 하기 전에 함수를 정의 해야 합니다.

이제 `main` 함수에서 인수에 대해 Pig 라틴어 생성기 함수를 호출 합니다.

```fsharp
[<EntryPoint>]
let main argv =
    for name in argv do
        let newName = PigLatin.toPigLatin name
        printfn %"{name} in Pig Latin is: {newName}"

    0
```

이제 명령줄에서 콘솔 앱을 실행할 수 있습니다.

```dotnetcli
dotnet run apple banana
```

스크립트 파일과 동일한 결과를 출력 하는 것을 볼 수 있지만 이번에는 실행 중인 프로그램입니다.

## <a name="troubleshooting-ionide"></a>문제가 있는 Ide 문제 해결

다음은 발생할 수 있는 특정 문제를 해결할 수 있는 몇 가지 방법입니다.

1. 기능이 없는 Ide의 코드 편집 기능을 가져오려면 F # 파일을 디스크에 저장 하 고 Visual Studio Code 작업 영역에 열려 있는 폴더 내에 저장 해야 합니다.
1. 시스템이 열려 있는 상태에서 시스템을 변경 하거나 Visual Studio Code를 설치한 경우 Visual Studio Code를 다시 시작 합니다.
1. 프로젝트 디렉터리에 잘못 된 문자가 있는 경우에는 작동 하지 않을 수 있습니다.  이 경우 프로젝트 디렉터리의 이름을 바꿉니다.
1. 작동 하는 지 여부 Ide 명령이 없으면 [Visual Studio Code 키 바인딩을](https://code.visualstudio.com/docs/getstarted/keybindings#_advanced-customization) 확인 하 여 실수로 재정의 하 고 있는지 확인 합니다.
1. 컴퓨터에서 손상 된 Ide가 손상 된 경우 어떤 것도 문제가 해결 되지 않으면 `ionide-fsharp` 컴퓨터에서 디렉터리를 제거 하 고 플러그 인 도구 모음을 다시 설치 하세요.
1. 프로젝트를 로드 하지 못한 경우 (F # 솔루션 탐색기 표시 됨) 해당 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 자세한 **정보 보기** 를 클릭 하 여 더 많은 진단 정보를 얻습니다.

이상 ide는 F # 커뮤니티의 멤버가 빌드하고 유지 관리 하는 오픈 소스 프로젝트입니다. 문제를 보고 하 고 무료 [ide-vscode-Fsharp.core GitHub 리포지토리에](https://github.com/ionide/ionide-vscode-fsharp)참여 하세요.

이상 Ide 개발자 및 F # 커뮤니티에서 강화 ide [Gitter 채널](https://gitter.im/ionide/ionide-project)의 추가 도움을 요청할 수도 있습니다.

## <a name="next-steps"></a>다음 단계

F #에 대 한 자세한 내용 및 언어의 기능에 대 한 자세한 내용은 [f # 둘러보기](../tour.md)를 참조 하세요.
