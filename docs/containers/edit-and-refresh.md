---
title: 在本地 Docker 容器中調試應用 |微軟文檔
description: 瞭解如何修改在本地 Docker 容器中運行的應用，通過"編輯"和"刷新"刷新容器，然後設置調試中斷點。
ms.author: ghogen
author: ghogen
manager: jillfra
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: conceptual
ms.workload: multiple
ms.date: 07/25/2019
ms.technology: vs-azure
ms.openlocfilehash: 9f1d80d540e9a25a3ef62ee0819c6f6655b9b3ab
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75916526"
---
# <a name="debug-apps-in-a-local-docker-container"></a>在本地 Docker 容器中調試應用

Visual Studio 提供了一種一致的方式來開發 Docker 容器並在本地驗證應用程式。 您可以在 Linux 或 Windows 容器中運行和調試應用，這些容器在安裝了 Docker 的本地 Windows 桌面上運行，並且不必在每次更改代碼時重新開機容器。

本文演示如何使用 Visual Studio 在本地 Docker 容器中啟動應用，進行更改，然後刷新瀏覽器以查看更改。 本文還介紹了如何為容器化應用設置調試的中斷點。 支援的專案類型包括 .NET 框架和 .NET 核心 Web 和主控台應用。 在本文中，我們使用ASP.NET核心 Web 應用和 .NET 框架主控台應用。

如果您已有受支援類型的專案，Visual Studio 可以創建 Dockerfile 並將專案配置為在容器中運行。 請參閱[視覺化工作室中的容器工具](overview.md)。

## <a name="prerequisites"></a>必要條件

要調試本地 Docker 容器中的應用，必須安裝以下工具：

::: moniker range="vs-2017"

