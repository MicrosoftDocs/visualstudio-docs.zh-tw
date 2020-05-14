---
title: 庫伯內斯工具教程 |微軟文件
ms.date: 06/08/2018
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.workload:
- azure
ms.openlocfilehash: 931f8c2a6d3be130ef78f59f9b3853d28fad8cd4
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444683"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>開始使用視覺工作室庫伯奈斯工具

視覺工作室庫伯奈斯工具有助於簡化針對庫伯奈斯的容器化應用程式的開發。 Visual Studio 可以自動建立支援 Kubernetes 部署所需的配置即代碼檔案,如 Dockerfile 和 Helm 圖表。 您可以使用 Azure 開發空間在即時 Azure 庫伯內斯服務 (AKS) 群集中調試代碼,或者直接從 Visual Studio 內部發布到 AKS 群集。

本教程介紹使用 Visual Studio 將 Kubernetes 支援添加到專案併發佈到 AKS。 如果您主要對使用 Azure[開發人員空間](/azure/dev-spaces/)來除錯和測試在 AKS 執行的項目感興趣,則可以跳到[Azure 開發空間教學](/azure/dev-spaces/get-started-netcore-visualstudio)。

## <a name="prerequisites"></a>Prerequisites

要利用此新功能,您需要:

::: moniker range="vs-2017"
- 最新版本的[Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)具有*ASP.NET和 Web 開發*工作負載。
- [Visual Studio 的庫伯內特工具](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes)可單獨下載。
::: moniker-end
::: moniker range="vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)，其中包含 *ASP.NET 和 Web 部署*工作負載。
::: moniker-end
- 如果要建構 Docker 映像、除錯本地執行的 Docker 容器或發布到 AKS,則安裝在開發工作站(即運行 Visual Studio 的位置)上安裝的[Docker Desktop。](https://store.docker.com/editions/community/docker-ce-desktop-windows) (使用 Azure 開發人員空間在 AKS 中建構和除錯 Docker 容器*不需要*Docker。
::: moniker range="vs-2017"
- 如果要從可視化工作室發佈到 AKS(使用 Azure 開發空間在 AKS 中調試*不需要*):

    1. [AKS 發佈工具](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes), 可單獨下載.

    1. Azure Kubernetes Service 叢集。 有關詳細資訊,請參閱建立[AKS 群組 。](/azure/aks/kubernetes-walkthrough-portal#create-an-aks-cluster) 請務必從開發工作站[連接到叢集](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster)。

    1. Helm CLI 安裝在您的開發工作站上。 有關詳細資訊,請參閱[安裝頭盔](https://github.com/helm/helm-www/blob/master/content/en/docs/helm/helm_install.md)。

    1. 使用`helm init`指令針對 AKS 群集配置的 Helm。 有關如何執行此操作的詳細資訊,請參閱[如何配置 Helm](/azure/aks/kubernetes-helm#configure-helm)。
::: moniker-end

## <a name="create-a-new-kubernetes-project"></a>建立新的庫伯內斯項目

::: moniker range="vs-2017"

安裝適當的工具後,啟動 Visual Studio 並創建新專案。 在 **"雲**"下,選擇**庫伯內斯專案的容器應用程式**類型。 選擇此項目類型並選擇 **「確定**」。

![建立新的庫伯奈斯應用項目的螢幕擷取](media/tutorial-kubernetes-tools/k8s-tools-new-k8s-app.png)

::: moniker-end
::: moniker range=">= vs-2019"

在視覺化工作室啟動視窗中,搜尋*庫伯內特*斯,然後選擇**庫伯奈斯的容器應用程式**。

![建立新的庫伯奈斯應用項目的螢幕擷取](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app1.png)

提供專案名稱。

![建立新的庫伯奈斯應用項目的螢幕擷取](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app2.png)

::: moniker-end

然後,您可以選擇要創建哪些類型的ASP.NET酷 Web 應用程式。 選擇 [Web 應用程式]****。 通常的**啟用 Docker 支援**選項不會出現在此對話框中。  默認情況下,為 Kubernetes 的容器應用程式啟用 Docker 支援。

::: moniker range="vs-2017"

![Web 應用選擇的螢幕擷取](media/tutorial-kubernetes-tools/k8s-tools-web-app-selection-screen.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Web 應用選擇的螢幕擷取](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-web-app-selection-screen-2019.png)

::: moniker-end

## <a name="add-kubernetes-support-to-an-existing-project"></a>將庫伯內斯支援新增到現有項目

或者,您可以將 Kubernetes 支援添加到現有的ASP.NET核心 Web 應用程式專案中。 為此,請右鍵單擊項目,然後選擇 **「添加** > **容器協調器支援**」。。

::: moniker range="vs-2017"

![新增容器協調器選單項目截圖](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator.png)

::: moniker-end
::: moniker range=">=vs-2019"

![新增容器協調器選單項目截圖](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-add-container-orchestrator-2019.png)

::: moniker-end

在對話方塊中,選擇**庫伯奈斯/赫爾姆**並選擇 **「確定**」。

![新增容器協調器對話框的螢幕截圖](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>視覺工作室為您建立的內容

**為 Kubernetes 專案建立新的容器應用程式**或將 Kubernetes 容器協調器支援添加到現有專案後,您會看到專案中的一些其他檔,這些文件有助於部署到庫貝內內斯。

::: moniker range="vs-2017"

![新增容器協調器支援後的解決方案資源管理員擷取](media/tutorial-kubernetes-tools/k8s-tools-solution-explorer.png)

::: moniker-end
::: moniker range="vs-2019"

![新增容器協調器支援後的解決方案資源管理員擷取](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-solution-explorer-2019.png)

::: moniker-end

新增的檔案包括:

- Dockerfile,它允許您生成承載此 Web 應用程式的 Docker 容器映射。 如您所見,可視化工作室工具在調試和部署到 Kubernetes 時利用此 Dockerfile。 如果您喜歡直接使用 Docker 映射,可以右鍵單擊 Dockerfile 並選擇 **"構建 Docker 映射**"。

   ![產生 Docker 映像選項的螢幕擷取](media/tutorial-kubernetes-tools/k8s-tools-build-docker-image.png)

- 一個赫爾姆圖表和一個*圖表*資料夾。 這些 yaml 檔構成應用程式的 Helm 圖表,您可以使用該圖表將其部署到庫伯奈斯。 有關 Helm 的詳細資訊,請[https://www.helm.sh](https://www.helm.sh)參閱 。

- *阿茲茲.亞瑪律*. 這包含 Azure 開發空間的設置,在 Azure Kubernetes 服務中提供快速的反覆運算調試體驗。 有關詳細資訊,請參閱[Azure 開發空間文件](/azure/dev-spaces/azure-dev-spaces)。

::: moniker range="vs-2017"

## <a name="publish-to-azure-kubernetes-service-aks"></a>發布到 Azure 庫伯奈斯服務 (AKS)

完成所有這些檔後,您可以使用 Visual Studio IDE 編寫和調試應用程式代碼,就像您一直擁有一樣。 您還可以使用 Azure[開發人員空間](/azure/dev-spaces/)快速執行和調試在 AKS 群集中即時運行的代碼。 有關詳細資訊,請參閱[Azure 開發空間教程](/azure/dev-spaces/get-started-netcore-visualstudio)

代碼按所需方式運行後,可以直接從 Visual Studio 發佈到 AKS 群集。

為此,您首先需要仔細檢查是否安裝了用於發佈到 AKS 的專案下的[「先決條件」](#prerequisites)部分中描述的所有內容,並運行連結中給出的所有命令行步驟。 然後,設置發佈設定檔,將容器映射發佈到 Azure 容器註冊表 (ACR)。 然後 AKS 可以從 ACR 中提取容器映射並將其部署到群集中。

1. 在**解決方案資源管理器**中,右鍵單擊*您的專案*並選擇 **「發布**」。

   ![發佈選單項目截圖](media/tutorial-kubernetes-tools/k8s-tools-publish-project.png)

2. 在 **「發布」** 螢幕中,選擇**容器註冊表**作為發佈目標,然後按照提示選擇容器註冊表。 如果還沒有容器註冊表,請選擇 **「創建新 Azure 容器註冊表**」以從 Visual Studio 創建註冊表。 有關詳細資訊,請參閱[將容器發布到 Azure 容器註冊表](hosting-web-apps-in-docker.md)。

   ![選擇發行目標螢幕的螢幕擷取](media/tutorial-kubernetes-tools/k8s-tools-publish-to-acr.png)

3. 回到解決方案資源管理器中,右鍵單擊*解決方案*,然後按兩下「**發布到 Azure AKS」。。**

   ![發表到 Azure AKS 選單的螢幕擷圖](media/tutorial-kubernetes-tools/k8s-tools-publish-solution.png)

4. 選擇訂閱和 AKS 群集,以及您剛剛建立的 ACR 發表設定檔。 然後按一下 **[確定]**。

   ![在 AKS 螢幕的螢幕截圖](media/tutorial-kubernetes-tools/k8s-tools-publish-to-aks.png)

   這將帶您到 **「發布到 Azure AKS」** 螢幕。

5. 選擇 **「設定頭盔」** 連結以更新用於在伺服器上安裝 Helm 圖表的命令列。

   ![設定頭盔連結的螢幕截圖](media/tutorial-kubernetes-tools/k8s-tools-configure-helm.png)

   如果存在要指定的自定義命令列參數(如其他 Kubernetes 上下文或圖表名稱,則更新命令行非常有用)。

   ![頭盔配置螢幕的螢幕截圖](media/tutorial-kubernetes-tools/k8s-tools-helm-configure-screen.png)

6. 準備好部署後,按下 **「發布」** 按鈕將應用程式發佈到 AKS。

   ![發表到 Azure AKS 螢幕的螢幕擷取](media/tutorial-kubernetes-tools/k8s-tools-publish-screen.png)

::: moniker-end

恭喜！ 現在,您可以將 Visual Studio 的全部功能用於所有 Kubernetes 應用開發。

## <a name="next-steps"></a>後續步驟

通過閱讀[AKS 文檔](/azure/aks),瞭解有關 Azure 上的庫伯內斯開發的更多知識。

透過閱讀[Azure 開發空間文件](/azure/dev-spaces/)瞭解有關 Azure 開發空間的更多資訊
