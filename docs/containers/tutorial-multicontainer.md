---
title: 使用 Docker 組合&ASP.NET核心的多容器教程
author: ghogen
description: 瞭解如何將多個容器與 Docker 組合使用
ms.author: ghogen
ms.date: 01/10/2020
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: b9e1a2fc7c9027c34aeb8a0e0d1d44fdb0211e65
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027324"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>教程：使用 Docker 合成創建多容器應用

在本教程中，您將學習如何在 Visual Studio 中使用容器工具時管理多個容器並在它們之間進行通信。  管理多個容器需要*容器業務流程*，並且需要協調器（如 Docker Compose、Kubernetes 或服務結構）。 在這裡，我們將使用 Docker 合成。 Docker Compose 非常適合開發週期中的本地調試和測試。

## <a name="prerequisites"></a>必要條件

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017，](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)安裝了**Web 開發****、Azure 工具**工作負載或 **.NET 核心跨平臺開發**工作負荷
::: moniker-end

::: moniker range=">= vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* 已安裝**網頁程式開發**、**Azure Tools** 工作負載及(或) **.NET Core 跨平台開發** 工作負載的 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
* 適用於 .NET Core 2.2 開發的 [.NET Core 2.2 開發工具](https://dotnet.microsoft.com/download/dotnet-core/2.2)
* [.NET 核心 3](https://dotnet.microsoft.com/download/dotnet-core/3.1)開發工具，用於 .NET 核心 3.1 的開發。
::: moniker-end

## <a name="create-a-web-application-project"></a>創建 Web 應用程式專案

在視覺化工作室中，創建**一個ASP.NET核心 Web** `WebFrontEnd`應用程式專案，名為 。 選擇**Web 應用程式**以創建具有 Razor 頁面的 Web 應用程式。 
  
::: moniker range="vs-2017"

請勿選取 [Enable Docker Support] (啟用 Docker 支援)****。 稍後將添加 Docker 支援。

![創建 Web 專案的螢幕截圖](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![創建 Web 專案的螢幕截圖](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project1.png)

請勿選取 [Enable Docker Support] (啟用 Docker 支援)****。 稍後將添加 Docker 支援。

![創建 Web 專案的螢幕截圖](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>創建 Web API 專案

將專案添加到同一解決方案，並稱之為*MyWebAPI。* 選擇**API**作為專案類型，然後清除**用於為 HTTPS 配置的**核取方塊。 在此設計中，我們只使用 SSL 與用戶端通信，而不是用於在同一 Web 應用程式中的容器之間進行通信。 只需要`WebFrontEnd`HTTPS，示例中的代碼假定您已清除該核取方塊。

::: moniker range="vs-2017"
   ![創建 Web API 專案的螢幕截圖](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![創建 Web API 專案的螢幕截圖](./media/tutorial-multicontainer/vs-2019/web-api-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>添加代碼以調用 Web API

1. 在專案中`WebFrontEnd`，打開*Index.cshtml.cs*檔，`OnGet`並將該方法替換為以下代碼。

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          // request.RequestUri = new Uri("http://mywebapi/WeatherForecast"); // ASP.NET 3 (VS 2019 only)
          request.RequestUri = new Uri("http://mywebapi/api/values/1"); // ASP.NET 2.x
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```
   
    > [!NOTE]
    > 在實際代碼中，不應在每個請求後進行處置`HttpClient`。 有關最佳做法，請參閱[使用 HttpClientFactory 實現彈性 HTTP 要求](https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests)。

   對於 Visual Studio 2019 或更高版本中的 .NET Core 3.1，Web API 範本使用 Weather預測 API，因此請不注釋該行並注釋出ASP.NET 2.x 的行。

1. 在 [Index.cshtml]** 檔案中，新增一行以顯示 `ViewData["Message"]`，讓檔案看起來像下列程式碼：
    
      ```cshtml
      @page
      @model IndexModel
      @{
          ViewData["Title"] = "Home page";
      }
    
      <div class="text-center">
          <h1 class="display-4">Welcome</h1>
          <p>Learn about <a href="/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
          <p>@ViewData["Message"]</p>
      </div>
      ```

1. （僅限 2 ASP.NET）現在在 Web API 專案中，向值控制器添加代碼，以自訂 API 返回的消息，以便從*Webfrontend*添加的調用。
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

    使用 .NET Core 3.1，您不需要這個，因為您可以使用已經存在的天氣預報 API。 但是，您需要注釋掉*Startup.cs*`Configure`中<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*>方法中的調用，因為此代碼使用 HTTP 而不是 HTTPS 來調用 Web API。

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. 在專案中`WebFrontEnd`，選擇 **"添加>容器協調器支援**。 將顯示 **"Docker 支援選項"** 對話方塊。

1. 選擇**Docker 撰寫**。

1. 選擇目標作業系統，例如 Linux。

   ![選擇目標作業系統的螢幕截圖](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio 在解決方案中的**docker-compose.yml**檔中創建了一個*docker-compose.yml*檔和 *.dockerignore*檔，該專案以粗體顯示，這表明它是啟動專案。

   ![添加了 Docker 組合專案的解決方案資源管理器螢幕截圖](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

   *docker-compose.yml*如下所示：

   ```yaml
   version: '3.4'

    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
   ```

   *.dockerignore*檔包含不希望 Docker 包含在容器中的檔案類型和副檔名。 這些檔通常與開發環境和原始程式碼管理相關聯，而不是您正在開發的應用或服務的一部分。

   有關正在運行的命令的詳細資訊，請查看輸出窗格的 **"容器工具**"部分。  您可以看到命令列工具 Docker-compose 用於配置和創建運行時容器。

1. 在 Web API 專案中，再次按右鍵專案節點，然後選擇 **"添加** > **容器協調器支援**"。 選擇**Docker 撰寫**，然後選擇相同的目標作業系統。  

    > [!NOTE]
    > 在此步驟中，Visual Studio 將提供創建 Dockerfile。 如果對已具有 Docker 支援的專案執行此操作，系統將提示您是否要覆蓋現有的 Dockerfile。 如果您在 Dockerfile 中進行了要保留的更改，請選擇"否"。

    Visual Studio 對 Docker 撰寫 YML 檔進行了一些更改。 現在，這兩種服務都包括在內。

    ```yaml
    version: '3.4'
    
    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
    
      mywebapi:
        image: ${DOCKER_REGISTRY-}mywebapi
        build:
          context: .
          dockerfile: MyWebAPI/Dockerfile
    ```

1. 立即在本地運行網站（F5 或 Ctrl+F5），以驗證其是否按預期工作。 如果一切都正確配置了 .NET Core 2.x 版本，您將看到消息"來自 Webfrontend 和 Webapi（值 1）你好"。  使用 .NET 核心 3，您將看到天氣預報資料。

   添加容器業務流程時使用的第一個專案將設置為在運行或調試時啟動。 您可以在 Docker 組合**專案中的專案屬性**中配置啟動操作。  在 Docker-compose 專案節點上，按右鍵以打開內容功能表，然後選擇 **"屬性**"或使用 Alt_Enter。  以下螢幕截圖顯示了此處使用的解決方案所需的屬性。  例如，您可以通過自訂**服務 URL**屬性來更改載入的頁面。

   ![Docker 組合專案屬性的螢幕截圖](media/tutorial-multicontainer/launch-action.png)

   以下是您啟動時看到的內容（.NET Core 2.x 版本）：

   ![運行 Web 應用的螢幕截圖](media/tutorial-multicontainer/webfrontend.png)

   .NET 3.1 的 Web 應用以 JSON 格式顯示天氣資料。

## <a name="next-steps"></a>後續步驟

查看將容器部署到[Azure](/azure/containers)的選項。

## <a name="see-also"></a>另請參閱
  
[Docker Compose](https://docs.docker.com/compose/)  
[容器工具](/visualstudio/containers/)
