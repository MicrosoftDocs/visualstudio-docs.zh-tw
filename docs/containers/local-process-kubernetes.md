---
title: '搭配 Visual Studio (Preview 使用本機進程與 Kubernetes) '
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: how-to
description: 瞭解如何搭配使用 Visual Studio 的本機進程與 Kubernetes，將您的開發電腦連線至 Kubernetes 叢集
keywords: 使用 Kubernetes、Azure Dev Spaces、Dev Spaces、Docker、Kubernetes、Azure、容器的本機進程
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jillfra
ms.openlocfilehash: 191fd1df377bd15d78c329b88d20f1fed8669663
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "87913278"
---
# <a name="use-local-process-with-kubernetes-preview"></a>使用本機進程搭配 Kubernetes (預覽版) 

使用 Kubernetes 的本機程式可讓您在開發電腦上執行和偵錯工具代碼，同時仍會與您的應用程式或服務的其餘部分連接到您的 Kubernetes 叢集。 例如，如果您有一個具有許多相依服務和資料庫的大型微服務架構，在您的開發電腦上複寫這些相依性可能會很困難。 此外，在內部迴圈開發期間，針對每個程式碼變更建立程式碼並部署到您的 Kubernetes 叢集，可能會很慢、耗時且難以與偵錯工具搭配使用。

使用 Kubernetes 的本機程式可避免建立您的程式碼，並將其部署到您的叢集，而改為直接在您的開發電腦與叢集之間建立連接。 在進行偵錯工具時，將您的開發電腦連接到您的叢集，可讓您在完整應用程式的內容中快速測試及開發您的服務，而不需要建立任何 Docker 或 Kubernetes 設定。

使用 Kubernetes 的本機進程會重新導向連線 Kubernetes 叢集與開發電腦之間的流量。 此流量重新導向可讓您的開發電腦上的程式碼和在 Kubernetes 叢集中執行的服務進行通訊，就像是在相同的 Kubernetes 叢集中一樣。 使用 Kubernetes 的本機程式也提供一種方式，可將環境變數和掛接的磁片區複寫到您的開發電腦上 Kubernetes 叢集中的 pod。 在您的開發電腦上提供環境變數和載入的磁片區的存取權，可讓您快速地處理程式碼，而不需要手動複寫這些相依性。

在本指南中，您將瞭解如何使用 Kubernetes 的本機進程，重新導向您的 Kubernetes 叢集和開發電腦上執行的程式碼之間的流量。 本指南也會提供一個腳本，以在 Kubernetes 叢集上部署具有多個微服務的大型範例應用程式。

> [!IMPORTANT]
> 此功能目前為預覽狀態。 若您同意[補充的使用規定][preview-terms]即可取得預覽。 在公開上市 (GA) 之前，此功能的某些領域可能會變更。

## <a name="before-you-begin"></a>開始之前

本指南使用 [自行車共用範例應用程式][bike-sharing-github] ，示範如何將您的開發電腦連接到 Kubernetes 叢集。 如果您已經在 Kubernetes 叢集上執行自己的應用程式，您仍然可以遵循下列步驟，並使用您自己的服務名稱。

### <a name="prerequisites"></a>先決條件

