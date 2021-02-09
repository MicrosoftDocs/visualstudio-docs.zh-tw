---
title: 將橋接至 Kubernetes 與 Visual Studio 搭配使用
titleSuffix: ''
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: how-to
description: 瞭解如何使用橋接器與 Visual Studio Kubernetes，以將您的開發電腦連線至 Kubernetes 叢集
keywords: 橋接至 Kubernetes、Azure Dev Spaces、Dev Spaces、Docker、Kubernetes、Azure、容器
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jmartens
ms.openlocfilehash: 23d060489a13aa8e02316e253d9367e9e3372bbe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859628"
---
# <a name="use-bridge-to-kubernetes"></a>使用 Bridge Kubernetes

您可以使用 Bridge Kubernetes，在您的 Kubernetes 叢集和開發電腦上執行的程式碼之間重新導向流量。 本指南也會提供一個腳本，以在 Kubernetes 叢集上部署具有多個微服務的大型範例應用程式。

## <a name="before-you-begin"></a>開始之前

本指南使用 [自行車共用範例應用程式][bike-sharing-github] ，示範如何將您的開發電腦連接到 Kubernetes 叢集。 如果您已經在 Kubernetes 叢集上執行自己的應用程式，您仍然可以遵循下列步驟，並使用您自己的服務名稱。

### <a name="prerequisites"></a>必要條件

