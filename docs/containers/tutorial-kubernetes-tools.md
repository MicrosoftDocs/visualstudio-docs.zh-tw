---
title: Kubernetes 工具教學課程 |Microsoft Docs
ms.date: 06/08/2018
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.workload:
- azure
ms.openlocfilehash: 8b6aef437519a4fe92f11a3b21546b3dda9981bb
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188767"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>開始使用 Visual Studio Kubernetes 工具

Visual Studio Kubernetes 工具可協助簡化以 Kubernetes 為目標的容器化應用程式開發。 Visual Studio 可以自動建立支援 Kubernetes 部署所需的設定即程式碼檔案，例如 Dockerfile 和 Helm 圖表。 您可以使用 Azure Dev Spaces 在 live Azure Kubernetes Service （AKS）叢集中進行程式碼的驗證，或從 Visual Studio 內部直接發行至 AKS 叢集。

本教學課程涵蓋如何使用 Visual Studio 將 Kubernetes 支援新增至專案，併發布至 AKS。 如果您主要想要使用[Azure Dev Spaces](https://aka.ms/get-azds)來對 AKS 中執行的專案進行偵錯工具和測試，您可以改為跳至[Azure Dev Spaces 教學](/azure/dev-spaces/get-started-netcore-visualstudio)課程。

## <a name="prerequisites"></a>Prerequisites

若要利用這種新功能，您需要：

::: moniker range="vs-2017"
- [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)的最新版本，其中包含*ASP.NET 和 網頁程式開發*工作負載。
- 適用[于 Visual Studio 的 Kubernetes 工具](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes)，以個別下載的形式提供。
::: moniker-end
::: moniker range="vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)搭配*ASP.NET 和 網頁程式開發*工作負載。
::: moniker-end
- [Docker Desktop](https://store.docker.com/editions/community/docker-ce-desktop-windows)安裝在您的開發工作站上（也就是您執行 Visual Studio 的位置），如果您想要建立 Docker 映射、在本機上對 docker 容器進行偵錯工具，或發佈至 AKS。 （使用 Azure Dev Spaces 在 AKS 中建立和偵測 Docker 容器並*不*需要 docker）。
::: moniker range="vs-2017"
- 如果您想要從 Visual Studio 發行至 AKS （*不*需要使用 AZURE DEV SPACES 在 AKS 中進行偵錯工具）：

    1. [AKS 發行工具](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes)可供個別下載。

    1. Azure Kubernetes Service 叢集。 如需詳細資訊，請參閱[建立 AKS](/azure/aks/kubernetes-walkthrough-portal#create-an-aks-cluster)叢集。 請務必從您的開發工作站[連接到](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster)叢集。

    1. Helm CLI 安裝在您的開發工作站上。 如需詳細資訊，請參閱[安裝 Helm](https://github.com/kubernetes/helm/blob/master/docs/install.md)。

    1. Helm 會使用 `helm init` 命令，針對您的 AKS 叢集進行設定。 如需如何執行此動作的詳細資訊，請參閱 how [to Configure Helm](/azure/aks/kubernetes-helm#configure-helm)。
::: moniker-end

## <a name="create-a-new-kubernetes-project"></a>建立新的 Kubernetes 專案

::: moniker range="vs-2017"

安裝適當的工具之後，請啟動 Visual Studio，然後建立新的專案。 在 [**雲端**] 底下，選擇 [Kubernetes] 專案類型的 [**容器應用程式**]。 選取此專案類型，然後選擇 **[確定]** 。

![建立新 Kubernetes 應用程式專案的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-new-k8s-app.png)

::: moniker-end
::: moniker range=">= vs-2019"

在 [Visual Studio 開始] 視窗中，搜尋*Kubernetes*，然後選擇**要 Kubernetes 的容器應用程式**。

![建立新 Kubernetes 應用程式專案的螢幕擷取畫面](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app1.png)

提供專案名稱。

![建立新 Kubernetes 應用程式專案的螢幕擷取畫面](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app2.png)

::: moniker-end

然後，您可以選擇要建立哪一種類型的 ASP.NET Core web 應用程式。 選擇 [Web 應用程式]。 一般的 [**啟用 Docker 支援**] 選項不會出現在此對話方塊上。  針對 Kubernetes 的容器應用程式，預設會啟用 Docker 支援。

::: moniker range="vs-2017"

![Web 應用程式選取專案的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-web-app-selection-screen.png)

::: moniker-end
::: moniker range=">=vs-2019"

![Web 應用程式選取專案的螢幕擷取畫面](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-web-app-selection-screen-2019.png)

::: moniker-end

## <a name="add-kubernetes-support-to-an-existing-project"></a>將 Kubernetes 支援新增至現有的專案

或者，您可以將 Kubernetes 支援新增至現有的 ASP.NET Core web 應用程式專案。 若要這麼做，請以滑鼠右鍵按一下專案，然後選擇 **新增** > **容器協調器支援**。

::: moniker range="vs-2017"

![[新增容器協調器] 功能表項目的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator.png)

::: moniker-end
::: moniker range=">=vs-2019"

![[新增容器協調器] 功能表項目的螢幕擷取畫面](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-add-container-orchestrator-2019.png)

::: moniker-end

在對話方塊中，選取 [ **Kubernetes]/[Helm** ]，然後選擇 **[確定]** 。

![[新增容器協調器] 對話方塊的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>Visual Studio 為您建立的內容

為 Kubernetes 專案建立新的**容器應用程式**，或將 Kubernetes 容器協調器支援新增至現有的專案之後，您會在專案中看到一些有助於部署至 Kubernetes 的其他檔案。

::: moniker range="vs-2017"

![新增容器協調器支援之後的方案總管螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-solution-explorer.png)

::: moniker-end
::: moniker range="vs-2019"

![新增容器協調器支援之後的方案總管螢幕擷取畫面](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-solution-explorer-2019.png)

::: moniker-end

新增的檔案包括：

- 一種 Dockerfile，可讓您產生裝載此 web 應用程式的 Docker 容器映射。 如您所見，Visual Studio 工具會在進行調試和部署至 Kubernetes 時，利用此 Dockerfile。 如果您想要直接使用 Docker 映射，您可以在 Dockerfile 上按一下滑鼠右鍵，然後選擇 [**組建 Docker 映射**]。

   ![組建 Docker 映射選項的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-build-docker-image.png)

- Helm 圖表和*圖表*資料夾。 這些 yaml 檔組成應用程式的 Helm 圖表，您可以用它來將它部署到 Kubernetes。 如需 Helm 的詳細資訊，請參閱[https://www.helm.sh](https://www.helm.sh)。

- *azds. yaml*。 這包含 Azure Dev Spaces 的設定，可在 Azure Kubernetes Service 中提供快速、反復的偵錯工具體驗。 如需詳細資訊，請參閱[Azure Dev Spaces 檔](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces)。

::: moniker range="vs-2017"

## <a name="publish-to-azure-kubernetes-service-aks"></a>發行至 Azure Kubernetes Service （AKS）

所有這些檔案都備妥之後，您就可以使用 Visual Studio IDE 來撰寫和偵錯工具程式碼，就像往常一樣。 您也可以使用[Azure Dev Spaces](https://aka.ms/get-azds)來快速地執行和偵錯工具代碼，在 AKS 叢集中執行。 如需詳細資訊，請參閱[Azure Dev Spaces 教學](https://docs.microsoft.com/azure/dev-spaces/get-started-netcore-visualstudio)課程

當您的程式碼以您想要的方式執行時，您可以直接從 Visual Studio 發行至 AKS 叢集。

若要這樣做，您必須先仔細檢查是否已安裝所有內容，如發佈至 AKS 專案底下的[必要條件](#prerequisites)一節中所述，並執行連結中提供的所有命令列步驟。 然後，設定發行設定檔，將您的容器映射發佈至 Azure Container Registry （ACR）。 然後，AKS 可以從 ACR 提取您的容器映射，並將它部署到叢集。

1. 在**方案總管**中，以滑鼠右鍵按一下您的*專案*，然後選擇 [**發行**]。

   ![[發行] 功能表項目的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-publish-project.png)

2. 在 [**發佈**] 畫面中，選擇 [ **Container registry** ] 作為發佈目標，然後依照提示來選取您的容器登錄。 如果您還沒有容器登錄，請選擇 [**建立新的 Azure Container Registry** ]，從 Visual Studio 建立一個。 如需詳細資訊，請參閱將[容器發佈至 Azure Container Registry](hosting-web-apps-in-docker.md)。

   ![[挑選發行目標] 畫面的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-publish-to-acr.png)

3. 回到方案總管，以滑鼠右鍵按一下您的*方案*，然後按一下 [**發佈至 Azure AKS**]。

   ![[發行至 Azure AKS] 功能表項目的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-publish-solution.png)

4. 選擇您的訂用帳戶和 AKS 叢集，以及您剛才建立的 ACR 發行設定檔。 然後按一下 [確定]。

   ![[發佈至 AKS] 畫面的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-publish-to-aks.png)

   這會帶您前往 [**發行至 AZURE AKS** ] 畫面。

5. 選擇 [**設定 Helm** ] 連結，以更新在伺服器上安裝 Helm 圖表所用的命令列。

   ![設定 Helm 連結的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-configure-helm.png)

   如果您想要指定自訂命令列引數，例如不同的 Kubernetes 內容或圖表名稱，則更新命令列會很有用。

   ![Helm 設定畫面的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-helm-configure-screen.png)

6. 當您準備好部署時，請按一下 [**發佈**] 按鈕，將您的應用程式發佈至 AKS。

   ![[發佈至 Azure AKS] 畫面的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-publish-screen.png)

::: moniker-end

恭喜您！ 您現在可以針對所有的 Kubernetes 應用程式開發，使用完整的 Visual Studio 功能。

## <a name="next-steps"></a>後續步驟

閱讀[AKS 檔](/azure/aks)，以深入瞭解 Azure 上的 Kubernetes 開發。

閱讀[Azure Dev Spaces 檔](https://aka.ms/get-azds)，深入瞭解 Azure Dev Spaces
