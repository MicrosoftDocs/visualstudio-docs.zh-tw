---
title: 使用 Visual Studio 在雲端中以使用 Kubernetes 的容器建立 .NET Core 開發環境 - 步驟 5 - 呼叫其他的容器 | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: 在 Azure 上使用容器和微服務快速開發 Kubernetes
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, 容器
manager: ghogen
ms.openlocfilehash: 8b0a0c78496b8f57764383d737e2a1cebb2dd6b9
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>使用 .NET Core 和 Visual Studio 開始使用已連線的環境

上一個步驟：[在 Kubernetes 中偵錯容器](get-started-netcore-visualstudio-04.md)

## <a name="call-another-container"></a>呼叫其他容器
我們會在本節中建立第二項服務 `mywebapi`，並讓 `webfrontend` 呼叫它。 每項服務會在不同的容器中執行。 然後，我們會偵錯這兩個容器。

![](media/multi-container.png)

## <a name="download-sample-code-for-mywebapi"></a>下載 *mywebapi* 的範例程式碼
因為時間有限，讓我們從 GitHub 存放庫下載範例程式碼。 移至 https://github.com/Azure/vsce 選取 [Clone or Download] (複製或下載)，下載 GitHub 存放庫。 這個區段的程式碼位於 `vsce/samples/dotnetcore/getting-started/mywebapi`。

## <a name="run-mywebapi"></a>執行 *mywebapi*
1. 在「不同的 Visual Studio 視窗」中開啟專案 `mywebapi`。
1. 如同您之前對 `webfrontend` 專案所做的那樣，從 [啟動設定] 下拉式清單中選取 [Connected Environment for AKS] (適用於 AKS 之已連線的環境)。 此時，請選取您已經建立的同一個開發環境，而不是建立新的開發環境。 如同前文，保留空間的預設值為 `mainline`，然後按一下 [確定]。 在 [輸出] 視窗中，您會發現 Visual Studio 在開發環境中開始「暖機」這項新的服務，以在您啟動偵錯時加速各項活動。
1. 按 F5，等候建置和部署服務。 當 Visual Studio 狀態列變成橙色時，您就知道它已就緒
1. 記下 [輸出] 視窗之 [Connected Environment for AKS] (適用於 AKS 之已連線的環境) 窗格中所顯示的端點 URL，它看起來類似 http://localhost:\<連接埠號碼\>。 容器可能看起來像是在本機執行，但實際上是在我們的 Azure 開發環境中執行。
1. 當 `mywebapi` 就緒後，請用您的瀏覽器開啟 localhost 位址，將 `/api/values` 附加至 URL，以叫用 `ValuesController` 的預設 GET API。 
1. 如果所有步驟都成功，您應該能夠看見來自 `mywebapi` 服務的回應，看起來像這樣。

    ![](images/WebAPIResponse.png)

## <a name="make-a-request-from-webfrontend-to-mywebapi"></a>從 *webfrontend* 向 *mywebapi* 提出要求
現在在 `webfrontend` 中撰寫程式碼，向 `mywebapi` 提出要求。 切換至 `webfrontend` 專案的 Visual Studio 視窗。 在 `HomeController.cs` 檔案中，使用下列內容「取代」About 方法的程式碼：

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

請注意如何運用 Kubernetes 的 DNS 服務探索以參考服務為 `http://mywebapi`。 **程式碼在我們開發環境中執行的方式，和在生產環境中執行的方式相同**。

上述程式碼範例也使用 `HeaderPropagatingHttpClient` 類別。 這個協助程式類別是當您設定專案使用已連線的環境時，新增至您專案的檔案 `HeaderPropagation.cs`。 `HeaderPropagatingHttpClient` 衍生自眾所周知的 `HttpClient` 類別，而且會新增功能以將特定的標頭從現有的 ASP.NET HttpRequest 物件傳播到外送的 HttpRequestMessage 物件。 我們稍後會看到這在小組案例中會怎麼協助更具生產力的開發經驗。

## <a name="debug-across-multiple-services"></a>偵錯多項服務
1. 此時，`mywebapi` 應仍在附加偵錯工具的狀態下執行。 如果不是，請在 `mywebapi` 專案中點擊 F5。
1. 在處理 GET 要求之 `api/values/{id}` 的 `ValuesController.cs` 檔案的 `Get(int id)` 方法中設定中斷點。
1. 在貼有上述程式碼的 `webfrontend` 專案中，在它要將 GET 要求傳送到 `mywebapi/api/values` 之前設定中斷點。
1. 在 `webfrontend` 專案中點擊 F5。 Visual Studio 會再次以瀏覽器開啟適當的 localhost 連接埠並顯示 Web 應用程式。
1. 按一下頁面頂端的 [關於] 連結觸發 `webfrontend` 專案的中斷點。 
1. 點擊 F10 以繼續。 現在會觸發 `mywebapi` 專案的中斷點。
1. 點擊 F5 以繼續，然後您會回到 `webfrontend` 專案中的程式碼。
1. 再點擊 F5 一次會完成要求，並在瀏覽器中傳回頁面。 在 Web 應用程式中，[關於] 頁面會顯示兩項服務串連的訊息："Hello from webfrontend and Hello from mywebapi"。

做得好！ 現在，您會有每個容器可分別開發與部署的多容器應用程式。

> [!div class="nextstepaction"]
> [了解小組開發](get-started-netcore-visualstudio-06.md)

