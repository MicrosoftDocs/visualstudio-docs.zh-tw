---
title: 在本機 Docker 容器中偵錯工具 |Microsoft Docs
description: 瞭解如何修改在本機 Docker 容器中執行的應用程式、透過 [編輯] 和 [重新整理] 重新整理容器，然後設定偵錯工具中斷點。
ms.author: ghogen
author: ghogen
manager: jmartens
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: how-to
ms.workload: multiple
ms.date: 07/25/2019
ms.technology: vs-azure
ms.openlocfilehash: 8fb821acb48dd05aa09723fe5c6c254e7d1ca648
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306380"
---
# <a name="debug-apps-in-a-local-docker-container"></a>在本機 Docker 容器中偵錯工具

Visual Studio 可提供一致的方式來開發 Docker 容器，並在本機驗證您的應用程式。
您可以在已安裝 Docker 的本機 Windows 桌面上執行 Linux 或 Windows 容器中的應用程式，並在每次進行程式碼變更時都不需要重新開機容器。

本文說明如何使用 Visual Studio 在本機 Docker 容器中啟動應用程式、進行變更，然後重新整理瀏覽器以查看變更。 本文也會示範如何設定中斷點，以進行容器化應用程式的偵錯工具。 支援的專案類型包括 .NET Framework 和 .NET Core web 和主控台應用程式。 在本文中，我們會使用 ASP.NET Core web 應用程式和 .NET Framework 主控台應用程式。

如果您已經有受支援類型的專案，Visual Studio 可以建立 Dockerfile，並將您的專案設定為在容器中執行。 請參閱 [Visual Studio 中的容器工具](overview.md)。

## <a name="prerequisites"></a>先決條件

若要在本機 Docker 容器中對應用程式進行偵錯工具，必須安裝下列工具：

::: moniker range="vs-2017"

