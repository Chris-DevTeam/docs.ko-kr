---
title: 탄력적 스택으로 로깅
description: 탄력적 스택, Logstash 태 시 및 Kibana를 사용 하 여 로깅
ms.date: 01/19/2021
ms.openlocfilehash: f8dbcd68bf809715a10d0ea1ab36cf5ceb6a96a9
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/04/2021
ms.locfileid: "99548086"
---
# <a name="logging-with-elastic-stack"></a>탄력적 스택으로 로깅

다양 한 중앙 집중식 로깅 도구를 사용할 수 있으며, 무료 오픈 소스 도구에서 비용이 많이 드는 옵션에 이르기까지 다양 합니다. 대부분의 경우 무료 도구는 유료 제품 보다 우수 하거나 더 효율적입니다. 이러한 도구 중 하나는 탄력적 검색, Logstash 및 Kibana의 세 가지 오픈 소스 구성 요소를 조합한 것입니다.

이러한 도구를 집합적으로 탄력적 스택 또는 ELK 스택 이라고 합니다.

## <a name="elastic-stack"></a>탄력적 스택

탄력적 스택은 Kubernetes 클러스터에서 정보를 수집 하는 강력한 옵션입니다. Kubernetes는 Elasticsearch 끝점에 로그를 보내는 작업을 지원 하며, [대부분](https://v1-19.docs.kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/)의 경우 그림 7-5에 표시 된 것 처럼 환경 변수를 설정 하기만 하면 됩니다.

```kubernetes
KUBE_LOGGING_DESTINATION=elasticsearch
KUBE_ENABLE_NODE_LOGGING=true
```

**그림 7-5**. Kubernetes에 대 한 구성 변수

이 단계에서는 클러스터에 Elasticsearch를 설치 하 고 모든 클러스터 로그를 대상으로 보냅니다.

![Kubernetes 그림 7-6의 수집 로그에 대 한 쿼리 결과를 보여 주는 Kibana 대시보드의 예 ](./media/kibana-dashboard.png)
 입니다. Kubernetes의 수집 로그에 대 한 쿼리 결과를 보여 주는 Kibana 대시보드의 예

## <a name="what-are-the-advantages-of-elastic-stack"></a>탄력적 스택의 장점은 무엇 인가요?

탄력적 스택은 경제적인 확장 가능 하 고 안전한 방식으로 중앙 집중식 로깅을 제공 합니다. 사용자 인터페이스를 사용 하면 데이터 분석을 간소화 하므로 clunky 인터페이스를 사용 하는 대신 데이터에서 사항은 정보를 사용할 수 있습니다. 분산 응용 프로그램이 더 많은 종류의 서비스에 걸쳐 있는 경우에는 다양 한 입력을 지원 하므로 로그 및 메트릭 데이터를 시스템에 계속 제공할 수 있습니다. 또한 탄력적 스택은 많은 데이터 집합에 대해서도 빠른 검색을 지원 하므로, 규모가 많은 응용 프로그램 에서도 자세한 데이터를 기록 하 고 성능에 대 한 가시성을 얻을 수 있습니다.

## <a name="logstash"></a>Logstash

첫 번째 구성 요소는 [Logstash 태](https://www.elastic.co/products/logstash)입니다. 이 도구는 다양 한 원본에서 로그 정보를 수집 하는 데 사용 됩니다. 예를 들어 Logstash 태는 디스크에서 로그를 읽고 [Serilog](https://serilog.net/)같은 로깅 라이브러리에서 메시지를 받을 수 있습니다. Logstash 태 시 로그에서 몇 가지 기본 필터링 및 확장을 수행할 수 있습니다. 예를 들어 로그에 IP 주소가 포함 되어 있는 경우, Logstash 태 시 지리적 조회를 수행 하 고 해당 메시지에 대 한 국가 또는 시/도를 가져오도록 구성할 수 있습니다.

Serilog는 매개 변수가 있는 로깅을 허용 하는 .NET 언어의 로깅 라이브러리입니다. 필드를 포함 하는 텍스트 로그 메시지를 생성 하는 대신 매개 변수는 별도로 유지 됩니다. 이 라이브러리는 더 지능적인 필터링 및 검색을 허용 합니다. Logstash 태 시 쓰기에 대 한 샘플 Serilog 구성은 그림 7-7에 나와 있습니다.

```csharp
var log = new LoggerConfiguration()
         .WriteTo.Http("http://localhost:8080")
         .CreateLogger();
```

**그림 7-7**. HTTP를 통한 logstash 태에 직접 로그 정보를 쓰기 위한 Serilog config

Logstash 태는 그림 7-8에 표시 된 것과 같은 구성을 사용 합니다.

```
input {
    http {
        #default host 0.0.0.0:8080
        codec => json
    }
}

output {
    elasticsearch {
        hosts => "elasticsearch:9200"
        index=>"sales-%{+xxxx.ww}"
    }
}
```

**그림 7-8**. Serilog에서 로그를 사용 하기 위한 Logstash 태 시 구성

광범위 한 로그 조작이 필요 하지 않은 시나리오의 경우 [에는 보다](https://www.elastic.co/products/beats)큰 것으로 알려진 logstash 태의 대안이 있습니다. 비트는 로그에서 네트워크 데이터 및 작동 시간 정보에 이르는 다양 한 데이터를 수집할 수 있는 도구 제품군입니다. 많은 응용 프로그램은 Logstash 태 시와 비트를 모두 사용 합니다.

Logstash 태에서 로그를 수집한 후에는 해당 로그를 저장 해야 합니다. Logstash 태은 다양 한 출력을 지원 하지만, 더 흥미로운 방법 중 하나는 탄력적 검색입니다.

## <a name="elastic-search"></a>탄력적 검색

탄력적 검색은 도착 하면 로그를 인덱싱할 수 있는 강력한 검색 엔진입니다. 로그에 대 한 쿼리를 신속 하 게 실행 합니다. 탄력적 검색은 대량의 로그를 처리할 수 있으며 극단적인 경우 많은 노드에서 확장할 수 있습니다.

매개 변수를 포함 하기 위해 또는 Logstash 태 시 처리를 통해 분할 된 매개 변수를 포함 하도록 만들어진 로그 메시지는 Elasticsearch에서이 정보를 유지 하기 때문에 직접 쿼리할 수 있습니다.

에서 방문한 상위 10 페이지를 검색 하는 쿼리는 `jill@example.com` 그림 7-9에 나와 있습니다.

```json
"query": {
    "match": {
      "user": "jill@example.com"
    }
  },
  "aggregations": {
    "top_10_pages": {
      "terms": {
        "field": "page",
        "size": 10
      }
    }
  }
```

**그림 7-9**. 사용자가 방문 하는 상위 10 개 페이지를 찾기 위한 Elasticsearch 쿼리

## <a name="visualizing-information-with-kibana-web-dashboards"></a>Kibana 웹 대시보드를 사용 하 여 정보 시각화

스택의 최종 구성 요소는 Kibana입니다. 이 도구는 웹 대시보드에 대화형 시각화를 제공 하는 데 사용 됩니다. 대시보드는 비기술적 사용자가 아니더라도 제작 될 수 있습니다. Elasticsearch 인덱스에 상주 하는 대부분의 데이터는 Kibana 대시보드에 포함 될 수 있습니다. 개별 사용자는 다른 대시보드를 사용할 수 있으며, Kibana 사용자 특정 대시보드를 허용 하 여이 사용자 지정을 수행할 수 있습니다.

## <a name="installing-elastic-stack-on-azure"></a>Azure에서 탄력적 스택 설치

탄력적 스택은 여러 가지 방법으로 Azure에 설치할 수 있습니다. 항상으로 [가상 컴퓨터를 프로 비전 하 고 탄력적 스택을 직접 설치할](/azure/virtual-machines/linux/tutorial-elasticsearch)수 있습니다. 이 옵션은 가장 높은 수준의 사용자 지정 가능성를 제공 하므로 숙련 된 사용자가 선호 합니다. 인프라를 서비스로 배포 하는 경우에는 해당 경로를 사용 하 여 컴퓨터를 보호 하 고 패치를 최신 상태로 유지 하는 등의 서비스와 관련 된 모든 작업의 소유권을 유지 하는 데 중요 한 관리 오버 헤드가 발생 합니다.

오버 헤드가 감소 하는 옵션은 탄력적 스택이 이미 구성 된 많은 Docker 컨테이너 중 하나를 사용 하는 것입니다. 이러한 컨테이너는 기존 Kubernetes 클러스터로 끌어와 응용 프로그램 코드와 함께 실행할 수 있습니다. [Sebp/elk](https://elk-docker.readthedocs.io/) 컨테이너는 잘 문서화 되 고 테스트 된 탄력적 스택 컨테이너입니다.

또 다른 옵션은 [최근에 발표 한 ELK as a service 제품](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/)입니다.

## <a name="references"></a>참조

- [Azure에 탄력적 스택 설치](/azure/virtual-machines/linux/tutorial-elasticsearch)

>[!div class="step-by-step"]
>[이전](observability-patterns.md)
>[다음](monitoring-azure-kubernetes.md)
