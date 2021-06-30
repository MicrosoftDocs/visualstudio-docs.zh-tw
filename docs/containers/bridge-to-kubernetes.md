---
title: 教學課程：使用 Bridge 將開發電腦連線至 Kubernetes
ms.technology: vs-azure
ms.date: 03/24/2021
ms.topic: tutorial
description: 將您的開發電腦連線至 Kubernetes 叢集，並搭配使用 Bridge 與 Kubernetes 與 Visual Studio。
keywords: 橋接至 Kubernetes、Azure Dev Spaces、Dev Spaces、Docker、Kubernetes、Azure、容器
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jmartens
ms.openlocfilehash: b8d6c98d2e2146ad57871b74cd2d522ed2b04259
ms.sourcegitcommit: 0499d813d5c24052c970ca15373d556a69507250
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2021
ms.locfileid: "113046114"
---
# <a name="tutorial-use-bridge-to-kubernetes-to-connect-your-clusters-and-your-development-computers"></a>教學課程：使用 Bridge Kubernetes 來連接您的叢集和開發電腦

在本教學課程中，您將瞭解如何使用 Bridge Kubernetes，在您的 Kubernetes 叢集和開發電腦上執行的程式碼之間重新導向流量。 

本指南也會提供一個腳本，以在 Kubernetes 叢集上部署具有多個微服務的大型範例應用程式。

若要深入瞭解 Kubernetes 的橋樑，請參閱 [Kubernetes 如何運作的橋樑](overview-bridge-to-kubernetes.md)。

## <a name="prerequisites"></a>必要條件

- Kubernetes 叢集
- [Visual Studio 2019][visual-studio] 16.7 版 Preview 4 或更高版本的 Windows 10 上執行。
- [已安裝橋接器至 Kubernetes 擴充功能][btk-extension]

## <a name="about-the-data"></a>關於資料

