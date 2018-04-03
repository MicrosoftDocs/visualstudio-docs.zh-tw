---
title: 在雲端中以使用 Kubernetes 的容器建立 Node.js 開發環境 - 步驟 5 - 呼叫其他的容器 | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: 在 Azure 上使用容器和微服務快速開發 Kubernetes
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, 容器
manager: ghogen
ms.openlocfilehash: 5b7065714475ee700fb1a04502a50a4fce0b0e8d
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>使用 Node.js 開始使用已連線的環境

上一個步驟：[在 Kubernetes 中偵錯容器](get-started-nodejs-04.md)

我們會在本節中建立第二項服務 `mywebapi`，並讓 `webfrontend` 呼叫它。 每項服務會在不同的容器中執行。 然後，我們會偵錯這兩個容器。

![](media/multi-container.png)

## <a name="open-sample-code-for-mywebapi"></a>開啟 *mywebapi* 的範例程式碼
您在名為 `vsce/samples` 的資料夾下應該已有本指南 `mywebapi` 的範例程式碼，(如果沒有，請移至 https://github.com/Azure/vsce 選取 [Clone or Download] (複製或下載)，下載 GitHub 存放庫)。這個區段的程式碼位於 `vsce/samples/nodejs/getting-started/mywebapi`。

## <a name="run-mywebapi"></a>執行 *mywebapi*
1. 在*不同的 VS Code 視窗*中開啟資料夾 `mywebapi`。
1. 按 F5，等候建置和部署服務。 當 VS Code 偵錯列出現時，您就知道它已就緒。
1. 記下端點 URL，它看起來像 http://localhost:\<連接埠號碼\>。 **提示：VS Code 狀態列會顯示可點選的 URL。** 容器可能看起來像是在本機執行，但實際上是在我們的 Azure 開發環境中執行。 之所以使用本機位址，是因為 `mywebapi` 尚未定義任何公用端點，只能從 Kubernetes 執行個體中存取。 為方便起見，並促進與您本機電腦私用服務的互動，已連線的環境會建立在 Azure 中執行之容器的暫存 SSH 通道。
1. 當 `mywebapi` 就緒時，請在瀏覽器中開啟 localhost 位址。 您應該會看到來自 `mywebapi` 服務的回應 ("Hello from mywebapi")。


## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>從 *webfrontend* 向 *mywebapi* 提出要求
現在在 `webfrontend` 中撰寫程式碼，向 `mywebapi` 提出要求。
1. 切換至 `webfrontend` 的 VS Code 視窗。
1. 在 `server.js` 的上方新增這些程式碼：
```javascript
var request = require('request');
var propagateHeaders = require('./propagateHeaders');
```

3. 「取代」`/api` GET 處理常式的程式碼。 處理要求時，會輪流呼叫 `mywebapi`，然後傳回這兩項服務的結果。

```javascript
app.get('/api', function (req, res) {
    request({
        uri: 'http://mywebapi',
        headers: propagateHeaders.from(req) // propagate headers to outgoing requests
    }, function (error, response, body) {
        res.send('Hello from webfrontend and ' + body);
    });
});
```

請注意如何運用 Kubernetes 的 DNS 服務探索來將服務參考為 `http://mywebapi`。 **程式碼在我們開發環境中執行的方式，和在生產環境中執行的方式相同**。

上述程式碼範例會利用名為 `propagateHeaders` 的協助程式模組。 此協助程式已在您執行 `vsce init` 時，新增至您的程式碼資料夾。 `propagateHeaders.from()` 函式會從現有的 http.IncomingMessage 物件將特定的標頭傳播至傳出要求的標頭物件。 我們稍後會看到這在小組案例中會怎麼協助更具生產力的開發經驗。


## <a name="debug-across-multiple-services"></a>偵錯多項服務
1. 此時，`mywebapi` 應仍在附加偵錯工具的狀態下執行。 如果不是，請在 `mywebapi` 專案中點擊 F5。
1. 在預設的 GET `/` 處理常式中設定中斷點。
1. 在 `webfrontend` 專案中，在它要將 GET 要求傳送到 `http://mywebapi` 之前設定中斷點。
1. 在 `webfrontend` 專案中點擊 F5。
1. 開啟 Web 應用程式，並逐步執行這兩項服務中的程式碼。 Web 應用程式中應會顯示兩項服務串連的訊息："Hello from webfrontend and Hello from mywebapi"。


做得好！ 現在，您會有每個容器可分別開發與部署的多容器應用程式。

> [!div class="nextstepaction"]
> [了解小組開發](get-started-nodejs-06.md)
