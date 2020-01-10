---
title: 教學課程 - 使用 Docker Compose 建立多容器應用程式
description: 了解如何在 Visual Studio for Mac 中管理多個容器並在它們之間通訊
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/17/2019
ms.openlocfilehash: 487945399252ca3627d625e3572637b5b2af2916
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74983948"
---
# <a name="create-a-multi-container-app-with-docker-compose"></a>使用 Docker Compose 建立多容器應用程式

在本教學課程中，您將了解如何在 Visual Studio for Mac 中使用 Docker Compose 管理多個容器並在它們之間通訊。

## <a name="prerequisites"></a>必要條件

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio for Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="create-an-aspnet-core-web-application-and-add-docker-support"></a>建立 ASP.NET Core Web 應用程式並新增 Docker 支援

1. 藉由移至 [檔案] > [新增解決方案] 來建立新解決方案。
1. 在 [.NET Core] > [應用程式] 底下，選擇 [Web 應用程式] 範本：![建立新的 ASP.NET 應用程式](media/docker-quickstart-1.png)
1. 選取目標 Framework。 在此範例中，我們將會使用 .NET Core 2.2：![設定目標 Framework](media/docker-quickstart-2.png)
1. 輸入專案詳細資料，例如，[專案名稱] \(此範例中為 _DockerDemoFrontEnd_\) 和 [解決方案名稱] \(_DockerDemo_\)。 所建立的專案包含建置和執行 ASP.NET Core 網站所需的所有基本項目。
1. 在 Solution Pad 中，以滑鼠右鍵按一下 [DockerDemoFrontEnd] 專案，然後選取 [新增] > [新增 Docker 支援]：![新增 Docker 支援](media/docker-quickstart-3.png)

Visual Studio for Mac 會將稱為 **docker-compose** 的專案自動新增到解決方案，並將 **Dockerfile** 新增到您的現有專案。

## <a name="create-an-aspnet-core-web-api-and-add-docker-support"></a>建立 ASP.NET Core Web API 並新增 Docker 支援

接下來，我們將會建立第二個專案，作為我們的後端 API。 **.NET Core API** 範本包括一個控制器，可讓我們處理 RESTful 要求。

1. 以滑鼠右鍵按一下現有解決方案，選取 [新增] > [新增專案] 以新增專案。
1. 在 [.NET Core] > [應用程式] 底下，選擇 [API] 範本。
1. 選取目標 Framework。 在此範例中，我們將會使用 .NET Core 2.2
1. 輸入專案詳細資料，例如，[專案名稱] \(此範例中為 _DockerDemoAPI_\)。
1. 建立之後，移至 Solution Pad 並以滑鼠右鍵按一下 [DockerDemoAPI] 專案，然後選取 [新增] > [新增 Docker 支援]。

系統會自動更新 **docker-compose** 專案中的 **docker-compose.yml** 檔案，將 API 專案納入現有 Web 應用程式專案。 當我們建置並執行 **docker-compose** 專案時，這些專案每個都會部署到個別的 Docker 容器。

```
version: '3.4'

services:
  dockerdemofrontend:
    image: ${DOCKER_REGISTRY-}dockerdemofrontend
    build:
      context: .
      dockerfile: DockerDemoFrontEnd/Dockerfile

  dockerdemoapi:
    image: ${DOCKER_REGISTRY-}dockerdemoapi
    build:
      context: .
      dockerfile: DockerDemoAPI/Dockerfile
```

## <a name="integrate-the-two-containers"></a>整合兩個容器

我們的解決方案中現在有兩個 ASP.NET 專案，且兩個都已設定 Docker 支援。 接下來，我們需要新增一些程式碼！

1. 在 `DockerDemoFrontEnd` 專案中，開啟 [Index.cshtml.cs] 檔案，並將 `OnGet` 方法取代為下列程式碼：

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          request.RequestUri = new Uri("http://dockerdemoapi/api/values/1");
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```

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

1. 現在，在 Web API 專案中，將程式碼加入至 Values 控制器，以針對從 *webfrontend* 新增之呼叫，自訂由 API 傳回的訊息：

      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

1. 將 `docker-compose` 專案設定為啟始專案並移至 [執行] > [開始偵錯]。 如果一切都設定正確，您會看到訊息 [Hello from webfrontend and webapi (with value 1).]：

![執行中的 Docker 多容器解決方案](media/docker-multicontainer-debug.png)
