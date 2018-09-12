---
title: Kubernetes 工具教學課程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2018
ms.technology: vs-ide-deployment
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: douge
ms.workload:
- azure
ms.openlocfilehash: f842d1f9c103e9673d3295b2b285498d6ff58045
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2018
ms.locfileid: "43138939"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>開始使用 Visual Studio 的 Kubernetes 工具

Visual Studio Kubernetes 工具可協助簡化目標 Kubernetes 的容器化應用程式的開發。 Visual Studio 可以自動建立設定即程式碼所需的檔案來支援 Kubernetes 部署，例如 Dockerfile 和 Helm 圖表。 您可以偵錯您的程式碼，在即時 Azure Kubernetes Service (AKS) 叢集中使用 Azure 開發人員的空間，或直接發行至 AKS 叢集中從 Visual Studio 內。

## <a name="prerequisites"></a>必要條件

若要利用這項新功能，您將需要：

- 最新版[Visual Studio 2017](https://visualstudio.microsoft.com/download)具有*ASP.NET 和 web 開發*工作負載。

- [適用於 Visual Studio 的 Kubernetes 工具](https://aka.ms/get-vsk8stools)、 提供個別下載。

- [適用於 Windows 的 docker](https://store.docker.com/editions/community/docker-ce-desktop-windows)開發工作站上安裝 （也就是您執行 Visual Studio），如果您想要建置 Docker 映像，在本機執行的 Docker 容器進行偵錯或發行至 AKS。

- 如果您想要從 Visual Studio 發佈至 AKS:

    1.  [AKS 發佈工具](https://aka.ms/get-vsk8spublish)、 提供個別下載。

    1.  Azure Kubernetes 服務叢集。 如需詳細資訊，請參閱 <<c0> [ 建立 AKS 叢集](/azure/aks/kubernetes-walkthrough-portal#create-aks-cluster)。 請務必[連線到叢集](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster)從您的開發工作站。

    1.  Helm CLI 安裝在您的開發工作站上。 如需詳細資訊，請參閱[安裝 Helm](https://github.com/kubernetes/helm/blob/master/docs/install.md)。

    1.  針對您的 AKS 叢集設定 helm。 如需有關如何執行這項操作的詳細資訊，請參閱 <<c0> [ 如何設定 Helm](/azure/aks/kubernetes-helm#configure-helm)。

## <a name="create-a-new-kubernetes-project"></a>建立新的 Kubernetes 專案

一旦您有安裝適當的工具，啟動 Visual Studio，並建立新的專案。 底下**雲端**，選擇**Kubernetes 容器應用程式**專案類型。 選取此專案類型，然後選擇**確定**。

![建立新的 Kubernetes 應用程式專案的螢幕擷取畫面](media/k8s-tools-new-k8s-app.png)

若要建立的 web 應用程式時，可以選擇哪種類型的 ASP.NET Core。 選擇**Web 應用程式**，然後選擇**確定**。 平常**啟用 Docker 支援**選項未出現在此對話方塊。  容器應用程式預設會啟用 docker 支援 kubernetes。

![Web 應用程式選取範圍的螢幕擷取畫面](media/k8s-tools-web-app-selection-screen.png)

## <a name="add-kubernetes-support-to-an-existing-project"></a>加入現有的專案中的 Kubernetes 支援

或者，您可以將 Kubernetes 支援新增至現有的 ASP.NET Core web 應用程式專案。 若要這樣做，以滑鼠右鍵按一下專案，然後選擇**新增** > **容器協調器支援**。

![新增容器協調器的螢幕擷取畫面功能表項目](media/k8s-tools-add-container-orchestrator.png)

在對話方塊中，選取 「 Kubernetes/Helm 」 並選擇**確定**。

![新增容器協調器的螢幕擷取畫面 對話方塊](media/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>為您建立的 Visual Studio

建立新之後**Kubernetes 容器應用程式**專案或加入現有的專案中的 Kubernetes 容器協調器支援，您會看到一些其他檔案專案中的，以便部署至 Kubernetes。

![方案總管的螢幕擷取畫面之後新增容器協調器支援](media/k8s-tools-solution-explorer.png)

加入的檔案如下：

- Dockerfile，可讓您產生的 Docker 容器映像裝載此 web 應用程式。 如您所見，Visual Studio 工具會利用這個 Dockerfile 中偵錯和部署至 Kubernetes 時。 如果您想要直接使用 Docker 映像，您可以以滑鼠右鍵按一下 Dockerfile，並選擇**建置 Docker 映像**。

   ![建置 Docker 映像的螢幕擷取畫面選項](media/k8s-tools-build-docker-image.png)

- Helm 圖表，以及*圖表*資料夾。 這些 yaml 檔案是由應用程式，您可以將它部署到 Kubernetes 使用 Helm 圖表所組成。 如需有關 Helm 的詳細資訊，請參閱[ https://www.helm.sh ](https://www.helm.sh)。

- *azds.yaml*。 這包含適用於 Azure 開發人員空間，提供快速的反覆式偵錯體驗，Azure Kubernetes 服務中的設定。 如需詳細資訊，請參閱[Azure 開發人員空間 > 文件](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces)。

## <a name="publish-to-azure-kubernetes-service-aks"></a>發佈至 Azure Kubernetes Service (AKS)

使用中的所有這些檔案的位置，您可以撰寫和偵錯您的應用程式程式碼，使用 Visual Studio IDE，就像您永遠有。

一旦您的程式碼執行的方式，可以直接從 Visual Studio 發行至 AKS 叢集。

若要這樣做，您首先要設定將您的容器映像發佈至 Azure Container Registry (ACR) 的發行設定檔。 然後可以提取容器映像從 ACR AKS，並將其部署到叢集。

1. 在 **方案總管 中**，以滑鼠右鍵按一下您*專案*，然後選擇 **發行**。

   ![螢幕擷取畫面的發行功能表項目](media/k8s-tools-publish-project.png)

1. 在 **發佈**畫面上，選擇**Container Registry**做為發佈目標，並遵循提示來選取您的容器登錄。 如果您還沒有容器登錄庫，選擇**建立新的 Azure Container Registry**建立一個從 Visual Studio。 如需詳細資訊，請參閱 <<c0> [ 作為您容器發行至 Azure Container Registry](#publish-your-container-to-azure-container-registry)。

   ![挑選發佈目標畫面的螢幕擷取畫面](media/k8s-tools-publish-to-acr.png)

1. 在 [方案總管] 中，以滑鼠右鍵按一下您*解決方案*然後按一下**發佈至 Azure AKS**。

   ![螢幕擷取畫面的發佈至 Azure AKS 功能表項目](media/k8s-tools-publish-solution.png)

1. 選擇您的訂用帳戶和您的 AKS 叢集，以及 ACR 發行您剛才建立的設定檔。 然後按一下 [確定]。 

   ![螢幕擷取畫面的發佈至 AKS 畫面](media/k8s-tools-publish-to-aks.png)

   這會帶您前往**發佈至 Azure AKS**螢幕。

1.  選擇**設定 Helm**更新用來在伺服器上安裝 Helm 圖表的命令列的連結。

   ![連結的設定 Helm 的螢幕擷取畫面](media/k8s-tools-configure-helm.png)

   更新命令列是很有用，如果您想要指定，例如不同的 Kubernetes 內容或圖表名稱的自訂命令列引數。

   ![螢幕擷取畫面的 Helm 設定畫面](media/k8s-tools-helm-configure-screen.png)

1. 當您準備好部署時，請按一下**發佈** 按鈕，應用程式發佈至 AKS。

   ![發行至 Azure AKS 螢幕的螢幕擷取畫面](media/k8s-tools-publish-screen.png)

恭喜您！ 您現在可以使用 Visual Studio 的完整功能的所有 Kubernetes 應用程式開發。

## <a name="next-steps"></a>後續步驟

深入了解在 Azure 上的 Kubernetes 開發，請閱讀[AKS 文件](/azure/aks)。
