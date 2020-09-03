---
title: Kubernetes 工具教學課程 |Microsoft Docs
ms.date: 06/08/2018
ms.topic: tutorial
author: ghogen
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.workload:
- azure
ms.openlocfilehash: 7778019e73119a4b8b1a5842bb7a8c04ef017143
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "87913297"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>開始使用 Visual Studio Kubernetes 工具

Visual Studio Kubernetes 工具有助於簡化以 Kubernetes 為目標的容器化應用程式開發。 Visual Studio 可以自動建立支援 Kubernetes 部署所需的設定即程式碼檔案，例如 Dockerfile 和 Helm 圖表。 您可以使用 Azure Dev Spaces 在即時 Azure Kubernetes Service 中進行程式碼的偵錯工具 (AKS) 叢集，或從 Visual Studio 內部直接發行至 AKS 叢集。

本教學課程說明如何使用 Visual Studio 將 Kubernetes 支援新增至專案，並將其發佈至 AKS。 如果您的主要興趣是使用 [Azure Dev Spaces](/azure/dev-spaces/) 來對 AKS 中執行的專案進行偵錯工具和測試，您可以跳到 [Azure Dev Spaces 教學](/azure/dev-spaces/get-started-netcore-visualstudio) 課程。

## <a name="prerequisites"></a>先決條件

若要利用這種新功能，您將需要：

