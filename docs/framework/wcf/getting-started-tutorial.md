---
title: '자습서: Windows Communication Foundation 응용 프로그램 시작'
description: 이러한 자습서에서는 WCF 응용 프로그램을 만드는 방법을 소개 합니다.
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: 620a83260f01e27a19b19227165695a621c88e5e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238238"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a>자습서: Windows Communication Foundation 응용 프로그램 시작

다음 일련의 자습서에서는 WCF (Windows Communication Foundation) 프로그래밍 환경을 소개 합니다. 이러한 자습서를 순서 대로 진행 하면 WCF 응용 프로그램을 만드는 데 필요한 단계를 이해 하는 데 도움이 됩니다. 완료 되 면 서비스를 호출 하는 wcf 클라이언트 및 wcf 서비스가 실행 됩니다.

이 자습서에서는 Visual Studio를 개발 환경으로 사용 하 고 있다고 가정 합니다. 다른 개발 환경을 사용 하는 경우 Visual Studio 관련 지침을 무시 합니다.

다운로드 하 여 실행할 수 있는 샘플 WCF 응용 프로그램은 [Windows Communication Foundation 샘플](samples/index.md)을 참조 하세요. 샘플에 대 한 소개는 [시작 샘플](samples/getting-started-sample.md)을 참조 하세요.

서비스 및 클라이언트를 만드는 방법에 대 한 자세한 내용은 [기본 WCF 프로그래밍](basic-wcf-programming.md)을 참조 하세요.

## <a name="wcf-tutorials"></a>WCF 자습서

처음 세 가지 자습서에서는 WCF 서비스 계약을 정의 하는 방법, 구현 방법 및 호스트 하는 방법을 설명 합니다. 만든 서비스는 콘솔 응용 프로그램 내에서 자체 호스팅됩니다. Microsoft 인터넷 정보 서비스 (IIS)에서 서비스를 호스팅할 수도 있습니다. 자세한 내용은 [방법: IIS에서 WCF 서비스 호스팅](feature-details/how-to-host-a-wcf-service-in-iis.md)을 참조 하세요. 자습서에서 코드를 사용 하 여 서비스를 구성 하더라도 [구성 파일 내에서 서비스를 구성할](configuring-services-using-configuration-files.md)수도 있습니다.

- [자습서: 서비스 계약 정의](how-to-define-a-wcf-service-contract.md)

    사용자 정의 인터페이스를 사용 하 여 WCF 계약을 만듭니다. 이 계약은 서비스에서 노출 하는 기능을 정의 합니다.

- [자습서: 서비스 계약 구현](how-to-implement-a-wcf-contract.md)

    계약을 정의한 후에는 서비스 클래스를 사용 하 여 계약을 구현 해야 합니다.

- [자습서: 기본 서비스 호스트 및 실행](how-to-host-and-run-a-basic-wcf-service.md)

    서비스에 대 한 끝점을 구성 하 고 콘솔 응용 프로그램에서 서비스를 호스팅합니다. 서비스를 활성화 하려면 해당 서비스를 구성 하 고 런타임 환경 내에서 호스트 해야 합니다. 이 런타임 환경에서는 서비스를 만들고 해당 컨텍스트 및 수명을 제어 합니다.

다음 두 자습서에서는 클라이언트 응용 프로그램을 만들고 구성 하 고 사용 하 여 서비스에서 노출 하는 작업을 호출 하는 방법을 설명 합니다. 서비스는 클라이언트 애플리케이션이 서비스와 통신하는 데 필요한 정보를 정의하는 메타데이터를 게시합니다. Visual Studio는이 메타 데이터에 액세스 하는 프로세스를 자동화 하 고이를 사용 하 여 서비스에 대 한 클라이언트 응용 프로그램을 생성 합니다. Visual Studio를 사용 하지 않기로 결정 한 경우에는 [ServiceModel Metadata 유틸리티 도구 (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) 를 대신 사용할 수 있습니다.

- [자습서: 클라이언트 만들기](how-to-create-a-wcf-client.md)

    WCF 서비스에서 WCF 클라이언트 프록시를 만들기 위한 메타 데이터를 검색 합니다. Visual Studio를 사용 하 여 서비스 참조를 추가 하거나 ServiceModel Metadata 유틸리티 도구를 사용 하 여 메타 데이터를 검색할 수 있습니다. 클라이언트에서 서비스에 액세스 하는 데 사용 하는 끝점을 지정 합니다.

- [자습서: 클라이언트 사용](how-to-use-a-wcf-client.md)

    WCF 클라이언트 프록시를 사용 하 여 서비스 작업을 호출 합니다.

## <a name="reference"></a>참고

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a>참조

- [개념적 개요](conceptual-overview.md)
- [설명서 가이드](guide-to-the-documentation.md)
- [Windows Communication Foundation 정의](whats-wcf.md)
- [WCF 기능 정보](feature-details/index.md)
- [기본 프로그래밍 수명 주기](basic-programming-lifecycle.md)
- [클라이언트 빌드](building-clients.md)
- [기본 WCF 프로그래밍](basic-wcf-programming.md)
- [방법: 이중 계약 만들기](feature-details/how-to-create-a-duplex-contract.md)
- [방법: 이중 계약을 사용 하 여 서비스 액세스](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [ServiceModel Metadata 유틸리티 도구 (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [방법: Svcutil.exe를 사용 하 여 메타 데이터 문서 다운로드](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [방법: 구성 파일을 사용 하 여 서비스에 대 한 메타 데이터 게시](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [바인딩을 사용 하 여 서비스 및 클라이언트 구성](using-bindings-to-configure-services-and-clients.md)
- [시작 샘플](samples/getting-started-sample.md)
- [Windows Communication Foundation 샘플](samples/index.md)
- [자체 호스팅](samples/self-host.md)
