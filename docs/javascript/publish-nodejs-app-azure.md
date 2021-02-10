---
title: 將 Node.js 應用程式發佈到 Linux App Service
description: 您可以將 Visual Studio 中建立的 Node.js 應用程式發佈到 Azure 上的 Linux App Service
ms.date: 11/22/2019
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: c83516891a33a026399a6e5fcfc2458b5e03a0bd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945431"
---
# <a name="publish-a-nodejs-application-to-azure-linux-app-service"></a>將 Node.js 應用程式發佈到 Azure (Linux App Service)

本教學課程會引導您完成建立簡單的 Node.js 應用程式，並將其發佈到 Azure 的工作。

將 Node.js 應用程式發佈到 Azure 有數個選項。 這些選項包括 Azure App Service、執行您所選擇之 OS 的 VM、用於 Kubernetes 管理的 Azure Container Service (AKS)、使用 Docker 的容器執行個體等等。 如需每個選項的詳細資料，請參閱[計算](https://azure.microsoft.com/product-categories/compute/)。

在本教學課程中，您會將應用程式部署至 [Linux App Service](/azure/app-service/containers/app-service-linux-intro)。
Linux App Service 會部署 Linux Docker 容器來執行 Node.js 應用程式 (相對於 Windows App Service，它會在 Windows 的 IIS 背後執行 Node.js 應用程式)。

本教學課程示範如何建立 Node.js 應用程式 (從使用適用於 Visual Studio 的 Node.js 工具所安裝的範本開始)、將程式碼推送至 GitHub 上的存放庫，然後透過 Azure 入口網站佈建 Azure App Service，讓您可以從 GitHub 存放庫進行部署。 若要使用命令列來佈建 Azure App Service，並從本機 Git 存放庫推送程式碼，請參閱[建立 Node.js 應用程式](/azure/app-service/containers/quickstart-nodejs)。

在本教學課程中，您會了解如何：
> [!div class="checklist"]
> * 建立 Node.js 專案
> * 建立程式碼的 GitHub 存放庫
> * 在 Azure 上建立 Linux App Service
> * 部署至 Linux

## <a name="prerequisites"></a>必要條件

* 您必須安裝 Visual Studio 和 Node.js 開發工作負載。

    ::: moniker range=">=vs-2019"
    如果您尚未安裝 Visual Studio 2019，請移至 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/) 頁面，免費進行安裝。
    ::: moniker-end
    ::: moniker range="vs-2017"
    如果您尚未安裝 Visual Studio 2017，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)頁面免費進行安裝。
    ::: moniker-end

    如果您需要安裝工作負載，但已有 Visual Studio，請移至 [**工具**  >  **取得工具和功能**]，這會開啟 Visual Studio 安裝程式。 選擇 [Node.js 開發] 工作負載，然後選擇 [修改]。

    ![VS 安裝程式中的 Node.js 工作負載](../ide/media/quickstart-nodejs-workload.png)

