---
title: 在雲端中以使用 Kubernetes 的容器建立 .NET Core 開發環境 - 步驟 5 - 呼叫其他的容器 | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: 在 Azure 上使用容器和微服務快速開發 Kubernetes
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, 容器
manager: douge
ms.openlocfilehash: 6ef3a79d0b79feae64adcaebe31daa48ba75ab75
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31887332"
---
# <a name="get-started-on-connected-environment-with-net-core"></a>使用 .NET Core 開始使用已連線的環境

上一個步驟：[在 Kubernetes 中偵錯容器](get-started-netcore-04.md)

我們會在本節中建立第二項服務 `mywebapi`，並讓 `webfrontend` 呼叫它。 每項服務會在不同的容器中執行。 然後，我們會偵錯這兩個容器。

![](media/multi-container.png)

## <a name="download-sample-code-for-mywebapi"></a>下載 *mywebapi* 的範例程式碼
因為時間有限，讓我們從 GitHub 存放庫下載範例程式碼。 移至 https://github.com/Azure/vsce 選取 [Clone or Download] (複製或下載)，下載 GitHub 存放庫。 這個區段的程式碼位於 `vsce/samples/dotnetcore/getting-started/mywebapi`。


## <a name="run-mywebapi"></a>執行 *mywebapi*
1. 在「不同的 VS Code 視窗」中開啟資料夾 `mywebapi`。
1. 按 F5，等候建置和部署服務。 當 VS Code 偵錯列出現時，您就知道它已就緒。
1. 記下端點 URL，它看起來像 http://localhost:\<連接埠號碼\>。 **提示：VS Code 狀態列會顯示可點選的 URL。** 容器可能看起來像是在本機執行，但實際上是在我們的 Azure 開發環境中執行。 之所以使用本機位址，是因為 `mywebapi` 尚未定義任何公用端點，只能從 Kubernetes 執行個體中存取。 為方便起見，並促進與您本機電腦私用服務的互動，已連線的環境會建立在 Azure 中執行之容器的暫存 SSH 通道。
1. 當 `mywebapi` 就緒時，請在瀏覽器中開啟 localhost 位址。 將 `/api/values` 附加至 URL，以叫用 `ValuesController` 的預設 GET API。 
1. 如果所有步驟都成功，您應該能夠看見來自 `mywebapi` 服務的回應。


## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>從 *webfrontend* 向 *mywebapi* 提出要求
現在在 `webfrontend` 中撰寫程式碼，向 `mywebapi` 提出要求。
1. 切換至 `webfrontend` 的 VS Code 視窗。
1. 「取代」About 方法的程式碼：

```csharp
public async Task<IActionResult> About()
{
    ViewData["Message"] = "Hello from webfrontend";
    
    // Use HeaderPropagatingHttpClient instead of HttpClient so we can propagate
    // headers in the incoming request to any outgoing requests
    using (var client = new HeaderPropagatingHttpClient(this.Request))
    {
        // Call *mywebapi*, and display its response in the page
        var response = await client.GetAsync("http://mywebapi/api/values/1");
        ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
    }

    return View();
}
```

請注意如何運用 Kubernetes 的 DNS 服務探索來將服務參考為 `http://mywebapi`。 **程式碼在我們開發環境中執行的方式，和在生產環境中執行的方式相同**。

上述程式碼範例也使用 `HeaderPropagatingHttpClient` 類別。 此協助程式類別已在您執行 `vsce init` 時，新增至您的程式碼資料夾。 `HeaderPropagatingHttpClient` 衍生自眾所周知的 `HttpClient` 類別，而且會新增功能以將特定的標頭從現有的 ASP.NET HttpRequest 物件傳播到外送的 HttpRequestMessage 物件。 我們稍後會看到這在小組案例中會怎麼協助更具生產力的開發經驗。


## <a name="debug-across-multiple-services"></a>偵錯多項服務
1. 此時，`mywebapi` 應仍在附加偵錯工具的狀態下執行。 如果不是，請在 `mywebapi` 專案中點擊 F5。
1. 在處理 `api/values/{id}` GET 要求的 `Get(int id)` 方法中設定中斷點。
1. 在 `webfrontend` 專案中，在它要將 GET 要求傳送到 `mywebapi/api/values` 之前設定中斷點。
1. 在 `webfrontend` 專案中點擊 F5。
1. 叫用 Web 應用程式，並逐步執行這兩項服務中的程式碼。
1. 在 Web 應用程式中，[關於] 頁面會顯示兩項服務串連的訊息："Hello from webfrontend and Hello from mywebapi"。


做得好！ 現在，您會有每個容器可分別開發與部署的多容器應用程式。

> [!div class="nextstepaction"]
> [了解小組開發](get-started-netcore-06.md)

