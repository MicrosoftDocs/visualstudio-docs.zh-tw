---
title: 疑難排解 | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: troubleshooting
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: 在 Azure 上使用容器和微服務快速開發 Kubernetes
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, 容器
manager: douge
ms.openlocfilehash: b41d228bcced6149c95b09b2445dd656ed9772d6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="troubleshooting-guide"></a>疑難排解指南

## <a name="error-upstream-connect-error-or-disconnectreset-before-headers"></a>錯誤「上游連線錯誤或標頭前的中斷連線/重設」
嘗試存取您的服務時，您可能會看到這個錯誤。 例如，當您在瀏覽器中移至服務的 URL 時。 

**原因：** 容器連接埠無法使用。 以下為最常見的原因： 
* 容器仍在建置和部署中。 如果您執行 `vsce up` 或啟動偵錯工具，然後在容器成功部署前嘗試存取容器，就可能會發生這種狀況。
* Dockerfile、Helm 圖表和任何開放連接埠的伺服端程式碼間的連接埠組態不一致。

**請嘗試：**
1. 如果正在建置/部署容器，您可以等候 2-3 秒，然後再次嘗試存取服務。 
1. 檢查連接埠組態。 以下所有資產的指定連接埠號碼應該**相同**：
    * **Dockerfile：** 由 `EXPOSE` 指令所指定。
    * **[Helm 圖表](https://docs.helm.sh)：** 由服務的 `externalPort` 和 `internalPort` 值所指定 (通常位於 `values.yml` 檔案中)。
    * 在應用程式程式碼中開放的任何連接埠，例如在 Node.js 中為：`var server = app.listen(80, function () {...}`


## <a name="config-file-not-found"></a>找不到組態檔
您執行 `vsce up` 並收到下列錯誤：`Config file not found: .../vsce.yaml`

**原因：**`vsce up` 需要從您要執行的程式碼根目錄執行，而且需要已初始化程式碼資料夾才能在已連線的環境中執行。

**請嘗試：**
1. 將您目前的目錄變更為包含您服務程式碼的根資料夾。 
1. 如果您的程式碼資料夾中沒有 vsce.yaml 檔案，請執行 `vsce init` 產生 Docker、Kubernetes 和 VSCE 資產。

## <a name="error-the-pipe-program-vsce-exited-unexpectedly-with-code-126"></a>錯誤：「管道程式 'vsce' 非預期結束，代碼 126。」
啟動 VS Code 偵錯工具有時會導致這個錯誤。 這是一個 Bug。

**請嘗試：**
1. 關閉並重新開啟 VS Code。
2. 再次點擊 F5。


## <a name="debugging-error-configured-debug-type-coreclr-is-not-supported"></a>偵錯錯誤「不支援設定的偵錯類型 'coreclr'」
執行 VS Code 偵錯工具會回報錯誤：`Configured debug type 'coreclr' is not supported.`

**原因：** 您沒有在開發電腦上安裝已連線環境的 VS Code 延伸模組。

**請嘗試：** 安裝[已連線環境的 Visual Studio 延伸模組](get-started-netcore-01.md#get-kubernetes-debugging-for-vs-code)。


## <a name="the-azure-portal-doesnt-show-connected-environment-instances"></a>Azure 入口網站不會顯示已連線的環境執行個體

**原因：** 已連線環境的 Azure 入口網站體驗尚未備妥，無法提供預覽。


## <a name="the-type-or-namespace-name-mylibrary-could-not-be-found"></a>找不到類型或命名空間名稱 'MyLibrary'

**原因：** 組建的內容預設為專案/服務層級，因此找不到您要使用的程式庫專案。

**請嘗試：** 需要完成的內容：
1. 修改 vsce.yaml 檔案以將組建內容設為解決方案層級。
2. 修改 Dockerfile 和 Dockerfile.develop 檔案以正確指向 csproj 檔案，相對於新的組建內容。
3. 將 .dockerignore 檔案放在 .sln 檔案旁邊，然後視需要修改。

您可以在 https://github.com/sgreenmsft/buildcontextsample 找到範例

## <a name="microsoftconnectedenvironmentregisteraction-authorization-error-when-creating-an-environment"></a>建立環境時發生「Microsoft.ConnectedEnvironment/註冊/動作」授權錯誤
您可能會在管理環境時看到下列錯誤，而且您是在沒有擁有者或參與者存取權限的 Azure 訂用帳戶中工作。
`The client '<User email/Id>' with object id '<Guid>' does not have authorization to perform action 'Microsoft.ConnectedEnvironment/register/action' over scope '/subscriptions/<Subscription Id>'.`

**原因：** 所選 Azure 訂用帳戶尚未註冊 Microsoft.ConnectedEnvironment 命名空間。

**請嘗試：** 擁有 Azure 訂用帳戶擁有者或參與者存取權限的使用者可以執行下列 Azure CLI 命令，手動註冊 Microsoft.ConnectedEnvironment 命名空間：

```cmd
az provider register --namespace Microsoft.ConnectedEnvironment
```

## <a name="vsce-doesnt-seem-to-use-my-existing-dockerfile-to-build-a-container"></a>VSCE 似乎不使用我現有的 Dockerfile 來建置容器 

**原因：** VSCE 可以設定為指向您專案中的特定 Dockerfile。 如果 VSCE 似乎不使用您預期的 Dockerfile 來建置您的容器，您可能需要明確告知 VSCE 它的位置。 

**請嘗試：** 開啟 VSCE 在您專案中產生的 `vsce.yaml` 檔案。 使用 `configurations->develop->build->dockerfile` 指示詞指向您想要使用 Dockerfile：

```
...
configurations:
  develop:
    build:
      dockerfile: Dockerfile.develop
```