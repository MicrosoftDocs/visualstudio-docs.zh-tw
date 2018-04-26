---
title: 在雲端中以使用 Kubernetes 的容器建立 .NET Core 開發環境 - 步驟 4 - 在 Kubernetes 中偵錯容器 | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: 在 Azure 上使用容器和微服務快速開發 Kubernetes
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, 容器
manager: douge
ms.openlocfilehash: 043052dec78251647a3ef12e0b612355b6334692
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>使用 .NET Core 開始使用已連線的環境
 
上一個步驟：[建立 ASP.NET Core Web 應用程式](get-started-netcore-03.md)

[!INCLUDE[](includes/debug-intro.md)]

[!INCLUDE[](includes/init-debug-assets-vscode.md)]


## <a name="select-the-vsce-debug-configuration"></a>選取 VSCE 偵錯組態
1. 若要開啟 [偵錯] 檢視，請按一下 VS Code 旁邊**活動列**的偵錯圖示。
1. 選取 [.NET Core Launch (VSCE)] (.NET Core 啟動 (VSCE)) 作為使用中的偵錯組態。

![](media/debug-configuration.png)

> [!Note]
> 如果您在命令選擇區中沒有看到任何已連線的環境命令，請確定您已[安裝已連線環境的 VS Code 延伸模組](get-started-netcore-01.md#get-kubernetes-debugging-for-vs-code)。


## <a name="debug-the-container-in-kubernetes"></a>在 Kubernetes 中偵錯容器
點擊 **F5** 在 Kubernetes 中偵錯程式碼。

如同 `up` 命令一樣，程式碼已同步處理到開發環境，並建置容器部署到 Kubernetes。 當然，偵錯工具此時已附加至遠端容器。

[!INCLUDE[](includes/tip-vscode-status-bar-url.md)]

在伺服器端程式碼檔案中設定中斷點，例如在 `Controllers/HomeController.cs` 原始程式檔的 `Index()` 函式中。 重新整理瀏覽器頁面會導致點擊中斷點。

您擁有完整的存取權，可像程式碼在本機執行一樣偵錯資訊，例如呼叫堆疊、區域變數、例外狀況資訊等等。

## <a name="edit-code-and-refresh"></a>編輯程式碼並重新整理
在啟動偵錯工具的狀態下，編輯程式碼。 例如，修改 `Controllers/HomeController.cs` 中的 [關於] 頁面訊息。 

```csharp
public IActionResult About()
{
    ViewData["Message"] = "My custom message in the About page.";
    return View();
}
```

儲存檔案，並按一下 [偵錯動作] 窗格的 [重新整理] 按鈕。 

![](media/debug-action-refresh.png)

已連線的環境不是在每次編輯程式碼後重建及重新部署新的容器映像，這通常需要相當長的時間，而是以累加方式重新編譯現有容器中的程式碼，以提供更快的編輯/偵錯迴圈。

重新整理瀏覽器中的 Web 應用程式，移至 [關於] 頁面。 您應該會看到您的自訂訊息出現在 UI 中。

**現在您有方法可以快速重複程式碼並直接在 Kubernetes 中偵錯！** 接下來，我們會看到如何建立及呼叫第二個容器。

> [!div class="nextstepaction"]
> [呼叫在不同容器中執行的服務](get-started-netcore-05.md)
