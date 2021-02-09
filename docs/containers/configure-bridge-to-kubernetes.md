---
title: 使用 KubernetesLocalProcessConfig yaml 進行額外的設定，以使用 Bridge 來 Kubernetes
services: azure-dev-spaces
ms.date: 07/28/2020
ms.topic: conceptual
description: 說明使用 KubernetesLocalProcessConfig yaml 橋接器至 Kubernetes 的其他設定選項。
keywords: 橋接至 Kubernetes、Azure Dev Spaces、Dev Spaces、Docker、Kubernetes、Azure、AKS、Azure Kubernetes Service、容器
monikerRange: '>=vs-2019'
author: ghogen
ms.author: ghogen
manager: jmartens
ms.openlocfilehash: b250454fe5e80ec18f75add92c8c2f653893e994
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867616"
---
# <a name="configure-bridge-to-kubernetes"></a>設定 Bridge to Kubernetes

此檔案可 `KubernetesLocalProcessConfig.yaml` 讓您將環境變數和已掛接的檔案複寫至 AKS 叢集中的 pod。 您可以在檔案中指定下列動作 `KubernetesLocalProcessConfig.yaml` ：

* 下載磁片區，並將該磁片區的路徑設定為環境變數。
* 在您的叢集上執行的服務可供在您的開發電腦上執行的進程使用。
* 建立具有常數值的環境變數。

預設檔案 `KubernetesLocalProcessConfig.yaml` 不會自動建立，因此您必須在專案的根目錄手動建立檔案。

## <a name="download-a-volume"></a>下載磁片區

在 [ *env*] 下，為您要下載的每個磁片區指定 *名稱* 和 *值* 。 *名稱* 是將在您的開發電腦上使用的環境變數。 *值* 是磁片區的名稱，以及您開發電腦上的路徑。 *Value* 值的格式為 *$ (volumeMounts： VOLUME_NAME) /PATH/TO/FILES*。

例如：

```yaml
version: 0.1
env:
  - name: ALLOW_LIST_PATH
    value: $(volumeMounts:allow-list)/allow-list
```

上述範例會從容器下載 *允許清單* 磁片區，並將該位置加上環境變數 *ALLOW_LIST_PATH* 的路徑。 預設行為是將檔案下載至您在開發電腦上的臨時目錄下指定的路徑。 在上述範例中， *ALLOW_LIST_PATH* 設定為 `/TEMPORARY_DIR/allow-list` 。 

> [!NOTE]
> 無論您設定的路徑為何，下載磁片區都會下載該磁片區的整個內容。 路徑只會用來設定要在開發電腦上使用的環境變數。 將 */allow-list* 或 */path/to/files* 新增至權杖結尾，實際上並不會影響磁片區的保存位置。 如果您的應用程式需要參考該磁片區中的特定檔案，則環境變數只是方便的。

您也可以選擇指定要在開發電腦上下載磁片區掛接的位置，而不是使用臨時目錄。 在 [ *volumeMounts*] 底下，指定每個特定位置的 *名稱* 和 *localPath* 。 *名稱* 是您想要比對的磁片區名稱，而 *localPath* 是您開發電腦上的絕對路徑。 例如：

```yaml
version: 0.1
volumeMounts:
  - name: default-token-*
    localPath: /var/run/secrets/kubernetes.io/serviceaccount
env:
  - name: KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE
    value: $(volumeMounts:default-token-*)
```

上述範例會使用 *env* 中的專案來下載符合 *\* 預設權杖* 的磁片區，例如 *預設-token-1111* 或 *預設權杖-1234-5678-90abcdef*。 在多個磁片區相符的情況下，會使用第一個相符的磁片區。 所有檔案都會在 `/var/run/secrets/kubernetes.io/serviceaccount` 您的開發電腦上使用 *volumeMounts* 中的專案下載到您的開發電腦上。 *KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE* 環境變數設為 `/var/run/secrets/kubernetes.io/serviceaccount` 。

## <a name="make-a-service-available"></a>讓服務可供使用

在 [ *env*] 下，為您想要在開發電腦上提供的每個服務指定 *名稱* 和 *值* 。 *名稱* 是將在您的開發電腦上使用的環境變數。 *值* 是來自您的叢集的服務名稱和路徑。 *值* 的值採用 " *(services： SERVICE_NAME) /path* 格式。

例如：

```yaml
version: 0.1
env:
  - name: MYAPP1_SERVICE_HOST
    value: $(services:myapp1)/api/v1/
```

上述範例會將 *myapp1* 服務提供給您的開發電腦使用，且 *MYAPP1_SERVICE_HOST* 環境變數會設定為 *myapp1* 服務的本機 IP 位址 `/api/v1` ，路徑 (也就是 `127.1.1.4/api/v1`) 。 您可以使用環境變數、 *myapp1* 或 *myapp1* 來存取 *myapp1* 服務。

> [!NOTE]
> 無論您設定的路徑為何，在您的開發電腦上提供的服務都會讓整個服務都可供使用。 路徑只會用來設定要在開發電腦上使用的環境變數。
您也可以使用 *$ (services： SERVICE_NAME，從可用的特定 Kubernetes 命名空間中建立服務。NAMESPACE_NAME)*。 例如：

```yaml
version: 0.1
env:
  - name: MYAPP2_SERVICE_HOST
    value: $(services:myapp2.mynamespace)
```

上述範例會從您的開發電腦上提供 *mynamespace* 命名空間中的 *myapp2* ，並將 *MYAPP2_SERVICE_HOST* 環境變數設定為 *MYNAMESPACE* 命名空間中 *myapp2* 的本機 IP 位址。

## <a name="create-an-environment-variable-with-a-constant-value"></a>建立具有常數值的環境變數

在 [ *env*] 下，為您想要在開發電腦上建立的每個環境變數指定 *名稱* 和 *值* 。 *名稱* 是將在您的開發電腦上使用的環境變數，而 *值* 則是值。 例如：

```yaml
version: 0.1
env:
  - name: DEBUG_MODE
    value: "true"
```

上述範例會建立名為 *DEBUG_MODE* 的環境變數，並將值 *設為 true*。

## <a name="example-kuberneteslocalprocessconfigyaml"></a>範例 KubernetesLocalProcessConfig. yaml

以下是完整檔案的範例 `KubernetesLocalProcessConfig.yaml` ：

```yaml
version: 0.1
volumeMounts:
  - name: default-token-*
    localPath: /var/run/secrets/kubernetes.io/serviceaccount
env:
  - name: KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE
    value: $(volumeMounts:default-token-*)
  - name: ALLOW_LIST_PATH
    value: $(volumeMounts:allow-list)/allow-list
  - name: MYAPP1_SERVICE_HOST
    value: $(services:myapp1)/api/v1/
  - name: MYAPP2_SERVICE_HOST
    value: $(services:myapp2.mynamespace)
  - name: DEBUG_MODE 
    value: "true"
```

## <a name="next-steps"></a>後續步驟

若要開始使用 Bridge 來 Kubernetes，以連接到您的本機開發電腦至您的叢集，請參閱搭配 [使用 bridge 與 Kubernetes 與 Visual Studio Code][bridge-to-kubernetes-vs-code] ，並 [使用 bridge 搭配 Visual Studio 來 Kubernetes][bridge-to-kubernetes-vs]。

[bridge-to-kubernetes-vs-code]: https://code.visualstudio.com/docs/containers/bridge-to-kubernetes
[bridge-to-kubernetes-vs]: bridge-to-kubernetes.md
