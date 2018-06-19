---
title: 在雲端中以使用 Kubernetes 的容器建立 .NET Core 開發環境 - 步驟 3 - 建立 ASP.NET Core Web 應用程式 | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: 在 Azure 上使用容器和微服務快速開發 Kubernetes
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, 容器
manager: douge
ms.openlocfilehash: 72c7df0a82b91f7b4665b8b7e2cecdfc2eea26cf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31887748"
---
# <a name="get-started-on-connected-environment-with-net-core"></a>使用 .NET Core 開始使用已連線的環境

上一個步驟：[在 Azure 中建立 Kubernetes 開發環境](get-started-netcore-02.md)

## <a name="create-an-aspnet-core-web-app"></a>建立 ASP.NET Core Web 應用程式
如果您已安裝 [.NET Core](https://www.microsoft.com/net)，您可以在名為 `webfrontend` 的資料夾中快速建立 ASP.NET Core Web 應用程式。
```cmd
dotnet new mvc --name webfrontend
```

或者，巡覽至 https://github.com/Azure/vsce 選取 [Clone or Download] (複製或下載)，**從 GitHub 下載範例程式碼**，將 GitHub 存放庫下載到您的本機環境。 本指南中的程式碼位於 `vsce/samples/dotnetcore/getting-started/webfrontend`。

[!INCLUDE[](includes/vsce-init.md)]

[!INCLUDE[](includes/ensure-env-created.md)]

[!INCLUDE[](includes/build-and-run-in-k8s-cli.md)]

## <a name="update-a-content-file"></a>更新內容檔案
已連線的環境不只是要在 Kubernetes 中執行程式碼，它能讓您快速反覆看到程式碼變更在雲端 Kubernetes 環境中的效果。

1. 找出檔案 `./Views/Home/Index.cshtml` 並編輯 HTML。 例如，將內容為 `<h2>Application uses</h2>` 的程式碼行 70 變更為：`<h2>Hello k8s in Azure!</h2>`
1. 儲存檔案。 稍後，在終端機視窗中，您會看到有訊息指出執行中的容器檔案已更新。
1. 移至您的瀏覽器並重新整理頁面。 您應該會看到顯示已更新 HTML 的網頁。

發生什麼情況？ 編輯 HTML 和 CSS 等內容檔案，不需要在 .NET Core Web 應用程式中重新編譯，所以有效的 `vsce up` 命令會自動將任何修改過的內容檔案同步處理到 Azure 中執行的容器，進而提供快速的方法以查看您的內容編輯。

## <a name="update-a-code-file"></a>更新程式碼檔案
更新程式碼檔案需要多一點的工作，因為 .NET Core 應用程式需要重建和產生更新的應用程式二進位檔。

1. 在終端機視窗中，按下 `Ctrl+C` (停止 `vsce up`)。
1. 開啟名為 `Controllers/HomeController.cs` 的程式碼檔案，並編輯 [關於] 頁面顯示的訊息：`ViewData["Message"] = "Your application description page.";`
1. 儲存檔案。
1. 在終端機視窗中執行 `vsce up`。 

這會重建容器映像，並重新部署 Helm 圖表。 若要在執行中的應用程式中查看生效的程式碼變更，請移至 Web 應用程式的 [關於] 功能表。


但開發程式碼還有一個「更快速的方法」，我們會在下一節中探討。 
> [!div class="nextstepaction"]
> [在 Kubernetes 中偵錯容器](get-started-netcore-04.md)

