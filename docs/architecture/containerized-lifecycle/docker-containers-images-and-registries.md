---
title: Docker 컨테이너, 이미지 및 레지스트리
description: 애플리케이션 배포의 Docker 방식에서 리지스트리가 전체적으로 수행하는 주요 역할을 알아봅니다.
ms.date: 02/15/2019
ms.openlocfilehash: 7becadc3de16d96f8d6f167cf49c6cdd3bcc0d32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68673520"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="ba119-103">Docker 컨테이너, 이미지 및 레지스트리</span><span class="sxs-lookup"><span data-stu-id="ba119-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="ba119-104">Docker를 사용할 때 앱 또는 서비스를 만들고 컨테이너 및 해당 종속성을 컨테이너 이미지에 패키징합니다.</span><span class="sxs-lookup"><span data-stu-id="ba119-104">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="ba119-105">이미지는 앱 또는 서비스와 그 구성 및 종속성을 정적으로 표현합니다.</span><span class="sxs-lookup"><span data-stu-id="ba119-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="ba119-106">앱 또는 서비스를 실행하려면 앱의 이미지가 인스턴스화되어 Docker 호스트에서 실행되는 컨테이너를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ba119-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="ba119-107">컨테이너는 개발 환경 또는 PC에서 초기에 테스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba119-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="ba119-108">이미지 라이브러리로 사용되는 이미지를 레지스티리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ba119-108">You store images in a registry, that acts as a library of images.</span></span> <span data-ttu-id="ba119-109">프로덕션 오케스트레이터에 배포할 때 레지스트리가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ba119-109">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="ba119-110">Docker는 [Docker 허브](https://hub.docker.com/)를 통해 공용 레지스트리를 관리합니다. 다른 공급업체는 다른 이미지 컬렉션을 위한 [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) 등의 레지스트리를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ba119-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images, including [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span></span> <span data-ttu-id="ba119-111">또는 기업에서는 자체 Docker 이미지를 위해 개인 레지스트리 온-프레미스를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba119-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="ba119-112">그림 1-4는 Docker의 이미지와 레지스트리가 다른 구성 요소와 어떤 관계가 있는지 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="ba119-112">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="ba119-113">그것은 또한 공급업체로부터 제공되는 여러 레지스트리를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="ba119-113">It also shows the multiple registry offerings from vendors.</span></span>

![Docker의 기본 분류: 레지스트리는 이미지가 저장되고 컨테이너를 빌드하여 서비스 또는 웹앱을 실행하기 위해 가져올 수 있는 책장과 같습니다.](./media/image4.png)

<span data-ttu-id="ba119-118">**그림 1-4**.</span><span class="sxs-lookup"><span data-stu-id="ba119-118">**Figure 1-4**.</span></span> <span data-ttu-id="ba119-119">Docker 용어 및 개념의 분류</span><span class="sxs-lookup"><span data-stu-id="ba119-119">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="ba119-120">레지스티리에 이미지를 저장하면 프레임워크 수준에서 모든 종속성을 포함한 정적 및 변경할 수 없는 애플리케이션 비트를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba119-120">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="ba119-121">그런 다음, 여러 환경에서 이미지를 버전화하고 배포할 수 있으므로 일관된 배포 단위를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba119-121">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="ba119-122">온-프레미스 또는 클라우드에서 호스팅되는 개인 이미지 레지스티리는 다음과 같은 경우에 권장됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba119-122">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

- <span data-ttu-id="ba119-123">기밀로 인해 이미지를 공개적으로 공유해서는 안됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba119-123">Your images must not be shared publicly due to confidentiality.</span></span>

- <span data-ttu-id="ba119-124">이미지와 선택한 배포 환경 사이에는 최소 네트워크 대기 시간이 요구됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba119-124">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="ba119-125">예를 들어, 프로덕션 환경이 Azure인 경우 [Azure Container Registry](https://azure.microsoft.com/services/container-registry/)에 이미지를 저장하여 네트워크 대기 시간을 최소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba119-125">For example, if your production environment is Azure, you probably want to store your images in [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) so that network latency is minimal.</span></span> <span data-ttu-id="ba119-126">프로덕션 환경이 동일한 로컬 네트워크 내에서 사용 가능한 온-프레미스 Docker Trusted Registry인 경우에도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="ba119-126">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ba119-127">[이전](docker-terminology.md)
>[다음](road-to-modern-applications-based-on-containers.md)</span><span class="sxs-lookup"><span data-stu-id="ba119-127">[Previous](docker-terminology.md)
[Next](road-to-modern-applications-based-on-containers.md)</span></span>