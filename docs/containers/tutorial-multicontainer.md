---
title: 使用 Docker Compose & ASP.NET Core 的多容器教學課程
author: ghogen
description: 瞭解如何搭配 Docker Compose 使用多個容器
ms.author: ghogen
ms.date: 02/21/2019
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 298ac91a7e7cf89f7723a3fd8bb3e8056da798ba
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75399759"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>教學課程：使用 Docker Compose 建立多容器應用程式

在本教學課程中，您將瞭解如何管理一個以上的容器，並在使用 Visual Studio 中的容器工具時，在兩者之間進行通訊。  管理多個容器需要*容器協調流程*，而且需要協調器，例如 Docker Compose、Kubernetes 或 Service Fabric。 在這裡，我們將使用 Docker Compose。 Docker Compose 在開發週期的過程中，很適合用於本機的偵錯工具和測試。

## <a name="prerequisites"></a>必要條件：

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* 已安裝**Web 開發**、 **Azure 工具**工作負載或 **.net Core 跨平臺開發**工作負載的[Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)
::: moniker-end

::: moniker range=">= vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* 已安裝**網頁程式開發**、**Azure Tools** 工作負載及(或) **.NET Core 跨平台開發** 工作負載的 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
* 適用於 .NET Core 2.2 開發的 [.NET Core 2.2 開發工具](https://dotnet.microsoft.com/download/dotnet-core/2.2)
* [.Net core 3 開發工具](https://dotnet.microsoft.com/download/dotnet-core/3.1)，可使用 .net core 3.1 進行開發。
::: moniker-end

## <a name="create-a-web-application-project"></a>建立 Web 應用程式專案

在 Visual Studio 中，建立名為 `WebFrontEnd`的**ASP.NET Core Web 應用程式**專案。 選取 [ **Web 應用程式**] 以建立含有 Razor pages 的 web 應用程式。 
  
::: moniker range="vs-2017"

請勿選取 [**啟用 Docker 支援**]。 您會在稍後新增 Docker 支援。

![建立 Web 專案的螢幕擷取畫面](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![建立 Web 專案的螢幕擷取畫面](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project1.png)

請勿選取 [**啟用 Docker 支援**]。 您會在稍後新增 Docker 支援。

![建立 Web 專案的螢幕擷取畫面](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>建立 Web API 專案

將專案新增至相同的方案，並呼叫它*MyWebAPI*。 選取 [ **API** ] 做為專案類型，並清除 [針對**HTTPS 設定**] 核取方塊。 在此設計中，我們只會使用 SSL 來與用戶端通訊，而不是在相同 web 應用程式中的容器之間進行通訊。 只有 `WebFrontEnd` 需要 HTTPS，而範例中的程式碼假設您已清除該核取方塊。

::: moniker range="vs-2017"
   ![建立 Web API 專案的螢幕擷取畫面](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![建立 Web API 專案的螢幕擷取畫面](./media/tutorial-multicontainer/vs-2019/web-api-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>新增程式碼以呼叫 Web API

1. 在 `WebFrontEnd` 專案中，開啟*Index.cshtml.cs*檔案，並以下列程式碼取代 `OnGet` 方法。

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

   針對 Visual Studio 2019 或更新版本中的 .NET Core 3.1，Web API 範本會使用 WeatherForecast API，因此請將該行取消批註，並將 ASP.NET 2.x 的程式碼標記為批註。

1. 在 [Index.cshtml] 檔案中，新增一行以顯示 `ViewData["Message"]`，讓檔案看起來像下列程式碼：
    
      ```cshtml
      @page
      @model IndexModel
      @{
          ViewData["Title"] = "Home page";
      }
    
      <div class="text-center">
          <h1 class="display-4">Welcome</h1>
          <p>Learn about <a href="https://docs.microsoft.com/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
          <p>@ViewData["Message"]</p>
      </div>
      ```

1. （僅限 ASP.NET 2.x）現在，在 Web API 專案中，將程式碼新增至 [值] 控制器，以自訂 API 針對您從*webfrontend*新增的呼叫所傳回的訊息。
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

    有了 .NET Core 3.1，您就不需要這麼做，因為您可以使用已經存在的 WeatherForecast API。 不過，您必須在*Startup.cs*的 `Configure` 方法中，將對 `UseHttpsRedirections` 的呼叫加上批註，因為此程式碼使用 HTTP not HTTPS 來呼叫 Web API。

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. 在 `WebFrontEnd` 專案中，選擇 [**新增 > 容器協調器支援**]。 [ **Docker 支援選項**] 對話方塊隨即出現。

1. 選擇 [ **Docker Compose**]。

1. 選擇您的目標作業系統（例如 Linux）。

   ![選擇目標作業系統的螢幕擷取畫面](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio 會在方案的**docker 撰寫**節點中建立*docker-compose.dev.debug.yml yml*檔案和 *.dockerignore*檔案，而該專案會以粗體字型顯示，這表示它是啟始專案。

   ![已新增 docker 撰寫專案之方案總管的螢幕擷取畫面](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

   *Docker-compose.dev.debug.yml*會如下所示：

   ```yaml
   version: '3.4'

    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
   ```

   *.Dockerignore*檔案包含您不想要 Docker 包含在容器中的檔案類型和副檔名。 這些檔案通常與開發環境和原始檔控制相關聯，而不是您正在開發的應用程式或服務的一部分。

   查看 [輸出] 窗格的 [**容器工具**] 區段，以取得所執行命令的詳細資料。  您可以看到使用 docker 撰寫的命令列工具來設定和建立執行時間容器。

1. 在 Web API 專案中，再次以滑鼠右鍵按一下專案節點，然後選擇 **新增** > **容器協調器支援**。 選擇 [ **Docker Compose**]，然後選取相同的目標 OS。  

    > [!NOTE]
    > 在此步驟中，Visual Studio 將提供來建立 Dockerfile。 如果您在已有 Docker 支援的專案上執行此動作，系統會提示您是否要覆寫現有的 Dockerfile。 如果您已在您要保留的 Dockerfile 中進行變更，請選擇 [否]。

    Visual Studio 對 docker 撰寫 YML 檔案進行一些變更。 現在會包含這兩個服務。

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

1. 立即在本機執行網站（F5 或 Ctrl + F5）以確認其如預期般運作。 如果所有專案都已正確設定 .NET Core 2.x 版本，您會看到訊息 "Hello from webfrontend and webapi （with value 1）"。  使用 .NET Core 3 時，您會看到氣象預報資料。

   您在新增容器協調流程時所使用的第一個專案會設定為在執行或 debug 時啟動。 您可以在 docker 撰寫專案的**專案屬性**中設定 [啟動] 動作。  在 [docker 撰寫專案] 節點上，以滑鼠右鍵按一下以開啟內容功能表，然後選擇 [**屬性**]，或使用 Alt + Enter。  下列螢幕擷取畫面顯示您想要用於此處解決方案的屬性。  例如，您可以藉由自訂 [**服務 URL** ] 屬性來變更載入的頁面。

   ![Docker 撰寫專案屬性的螢幕擷取畫面](media/tutorial-multicontainer/launch-action.png)

   以下是您在啟動時所看到的內容（.NET Core 2.x 版）：

   ![執行 web 應用程式的螢幕擷取畫面](media/tutorial-multicontainer/webfrontend.png)

   適用于 .NET 3.1 的 web 應用程式會以 JSON 格式顯示氣象資料。

## <a name="next-steps"></a>後續步驟

查看將您的[容器部署至 Azure](/azure/containers)的選項。

## <a name="see-also"></a>請參閱
  
[Docker Compose](https://docs.docker.com/compose/)  
[容器工具](/visualstudio/containers/)