* 已安裝 Web 開發工作負載的[Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

::: moniker-end

::: moniker range="vs-2019"

* 已安裝 Web 開發工作負載的[Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

::: moniker range="vs-2022"

* 已安裝 Web 開發工作負載的[Visual Studio 2022 Preview]()

::: moniker-end

若要在本機執行 Docker 容器，您必須有本機 Docker 用戶端。 您可以使用 [適用於 Windows 的 Docker](https://www.docker.com/get-docker)，這會使用 hyper-v 並需要 Windows 10。

Docker 容器適用于 .NET Framework 和 .NET Core 專案。 讓我們來看以下兩個範例。 首先，我們會查看 .NET Core web 應用程式。 然後，我們會查看 .NET Framework 主控台應用程式。

## <a name="create-a-web-app"></a>建立 Web 應用程式

如果您有專案，而且已依照 [總覽](overview.md)所述新增 Docker 支援，請略過本節。

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>編輯您的程式碼並重新整理

若要快速反復查看變更，您可以在容器中啟動應用程式。 然後，繼續進行變更，如同使用 IIS Express 一樣加以查看。

1. 請確定 Docker 已設定為使用您所使用 (Linux 或 Windows) 的容器類型。 以滑鼠右鍵按一下工作列上的 Docker 圖示，然後選擇 [ **切換至 Linux 容器** ] 或 [適當 **地切換到 Windows 容器** ]。

1.  ( .NET Core 3 和更新版本僅) 編輯您的程式碼，以及重新整理執行中的網站，如本節中的預設範本未在 .NET Core >= 3.0 中啟用。 若要啟用它，請新增 NuGet 套件 [AspNetCore >microsoft.aspnetcore.mvc.razor.runtimecompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/)。 在 *Startup* 中，將擴充方法的呼叫加入 `IMvcBuilder.AddRazorRuntimeCompilation` 至方法中的程式碼 `ConfigureServices` 。 您只需要在「偵錯工具」模式中啟用此功能，因此請依照下列程式碼：

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

    修改方法，如下所示 `Startup` ：

    ```csharp
    public Startup(IConfiguration configuration, IWebHostEnvironment webHostEnvironment)
    {
        Configuration = configuration;
        Env = webHostEnvironment;
    }
    ```

   如需詳細資訊，請參閱 [ASP.NET Core 中的 Razor 檔案編譯](/aspnet/core/mvc/views/view-compilation?view=aspnetcore-3.1&preserve-view=true)。

1. 將 **解決方案** 設定設定為 **Debug**。 然後，按下 **Ctrl** + **F5** 以建立您的 Docker 映射，並在本機執行它。

    在 Docker 容器中建立並執行容器映射時，Visual Studio 會在預設瀏覽器中啟動 web 應用程式。

1. 移至 [ *索引* ] 頁面。 我們將在此頁面上進行變更。
1. 返回 Visual Studio 並開啟 *Index. cshtml*。
1. 將下列 HTML 內容新增至檔案結尾，然後儲存變更。

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

1. 在 [輸出] 視窗中，當 .NET 組建完成時，您會看到下列幾行，請切換回瀏覽器並重新整理頁面：

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

您的變更已經套用！

### <a name="debug-with-breakpoints"></a>使用中斷點進行偵錯

變更通常需要進一步檢查。 您可以針對這項工作使用 Visual Studio 的偵錯工具功能。

1. 在 Visual Studio 中， *開啟 [...]*。
2. 使用下列程式碼來取代 `OnGet` 方法的內容：

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. 在程式程式碼的左邊，設定中斷點。
4. 若要啟動調試和點擊中斷點，請按 F5。
5. 切換至 Visual Studio 以查看中斷點。 檢查值。

   ![顯示 Visual Studio 中的部分程式碼的螢幕擷取畫面，其中中斷點是設定為以黃色反白顯示的程式程式碼左方。](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app&quot;></a>建立.NET Framework 主控台應用程式

當您使用 .NET Framework 主控台應用程式專案時，不支援在沒有協調流程的情況下新增 Docker 支援的選項。 即使您只使用單一 Docker 專案，仍然可以使用下列程式。

1. 建立新的 .NET Framework 主控台應用程式專案。
1. 在方案總管中，以滑鼠右鍵按一下專案節點，然後選取 [**新增**  >  **容器協調流程支援**]。  在出現的對話方塊中，選取 [ **Docker Compose**]。 Dockerfile 會加入至您的專案，並新增具有相關聯支援檔案的 Docker Compose 專案。

### <a name=&quot;debug-with-breakpoints&quot;></a>使用中斷點進行偵錯

1. 在方案總管中，開啟 *程式 .cs*。
2. 使用下列程式碼來取代 `Main` 方法的內容：

   ```csharp
       System.Console.WriteLine(&quot;Hello, world!");
   ```

3. 在程式碼行的左側設定中斷點。
4. 按 F5 開始調試，並點擊中斷點。
5. 切換至 Visual Studio 以查看中斷點並檢查值。

   ![Visual Studio 中的程式碼視窗的螢幕擷取畫面，其中中斷點設定為以黃色反白顯示的程式程式碼左邊。](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>容器重複使用

在開發週期期間，Visual Studio 在變更 Dockerfile 時只重建您的容器映射和容器本身。 如果您未變更 Dockerfile，Visual Studio 會重複使用先前執行的容器。

如果您手動修改容器，並想要以乾淨的容器映射重新開機，請在 Visual Studio 中使用 [**建立**  >  **清理**] 命令，然後以正常方式建立。

## <a name="troubleshoot"></a>疑難排解

瞭解如何針對 [Docker 開發 Visual Studio 進行疑難排解](troubleshooting-docker-errors.md)。

## <a name="next-steps"></a>後續步驟

閱讀 [Visual Studio 建立容器化應用程式的方式](container-build.md)，以取得更多詳細資料。

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>進一步了解 Docker 與 Visual Studio、Windows 和 Azure

* 深入瞭解 [使用 Visual Studio 的容器開發](./index.yml)。
* 若要建立和部署 Docker 容器，請參閱 [Azure Pipelines 的 docker 整合](https://marketplace.visualstudio.com/items?itemName=ms-vscs-rm.docker)。
* 如需 Windows Server 和 Nano Server 文章的索引，請參閱 [windows 容器資訊](/virtualization/windowscontainers/)。
* 瞭解 [Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/) 並查看 [Azure Kubernetes Service 檔](/azure/aks)。
