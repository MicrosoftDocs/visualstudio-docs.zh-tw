---
title: 庫伯內斯工具教程 |微軟文檔
ms.date: 06/08/2018
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.workload:
- azure
ms.openlocfilehash: f5868f97301eba62d16ea68cdaa0c97c8e20edd1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75916954"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>開始使用視覺工作室庫伯奈斯工具

視覺工作室庫伯奈斯工具有助於簡化針對庫伯奈斯的容器化應用程式的開發。 Visual Studio 可以自動創建支援 Kubernetes 部署所需的配置即代碼檔，如 Dockerfile 和 Helm 圖表。 您可以使用 Azure 開發空間在即時 Azure 庫伯內斯服務 （AKS） 群集中調試代碼，或者直接從 Visual Studio 內部發佈到 AKS 群集。

本教程介紹使用 Visual Studio 將 Kubernetes 支援添加到專案併發布到 AKS。 如果您主要對使用 Azure[開發人員空間](/azure/dev-spaces/)來調試和測試在 AKS 中運行的專案感興趣，則可以跳轉到[Azure 開發空間教程](/azure/dev-spaces/get-started-netcore-visualstudio)。

## <a name="prerequisites"></a>必要條件

要利用此新功能，您需要：

::: moniker range="vs-2017"
- 最新版本的[Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)具有*ASP.NET和 Web 開發*工作負載。
- [Visual Studio 的庫伯內特工具](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes)可單獨下載。
::: moniker-end
::: moniker range="vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)，其中包含 *ASP.NET 和 Web 部署*工作負載。
::: moniker-end
- 如果要構建 Docker 映射、調試本地運行的 Docker 容器或發佈到 AKS，則安裝在開發工作站（即運行 Visual Studio 的位置）上安裝的[Docker Desktop。](https://store.docker.com/editions/community/docker-ce-desktop-windows) （使用 Azure 開發人員空間在 AKS 中構建和調試 Docker 容器*不需要*Docker。
::: moniker range="vs-2017"
- 如果要從視覺化工作室發佈到 AKS（使用 Azure 開發空間在 AKS 中調試*不需要*）：

    1. [AKS 發佈工具](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes)， 可單獨下載.

    1. Azure Kubernetes Service 叢集。 有關詳細資訊，請參閱創建[AKS 群集](/azure/aks/kubernetes-walkthrough-portal#create-an-aks-cluster)。 請務必從開發工作站[連接到群集](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster)。

    1. Helm CLI 安裝在您的開發工作站上。 有關詳細資訊，請參閱[安裝頭盔](https://github.com/kubernetes/helm/blob/master/docs/install.md)。

    1. 使用`helm init`命令針對 AKS 群集配置的 Helm。 有關如何執行此操作的詳細資訊，請參閱[如何配置 Helm](/azure/aks/kubernetes-helm#configure-helm)。
::: moniker-end

## <a name="create-a-new-kubernetes-project"></a>創建新的庫伯內斯專案

::: moniker range="vs-2017"

安裝適當的工具後，啟動 Visual Studio 並創建新專案。 在 **"雲**"下，選擇**庫伯內斯專案的容器應用程式**類型。 選擇此專案類型並選擇 **"確定**"。

![創建新的庫伯奈斯應用專案的螢幕截圖](media/tutorial-kubernetes-tools/k8s-tools-new-k8s-app.png)

::: moniker-end
::: moniker range=">= vs-2019"

在視覺化工作室啟動視窗中，搜索*庫伯內特*斯，然後選擇**庫伯奈斯的容器應用程式**。

![創建新的庫伯奈斯應用專案的螢幕截圖](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app1.png)

提供專案名稱。

![創建新的庫伯奈斯應用專案的螢幕截圖](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app2.png)

::: moniker-end

然後，您可以選擇要創建哪些類型的ASP.NET酷 Web 應用程式。 選擇 [Web 應用程式]****。 通常的**啟用 Docker 支援**選項不會出現在此對話方塊中。  預設情況下，為 Kubernetes 的容器應用程式啟用 Docker 支援。

::: moniker range="vs-2017"

![Web 應用選擇的螢幕截圖](media/tutorial-kubernetes-tools/k8s-tools-web-app-selection-screen.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Web 應用選擇的螢幕截圖](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-web-app-selection-screen-2019.png)

::: moniker-end

## <a name="add-kubernetes-support-to-an-existing-project"></a>將庫伯內斯支援添加到現有專案

或者，您可以將 Kubernetes 支援添加到現有的ASP.NET核心 Web 應用程式專案中。 為此，請按右鍵專案，然後選擇 **"添加** > **容器協調器支援**"。

::: moniker range="vs-2017"

![添加容器協調器功能表項目的螢幕截圖](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator.png)

::: moniker-end
::: moniker range=">=vs-2019"

![添加容器協調器功能表項目的螢幕截圖](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-add-container-orchestrator-2019.png)

::: moniker-end

在對話方塊中，選擇**庫伯奈斯/赫爾姆**並選擇 **"確定**"。

![添加容器協調器對話方塊的螢幕截圖](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>視覺工作室為您創建的內容

**為 Kubernetes 專案創建新的容器應用程式**或將 Kubernetes 容器協調器支援添加到現有專案後，您會看到專案中的一些其他檔，這些檔有助於部署到庫貝內內斯。

::: moniker range="vs-2017"

![添加容器協調器支援後的解決方案資源管理器螢幕截圖](media/tutorial-kubernetes-tools/k8s-tools-solution-explorer.png)

::: moniker-end
::: moniker range="vs-2019"

![添加容器協調器支援後的解決方案資源管理器螢幕截圖](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-solution-explorer-2019.png)

::: moniker-end

添加的檔包括：

- Dockerfile，它允許您生成承載此 Web 應用程式的 Docker 容器映射。 如您所見，視覺化工作室工具在調試和部署到 Kubernetes 時利用此 Dockerfile。 如果您喜歡直接使用 Docker 映射，可以按右鍵 Dockerfile 並選擇 **"構建 Docker 映射**"。

   ![生成 Docker 映射選項的螢幕截圖](media/tutorial-kubernetes-tools/k8s-tools-build-docker-image.png)

- 一個赫爾姆圖表和一個*圖表*資料夾。 這些 yaml 檔構成應用程式的 Helm 圖表，您可以使用該圖表將其部署到庫伯奈斯。 有關 Helm 的詳細資訊，請參閱[https://www.helm.sh](https://www.helm.sh)。

- *阿茲茲.亞瑪律*. 這包含 Azure 開發空間的設置，在 Azure Kubernetes 服務中提供快速的反覆運算調試體驗。 有關詳細資訊，請參閱[Azure 開發空間文檔](/azure/dev-spaces/azure-dev-spaces)。

::: moniker range="vs-2017"

## <a name="publish-to-azure-kubernetes-service-aks"></a>發佈到 Azure 庫伯奈斯服務 （AKS）

完成所有這些檔後，您可以使用 Visual Studio IDE 編寫和調試應用程式代碼，就像您一直擁有一樣。 您還可以使用 Azure[開發人員空間](/azure/dev-spaces/)快速運行和調試在 AKS 群集中即時運行的代碼。 有關詳細資訊，請參閱[Azure 開發空間教程](/azure/dev-spaces/get-started-netcore-visualstudio)

代碼按所需方式運行後，可以直接從 Visual Studio 發佈到 AKS 群集。

為此，您首先需要仔細檢查是否安裝了用於發佈到 AKS 的專案下的["先決條件"](#prerequisites)部分中描述的所有內容，並運行連結中給出的所有命令列步驟。 然後，設置發佈設定檔，將容器映射發佈到 Azure 容器註冊表 （ACR）。 然後 AKS 可以從 ACR 中提取容器映射並將其部署到群集中。

1. 在**解決方案資源管理器**中，按右鍵*您的專案*並選擇 **"發佈**"。

   ![發佈功能表項目的螢幕截圖](media/tutorial-kubernetes-tools/k8s-tools-publish-project.png)

2. 在 **"發佈"** 螢幕中，選擇**容器註冊表**作為發佈目標，然後按照提示選擇容器註冊表。 如果還沒有容器註冊表，請選擇 **"創建新 Azure 容器註冊表**"以從 Visual Studio 創建註冊表。 有關詳細資訊，請參閱[將容器發佈到 Azure 容器註冊表](hosting-web-apps-in-docker.md)。

   ![選擇發佈目標螢幕的螢幕截圖](media/tutorial-kubernetes-tools/k8s-tools-publish-to-acr.png)

3. 回到解決方案資源管理器中，按右鍵*解決方案*，然後按一下"**發佈到 Azure AKS**"。

   ![發佈到 Azure AKS 功能表項目的螢幕截圖](media/tutorial-kubernetes-tools/k8s-tools-publish-solution.png)

4. 選擇訂閱和 AKS 群集，以及您剛剛創建的 ACR 發佈設定檔。 然後按一下 **[確定]**。

   ![發佈到 AKS 螢幕的螢幕截圖](media/tutorial-kubernetes-tools/k8s-tools-publish-to-aks.png)

   這將帶您到 **"發佈到 Azure AKS"** 螢幕。

5. 選擇 **"配置頭盔"** 連結以更新用於在伺服器上安裝 Helm 圖表的命令列。

   ![配置頭盔連結的螢幕截圖](media/tutorial-kubernetes-tools/k8s-tools-configure-helm.png)

   如果存在要指定的自訂命令列參數（如其他 Kubernetes 上下文或圖表名稱，則更新命令列非常有用）。

   ![頭盔配置螢幕的螢幕截圖](media/tutorial-kubernetes-tools/k8s-tools-helm-configure-screen.png)

6. 準備好部署後，按一下 **"發佈"** 按鈕將應用程式發佈到 AKS。

   ![發佈到 Azure AKS 螢幕的螢幕截圖](media/tutorial-kubernetes-tools/k8s-tools-publish-screen.png)

::: moniker-end

恭喜！ 現在，您可以將 Visual Studio 的全部功能用於所有 Kubernetes 應用開發。

## <a name="next-steps"></a>後續步驟

通過閱讀[AKS 文檔](/azure/aks)，瞭解有關 Azure 上的庫伯內斯開發的更多知識。

通過閱讀[Azure 開發空間文檔](/azure/dev-spaces/)瞭解有關 Azure 開發空間的更多資訊
