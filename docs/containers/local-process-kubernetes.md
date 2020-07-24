---
title: 搭配 Visual Studio 使用本機進程與 Kubernetes （預覽）
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: conceptual
description: 瞭解如何搭配使用 Kubernetes 與具有 Visual Studio 的本機進程，將您的開發電腦連線到 Kubernetes 叢集
keywords: Kubernetes、Azure Dev Spaces、Dev Spaces、Docker、Kubernetes、Azure、容器的本機進程
monikerRange: '>=vs-2019'
ms.openlocfilehash: fd2e456f1ffdaaea90c0594b73d5367e51c8f655
ms.sourcegitcommit: debf31a8fb044f0429409bd0587cdb7d5ca6f836
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87133992"
---
# <a name="use-local-process-with-kubernetes-preview"></a>搭配 Kubernetes 使用本機進程（預覽）

使用 Kubernetes 的本機程式可讓您在開發電腦上執行和偵錯工具代碼，同時繼續與您的應用程式或服務的其餘部分連線到您的 Kubernetes 叢集。 例如，如果您有一個大型的微服務架構，其中包含許多互相相依的服務與資料庫，則在開發電腦上複寫這些相依性可能會很棘手。 此外，在內部迴圈開發期間，針對每個程式碼變更建立程式碼並將其部署到您的 Kubernetes 叢集，可能會很慢、耗時，而且很容易與偵錯工具搭配使用。

透過 Kubernetes 的本機程式可避免在您的開發電腦與叢集之間直接建立連線，而必須建立程式碼並將其部署到您的叢集。 在進行偵錯工具時，將您的開發電腦連接到叢集，可讓您在完整應用程式的內容中快速測試和開發服務，而不需要建立任何 Docker 或 Kubernetes 設定。

具有 Kubernetes 的本機進程會重新導向已連線的 Kubernetes 叢集與您的開發電腦之間的流量。 此流量重新導向可讓您的開發電腦上執行的程式碼與 Kubernetes 叢集中執行的服務進行通訊，就好像它們位於相同的 Kubernetes 叢集中一樣。 使用 Kubernetes 的本機進程也會提供一種方法，將環境變數和掛接的磁片區複寫至您的開發電腦中 Kubernetes 叢集中的 pod。 在您的開發電腦上提供環境變數和裝載的磁片區存取，可讓您快速處理常式代碼，而不需要手動複寫這些相依性。

在本指南中，您將瞭解如何搭配 Kubernetes 使用本機進程，以重新導向您的 Kubernetes 叢集與在開發電腦上執行的程式碼之間的流量。 本指南也提供在 Kubernetes 叢集上部署具有多個微服務之大型範例應用程式的腳本。

> [!IMPORTANT]
> 此功能目前為預覽狀態。 若您同意[補充的使用規定][preview-terms]即可取得預覽。 在公開上市 (GA) 之前，此功能的某些領域可能會變更。

## <a name="before-you-begin"></a>開始之前

本指南使用[自行車分享範例應用程式][bike-sharing-github]，示範如何將您的開發電腦連接到 Kubernetes 叢集。 如果您已經在 Kubernetes 叢集上執行自己的應用程式，您仍然可以遵循下列步驟，並使用您自己的服務名稱。

### <a name="prerequisites"></a>必要條件

