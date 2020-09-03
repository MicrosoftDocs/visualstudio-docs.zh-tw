---
title: 具有 Docker Compose 的多容器應用程式
description: 了解如何在 Visual Studio for Mac 中管理多個容器並在它們之間通訊
author: heiligerdankgesang
ms.author: dominicn
ms.date: 07/03/2020
ms.topic: tutorial
ms.openlocfilehash: 4dd8695ccf8f1fcf13b9b52387d28c68f8812aec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "88800719"
---
# <a name="create-a-multi-container-app-with-docker-compose"></a>使用 Docker Compose 建立多容器應用程式

在本教學課程中，您將了解如何在 Visual Studio for Mac 中使用 Docker Compose 管理多個容器並在它們之間通訊。

## <a name="prerequisites"></a>先決條件

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio for Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="create-an-aspnet-core-web-application-and-add-docker-support"></a>建立 ASP.NET Core Web 應用程式並新增 Docker 支援

1. 藉由移至 [檔案] > [新增解決方案]**** 來建立新解決方案。
1. 在 [ **web 和主控台] > 應用** 程式下，選擇 [ **web 應用程式** ] 範本： ![ 建立新的 ASP.NET 應用程式](media/docker-quickstart-1.png)
1. 選取目標 Framework。 在此範例中，我們將使用 .NET Core 3.1： ![ 設定目標 framework](media/docker-quickstart-2.png)
1. 輸入專案詳細資料，例如，[專案名稱] \(此範例中為 _DockerDemoFrontEnd_\) 和 [解決方案名稱] \(_DockerDemo_\)。 所建立的專案包含建置和執行 ASP.NET Core 網站所需的所有基本項目。
1. 在 Solution Pad 中，以滑鼠右鍵按一下 DockerDemoFrontEnd 專案，然後選取 [新增 **> 新增 Docker 支援**： ![ 新增 docker 支援]](media/docker-quickstart-3.png)

Visual Studio for Mac 會將稱為 **docker-compose** 的專案自動新增到解決方案，並將 **Dockerfile** 新增到您的現有專案。

## <a name="create-an-aspnet-core-web-api-and-add-docker-support"></a>建立 ASP.NET Core Web API 並新增 Docker 支援

接下來，我們將會建立第二個專案，作為我們的後端 API。 **.NET Core API** 範本包括一個控制器，可讓我們處理 RESTful 要求。

1. 以滑鼠右鍵按一下現有解決方案，選取 [新增] > [新增專案]**** 以新增專案。
1. 在 [ **Web 和主控台] > 應用程式** 下，選擇 **API** 範本。
1. 選取目標 Framework。 在此範例中，我們將使用 .NET Core 3.1。
1. 在此範例中，輸入專案詳細資料，例如專案名稱 (_MyWebAPI_) 。
1. 建立之後，請移至 Solution Pad 並以滑鼠右鍵按一下 MyWebAPI 專案，然後選取 [ **新增] > 新增 Docker 支援**。

系統會自動更新 **docker-compose** 專案中的 **docker-compose.yml** 檔案，將 API 專案納入現有 Web 應用程式專案。 當我們建置並執行 **docker-compose** 專案時，這些專案每個都會部署到個別的 Docker 容器。

```yaml
version: '3.4'

services:
  dockerdemofrontend:
    image: ${DOCKER_REGISTRY-}dockerdemofrontend
    build:
      context: .
      dockerfile: DockerDemoFrontEnd/Dockerfile

  mywebapi:
    image: ${DOCKER_REGISTRY-}mywebapi
    build:
      context: .
      dockerfile: MyWebAPI/Dockerfile
```

## <a name="integrate-the-two-containers"></a>整合兩個容器

我們的解決方案中現在有兩個 ASP.NET 專案，且兩個都已設定 Docker 支援。 接下來，我們需要新增一些程式碼！

1. 在 `DockerDemoFrontEnd` 專案中，開啟 *Pages/Index. .cs* 檔案，然後 `OnGet` 以下列程式碼取代方法：

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          request.RequestUri = new Uri("http://mywebapi/WeatherForecast");
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```
   
    > [!NOTE]
    > 在實際執行的程式碼中，您不應該在 `HttpClient` 每個要求之後處置。 如需最佳作法，請參閱 [使用 HttpClientFactory 來執行復原的 HTTP 要求](https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests)。

1. 在 [Index.cshtml]** 檔案中，新增一行以顯示 `ViewData["Message"]`，讓檔案看起來像下列程式碼：

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
  
1. 在前端和 Web API 專案中，將 Startup.cs 中的 AspNetCore 的呼叫批註為[HttpsPolicyBuilderExtensions](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.builder.httpspolicybuilderextensions.usehttpsredirection) `Configure` ，因為此範例程式碼會使用 HTTP， *Startup.cs*而非 HTTPS 來呼叫 Web API。

      ```csharp
                  //app.UseHttpsRedirection();
      ```

1. 將 `docker-compose` 專案設定為啟始專案並移至 [執行] > [開始偵錯]****。 如果一切都設定正確，您會看到訊息 [Hello from webfrontend and webapi (with value 1).]：

![執行中的 Docker 多容器解決方案](media/docker-multicontainer-debug.png)