* 您必須安裝 Node.js 執行階段。

    如果您沒有安裝，請從 [Node.js](https://nodejs.org/en/download/) 網站安裝 LTS 版本。 一般而言，Visual Studio 會自動偵測已安裝的 Node.js 執行階段。 如果偵測不到已安裝的執行階段，您可以在屬性頁面中將專案設定為參考已安裝的執行階段 (建立專案之後，以滑鼠右鍵按一下專案節點，然後選擇 [屬性])。

## <a name="create-a-nodejs-project-to-run-in-azure"></a>建立 Node.js 專案以在 Azure 執行

1. 開啟 Visual Studio。

1. 建立新的 TypeScript Express 應用程式。

    ::: moniker range=">=vs-2019"
    按 **Esc** 關閉開始視窗。 鍵入 **Ctrl + Q** 開啟 [搜尋] 方塊，鍵入 **Node.js**，然後選擇 [建立新的基礎 Azure Node.js Express 4 應用程式] (TypeScript)。 在出現的對話方塊中選擇 [建立]。
    ::: moniker-end
    ::: moniker range="vs-2017"
    從頂端功能表列中 **，選擇 [** 檔案  >  **新增**  >  **專案**]。 在 [新增專案] 對話方塊的左窗格中，展開 **TypeScript**，然後選擇 **Node.js**。 在中間窗格中，選擇 [ **基本 Azure Node.js Express 4 應用程式**]，然後選擇 **[確定]**。

    ![建立新的 TypeScript Express 應用程式](../javascript/media/azure-ts-express-app.png)
    ::: moniker-end
    如果您看不到 [基本的 Azure Node.js Express 4 應用程式] 專案範本，則必須新增 **Node.js 開發** 工作負載。 如需詳細指示，請參閱[必要條件](#prerequisites)。

    Visual Studio 隨即建立專案，並在 [方案總管] (右窗格) 中開啟該專案。

1. 按 **F5** 來建置和執行應用程式，並確定一切都如預期般運作。

1. 選取  >  [檔案 **新增至原始檔控制**]，以建立專案的本機 Git 存放庫。

    此時，使用 Express 架構且以 TypeScript 撰寫的 Node.js 應用程式會運作，並簽入至本機原始檔控制。

1. 視需要編輯專案，再繼續下一個步驟。

## <a name="push-code-from-visual-studio-to-github"></a>將來自 Visual Studio 的程式碼推送至 GitHub

設定適用於 Visual Studio 的 GitHub：

1. 確定已使用 [工具] > [延伸模組和更新] 功能表項目安裝和啟用 [Visual Studio 的 GitHub 延伸模組](https://visualstudio.github.com/)。

2. 從功能表選取 [ **View**  >  **Other Windows**  >  **GitHub**]。

    [GitHub] 視窗隨即開啟。

3. 如果您在 [GitHub] 視窗中沒有看到 [開始使用] 按鈕，請按一下 [檔案] > [新增至原始檔控制] 並等候 UI 更新。

    ![開啟 [GitHub] 視窗](../javascript/media/azure-github-get-started.png)

4. 按一下 [開始使用]。

    如果您已連線至 GitHub，顯示的工具箱類似於下圖。

    ![GitHub 存放庫設定](../javascript/media/azure-github-publish.png)

5. 完成要發佈之新存放庫的欄位，然後按一下 [發佈]。

    幾分鐘之後會出現橫幅，指出「成功建立存放庫」。

    在下一節中，您將了解如何從這個存放庫發佈到 Linux 上的 Azure App Service。

## <a name="create-a-linux-app-service-in-azure"></a>在 Azure 中建立 Linux App Service

1. 登入 [Azure 入口網站](https://portal.azure.com)。

2. 從左側的服務清單中選取 [應用程式服務]，然後按一下 [新增]。

3. 若需要，請建立新的資源群組和 App Service 方案來裝載新的應用程式。

4. 務必將 [OS] 設定為 [Linux]，並將 [執行階段堆疊] 設定為所需的 Node.js 版本，如圖所示。

    ![建立 Linux App Service](../javascript/media/azure-create-appservice-annotated.png)

5. 按一下 [建立] 來建立 App Service。

    部署可能需要幾分鐘的時間。

6. 完成部署後，請移至 [應用程式設定] 區段，並新增名稱為 `SCM_SCRIPT_GENERATOR_ARGS` 且值為 `--node` 的設定。

    ![應用程式設定](../javascript/media/azure-script-generator-args.png)

    > [!WARNING]
    > App Service 部署流程會使用一組啟發學習法，來決定要嘗試和執行哪一種類型的應用程式。 如果在已部署的內容中偵測到 .*sln* 檔案，則會假設正在部署 MSBuild 型專案。 上述新增的設定會覆寫此邏輯，並明確指定這是 Node.js 應用程式。 若沒有此設定，當 .*sln* 檔案是部署至 App Service 之存放庫的一部分時，Node.js 應用程式將無法部署。

7. 在 [ **應用程式設定**] 下，新增名稱為 `WEBSITE_NODE_DEFAULT_VERSION` 和值的其他設定 `8.9.0` 。

8. 完成部署後，請開啟 App Service，然後選取 [部署選項]。

    ![部署選項](../javascript/media/azure-deployment-options.png)

9. 按一下 [選擇來源]，然後選擇 [GitHub]，並設定任何必要的權限。

    ![GitHub 權限](../javascript/media/azure-choose-source.png)

10. 選取要發佈的存放庫和分支，然後選取 [確定]。

    ![發佈到 Linux App Service](../javascript/media/azure-repo-and-branch.png)

    [部署選項] 頁面會在同步處理時顯示。

    ![部署 GitHub 和與其同步處理](../javascript/media/azure-deployment-options-sync.png)

    完成同步處理之後，就會顯示核取記號。

    網站現在正從 GitHub 存放庫執行 Node.js 應用程式，而且它可在針對 Azure App Service 建立的 URL 上進行存取 (預設提供給 Azure App Service 的名稱後面接著 ".azurewebsites.net")。

## <a name="modify-your-app-and-push-changes"></a>修改您的應用程式並推送變更

1. 在 *app.ts* 的 `app.use('/users', users);` 這一行後面新增此處所顯示的程式碼。 這會在 URL */api* 上新增 REST API。

    ```typescript
    app.use('/api', (req, res, next) => {
        res.json({"result": "success"});
    });
    ```

2. 建置程式碼並在本機上測試，然後將它簽入並推送至 GitHub。

    在 Azure 入口網站中，需要一些時間來偵測 GitHub 存放庫中的變更，然後開始進行新的部署同步處理。 其外觀應與下圖類似。

    ![修改和同步處理](../javascript/media/azure-changes-detected.png)

3. 部署完成之後，請巡覽至公用網站，並將 */api* 附加至 URL。 系統會傳回 JSON 回應。

## <a name="troubleshooting"></a>疑難排解

* 如果 node.exe 處理序終止 (亦即，發生未處理的例外狀況)，容器就會重新啟動。
* 當容器啟動時，它會執行各種不同的啟發學習法，來了解如何啟動 Node.js 處理序。 在 [generateStartupCommand.js](https://github.com/Azure/app-service-builtin-images/blob/master/node/8.9.4/startup/generateStartupCommand.js) 上可以查看實作的詳細資料。
* 您可以透過 SSH 連線至執行中的容器來進行調查。 使用 Azure 入口網站即可輕鬆完成此動作。 請選取 App Service，然後向下捲動工具清單，直到到達 [開發工具] 區段底下的 [SSH]。
* 若要協助進行疑難排解，請移至 App Service 的 [診斷記錄檔] 設定，並將 [Docker 容器記錄] 設定從 [關閉] 變更為 [檔案系統]。 記錄檔建立在容器的 */home/LogFiles/* _docker.log* 下，而且可以使用 SSH 或 FTP(S) 在電腦上進行存取。
* 您可以將自訂網域名稱指派給網站，而不是預設指派的 *.azurewebsites.net URL。 如需詳細資料，請參閱[對應自訂網域](/azure/app-service/app-service-web-tutorial-custom-domain)主題。
* 在移至生產環境之前，部署至預備網站以進行進一步測試是最佳做法。 如需如何設定此動作的詳細資料，請參閱[建立預備環境](/azure/app-service/web-sites-staged-publishing)主題。
* 如需更多常見問題，請參閱 [Linux 上的 App Service 常見問題集](/azure/app-service/containers/app-service-linux-faq)。

## <a name="next-steps"></a>下一步

在本教學課程中，您已了解如何建立 Linux App Service，以及將 Node.js 應用程式部署至服務。 您可能想要深入了解 Linux App Service。

> [!div class="nextstepaction"]
> [Linux App Service](/azure/app-service/containers/app-service-linux-intro)