* Azure 訂用帳戶。 如果您沒有 Azure 訂用帳戶，您可以建立[免費帳戶](https://azure.microsoft.com/free)。
* [已安裝 Azure CLI][azure-cli]。
* [Visual Studio 2019][visual-studio] 16.7 版 Preview 4 或更新版本，在已安裝 *Azure 開發* 工作負載的 Windows 10 上執行。
* [已安裝橋接器至 Kubernetes 延伸][btk-extension]模組。

此外，針對 .NET 主控台應用程式，請安裝 *VisualStudio* NuGet 套件。

## <a name="create-a-kubernetes-cluster"></a>建立 Kubernetes 叢集

在 [支援的區域][supported-regions]中建立 AKS 叢集。 下列命令會建立名為 MyResourceGroup  的資源群組與名為 MyAKS  的 AKS 叢集。

```azurecli-interactive
az group create \
    --name MyResourceGroup \
    --location eastus

az aks create \
    --resource-group MyResourceGroup \
    --name MyAKS \
    --location eastus \
    --node-count 3 \
    --generate-ssh-keys
```

## <a name="install-the-sample-application"></a>安裝範例應用程式

使用提供的腳本，在您的叢集上安裝範例應用程式。 您可以使用 [Azure Cloud Shell][azure-cloud-shell]來執行此腳本。

```azurecli-interactive
git clone https://github.com/Microsoft/mindaro
cd mindaro
chmod +x ./bridge-quickstart.sh
./bridge-quickstart.sh -g MyResourceGroup -n MyAKS
```

開啟應用程式的公用 URL （顯示在安裝腳本的輸出中），以流覽至執行叢集的範例應用程式。

```console
$ ./bridge-quickstart.sh -g MyResourceGroup -n MyAKS
Defaulting Dev spaces repository root to current directory : ~/mindaro
Setting the Kube context
...
To try out the app, open the url:
bikeapp.bikesharingweb.EXTERNAL_IP.nip.io
```

在上述範例中，公用 URL 是 `bikeapp.bikesharingweb.EXTERNAL_IP.nip.io` 。

## <a name="connect-to-your-cluster-and-debug-a-service"></a>連線至您的叢集並將服務進行偵錯工具

在您的開發電腦上，下載並設定 Kubernetes CLI 以使用 [az aks get 認證][az-aks-get-credentials]連接到您的 Kubernetes 叢集。

```azurecli
az aks get-credentials --resource-group MyResourceGroup --name MyAKS
```

從 GitHub 中的 [自行車共用範例應用程式][bike-sharing-github] 存放庫，使用 [綠色程式 **代碼** ] 按鈕上的下拉式清單，然後選擇 [ **在 Visual Studio 中開啟** ]，在本機複製存放庫，並在 Visual Studio 中開啟資料夾。 然後 **，使用**  >  [檔案 **開啟專案**] 來開啟 *samples/BikeSharingApp/ReservationEngine* 資料夾中的 **app.config** 專案。

在您的專案中，選取 [啟動設定] 下拉式清單中的 [ **要 Kubernetes 的橋接器** ]，如下所示。

![選擇橋接器至 Kubernetes](media/bridge-to-kubernetes/choose-bridge-to-kubernetes.png)

按一下 [ *橋接器至 Kubernetes*] 旁邊的 [開始] 按鈕。 在 [ **建立橋接器至 Kubernetes 的設定檔** ] 對話方塊中：

* 選取您的訂用帳戶。
* 為您的叢集選取 [ *MyAKS* ]。
* 針對您的命名空間選取 [ *bikeapp* ]。
* 選取服務要重新導向的 *reservationengine* 。
* 選取啟動設定檔的 *應用程式* 。
* 選取以 `http://bikeapp.bikesharingweb.EXTERNAL_IP.nip.io` 啟動瀏覽器的 URL。

![選擇橋接器至 Kubernetes 叢集](media/bridge-to-kubernetes/choose-bridge-cluster2.png)

> [!IMPORTANT]
> 您只能重新導向具有單一 pod 的服務。

選擇您是否要執行隔離，這表示使用叢集的其他人不會受到您的變更影響。 這種隔離模式的完成方式是將您的要求路由傳送至每個受影響服務的複本，但通常會路由傳送所有其他流量。 如需如何完成這項作業的詳細說明，請參閱 [Kubernetes 橋接器的運作][btk-overview-routing]方式。

按一下 [ **儲存並開始調試**]。

Kubernetes 叢集中的所有流量都會重新導向至您的開發電腦上執行的應用程式版本， *reservationengine* 服務。 橋接器至 Kubernetes 也會將應用程式的所有輸出流量路由傳送回您的 Kubernetes 叢集。

> [!NOTE]
> 系統會提示您允許 *EndpointManager* 提升許可權，並修改您的主機檔案。

當狀態列顯示您已連線到服務時，您的開發電腦就會連線 `reservationengine` 。

![開發電腦已連線](media/bridge-to-kubernetes/development-computer-connected.png)

> [!NOTE]
> 後續啟動時，系統不會提示您提供 [ **Bridge 到 Kubernetes 的建立設定檔** ] 對話方塊。 您可以在 [專案屬性] 的 [ **Debug** ] 中更新這些設定。

當您的開發電腦連線之後，流量就會開始重新導向至您的開發電腦，以取得您要取代的服務。

## <a name="set-a-break-point"></a>設定中斷點

開啟 [BikesHelper.cs][bikeshelper-cs-breakpoint] ，並在第26行的某處按一下，將游標放在該處。 按 *F9* 或選取 [ **Debug**  >  **切換中斷點**]，以設定中斷點。

開啟公用 URL 以流覽至範例應用程式。 選取 **Aurelia Briggs (客戶)** 作為使用者，然後選取要租借的自行車。 選擇 **出租自行車**。 返回 Visual Studio，觀察行26已反白顯示。 您所設定的中斷點已在第26行暫停服務。 若要繼續服務，請按 **F5** 或按一下 [ **Debug**  >  **Continue**]。 返回您的瀏覽器，確認頁面顯示您出租了自行車。

將游標放在第26行 `BikesHelper.cs` ，然後按 **F9 鍵**，以移除中斷點。

> [!NOTE]
> 根據預設，停止偵錯工具也會中斷您的開發電腦與 Kubernetes 叢集的連線。 您可以變更此行為，方法是在偵錯工具的 [Kubernetes 偵錯工具] 區段中，變更 [在偵錯工具 **後中斷連接]** `false` 。  更新此設定之後，當您停止並開始進行偵錯工具時，您的開發電腦將保持連線。 若要中斷您的開發電腦與叢集的連線，請按一下工具列上的 [ **中斷連線]** 按鈕。

## <a name="additional-configuration"></a>其他設定

橋接器至 Kubernetes 可以處理路由流量和複寫環境變數，而不需要任何額外的設定。 如果您需要下載任何掛接至 Kubernetes 叢集中容器的檔案，例如 ConfigMap 檔案，您可以建立， `KubernetesLocalProcessConfig.yaml` 將這些檔案下載到您的開發電腦。 如需詳細資訊，請參閱 [使用 KubernetesLocalProcessConfig yaml，以取得 Bridge 到 Kubernetes 的其他][kubernetesLocalProcessConfig-yaml]設定。

## <a name="using-logging-and-diagnostics"></a>使用記錄和診斷

您可以在 `Bridge to Kubernetes` 開發電腦的 *暫存* 目錄中尋找目錄中的診斷記錄。 

## <a name="remove-the-sample-application-from-your-cluster"></a>從您的叢集中移除範例應用程式

使用提供的腳本，從您的叢集中移除範例應用程式。

```azurecli-interactive
./bridge-quickstart.sh -c -g MyResourceGroup -n MyAKS
```

## <a name="next-steps"></a>下一步

瞭解 Kubernetes 的橋樑如何運作。

> [!div class="nextstepaction"]
> [Bridge to Kubernetes 的運作方式](overview-bridge-to-kubernetes.md)

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-vs-code]: https://marketplace.visualstudio.com/items?itemName=azuredevspaces.azds
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-lates&preserve-view=true
[azure-cloud-shell]: /azure/cloud-shell/overview.md
[az-aks-get-credentials]: /cli/azure/aks?view=azure-cli-latest&preserve-view=true#az-aks-get-credentials
[az-aks-vs-code]: https://marketplace.visualstudio.com/items?itemName=ms-kubernetes-tools.vscode-aks-tools
[bike-sharing-github]: https://github.com/Microsoft/mindaro
[preview-terms]: https://azure.microsoft.com/support/legal/preview-supplemental-terms/
[bikeshelper-cs-breakpoint]: https://github.com/Microsoft/mindaro/blob/master/samples/BikeSharingApp/ReservationEngine/BikesHelper.cs#L26
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-bridge-to-kubernetes.md
[btk-overview-routing]: overview-bridge-to-kubernetes.md#using-routing-capabilities-for-developing-in-isolation