---
title: 在雲端中以使用 Kubernetes 的容器建立 Node.js 開發環境 - 步驟 4 - 在 Kubernetes 中偵錯容器 | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: 在 Azure 上使用容器和微服務快速開發 Kubernetes
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, 容器
manager: douge
ms.openlocfilehash: 2d1ec5fe0436b394083a247faa4519505aa21ceb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31888541"
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>使用 Node.js 開始使用已連線的環境

上一個步驟：[在 Kubernetes 中建立 Node.js 容器](get-started-nodejs-03.md)

[!INCLUDE[](includes/debug-intro.md)]

[!INCLUDE[](includes/init-debug-assets-vscode.md)]


## <a name="select-the-vsce-debug-configuration"></a>選取 VSCE 偵錯組態
1. 若要開啟 [偵錯] 檢視，請按一下 VS Code 旁邊**活動列**的偵錯圖示。
1. 選取 [Launch Program (VSCE)] (啟動方案 (VSCE)) 作為使用中的偵錯組態。

![](media/debug-configuration-nodejs.png)

> [!Note]
> 如果您在命令選擇區中沒有看到任何已連線的環境命令，請確定您已[安裝已連線環境的 VS Code 延伸模組](get-started-nodejs-01.md#get-kubernetes-debugging-for-vs-code)。

## <a name="debug-the-container-in-kubernetes"></a>在 Kubernetes 中偵錯容器
點擊 **F5** 在 Kubernetes 中偵錯程式碼！

類似 `up` 命令，程式碼在您開始偵錯時已同步處理到開發環境，且已建置容器並部署到 Kubernetes。 當然，偵錯工具此時已附加至遠端容器。

[!INCLUDE[](includes/tip-vscode-status-bar-url.md)]

在伺服器端程式碼檔案中設定中斷點，例如在 `server.js` 的 `app.get('/api'...` 中。 重新整理瀏覽器頁面，或按 [Say It Again] (再說一次) 按鈕，而且您應該點擊中斷點，且能夠逐步執行程式碼。

您擁有完整的存取權，可像程式碼在本機執行一樣偵錯資訊，例如呼叫堆疊、區域變數、例外狀況資訊等等。

## <a name="edit-code-and-refresh-the-debug-session"></a>編輯程式碼並重新整理偵錯工作階段
在偵錯工具啟動的狀態下編輯程式碼，例如，再次修改歡迎訊息：

```javascript
app.get('/api', function (req, res) {
    res.send('**** Hello from webfrontend running in Azure! ****');
});
```

儲存檔案，並按一下 [偵錯動作] 窗格的 [重新整理] 按鈕。 

![](media/debug-action-refresh-nodejs.png)

已連線的環境不是在每次編輯程式碼後重建及重新部署新的容器映像，這通常需要相當長的時間，而是在偵錯工作階段間重新啟動 Node.js 程序，以提供更快的編輯/偵錯迴圈。

在瀏覽器中重新整理 Web 應用程式，或按 [Say It Again] (再說一次) 按鈕。 您應該會看到您的自訂訊息出現在 UI 中。


## <a name="use-nodemon-to-develop-even-faster"></a>使用 NodeMon 更快開發
*Nodemon* 是 Node.js 開發人員用於快速開發的常用工具。 開發人員不是在每次編輯伺服器端程式碼時以手動方式重新啟動節點處理序，而是通常會設定其節點專案變更 *nodemon* 監視檔案，並自動重新啟動伺服器程序。 在這種工作形態中，開發人員只需要在編輯程式碼後重新整理瀏覽器。

已連線的環境旨在讓您能夠使用您於本機開發時所採用的同一個具生產力的開發工作流程。 為加以說明，範例 `webfrontend` 專案已設定使用 *nodemon* (它在 `package.json` 中設定為開發相依性)。

請嘗試下列動作：
1. 停止 VS Code 偵錯工具。
1. 按一下 VS Code 旁**活動列**的偵錯圖示。 
1. 選取 [Attach (VSCE)] (附加 (VSCE)) 作為使用中的偵錯組態。
1. 點擊 F5。

在這個組態中，設定容器啟動 *nodemon*。 完成伺服器程式碼編輯後，*nodemon* 會自動重新啟動節點程序，就像您在本機開發時一樣。 
1. 再次編輯 `server.js` 中的歡迎訊息，然後儲存檔案。
1. 重新整理瀏覽器中，或按一下 [Say It Again] (再說一次) 按鈕，查看您生效的變更！

**現在您有方法可以快速重複程式碼並直接在 Kubernetes 中偵錯！** 接下來，我們會看到如何建立及呼叫第二個容器。

> [!div class="nextstepaction"]
> [呼叫在不同容器中執行的服務](get-started-nodejs-05.md)