::: moniker range="vs-2017"
- *ASP.NET 和 網頁程式開發*工作負載的最新版本[Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 。
- [Visual Studio 的 Kubernetes 工具](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes)，可個別下載。
::: moniker-end
::: moniker range="vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)，其中包含 *ASP.NET 和 Web 部署*工作負載。
::: moniker-end
- 在您的開發工作站上安裝的[Docker Desktop](https://store.docker.com/editions/community/docker-ce-desktop-windows) (也就是，如果您想要建立 docker 映射、將在本機執行的 docker 容器進行偵錯工具，或發佈至 AKS，您可以在其中執行 Visual Studio) 。 使用 Azure Dev Spaces 在 AKS 中建立及偵測 Docker 容器時， *不* 需要 (docker。 ) 
::: moniker range="vs-2017"
- 如果您想要從 Visual Studio 發行至 AKS， (使用 Azure Dev Spaces) ， *不* 需要在 AKS 中進行的偵錯工具：

    1. 以個別下載的形式提供的 [AKS 發行工具](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-tools-for-kubernetes)。

    1. Azure Kubernetes Service 叢集。 如需詳細資訊，請參閱 [建立 AKS](/azure/aks/kubernetes-walkthrough-portal#create-an-aks-cluster)叢集。 請務必從您的開發工作站 [連接到](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster) 叢集。

    1. 在您的開發工作站上安裝 Helm CLI。 如需詳細資訊，請參閱 [安裝 Helm](https://github.com/helm/helm-www/blob/master/content/en/docs/helm/helm_install.md)。

    1. 使用命令針對您的 AKS 叢集設定的 Helm `helm init` 。 如需有關如何進行此作業的詳細資訊，請參閱 [如何設定 Helm](/azure/aks/kubernetes-helm#configure-helm)。
::: moniker-end

## <a name="create-a-new-kubernetes-project"></a>建立新的 Kubernetes 專案

::: moniker range="vs-2017"

一旦安裝了適當的工具，請啟動 Visual Studio，然後建立新專案。 在 [ **雲端**] 下，選擇 Kubernetes 專案類型的 **容器應用程式** 。 選取此專案類型，然後選擇 **[確定]**。

![建立新 Kubernetes 應用程式專案的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-new-k8s-app.png)

::: moniker-end
::: moniker range=">= vs-2019"

在 Visual Studio 開始] 視窗中，搜尋 *Kubernetes*，然後選擇 **Kubernetes 的容器應用程式**。

![建立新 Kubernetes 應用程式專案的螢幕擷取畫面](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app1.png)

提供專案名稱。

![建立新 Kubernetes 應用程式專案的螢幕擷取畫面](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-new-k8s-app2.png)

::: moniker-end

然後，您可以選擇要建立哪一種 ASP.NET Core 的 web 應用程式。 選擇 [Web 應用程式]****。 一般的 [ **啟用 Docker 支援** ] 選項不會出現在此對話方塊中。  針對 Kubernetes 的容器應用程式，預設會啟用 Docker 支援。

::: moniker range="vs-2017"

![選取 web 應用程式的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-web-app-selection-screen.png)

::: moniker-end
::: moniker range=">=vs-2019"

![選取 web 應用程式的螢幕擷取畫面](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-web-app-selection-screen-2019.png)

::: moniker-end

## <a name="add-kubernetes-support-to-an-existing-project"></a>將 Kubernetes 支援新增至現有的專案

或者，您可以將 Kubernetes 支援新增至現有的 ASP.NET Core web 應用程式專案。 若要這樣做，請以滑鼠右鍵按一下專案，然後選擇 [**新增**  >  **容器協調器支援**]。

::: moniker range="vs-2017"

![[新增容器協調器] 功能表項目的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator.png)

::: moniker-end
::: moniker range=">=vs-2019"

![[新增容器協調器] 功能表項目的螢幕擷取畫面](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-add-container-orchestrator-2019.png)

::: moniker-end

在對話方塊中，選取 [ **Kubernetes]/[Helm** ]，然後選擇 **[確定]**。

![[新增容器協調器] 對話方塊的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>Visual Studio 為您建立的內容

為 Kubernetes 專案建立新的 **容器應用程式** ，或將 Kubernetes 容器協調器支援新增至現有的專案之後，您會在專案中看到一些額外的檔案，以便部署到 Kubernetes。

::: moniker range="vs-2017"

![新增容器協調器支援之後方案總管的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-solution-explorer.png)

::: moniker-end
::: moniker range="vs-2019"

![新增容器協調器支援之後方案總管的螢幕擷取畫面](media/tutorial-kubernetes-tools/vs-2019/k8s-tools-solution-explorer-2019.png)

::: moniker-end

新增的檔案如下：

- Dockerfile，可讓您產生裝載此 web 應用程式的 Docker 容器映射。 如您所見，在 Dockerfile 錯和部署至 Kubernetes 時，Visual Studio 工具會利用這個。 如果您想要直接使用 Docker 映射，您可以在 Dockerfile 上按一下滑鼠右鍵，然後選擇 [ **建立 Docker 映射**]。

   ![[組建 Docker 映射] 選項的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-build-docker-image.png)

- Helm 圖和 *圖表* 資料夾。 這些 yaml 檔案會構成應用程式的 Helm 圖表，您可以用它來將它部署到 Kubernetes。 如需 Helm 的詳細資訊，請參閱 [https://www.helm.sh](https://www.helm.sh) 。

- *azds. yaml*。 這包含 Azure Dev Spaces 的設定，可在 Azure Kubernetes Service 中提供快速、反復的偵錯工具體驗。 如需詳細資訊，請參閱 [Azure Dev Spaces 檔](/azure/dev-spaces/azure-dev-spaces)。

:::moniker range="vs-2017"

## <a name="publish-to-azure-kubernetes-service-aks"></a>發佈至 Azure Kubernetes Service (AKS) 

所有這些檔案都準備就緒後，您就可以使用 Visual Studio IDE 來撰寫和偵測應用程式的程式碼，就像往常一樣。 您也可以使用 [Azure Dev Spaces](/azure/dev-spaces/) 快速地執行和偵測在 AKS 叢集中執行的程式碼。 如需詳細資訊，請參閱[Azure Dev Spaces 教學](/azure/dev-spaces/get-started-netcore-visualstudio)課程

一旦您的程式碼以您想要的方式執行，您就可以直接從 Visual Studio 發行至 AKS 叢集。

若要這樣做，您必須先仔細檢查是否已安裝所有專案，如發佈至 AKS 之專案底下的 [必要條件](#prerequisites) 一節所述，並執行連結中提供的所有命令列步驟。 然後，設定發佈設定檔，以將您的容器映射發佈至 Azure Container Registry (ACR) 。 然後，AKS 可以從 ACR 提取您的容器映射，並將其部署到叢集中。

1. 在 **方案總管**中，以滑鼠右鍵按一下您的 *專案* ，然後選擇 [ **發行**]。

   ![[發佈] 功能表項目的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-publish-project.png)

2. 在 [ **發佈** ] 畫面中，選擇 [ **Container Registry** ] 作為發佈目標，然後遵循提示來選取您的容器登錄。 如果您還沒有容器登錄，請選擇 [ **建立新的 Azure Container Registry** ]，從 Visual Studio 建立一個。 如需詳細資訊，請參閱 [將您的容器發佈至 Azure Container Registry](hosting-web-apps-in-docker.md)。

   ![[挑選發佈目標] 畫面的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-publish-to-acr.png)

3. 回到方案總管中，以滑鼠右鍵按一下您的 *方案* ，然後按一下 [ **發佈到 Azure AKS**]。

   ![[發佈至 Azure AKS] 功能表項目的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-publish-solution.png)

4. 選擇您的訂用帳戶和 AKS 叢集，以及您剛才建立的 ACR 發行設定檔。 然後按一下 [確定]  。

   ![[發佈至 AKS] 畫面的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-publish-to-aks.png)

   這會將您帶到 [ **發佈至 Azure] AKS** 畫面。

5. 選擇 [ **設定 Helm** ] 連結，以更新用來在伺服器上安裝 Helm 圖表的命令列。

   ![[設定 Helm] 連結的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-configure-helm.png)

   如果您想要指定自訂命令列引數，例如不同的 Kubernetes 內容或圖表名稱，則更新命令列會很有用。

   ![Helm 設定畫面的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-helm-configure-screen.png)

6. 當您準備好要部署時，請按一下 [ **發佈** ] 按鈕，將您的應用程式發佈至 AKS。

   ![[發佈至 Azure AKS] 畫面的螢幕擷取畫面](media/tutorial-kubernetes-tools/k8s-tools-publish-screen.png)

::: moniker-end

恭喜！ 您現在可以為所有 Kubernetes 應用程式開發，使用完整的 Visual Studio 功能。

## <a name="remove-kubernetes-support"></a>移除 Kubernetes 支援

1. 在 **方案總管**的 [ **屬性**] 底下，開啟 *launchSettings.js開啟*]。

1. 刪除 **Kubernetes 中**的區段容器。

1. 如果您要切換回 Docker 撰寫，請在 **方案總管**中選取該專案，按一下滑鼠右鍵，然後選擇 [ **設定為啟始專案**]。

1.  (選擇性) 您也可以刪除如先前文章所述的其他成品，例如 **圖表** 資料夾和 *azds. yaml*。

## <a name="next-steps"></a>後續步驟

閱讀 [AKS 檔](/azure/aks)，以深入瞭解 Azure 上的 Kubernetes 開發。

閱讀[Azure Dev Spaces 檔](/azure/dev-spaces/)，以深入瞭解 Azure Dev Spaces
