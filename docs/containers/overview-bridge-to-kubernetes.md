---
title: Bridge to Kubernetes 的運作方式
ms.technology: vs-azure
ms.date: 11/19/2020
ms.topic: conceptual
description: 說明使用 Bridge Kubernetes 將您的開發電腦連線至 Kubernetes 叢集的程式
keywords: 橋接至 Kubernetes、Docker、Kubernetes、Azure、容器
monikerRange: '>=vs-2019'
manager: jillfra
author: ghogen
ms.author: ghogen
ms.openlocfilehash: d1a92433a90e6e6b7f71d0c7db6ced3a52c33315
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440606"
---
# <a name="how-bridge-to-kubernetes-works"></a>Bridge to Kubernetes 的運作方式

[橋接器至 Kubernetes] 可讓您在開發電腦上執行和偵測程式碼，同時仍會與您的應用程式或服務的其餘部分連接到您的 Kubernetes 叢集。 例如，如果您有一個具有許多相依服務和資料庫的大型微服務架構，在您的開發電腦上複寫這些相依性可能會很困難。 此外，在內部迴圈開發期間，針對每個程式碼變更建立程式碼並部署到您的 Kubernetes 叢集，可能會很慢、耗時且難以與偵錯工具搭配使用。

橋接器至 Kubernetes 可避免在您的開發電腦與叢集之間直接建立連線，而必須建立程式碼並將其部署至您的叢集。 在進行偵錯工具時，將您的開發電腦連接到您的叢集，可讓您在完整應用程式的內容中快速測試及開發您的服務，而不需要建立任何 Docker 或 Kubernetes 設定。

橋接器至 Kubernetes 會重新導向連線 Kubernetes 叢集與開發電腦之間的流量。 此流量重新導向可讓您的開發電腦上的程式碼和在 Kubernetes 叢集中執行的服務進行通訊，就像是在相同的 Kubernetes 叢集中一樣。 橋接器至 Kubernetes 也提供一種方法，可將環境變數和掛接的磁片區複寫到您的開發電腦上 Kubernetes 叢集中的 pod。 在您的開發電腦上提供環境變數和載入的磁片區的存取權，可讓您快速地處理程式碼，而不需要手動複寫這些相依性。

> [!WARNING]
> Bridge Kubernetes 僅供開發和測試案例使用。 不適用於生產叢集或主動使用中的即時服務。

## <a name="using-bridge-to-kubernetes"></a>使用 Bridge Kubernetes

若要使用橋接器在 Visual Studio 中 Kubernetes，您需要在已安裝 *ASP.NET 和 網頁程式開發* 工作負載的 Windows 10 上執行 [Visual Studio 2019][visual-studio] 16.7 Preview 4 版或更新版本，並安裝 [橋接器至 Kubernetes 擴充][btk-extension]功能。 當您使用 Bridge Kubernetes 來建立 Kubernetes 叢集的連線時，您可以選擇將叢集中現有 pod 的所有流量，重新導向至您的開發電腦。

> [!NOTE]
> 使用 Bridge Kubernetes 時，系統會提示您輸入服務的名稱，以重新導向至您的開發電腦。 此選項可讓您輕鬆地識別要重新導向的 pod。 Kubernetes 叢集與開發電腦之間的所有重新導向皆適用于 pod。

當 Bridge 與 Kubernetes 建立連線至您的叢集時，它會：

* 提示您設定要在您的叢集上取代的服務、開發電腦上要用於程式碼的埠，以及程式碼的啟動工作做為一次性動作。
* 以將流量重新導向至您開發電腦的遠端代理程式容器，取代叢集中 pod 的容器。
* 在您的開發電腦上執行 [kubectl 埠轉送][kubectl-port-forward] ，將流量從開發電腦轉送到叢集中執行的遠端代理程式。
* 使用遠端代理程式從您的叢集中收集環境資訊。 此環境資訊包括環境變數、可見服務、磁片區掛接和秘密裝載。
* 在 Visual Studio 中設定環境，讓開發電腦上的服務可以存取和在叢集上執行相同的變數。
* 更新您的主機檔案，將叢集上的服務對應至開發電腦上的本機 IP 位址。 這些主機檔案專案可讓程式碼在您的開發電腦上執行，以對叢集中執行的其他服務提出要求。 若要更新主機檔案，在連線到您的叢集時，Bridge 到 Kubernetes 會要求您的開發電腦上有系統管理員存取權。
* 開始在您的開發電腦上執行和偵錯工具代碼。 如有必要，藉由停止目前正在使用這些埠的服務或處理常式，橋接器至 Kubernetes 將可在您的開發電腦上釋放必要的埠。

