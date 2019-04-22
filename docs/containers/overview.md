---
title: Windows 上的 Visual Studio 容器工具
description: 了解 Visual Studio 中可用於使用 Docker 的工具
author: ghogen
ms.author: ghogen
ms.topic: overview
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 4b03ccddadf954b8430b7ad9b5a4ed765fccc3f5
ms.sourcegitcommit: cd91a8a4f6086cda9ba6948be25864fc7d6b8e44
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59538056"
---
# <a name="container-tools-in-visual-studio"></a>Visual Studio 中的容器工具

包含在 Visual Studio 中，針對使用容器進行開發的工具很容易使用，並可大幅簡化建置、偵錯和部署容器化應用程式。 您可以使用單一專案的容器，或使用容器協調流程搭配 Docker Compose、Service Fabric 或 Kubernetes，來使用容器中的多個服務。

> [!NOTE]
> 本文適用於 Windows 上的 Visual Studio，Visual Studio for Mac 則不支援。

> [!TIP]
> 若要深入了解安裝適用於 Windows 的 Docker，請參閱[適用於 Windows 的 Docker Desktop](https://docs.docker.com/docker-for-windows/)。

## <a name="docker-support-in-visual-studio"></a>Visual Studio 中的 Docker 支援

Docker 支援可供某些 .NET 專案類型使用。  它適用於 ASP.NET 專案、ASP.NET Core 專案，以及 .NET Core 和 .NET Framework 主控台專案。

Visual Studio 中對 Docker 的支援，已針對客戶需求在多個版本中進行了變更。 您可以將兩個層級的 Docker 支援新增至專案中，受支援的選項會因專案類型和 Visual Studio 的版本而異。 對於部分支援的專案類型，如果您只想要單一專案的容器而不需使用協調流程，則可以藉由新增 Docker 支援來實現。  下一個層級是容器協調流程支援，它會為您選擇的特定協調器新增適當的支援檔案。  

::: moniker range="vs-2017"

使用 Visual Studio 2017，您可以使用 Docker Compose 與 Service Fabric 為容器協調流程服務。  如果您安裝 [Visual Studio Tools for Kubernetes](https://aka.ms/get-vsk8stools)，也可以使用 Kubernetes。

> [!NOTE]
> 如果您使用的是 15.8 之前的 Visual Studio 2017 版本，或者您使用的是 .NET Framework 專案範本 (而不是 .NET Core)，則在新增 Docker 支援時，會自動新增使用 Docker Compose 的協調流程支援。 容器協調流程支援會透過 Docker Compose 自動新增至 Visual Studio 2017 (版本 15.0 至 15.7) 和 .NET Framework 專案中。

::: moniker-end

::: moniker range=">=vs-2019"

使用 Visual Studio 2019，您可以使用 Docker Compose、Kubernetes 和 Service Fabric 作為容器協調流程服務。

> [!NOTE]
> 如果您使用的是完整的 .NET Framework 主控台專案範本，則在新增 Docker 支援時，將自動新增對使用 Docker Compose 進行協調流程的支援。
::: moniker-end

[新增 > Docker 支援] 和 [新增 > 容器協調器支援] 命令位於 [方案總管] 中 ASP.NET Core 專案的專案節點右鍵操作功能表 (或操作功能表)，如下列螢幕擷取畫面所示：

![Visual Studio 中的 [新增 Docker 支援] 功能表選項](./media/overview/add-docker-support-menu.png)

### <a name="adding-docker-support-without-orchestration"></a>新增 Docker 支援 (不含協調流程)

您可以透過在 [方案總管] 中選取 [新增] > [Docker 支援]，為現有的專案新增 Docker 支援。 您還可以在專案建立期間，透過在建立新的專案時選取 [啟用 Docker 支援] 來啟用 Docker 支援，如下列螢幕擷取畫面所示：

::: moniker range="vs-2017"
![在 Visual Studio 中為新的 ASP.NET Core Web 應用程式啟用 Docker 支援](./media/overview/enable-docker-support-visual-studio.png)
::: moniker-end
::: moniker range=">=vs-2019"
![在 Visual Studio 中為新的 ASP.NET Core Web 應用程式啟用 Docker 支援](./media/overview/vs-2019/enable-docker-support-visual-studio.png)
::: moniker-end

當您新增或啟用 Docker 支援時，Visual Studio 會將以下內容加入到專案中：

- *Dockerfile* 檔案
- .dockerignore 檔案
- Microsoft.VisualStudio.Azure.Containers.Tools.Targets 的 NuGet 套件參考

::: moniker range=">=vs-2019"
新增 Docker 支援之後，方案看起來像這樣：

![Dockerfile 和.dockerignore 檔案的 [方案總管] 的螢幕擷取畫面](media/overview/vs-2019/dockerfile-dockerignore.png)
::: moniker-end

::: moniker range="vs-2017"
> [!NOTE]
> 在專案建立期間為 ASP.NET 專案 (.NET Framework，而不是 .NET Core 專案) 啟用 Docker 支援時，也會加入容器協調流程支援，如下列螢幕擷取畫面所示。

![針對 ASP.NET 專案啟用 Docker Compose 支援](media/overview/enable-docker-compose-support.png)
::: moniker-end

## <a name="docker-compose-support"></a>Docker Compose 支援

如果要使用 Docker Compose 撰寫多容器解決方案，請將容器協調流程支援新增至您的專案。 如果它們在同一個*docker-compose.yml*文件中定義，則允許您同時運行和調試一組容器（整個解決方案或一組項目）。

若要使用 Docker Compose 新增容器協調流程支援，請以滑鼠右鍵按一下 [方案總管] 中的方案或專案節點，然後選擇 [新增] > [容器協調流程支援]。 然後選擇 [Docker Compose] 以管理容器。

向專案新增容器協調流程支援後，您會看到專案中新增了 *Dockerfile* (如果找不到)，且 [方案總管] 中的方案新增了 **docker-compose** 資料夾，如下所示：

![Visual Studio 中 [方案總管] 中的 Docker 檔案](media/overview/docker-support-solution-explorer.png)

如果 *docker-compose.yml* 已存在，則 Visual Studio 只會向其新增所需的組態程式碼行。

使用 Docker Compose 對要控制的其他專案重複此程序。

## <a name="kubernetes-support"></a>Kubernetes 支援

::: moniker range="vs-2017"
若要新增 Kubernetes 支援，請安裝 [Visual Studio Tools for Kubernetes](https://aka.ms/get-vsk8stools)。
::: moniker-end

有了 Kubernetes 支援，您可以在本機專案和在 [Azure Kubernetes Service (AKS)](/azure/aks) 中執行的 Kubernetes 叢集之間建立連線，從而使用 Visual Studio 修改和偵錯在 AKS 中執行的服務。  這項服務由 [Azure Dev Spaces](/azure/dev-spaces/quickstart-netcore-visualstudio) 提供。 Azure Dev Spaces 還允許您針對開發目的，設定名為 *dev spaces* 的 Kubernetes 服務的個別分支，因此您可以有效率地將生產服務與開發中的工作版本隔離開來，並保持不同的修改彼此完全分隔。

若要向專案新增 Kubernetes 支援，請在新增容器協調流程支援時選擇 **Kubernetes/Helm**。 數個檔案會新增至您的專案，包括設定 Azure Dev Spaces 的 *azds.yaml*，和描述 Kubernetes 服務結構的 Helm 圖表。

## <a name="service-fabric-support"></a>Service Fabric 支援

使用 Visual Studio 中的 Service Fabric 工具，您可以開發及偵錯 Azure Service Fabric、在本機執行和偵錯，並部署至 Azure。

::: moniker range="vs-2017"
已安裝 Azure 開發工作負載的 Visual Studio 2017 版本 15.9 及更新版本，支援使用 Windows 容器和 Service Fabric 協調流程開發容器化微服務。
::: moniker-end
::: moniker range=">=vs-2019"
Visual Studio 2019 支援使用 Windows 容器和 Service Fabric 協調流程的開發容器化微服務。
::: moniker-end

如需詳細的教學課程，請參閱[教學課程：將 Windows 容器中的 .NET 應用程式部署至 Azure Service Fabric](/azure/service-fabric/service-fabric-host-app-in-a-container)。

如需有關 Azure Service Fabric 的詳細資訊，請參閱 [Service Fabric](/azure/service-fabric)。

## <a name="continuous-delivery-and-continuous-integration-cicd"></a>持續傳遞和持續整合 (CI/CD)

Visual Studio 可與 Azure Pipelines 輕鬆整合，實現服務程式碼和設定的自動化和持續整合與傳遞。 若要開始，請參閱[建立您的第一個管線](/azure/devops/pipelines/create-first-pipeline?view=azure-devops&tabs=tfs-2018-2)。

針對 Service Fabric，請參閱[教學課程：使用 Azure DevOps Projects 將 ASP.NET Core 應用程式部署至 Azure Service Fabric](/azure/devops-project/azure-devops-project-service-fabric)。

針對 Kubernetes，請參閱[將 Docker 容器應用程式部署至 Azure Kubernetes Service](/azure/devops/pipelines/apps/cd/deploy-aks?view=azure-devops)。

## <a name="next-steps"></a>後續步驟

如需服務實作和使用 Visual Studio 工具以處理容器的更多詳細資訊，請閱讀下列文章：

[對本機 Docker 容器中的應用程式偵錯](vs-azure-tools-docker-edit-and-refresh.md)

[使用 Visual Studio 將 ASP.NET 容器部署到容器登錄](vs-azure-tools-docker-hosting-web-apps-in-docker.md)
