---
title: 使用 Docker 撰寫來處理多個容器
author: ghogen
description: 瞭解如何搭配 Docker 撰寫使用多個容器
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 01/10/2020
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 1dd5e237e99333e9c2fb9414b3d32ff19b70dd9b
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101684270"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>教學課程：使用 Docker Compose 建立多容器應用程式

在本教學課程中，您將瞭解如何管理一個以上的容器，並在使用 Visual Studio 中的容器工具時在這些容器之間進行通訊。  管理多個容器需要 *容器協調流程* ，且需要 Docker 撰寫、Kubernetes 或 Service Fabric 等協調器。 在這裡，我們將使用 Docker 撰寫。 在開發週期的過程中，Docker 撰寫很適合用來進行本機的偵錯工具和測試。

## <a name="prerequisites"></a>必要條件

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* 已安裝 **Web 開發**、 **Azure Tools** 工作負載或 **.net Core 跨平臺開發** 工作負載的 [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)
::: moniker-end

::: moniker range=">= vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* 已安裝 **網頁程式開發**、**Azure Tools** 工作負載及(或) **.NET Core 跨平台開發** 工作負載的 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
* 適用於 .NET Core 2.2 開發的 [.NET Core 2.2 開發工具](https://dotnet.microsoft.com/download/dotnet-core/2.2)
* .Net [core 3 開發工具](https://dotnet.microsoft.com/download/dotnet-core/3.1)，可供使用 .net core 3.1 進行開發。
::: moniker-end

## <a name="create-a-web-application-project"></a>建立 Web 應用程式專案

在 Visual Studio 中，建立名為的 **ASP.NET Core Web 應用** 程式專案， `WebFrontEnd` 以建立包含 Razor 頁面的 web 應用程式。
  
::: moniker range="vs-2017"

請勿選取 [Enable Docker Support] (啟用 Docker 支援)。 您稍後將會新增 Docker 支援。

![建立 Web 專案的螢幕擷取畫面](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![建立 ASP.NET Core Web 應用程式專案](./media/tutorial-multicontainer/vs-2019/create-web-project1.png)

請勿選取 [Enable Docker Support] (啟用 Docker 支援)。 您稍後將會新增 Docker 支援。

![建立 Web 專案時，[其他資訊] 畫面的螢幕擷取畫面。 未選取啟用 Docker 支援的選項。](./media/tutorial-multicontainer/vs-2019/create-web-project-additional-information.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>建立 Web API 專案

將專案新增至相同的方案，並呼叫它 *MyWebAPI*。 選取 [ **API** ] 作為 [專案類型]，並清除 [ **針對 HTTPS 進行設定**] 核取方塊。 在此設計中，我們只會使用 SSL 來與用戶端通訊，而不是在相同 web 應用程式中的容器之間進行通訊。 只 `WebFrontEnd` 需要 HTTPS，而且範例中的程式碼會假設您已清除該核取方塊。 一般來說，只有外部對容器要求支援 Visual Studio 所使用的 .NET 開發人員憑證，而不支援容器對容器的要求。

::: moniker range="vs-2017"
   ![建立 Web API 專案的螢幕擷取畫面](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![建立 Web API 專案的螢幕擷取畫面](./media/tutorial-multicontainer/vs-2019/create-web-api-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>新增程式碼以呼叫 Web API

1. 在 `WebFrontEnd` 專案中，開啟 *Index.cshtml.cs* 檔案，並 `OnGet` 以下列程式碼取代方法。

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
    > 在真實世界的程式碼中，您不應該在 `HttpClient` 每個要求之後處置。 如需最佳作法，請參閱 [使用 HttpClientFactory 來執行復原的 HTTP 要求](/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests)。

   若為 Visual Studio 2019 或更新版本中的 .NET Core 3.1，Web API 範本會使用 WeatherForecast API，因此請將該行取消批註，並將 ASP.NET 2.x 的行加上批註。

1. 在 [Index.cshtml] 檔案中，新增一行以顯示 `ViewData["Message"]`，讓檔案看起來像下列程式碼：
    
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

1.  (ASP.NET 2.x 只) 在 Web API 專案中，請將程式碼加入至值控制器，以針對您從 *webfrontend* 新增的呼叫自訂 API 所傳回的訊息。
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

    使用 .NET Core 3.1 時，您不需要這麼做，因為您可以使用已經存在的 WeatherForecast API。 不過，您需要在 Startup.cs 的方法中將呼叫批註為 <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*> `Configure` ， 因為此程式碼會使用 HTTP 而非 HTTPS 來呼叫 Web API。

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. 在 `WebFrontEnd` 專案中，選擇 [ **新增 > 容器協調器支援**]。 [ **Docker 支援選項** ] 對話方塊隨即出現。

1. 選擇 [ **Docker 撰寫**]。

1. 選擇您的目標作業系統（例如 Linux）。

   ![選擇目標 OS 的螢幕擷取畫面](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio 會在解決方案的 **docker 撰寫** 節點中建立 *>docker-compose.yml yml* 檔案和 *>.dockerignore* 檔案，而該專案會顯示為粗體字型，其顯示為啟始專案。

   ![已新增 docker 撰寫專案的 [Solution Explorer] 螢幕擷取畫面](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

   *>docker-compose.yml* 會如下所示：

   ```yaml
   version: '3.4'

    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
   ```

   *>.dockerignore* 檔案包含您不希望 Docker 包含在容器中的檔案類型和延伸模組。 這些檔案通常會與開發環境和原始檔控制相關聯，而不是您正在開發的應用程式或服務的一部分。

   查看 [輸出] 窗格的 [ **容器工具** ] 區段，以取得執行中命令的詳細資料。  您可以看到使用 docker 撰寫的命令列工具來設定和建立執行時間容器。

1. 在 Web API 專案中，再次以滑鼠右鍵按一下專案節點，然後選擇 [**新增**  >  **容器協調器支援**]。 選擇 [ **Docker 撰寫**]，然後選取相同的目標 OS。  

    > [!NOTE]
    > 在這個步驟中，Visual Studio 會提供建立 Dockerfile。 如果您在已經有 Docker 支援的專案上這麼做，系統會提示您是否要覆寫現有的 Dockerfile。 如果您在 Dockerfile 中進行了想要保留的變更，請選擇 [否]。

    Visual Studio 會對您的 docker 撰寫 YML 檔案進行一些變更。 現在會包含這兩項服務。

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

1. 現在在本機執行網站 (F5 或 Ctrl + F5) 確認它是否如預期般運作。 如果所有專案都已正確設定 .NET Core 2.x 版本，您會看到訊息 "Hello from webfrontend and webapi (with value 1) "。  使用 .NET Core 3 時，您會看到氣象預報資料。

   當您加入容器協調流程時，您所使用的第一個專案會設定為在執行或 debug 時啟動。 您可以在 docker 撰寫專案的 **專案屬性** 中設定啟動動作。  在 docker 撰寫專案節點上，以滑鼠右鍵按一下以開啟內容功能表，然後選擇 [ **屬性**] 或 [使用 Alt + Enter]。  下列螢幕擷取畫面顯示您想要用於此方案的屬性。  例如，您可以藉由自訂 [ **服務 URL** ] 屬性來變更載入的頁面。

   ![Docker 撰寫專案屬性的螢幕擷取畫面](media/tutorial-multicontainer/launch-action.png)

   以下是當您啟動 (.NET Core 2.x 版) 時所看到的內容：

   ![正在執行 web 應用程式的螢幕擷取畫面](media/tutorial-multicontainer/webfrontend.png)

   適用于 .NET 3.1 的 web 應用程式會顯示 JSON 格式的氣象資料。

## <a name="next-steps"></a>下一步

查看將 [容器部署至 Azure](/azure/containers)的選項。

## <a name="see-also"></a>另請參閱
  
[Docker 撰寫](https://docs.docker.com/compose/)  
[容器工具](./index.yml)