建立與叢集的連線之後，您可以在電腦上以原生方式執行和偵測程式碼，而不需要容器化，而且程式碼可以直接與叢集的其餘部分互動。 遠端代理程式接收的任何網路流量都會重新導向至連線期間指定的本機埠，讓原生執行的程式碼可以接受和處理該流量。 您叢集的環境變數、磁片區和秘密可供開發電腦上執行的程式碼使用。 此外，由於主機檔案專案和埠轉送會藉由橋接器新增至 Kubernetes，因此您的程式碼可以使用叢集中的服務名稱，將網路流量傳送至叢集上執行的服務，並將流量轉送至叢集中正在執行的服務。 在您的開發電腦與您的叢集之間進行連線時，會在您的整個叢集中路由傳送流量。

此外，Bridge 與 Kubernetes 可讓您透過檔案，將環境變數和已掛接的檔案複寫至您的開發電腦上的叢集中的 pod `KubernetesLocalProcessConfig.yaml` 。 您也可以使用這個檔案來建立新的環境變數和磁片區裝載。

> [!NOTE]
> 在連線到叢集的持續期間 (加上15分鐘的) ，Bridge Kubernetes 會在您的本機電腦上以系統管理員許可權執行稱為 *EndpointManager* 的進程。

## <a name="additional-configuration-with-kuberneteslocalprocessconfigyaml"></a>使用 KubernetesLocalProcessConfig 的其他設定。 yaml

此檔案可 `KubernetesLocalProcessConfig.yaml` 讓您將環境變數和已掛接的檔案複寫至叢集中的 pod。 如需其他設定選項的詳細資訊，請參閱 [設定橋接器至 Kubernetes][using-config-yaml]。

## <a name="using-routing-capabilities-for-developing-in-isolation"></a>使用路由功能來以隔離方式進行開發

根據預設，Bridge 到 Kubernetes 會將服務的所有流量重新導向至您的開發電腦。 您也可以選擇使用路由功能，僅將源自子域的要求重新導向至您的開發電腦。 這些路由功能可讓您使用橋接器進行 Kubernetes，以隔離地進行開發，並避免中斷叢集中的其他流量。

下列動畫顯示兩位開發人員在相同叢集上進行隔離的開發人員：

![示範隔離的動畫 GIF](media/bridge-to-kubernetes/btk-graphic-isolated.gif)

當您啟用隔離時，除了連接到您的 Kubernetes 叢集之外，Bridge 到 Kubernetes 也會執行下列作業：

* 確認 Kubernetes 叢集未啟用 Azure Dev Spaces。
* 在相同的命名空間中，將您選擇的服務複寫至叢集中，並新增 *routing.visualstudio.io/route-from=SERVICE_NAME* 標籤和 *routing.visualstudio.io/route-on-header=kubernetes-route-as： GENERATED_NAME* 注釋。
* 在 Kubernetes 叢集上的相同命名空間中設定和啟動路由管理員。 當您在命名空間中設定路由時，路由管理員會使用標籤選取器來尋找 *routing.visualstudio.io/route-from=SERVICE_NAME* 標籤和  *routing.visualstudio.io/route-on-header=kubernetes-route-as： GENERATED_NAME* 注釋。

如果 Bridge 與 Kubernetes 偵測到您的 Kubernetes 叢集上已啟用 Azure Dev Spaces，系統會提示您停用 Azure Dev Spaces，然後才能使用 Bridge 來 Kubernetes。

路由管理員會在啟動時執行下列動作：
* 使用子域的 *GENERATED_NAME* ，複製在命名空間中找到的所有 ingresses。
* 針對與具有 *GENERATED_NAME* 子域的重複 ingresses 相關聯的每個服務建立 envoy pod。
* 為您正在隔離的服務建立額外的 envoy pod。 這可讓具有子域的要求路由傳送到您的開發電腦。
* 設定每個 envoy pod 的路由規則，以處理具有子域的服務路由。

下圖顯示在 Bridge 與 Kubernetes 連線至您的叢集之前的 Kubernetes 叢集：

![沒有 Bridge 到 Kubernetes 的叢集圖表](media/bridge-to-kubernetes/kubr-cluster.svg)

下圖顯示在隔離模式中啟用橋接器至 Kubernetes 的相同叢集。 在這裡，您可以看到重複的服務，以及支援隔離的路由 envoy pod。

![已啟用橋接器至 Kubernetes 的叢集圖表](media/bridge-to-kubernetes/kubr-cluster-devcomputer.svg)

在叢集上收到具有 *GENERATED_NAME* 子域的要求時，會將 *kubernetes-route as = GENERATED_NAME* 標頭新增至要求。 Envoy pod 會在叢集中處理對適當服務提出要求的路由。 如果將要求路由傳送至正在隔離運作的服務，則該要求會由遠端代理程式重新導向至您的開發電腦。

