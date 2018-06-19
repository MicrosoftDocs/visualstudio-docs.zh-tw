---
title: 在雲端中以使用 Kubernetes 的容器建立 Node.js 開發環境 - 步驟 3 - 建立 ASP.NET Web 應用程式 | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: 在 Azure 上使用容器和微服務快速開發 Kubernetes
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, 容器
manager: douge
ms.openlocfilehash: 34e1f07e173ccba6aab561fb4795abbe938e0127
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31890150"
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>使用 Node.js 開始使用已連線的環境

上一個步驟：[在 Azure 中建立 Kubernetes 開發環境](get-started-nodejs-02.md)

## <a name="create-a-nodejs-web-app"></a>建立 Node.js Web 應用程式
巡覽至 https://github.com/Azure/vsce 選取 [Clone or Download] (複製或下載)，從 GitHub 下載程式碼，將 GitHub 存放庫下載到您的本機環境。 本指南中的程式碼位於 `vsce/samples/nodejs/getting-started/webfrontend`。

[!INCLUDE[](includes/vsce-init.md)]

[!INCLUDE[](includes/ensure-env-created.md)]

[!INCLUDE[](includes/build-and-run-in-k8s-cli.md)]

## <a name="update-a-content-file"></a>更新內容檔案
已連線的環境不只是要在 Kubernetes 中執行程式碼，它能讓您快速反覆看到程式碼變更在雲端 Kubernetes 環境中的效果。

1. 找出檔案 `./public/index.html` 並編輯 HTML。 例如，將網頁的背景色彩變更為藍色陰影：

```html
<body style="background-color: #95B9C7; margin-left:10px; margin-right:10px;">
```

2. 儲存檔案。 稍後，在終端機視窗中，您會看到有訊息指出執行中的容器檔案已更新。
1. 移至您的瀏覽器並重新整理頁面。 您應該會看到您更新的色彩。

發生什麼情況？ 編輯 HTML 和 CSS 等內容檔案，不需要重新啟動 Node.js 程序，所以有效的 `vsce up` 命令會自動將任何修改過的內容檔案直接同步處理到 Azure 中執行的容器，進而提供快速的方法以查看您的內容編輯。

### <a name="test-from-a-mobile-device"></a>從行動裝置測試
如果您在行動裝置上開啟 Web 應用程式，您會發現該 UI 無法正確顯示在小型裝置上。

為修正此問題，我們會新增 `viewport` 中繼標籤：
1. 開啟檔案 `./public/index.html`
1. 在現有的 `head` 項目中新增 `viewport` 中繼標籤：

```html
<head>
    <!-- Add this line -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
</head>
```

1. 儲存檔案。
1. 重新整理您的裝置瀏覽器。 您現在應該會看到正確呈現的 Web 應用程式。 

有些問題要到您在打算使用應用程式的裝置上測試後才會發現，此即一例。 使用 VS 已連線的環境，您可以快速重複您的程式碼，並驗證目標裝置上的所有變更。

## <a name="update-a-code-file"></a>更新程式碼檔案
更新伺服器端程式碼檔案需要多一點的工作，因為需要重新啟動 Node.js 應用程式。

1. 在終端機視窗中，按下 `Ctrl+C` (停止 `vsce up`)。
1. 開啟名為 `server.js` 的程式碼檔案，編輯服務的歡迎訊息： 

```javascript
res.send('Hello from webfrontend running in Azure!');
```

3. 儲存檔案。
1. 在終端機視窗中執行 `vsce up`。 

這會重建容器映像，並重新部署 Helm 圖表。 重新載入瀏覽器頁面，查看生效的程式碼變更。


但開發程式碼還有一個「更快速的方法」，我們會在下一節中探討。 
> [!div class="nextstepaction"]
> [在 Kubernetes 中偵錯容器](get-started-nodejs-04.md)