* Azure 訂用帳戶。 如果您沒有 Azure 訂用帳戶，您可以建立[免費帳戶](https://azure.microsoft.com/free)。
* [已安裝 Azure CLI][azure-cli]。
* 在已安裝*Azure 開發*工作負載的 Windows 10 上執行[Visual Studio 2019][visual-studio] 16.7 版 Preview 4 或更高版本。
* [已安裝 Kubernetes 延伸模組的本機進程][lpk-extension]。

此外，針對 .NET 主控台應用程式，請安裝*Kubernetes* NuGet 套件。

## <a name="create-a-kubernetes-cluster"></a>建立 Kubernetes 叢集

在[支援的區域][supported-regions]中建立 AKS 叢集。 下列命令會建立名為 MyResourceGroup 的資源群組與名為 MyAKS 的 AKS 叢集。

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

使用所提供的腳本，在您的叢集上安裝範例應用程式。 您可以使用[Azure Cloud Shell][azure-cloud-shell]來執行此腳本。

```azurecli-interactive
git clone https://github.com/Microsoft/mindaro
cd mindaro
chmod +x ./local-process-quickstart.sh
./local-process-quickstart.sh -g MyResourceGroup -n MyAKS
```

流覽至執行叢集的範例應用程式，方法是開啟其 [公用 URL]，這會顯示在安裝腳本的輸出中。

```console
$ ./local-process-quickstart.sh -g MyResourceGroup -n MyAKS
Defaulting Dev spaces repository root to current directory : ~/mindaro
Setting the Kube context
...
To try out the app, open the url:
bikeapp.bikesharingweb.EXTERNAL_IP.nip.io
```

在上述範例中，公用 URL 是 `bikeapp.bikesharingweb.EXTERNAL_IP.nip.io` 。

## <a name="connect-to-your-cluster-and-debug-a-service"></a>連接到您的叢集並對服務進行偵錯工具

在您的開發電腦上，下載並設定 Kubernetes CLI，使用[az aks get-認證][az-aks-get-credentials]連接到您的 Kubernetes 叢集。

```azurecli
az aks get-credentials --resource-group MyResourceGroup --name MyAKS
```

從 Visual Studio 中的[自行車分享範例應用程式][bike-sharing-github]開啟*mindaro/samples/BikeSharingApp/ReservationEngine/app.config。*

在您的專案中，從 [啟動設定] 下拉式清單中選取 [*使用 Kubernetes 的本機進程*]，如下所示。

![選擇使用 Kubernetes 的本機進程](media/local-process-kubernetes/choose-local-process.png)

按一下 [本機進程] 旁的 [開始] 按鈕 *，並 Kubernetes*。 在 [*使用 Kubernetes 的本機進程*] 對話方塊中：

* 選取您的訂閱。
* 選取叢集的 [ *MyAKS* ]。
* 針對您的命名空間選取 [*開發*]。
* 選取 [ *reservationengine* ] 以讓服務重新導向。
* 選取 [啟動設定檔的*應用程式*]。
* 選取以 `http://bikeapp.bikesharingweb.EXTERNAL_IP.nip.io` 取得要啟動瀏覽器的 URL。

![選擇使用 Kubernetes 叢集的本機進程](media/local-process-kubernetes/choose-local-process-cluster.png)

> [!IMPORTANT]
> 您只能重新導向具有單一 pod 的服務。

按一下 [*儲存並開始調試*]。

Kubernetes 叢集中的所有流量都會重新導向至您的開發電腦上執行的應用程式版本，以供*reservationengine*服務使用。 具有 Kubernetes 的本機進程也會將應用程式的所有輸出流量，路由傳送回您的 Kubernetes 叢集。

> [!NOTE]
> 系統會提示您允許*KubernetesDNSManager*以提高許可權執行並修改您的主機檔案。

當狀態列顯示您已連線到*reservationengine*服務時，您的開發電腦就會連接。

![已連接的開發電腦](media/local-process-kubernetes/development-computer-connected.png)

> [!NOTE]
> 在 subesquent 啟動時，系統不會提示您使用 [Kubernetes] 對話方塊來進行*本機進程*。 您可以在 [*調試*] 窗格的 [專案屬性] 中更新這些設定。

在您的開發電腦連線之後，流量就會開始重新導向至您的開發電腦，以取得您要取代的服務。

## <a name="set-a-break-point"></a>設定中斷點

開啟[BikesHelper.cs][bikeshelper-cs-breakpoint] ，然後按一下第26行的某處，將游標放在該處。 藉由叫用*F9*或依序按一下 [ *Debug* ] 和 [*切換中斷點*] 來設定中斷點。

藉由開啟公用 URL，流覽至範例應用程式。 選取 [ *Aurelia Briggs （customer）* ] 作為使用者，然後選取要出租的自行車。 按一下 [*出租自行車*]。 回到 Visual Studio，觀察第26行已反白顯示。 您設定的中斷點已在第26行暫停服務。 若要讓服務繼續，請按 F5，或依序按一下 [偵錯] 和 [繼續]。 返回您的瀏覽器，並確認頁面顯示您已出租自行車。

將游標放在第26行，然後叫用 `BikesHelper.cs` *F9*，即可移除中斷點。

> [!NOTE]
> 根據預設，停止偵錯工具工作也會中斷您的開發電腦與 Kubernetes 叢集的連線。 您可以變更此行為，方法是在偵錯工具的 [ *Kubernetes 調試*程式] 區段中，將 [在*偵錯工具之後中斷連接]* 切換為*false* 。 更新此設定之後，當您停止並開始進行偵錯工具時，您的開發電腦仍會保持連線。 若要中斷您的開發電腦與叢集的連線，請按一下工具列上的 [*中斷連線]* 按鈕。
>
> 如果 Visual Studio 突然結束叢集的連線或終止，則您要重新導向的服務可能不會還原為其原始狀態，而是使用 Kubernetes 與本機進程連接。 若要修正此問題，請參閱[疑難排解指南][troubleshooting]。

## <a name="using-logging-and-diagnostics"></a>使用記錄和診斷

您可以在 `Azure Dev Spaces` [開發電腦的*TEMP*目錄][azds-tmp-dir]中，找到目錄中的診斷記錄。

## <a name="remove-the-sample-application-from-your-cluster"></a>從您的叢集中移除範例應用程式

使用提供的腳本從您的叢集中移除範例應用程式。

```azurecli-interactive
./local-process-quickstart.sh -c -g MyResourceGroup -n MyAKS
```

## <a name="next-steps"></a>後續步驟

瞭解本機進程 Kubernetes 的運作方式。

> [!div class="nextstepaction"]
> [本機處理序與 Kubernetes 搭配使用的方式](overview-local-process-kubernetes.md)

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
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