* Azure 訂用帳戶。 如果您沒有 Azure 訂用帳戶，您可以建立[免費帳戶](https://azure.microsoft.com/free)。
* [已安裝 Azure CLI][azure-cli]。
* [Visual Studio 2019][visual-studio] 16.7 版 Preview 4 或更新版本，在已安裝 *Azure 開發* 工作負載的 Windows 10 上執行。
* [已安裝 Kubernetes 延伸模組的本機進程][lpk-extension]。

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
chmod +x ./local-process-quickstart.sh
./local-process-quickstart.sh -g MyResourceGroup -n MyAKS
```

開啟應用程式的公用 URL （顯示在安裝腳本的輸出中），以流覽至執行叢集的範例應用程式。

```console
$ ./local-process-quickstart.sh -g MyResourceGroup -n MyAKS
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

在 Visual Studio 中，從[自行車共用範例應用程式][bike-sharing-github]中開啟*mindaro/samples/BikeSharingApp/ReservationEngine/app.config。*

在您的專案中，從 [啟動設定] 下拉式清單中選取 [ *使用 Kubernetes 的本機進程* ]，如下所示。

![使用 Kubernetes 選擇本機進程](media/local-process-kubernetes/choose-local-process.png)

在 [ *使用 Kubernetes 的本機進程*] 旁按一下 [開始] 按鈕。 在 [ *使用 Kubernetes 的本機進程* ] 對話方塊中：

* 選取您的訂用帳戶。
* 為您的叢集選取 [ *MyAKS* ]。
* 為您的命名空間選取 *dev* 。
* 選取服務要重新導向的 *reservationengine* 。
* 選取啟動設定檔的 *應用程式* 。
* 選取以 `http://bikeapp.bikesharingweb.EXTERNAL_IP.nip.io` 啟動瀏覽器的 URL。

![選擇使用 Kubernetes 叢集的本機進程](media/local-process-kubernetes/choose-local-process-cluster.png)

> [!IMPORTANT]
> 您只能重新導向具有單一 pod 的服務。

按一下 [ *儲存並開始調試*]。

Kubernetes 叢集中的所有流量都會重新導向至您的開發電腦上執行的應用程式版本， *reservationengine* 服務。 使用 Kubernetes 的本機進程也會將應用程式的所有輸出流量路由傳送回您的 Kubernetes 叢集。

> [!NOTE]
> 系統會提示您允許 *KubernetesDNSManager* 提升許可權，並修改您的主機檔案。

當狀態列顯示您已連線到 *reservationengine* 服務時，您的開發電腦就會連線。

![開發電腦已連線](media/local-process-kubernetes/development-computer-connected.png)

> [!NOTE]
> 在 subesquent 啟動時，系統不會提示您使用 [Kubernetes] 對話方塊進行 *本機處理* 。 您可以在 [ *調試* ] 窗格的 [專案屬性] 中更新這些設定。

當您的開發電腦連線之後，流量就會開始重新導向至您的開發電腦，以取得您要取代的服務。

## <a name="set-a-break-point"></a>設定中斷點

開啟 [BikesHelper.cs][bikeshelper-cs-breakpoint] ，並在第26行的某處按一下，將游標放在該處。 按 *F9 鍵* 或按一下 [ *Debug* ]，然後 *切換中斷點*，以設定中斷點。

開啟公用 URL 以流覽至範例應用程式。 選取 *Aurelia Briggs (客戶) * 作為使用者，然後選取要租借的自行車。 按一下 [ *租借自行車*]。 返回 Visual Studio，觀察行26已反白顯示。 您所設定的中斷點已在第26行暫停服務。 若要讓服務繼續，請按 F5，或依序按一下 [偵錯] 和 [繼續]。 返回您的瀏覽器，確認頁面顯示您出租了自行車。

將游標放在第26行 `BikesHelper.cs` ，然後按 *F9 鍵*，以移除中斷點。

> [!NOTE]
> 根據預設，停止偵錯工具也會中斷您的開發電腦與 Kubernetes 叢集的連線。 您可以變更此行為，方法是在偵錯工具的 [ *Kubernetes 調試*程式] 區段中，將 [偵錯工具] 變更為*False* *之後變更中斷連接*。 更新此設定之後，當您停止並開始進行偵錯工具時，您的開發電腦將保持連線。 若要中斷您的開發電腦與叢集的連線，請按一下工具列上的 [ *中斷連線]* 按鈕。
>
> 如果 Visual Studio 突然結束對叢集的連線或終止，則在使用 Kubernetes 連接到本機進程之前，您要重新導向的服務可能不會還原為其原始狀態。 若要修正此問題，請參閱 [疑難排解指南][troubleshooting]。

## <a name="additional-configuration"></a>其他設定

使用 Kubernetes 的本機進程可以處理路由流量和複寫環境變數，而不需要任何額外的設定。 如果您需要下載任何掛接至 Kubernetes 叢集中容器的檔案，例如 ConfigMap 檔案，您可以建立， `KubernetesLocalProcessConfig.yaml` 將這些檔案下載到您的開發電腦。 如需詳細資訊，請參閱 [使用 KubernetesLocalProcessConfig yaml 進行其他設定，以使用 Kubernetes 的本機進程][kubernetesLocalProcessConfig-yaml]。

## <a name="using-logging-and-diagnostics"></a>使用記錄和診斷

您可以在 `Local Process with Kubernetes` 開發電腦的 *暫存* 目錄中尋找目錄中的診斷記錄。 

## <a name="remove-the-sample-application-from-your-cluster"></a>從您的叢集中移除範例應用程式

使用提供的腳本，從您的叢集中移除範例應用程式。

```azurecli-interactive
./local-process-quickstart.sh -c -g MyResourceGroup -n MyAKS
```

## <a name="next-steps"></a>後續步驟

瞭解本機進程 Kubernetes 的運作方式。

> [!div class="nextstepaction"]
> [本機處理序與 Kubernetes 搭配使用的方式](overview-local-process-kubernetes.md)

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-vs-code]: https://marketplace.visualstudio.com/items?itemName=azuredevspaces.azds
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-lates
[azure-cloud-shell]: /azure/cloud-shell/w.md
[az-aks-get-credentials]: /cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials
[az-aks-vs-code]: https://marketplace.visualstudio.com/items?itemName=ms-kubernetes-tools.vscode-aks-tools
[bike-sharing-github]: https://github.com/Microsoft/mindaro
[preview-terms]: https://azure.microsoft.com/support/legal/preview-supplemental-terms/
[bikeshelper-cs-breakpoint]: https://github.com/Microsoft/mindaro/blob/master/samples/BikeSharingApp/ReservationEngine/BikesHelper.cs#L26
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[lpk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-local-process-with-kubernetes.md