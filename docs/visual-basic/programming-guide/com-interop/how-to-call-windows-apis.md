---
description: '자세한 정보: 방법: Windows Api 호출 (Visual Basic)'
title: '방법: Windows API 호출'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: ec25df3715b1f8a4612c1575b5f7192d0a133c4b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100464913"
---
# <a name="how-to-call-windows-apis-visual-basic"></a>방법: Windows API 호출(Visual Basic)

이 예제에서는 user32.dll에서 함수를 정의 하 고 호출한 `MessageBox` 다음 문자열을 전달 합니다.  
  
## <a name="example"></a>예  

 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a>코드 컴파일  

 이 예제에는 다음 사항이 필요합니다.  
  
- <xref:System> 네임스페이스에 대한 참조  
  
## <a name="robust-programming"></a>강력한 프로그래밍  

 다음 조건에서 예외가 발생합니다.  
  
- 메서드가 정적이 아니거나, 추상 이거나, 이전에 정의 되었습니다. 부모 형식이 인터페이스 이거나 *name* 또는 *dllName* 의 길이가 0입니다. (<xref:System.ArgumentException>)  
  
- *이름* 또는 *dllName* 은 `Nothing` 입니다. (<xref:System.ArgumentNullException>)  
  
- 포함하는 형식은 `CreateType`을 사용하여 이전에 만든 것입니다. (<xref:System.InvalidOperationException>)  
  
## <a name="see-also"></a>추가 정보

- [플랫폼 호출 자세히 보기](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [플랫폼 호출 예제](../../../framework/interop/platform-invoke-examples.md)
- [관리되지 않는 DLL 함수 사용](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- [리플렉션 내보내기를 사용하여 메서드 정의](/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))
- [연습: Windows API 호출](walkthrough-calling-windows-apis.md)
- [COM Interop](index.md)