本教學課程會使用 Bridge Kubernetes，在任何 Kubernetes 叢集上開發簡單待辦事項範例應用程式的微服務版本。 此 [TODO 應用程式範例應用程式][todo-app-github]（使用 Visual Studio）已從 [TodoMVC](http://todomvc.com)所提供的程式碼中進行調整。 

 這些步驟應該適用于任何 Kubernetes 叢集。 因此，如果您已經在 Kubernetes 叢集上執行自己的應用程式，您仍然可以遵循下列步驟，並使用您自己的服務名稱。

TODO 應用程式範例是由前端和後端所組成，可提供持續性的儲存體。 這個擴充的範例會新增統計資料元件，並將應用程式分成數個微服務，具體而言：

- 前端會呼叫資料庫 api 來保存和更新 TODO 專案;
- 資料庫 api 服務依賴 Mongo 資料庫來保存 TODO 專案;
- 前端會將新增、完成和刪除事件寫入至 RabbitMQ 佇列;
- 統計資料工作者接收來自 RabbitMQ 佇列的事件，並更新 Redis 快取;
- 統計資料 API 會公開快取的統計資料，讓前端顯示。

畢竟，這個延伸的 TODO 應用程式是由六個相互關聯的元件所組成。


## <a name="check-the-cluster"></a>檢查叢集

開啟命令提示字元，並檢查是否已 `kubectl` 安裝且在路徑上，您想要使用的叢集是否可用且就緒，並將內容設定為該叢集。

```cmd
kubectl cluster-info
kubectl config use-context {context-name}
```

其中 {coNtext-name} 是您想要用於 todo 應用程式範例之叢集的內容名稱。

## <a name="deploy-the-application"></a>部署應用程式

複製 [mindaro](https://github.com/Microsoft/mindaro) 存放庫，並使用目前的工作資料夾，將命令視窗開啟至 *範例/todo-應用程式*。

建立範例的命名空間。

```cmd
kubectl create namespace todo-app
```

然後，套用部署資訊清單：

```cmd
kubectl apply -n todo-app -f deployment.yaml
```

這是簡單的部署，使用型別的服務來公開前端 `LoadBalancer` 。 等候所有 pod 正在執行，而且服務的外部 IP `frontend` 變成可用。

如果您要使用 MiniKube 進行測試，您將需要使用 `minikube tunnel` 來解析外部 IP。 如果您使用 AKS 或其他雲端式 Kubernetes 提供者，系統會自動指派外部 IP。 使用下列命令來監視 `frontend` 服務，以等待其啟動並執行：

```output
kubectl get service -n todo-app frontend --watch

NAME       TYPE           CLUSTER-IP    EXTERNAL-IP     PORT(S)        AGE
frontend   LoadBalancer   10.0.245.78   20.73.226.228   80:31910/TCP   6m26s
```

使用外部 IP 和本機埠 (埠 (S) 欄) 中的第一個數位來流覽至應用程式。

```
http://{external-ip}:{local-port}
```

在瀏覽器中測試正在執行的應用程式。 當您新增、完成和刪除 todo 專案時，請注意，[統計資料] 頁面會以預期的計量進行更新。

## <a name="connect-to-your-cluster-and-debug-a-service"></a>連線至您的叢集並將服務進行偵錯工具

在 Visual Studio 中開啟 *samples\todo-app\database-api\database-api.csproj* 。 在專案中，選取 [啟動設定] 下拉式清單中的 [ **要 Kubernetes 的橋接器** ]，如下所示。

![選擇橋接器至 Kubernetes](media/bridge-to-kubernetes/choose-bridge-to-kubernetes.png)

按一下 [ *橋接器至 Kubernetes*] 旁邊的 [開始] 按鈕。 在 [ **建立橋接器至 Kubernetes 的設定檔** ] 對話方塊中：

- 選取您的叢集名稱。
- 針對您的命名空間選取 [ *待辦事項] 應用程式* 。
- 選取要重新導向之服務的 [ *資料庫-api* ]。
- 選取您先前用來啟動瀏覽器的相同 URL，HTTP：//{external-ip}： {本機埠}

![選擇橋接器至 Kubernetes 叢集](media/bridge-to-kubernetes/configure-bridge-debugging.png)

選擇您是否要執行隔離，這表示使用叢集的其他人不會受到您的變更影響。 這種隔離模式的完成方式是將您的要求路由傳送至每個受影響服務的複本，但通常會路由傳送所有其他流量。 如需如何完成這項作業的詳細說明，請參閱 [Kubernetes 橋接器的運作][btk-overview-routing]方式。

按一下 [確定]  。 Kubernetes 叢集中的所有流量都會重新導向至您的開發電腦上執行的應用程式版本，以供 *資料庫 api* 服務使用。 橋接器至 Kubernetes 也會將應用程式的所有輸出流量路由傳送回您的 Kubernetes 叢集。

> [!NOTE]
> 系統會提示您允許 *EndpointManager* 提升許可權，並修改您的主機檔案。

當狀態列顯示您已連線到服務時，您的開發電腦就會連線 `database-api` 。

![開發電腦已連線](media/bridge-to-kubernetes/development-computer-connected.png)

> [!NOTE]
> 後續啟動時，系統不會提示您提供 [ **Bridge 到 Kubernetes 的建立設定檔** ] 對話方塊。 您可以在 [專案屬性] 的 [ **Debug** ] 中更新這些設定。

當您的開發電腦連線之後，流量就會開始重新導向至您的開發電腦，以取得您要取代的服務。

> [!NOTE]
> 例如，稍後若要編輯偵錯工具設定檔（例如，如果您想要使用不同的 Kubernetes 服務進行測試），請選擇 [ **debug**  >  **debug Properties**]，然後按一下 [**變更**] 按鈕。

## <a name="set-a-break-point"></a>設定中斷點

開啟 MongoHelper，並在 CreateTask 方法中的第68行的某處按一下，將游標放在該處。 按 *F9* 或選取 [ **Debug**  >  **切換中斷點**]，以設定中斷點。

藉由開啟前端服務)  (外部 IP 位址的公用 URL，來流覽至範例應用程式。 若要繼續服務，請按 **F5** 或按一下 [ **Debug**  >  **Continue**]。

將游標放在含有中斷點的行上，然後按 **F9 鍵**，以移除中斷點。

> [!NOTE]
> 根據預設，停止偵錯工具也會中斷您的開發電腦與 Kubernetes 叢集的連線。 您可以變更此行為，方法是 `false` 在 [**工具** 選項] 對話方塊的 [ **Kubernetes 調試** 程式] 區段中，變更 [在偵錯工具後中斷連接]  >   。 更新此設定之後，當您停止並開始進行偵錯工具時，您的開發電腦將保持連線。 若要中斷您的開發電腦與叢集的連線，請按一下工具列上的 [ **中斷連線]** 按鈕。
>
>![Kubernetes 偵錯工具選項的螢幕擷取畫面](media/bridge-to-kubernetes/kubernetes-debugging-options.png)

## <a name="additional-configuration"></a>其他設定

橋接器至 Kubernetes 可以處理路由流量和複寫環境變數，而不需要任何額外的設定。 如果您需要下載任何掛接至 Kubernetes 叢集中容器的檔案，例如 ConfigMap 檔案，您可以建立， `KubernetesLocalProcessConfig.yaml` 將這些檔案下載到您的開發電腦。 如需詳細資訊，請參閱 [使用 KubernetesLocalProcessConfig yaml，以取得 Bridge 到 Kubernetes 的其他][kubernetesLocalProcessConfig-yaml]設定。

## <a name="using-logging-and-diagnostics"></a>使用記錄和診斷

您可以在 `Bridge to Kubernetes` 開發電腦的 *暫存* 目錄中尋找目錄中的診斷記錄。

## <a name="next-steps"></a>後續步驟

瞭解 Kubernetes 的橋樑如何運作。

> [!div class="nextstepaction"]
> [Bridge to Kubernetes 的運作方式](overview-bridge-to-kubernetes.md)

[todo-app-github]: https://github.com/Microsoft/mindaro
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-bridge-to-kubernetes.md
[btk-overview-routing]: overview-bridge-to-kubernetes.md#using-routing-capabilities-for-developing-in-isolation