當叢集上收到沒有 *GENERATED_NAME* 子域的要求時，就不會將標頭新增至要求。 Envoy pod 會在叢集中處理對適當服務提出要求的路由。 如果將要求路由傳送至即將被取代的服務，則該要求會改為路由傳送至原始服務，而不是路由至遠端代理程式。

> [!IMPORTANT]
> 發出額外的要求時，您叢集上的每個服務都必須轉送 *kubernetes-route as = GENERATED_NAME* 標頭。 例如，當 *services* 收到要求時，它接著會對 *serviceB* 提出要求，然後傳迴響應。 在此範例中， *services* 必須將其要求中的 *kubernetes-route as = GENERATED_NAME* 標頭轉送到 *serviceB*。 某些語言（例如 [ASP.NET][asp-net-header]）可能會有處理標頭傳播的方法。

當您中斷與叢集的連線時，根據預設，Bridge 到 Kubernetes 將會移除所有 envoy pod 和重複的服務。

> [!NOTE]
> 路由管理員部署和服務將會在您的命名空間中繼續執行。 若要移除部署和服務，請針對您的命名空間執行下列命令。
>
> ```azurecli
> kubectl delete deployment routingmanager-deployment -n NAMESPACE
> kubectl delete service routingmanager-service -n NAMESPACE
> ```

## <a name="diagnostics-and-logging"></a>診斷和記錄

使用 Bridge Kubernetes 連接到您的叢集時，叢集的診斷記錄會記錄到您的開發電腦在 *Bridge Kubernetes* 資料夾的 *暫存* 目錄中。

## <a name="rbac-authorization"></a>RBAC 授權

Kubernetes 會提供角色型存取控制 (RBAC) 來管理使用者和群組的許可權。 如需詳細資訊，請參閱 [Kubernetes](https://kubernetes.io/docs/reference/access-authn-authz/rbac/) 檔。您可以藉由建立 YAML 檔案並使用將其套用至叢集，來為啟用 RBAC 的叢集設定許可權 `kubectl` 。 

若要設定叢集的許可權，請建立或修改 YAML 檔，例如 *許可權。* 如下所示 yml、使用您自己的命名空間， `<namespace>` 以及 (使用者和) 群組需要存取權的主體。

```yml
kind: RoleBinding
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: bridgetokubernetes-<namespace>
  namespace: development
subjects:
  - kind: User
    name: jane.w6wn8.k8s.ginger.eu-central-1.aws.gigantic.io
    apiGroup: rbac.authorization.k8s.io
  - kind: Group
    name: dev-admin
    apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: ClusterRole
  name: admin
  apiGroup: rbac.authorization.k8s.io
```

使用命令來套用許可權：

```cmd
kubectl -n <namespace> apply -f <yaml file name>
```

## <a name="limitations"></a>限制

橋接器至 Kubernetes 具有下列限制：

* 服務必須由單一 pod 支援，才能連接至該服務。 您無法連接到具有多個 pod 的服務，例如具有複本的服務。
* Pod 可能只有在該 pod 中執行的單一容器，才能讓 Bridge Kubernetes 成功連接。 橋接器至 Kubernetes 無法連線到具有其他容器的 pod 的服務，例如側車由服務網格插入的容器。
* 目前，Kubernetes pod 的 Bridge 必須是 Linux 容器。 不支援 Windows 容器。
* 隔離無法與 HTTPS 一起使用。
* 橋接器至 Kubernetes 需要較高的許可權，才能在您的開發電腦上執行，以編輯主機檔案。
* 無法在已啟用 Azure Dev Spaces 的叢集上使用 Bridge 與 Kubernetes。

### <a name="bridge-to-kubernetes-and-clusters-with-azure-dev-spaces-enabled"></a>在啟用 Azure Dev Spaces 的情況下橋接至 Kubernetes 和叢集

您無法在已啟用 Azure Dev Spaces 的叢集上使用 Bridge 進行 Kubernetes。 如果您想要在已啟用 Azure Dev Spaces 的叢集上使用橋接器來 Kubernetes，則必須先停用 Azure Dev Spaces，然後再連接到您的叢集。

## <a name="next-steps"></a>後續步驟

若要開始使用 Bridge 來 Kubernetes，以連接到您的本機開發電腦至您的叢集，請參閱 [使用 bridge 來 Kubernetes](bridge-to-kubernetes.md)。

[asp-net-header]: https://www.nuget.org/packages/Microsoft.AspNetCore.HeaderPropagation/
[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-latest&preserve-view=true
[bridge-to-kubernetes-vs]: bridge-to-kubernetes.md
[kubectl-port-forward]: https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#port-forward
[visual-studio]: https://visualstudio.microsoft.com/downloads/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[using-config-yaml]: configure-bridge-to-kubernetes.md