* 安裝了 Web 開發工作負載的[視覺化工作室 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

::: moniker-end

::: moniker range="vs-2019"

* 安裝了 Web 開發工作負載的[視覺化工作室 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

要在本地運行 Docker 容器，您必須具有本地 Docker 用戶端。 您可以使用 Docker[工具箱](https://www.docker.com/products/docker-toolbox)，這需要禁用 Hyper-V。 您還可以使用 Docker[用於 Windows](https://www.docker.com/get-docker)，它使用 Hyper-V 並且需要 Windows 10。

Docker 容器可用於 .NET 框架和 .NET 核心專案。 讓我們來看以下兩個範例。 首先，我們查看 .NET 核心 Web 應用。 然後，我們查看 .NET 框架主控台應用。

## <a name="create-a-web-app"></a>建立 Web 應用程式

如果您有專案，並且添加了[概述](overview.md)中所述的 Docker 支援，請跳過此部分。

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>編輯您的程式碼並重新整理

要快速反覆運算更改，可以在容器中啟動應用程式。 然後，繼續進行更改，像使用 IIS Express 一樣查看它們。

1. 確保 Docker 設置為使用正在使用的容器類型（Linux 或 Windows）。 按右鍵 Taskbar 上的 Docker 圖示，然後根據需要選擇 **"切換到 Linux 容器**"或 **"切換到 Windows 容器**"。

1. （.NET 核心 3 及更高版本）在 .NET Core >= 3.0 的預設範本中，不會啟用編輯代碼並刷新本節中所述的運行網站。 要啟用它，添加 NuGet 包[Microsoft.AspNetCore.Mvc.Razor.運行時編譯](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/)。 在*Startup.cs*中，向 方法中的代碼`IMvcBuilder.AddRazorRuntimeCompilation`添加對分機方法`ConfigureServices`的調用。 您只需要在 DEBUG 模式下啟用此功能，因此請按照如下方式對其進行編碼：

    ```csharp
    public IWebHostEnvironment Env { get; set; }
    
    public void ConfigureServices(IServiceCollection services)
    {
        IMvcBuilder builder = services.AddRazorPages();
    
    #if DEBUG
        if (Env.IsDevelopment())
        {
            builder.AddRazorRuntimeCompilation();
        }
    #endif
    
        // code omitted for brevity
    }
    ```

   有關詳細資訊，請參閱[ASP.NET 酷睿中的 Razor 檔編譯](/aspnet/core/mvc/views/view-compilation?view=aspnetcore-3.1)。

1. 將**解決方案配置**設置為**調試**。 然後，按**Ctrl**+**F5**生成 Docker 映射並在本地運行。

    在 Docker 容器中生成和運行容器映射時，Visual Studio 會在預設瀏覽器中啟動 Web 應用。

1. 轉到 *"索引"* 頁。 我們將在此頁面上進行更改。
1. 返回到視覺化工作室並打開*索引.cshtml*。
1. 將以下 HTML 內容添加到檔的末尾，然後保存更改。

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

1. 在輸出視窗中，當 .NET 生成完成並且看到以下行時，切換回瀏覽器並刷新頁面：

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

您的變更已經套用！

### <a name="debug-with-breakpoints"></a>使用中斷點進行偵錯

通常，更改需要進一步檢查。 您可以為此任務使用 Visual Studio 的調試功能。

1. 在視覺工作室，打開*Index.cshtml.cs*。
2. 將`OnGet`方法的內容替換為以下代碼：

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. 在程式碼的左側，設置中斷點。
4. 要開始調試並命中中斷點，請按 F5。
5. 切換到視覺化工作室以查看中斷點。 檢查值。

   ![中斷點](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app"></a>建立.NET Framework 主控台應用程式

使用 .NET 框架主控台應用專案時，不支援添加不進行業務流程的 Docker 支援的選項。 即使您只使用單個 Docker 專案，您仍可以使用以下過程。

1. 創建新的 .NET 框架主控台應用專案。
1. 在解決方案資源管理器中，按右鍵專案節點，然後選擇"**添加** > **容器業務流程支援**"。  在顯示的對話方塊中，選擇 **"Docker 撰寫**"。 Dockerfile 將添加到您的專案中，並添加具有相關支援檔的 Docker 撰寫專案。

### <a name="debug-with-breakpoints"></a>使用中斷點進行偵錯

1. 在解決方案資源管理器中，打開*Program.cs*。
2. 將`Main`方法的內容替換為以下代碼：

   ```csharp
       System.Console.WriteLine("Hello, world!");
   ```

3. 在程式碼行的左側設定中斷點。
4. 按 F5 開始調試並命中中斷點。
5. 切換到視覺化工作室以查看中斷點並檢查值。

   ![中斷點](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>容器重用

在開發週期中，Visual Studio 僅在更改 Dockerfile 時重建容器映射和容器本身。 如果不更改 Dockerfile，Visual Studio 將從較早的運行中重用該容器。

如果手動修改了容器，並希望使用乾淨的容器映射重新開機，請使用 Visual Studio 中的 **"生成** > **乾淨"** 命令，然後正常生成。

## <a name="troubleshoot"></a>疑難排解

瞭解如何[排除視覺工作室 Docker 開發故障](troubleshooting-docker-errors.md)。

## <a name="next-steps"></a>後續步驟

通過閱讀 Visual [Studio 如何構建容器化應用程式](container-build.md)，獲取更多詳細資訊。

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>進一步了解 Docker 與 Visual Studio、Windows 和 Azure

* 瞭解有關使用[Visual Studio 的容器開發](/visualstudio/containers)方面。
* 要生成和部署 Docker 容器，請參閱[Azure 管道的 Docker 集成](https://marketplace.visualstudio.com/items?itemName=ms-vscs-rm.docker)。
* 有關 Windows 伺服器和 Nano 伺服器文章的索引，請參閱[Windows 容器資訊](/virtualization/windowscontainers/)。
* 瞭解[Azure 庫伯奈斯服務](https://azure.microsoft.com/services/kubernetes-service/)並查看[Azure 庫伯奈斯服務文件](/azure/aks)。
