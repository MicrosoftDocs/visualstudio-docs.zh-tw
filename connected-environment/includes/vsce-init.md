---
ms.topic: include
ms.openlocfilehash: 394e31bf0660557c1eba571006cacf213263c07e
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
## <a name="initialize-code-for-docker-and-kubernetes-development"></a>初始化 Docker 和 Kubernetes 開發的程式碼
截至目前為止，我們已有可在本機執行的基本 Web 應用程式。 我們現在要透過建立資產，以定義應用程式的容器並將它部署到 Kubernetes 的方式，將它容器化。 使用已連線的環境很容易執行此作業： 

1. 啟動 VS Code 並開啟 `webfrontend` 資料夾。 (您可以忽略任何預設提示，以新增偵錯資產或還原專案)。
1. 在 VS Code 中開啟整合式終端機 (使用 [檢視] | [整合式終端機] 功能表)。
1. 執行這個命令 (請確認 **webfrontend** 是您目前的資料夾)：

```cmd
vsce init --public
```

已連線的環境 CLI 之 ```init``` 命令會產生有預設設定的 Docker 和 Kubernetes 資產：
* `./Dockerfile` 會描述應用程式的容器映像，以及如何在容器內建置和執行原始程式碼。
* `./charts/webfrontend` 下的 [Helm 圖表](https://docs.helm.sh)會描述如何將容器部署到 Kubernetes。

目前不需要了解這些檔案的完整內容。 但有一點值得特別點出，**相同的 Kubernetes 和 Docker 組態即程式碼資產，可從開發一直用到生產環境中，因此為不同的環境提供較佳的一致性。**
 
`init` 命令也會產生名為 `./vsce.yaml` 的檔案，這是已連線的環境組態檔。 它使用可在 Azure 中反覆開發體驗的其他組態，完善了 Docker 和 Kubernetes 成品。 例如，預設的 Helm 圖表不公開任何公用端點。 但有時候，在開發期間暫時開放公用端點以便測試您的程式碼是很有用的，例如行動裝置或 Webhook URL 的公用端點。 使用 `init --public` 建立的 vsce.yaml 檔案會覆寫 Helm 預設參數，僅在開發期間公開公用端點。
