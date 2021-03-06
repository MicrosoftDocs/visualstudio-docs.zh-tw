---
title: 開始使用 ASP.NET Core
description: 本文說明如何在 Visual Studio for Mac 中開始使用 ASP.NET，包括安裝及建立新的專案。
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/06/2020
ms.assetid: 6E8B0C90-33D6-4546-8207-CE0787584565
ms.custom: video
no-loc:
- Blazor
- Blazor WebAssembly
ms.topic: how-to
ms.openlocfilehash: a2f45069967df412f9245f8044c53ef425a00fdf
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493357"
---
# <a name="getting-started-with-aspnet-core"></a>開始使用 ASP.NET Core

 Visual Studio for Mac 可讓您輕鬆地開發應用程式的服務，並支援最新的 ASP.NET Core Web 開發平臺。 ASP.NET Core 在 .NET Core 上執行，而 .NET Core 是 .NET Framework 和執行階段的最新演進。 它已針對快速效能進行調整，並針對小型安裝大小和重新發想在 Linux 和 macOS 上執行，以及 Windows 上執行。

## <a name="installing-net-core"></a>安裝 .NET Core

當您安裝 Visual Studio for Mac 時，會自動安裝 .NET Core 3.1。 如需 Visual Studio for Mac 中支援之 .NET Core 版本的詳細資訊，請參閱 [.Net Core 支援](./net-core-support.md)。

## <a name="creating-an-aspnet-core-app-in-visual-studio-for-mac"></a>在 Visual Studio for Mac 中建立 ASP.NET Core 應用程式

開啟 Visual Studio for Mac。 在開始畫面選取 [新增專案]

![New Project Dialog](media/asp-net-core-2019-new-asp-core.png)

這會顯示 [新增專案] 對話方塊，可讓您選取範本來建立應用程式。

有許多專案可為您提供預先建立的範本，以開始建置 ASP.NET Core 應用程式。 這些警告是：

- **.NET Core > 空白**
- **.NET Core > API**
- **.NET Core > Web 應用程式**
- **.NET Core > Web 應用程式 (模型-檢視-控制器)**
- **.NET Core > Blazor Server 應用程式**
- **.NET Core > Blazor WebAssembly 應用程式**

![ASP.NET 專案選項](media/asp-net-core-2019-new-asp-core.png)

選取 [ASP.NET Core 空白 Web 應用程式]，然後按 [下一步]。 提供專案名稱，然後按 [建立]。 這會建立新的 ASP.NET Core 應用程式。 在方案視窗的左窗格中，展開第二個箭號，然後選取 [ **Startup.cs** ]。 它看起來應該如下圖所示：

![新的 ASP.NET Core 空白專案檢視](media/asp-net-core-2019-empty-project.png)

ASP.NET Core 空白範本會建立具有兩個預設檔案的 web 應用程式： **Program.cs** 和 **Startup.cs** ，如下所述。 它也會建立相依性資料夾，其中包含專案的 NuGet 套件相依性，例如 ASP.NET Core、.NET Core framework 和建立專案的 MSBuild 目標：

![顯示相依性的解決方案視窗](media/asp-net-core-2019-solution-dependencies.png)

### <a name="programcs"></a>Program.cs

在專案中開啟並檢查 **Program.cs** 檔案。 請注意，`Main` 方法中會發生幾件事 - 對應用程式的輸入：

```csharp
    public class Program
    {
        public static void Main(string[] args)
        {
            CreateWebHostBuilder(args).Build().Run();
        }

        public static IWebHostBuilder CreateWebHostBuilder(string[] args) =>
            WebHost.CreateDefaultBuilder(args)
                .UseStartup<Startup>();
    }
```

ASP.NET Core 的應用程式會透過的實例設定和啟動主機，以在其主要方法中建立 web 伺服器 [`WebHostBuilder`](/aspnet/core/fundamentals/hosting) 。 這個建立器提供了一些方法來允許設定主機。 在範本應用程式中，會使用下列設定：

* `.UseStartup<Startup>()`：指定啟動類別。

不過，您也可以新增其他組態，例如：

* `UseKestrel`：指定應用程式將使用的 Kestrel 伺服器
* `UseContentRoot(Directory.GetCurrentDirectory())`：當應用程式從 Web 專案的根資料夾啟動時，使用這個資料夾作為應用程式的內容根目錄
* `.UseIISIntegration()`：指定應用程式應該使用 IIS。 若要搭配使用 IIS 與 ASP.NET Core，必須同時指定 `UseKestrel` 和 `UseIISIntegration`。

### <a name="startupcs"></a>Startup.cs

應用程式的啟動類別是在 `CreateWebHostBuilder` 的 `UseStartup()` 方法中指定。 在這個類別中，您將指定要求處理管線，並在其中設定任何服務。

在專案中開啟並檢查 **Startup.cs** 檔案：

```csharp
    public class Startup
    {
        // This method gets called by the runtime. Use this method to add services to the container.
        // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
        public void ConfigureServices(IServiceCollection services)
        {
        }

        // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
        public void Configure(IApplicationBuilder app, IHostingEnvironment env)
        {
            if (env.IsDevelopment())
            {
                app.UseDeveloperExceptionPage();
            }

            app.Run(async (context) =>
            {
                await context.Response.WriteAsync("Hello World!");
            });
        }
    }
```

這個啟動類別必須一律遵守下列規則：

- 必須一律為公用
- 必須包含兩個公用方法：`ConfigureServices` 和 `Configure`

`ConfigureServices` 方法會定義您的應用程式將使用的服務。

`Configure` 可讓您使用[中介軟體](/aspnet/core/fundamentals/middleware)撰寫要求管線。 這些是 ASP.NET 應用程式管線中用來處理要求和回應的元件。 HTTP 管線包含許多要求委派，這些委派將依順序呼叫。 每個委派可以選擇處理要求本身，或將它傳遞至下一個委派。

您可以在 `IApplicationBuilder` 上使用 `Run`、`Map` 和 `Use` 方法來設定委派，但 `Run` 方法永遠不會呼叫下一個委派，因此應該一律在管線結尾處使用。

預先建立範本的 `Configure` 方法是為了執行一些作業而建立的。 首先，它會設定例外狀況處理頁面以供開發期間使用。 然後，它會以簡單的 "Hello World" 傳送回應給要求網頁。

現在，無需新增任何其他程式碼，即可執行這個簡單的 Hello, World 專案。 若要執行應用程式，您可以使用 [播放] 按鈕的下拉式清單選取您想要用來執行應用程式的瀏覽器，或直接按下 [播放] (三角形) 按鈕，以使用您的預設瀏覽器：

![瀏覽器執行](media/asp-net-web-picker.png)

Visual Studio for Mac 會使用隨機的連接埠來啟動您的 Web 專案。 若要瞭解這是什麼埠，請開啟 [應用程式輸出]，它會列在 [ **> 其他視窗** ] 功能表的 [View] 之下。 您應該尋找的輸出類似如下：

![顯示接聽連接埠的應用程式輸出](media/asp-net-core-image6.png)

專案一經執行，您的預設網頁瀏覽器就應該啟動，並連線到應用程式輸出列出的 URL。 或者，您可以開啟選擇的任何瀏覽器，輸入 `http://localhost:5000/`，將 `5000` 取代為應用程式輸出中的 Visual Studio 輸出連接埠。 您應該會看到文字 `Hello World!`：

![顯示文字的瀏覽器](media/asp-net-core-image7.png)

## <a name="adding-a-controller"></a>新增控制器

ASP.NET Core 應用程式使用「模型-檢視-控制器 (MVC)」設計模式，為應用程式的每個部分提供責任的邏輯分隔。 MVC 設計模式包含下列概念：

- **模型** ：代表應用程式資料的類別。
- **檢視** ：顯示應用程式的使用者介面 (這通常是模型資料)。
- **控制器** ：用來處理瀏覽器要求、回應使用者輸入和互動的類別。

如需有關使用 MVC 的詳細資訊，請參閱 [ASP.NET CORE mvc](/aspnet/core/mvc/overview) 指南的總覽。

若要新增控制器，請執行下列作業：

1. 以滑鼠右鍵按一下專案名稱，然後選取 [新增] > [新增檔案]。 選取 [一般] > [空白類別]，然後輸入控制器名稱：

    ![[新增檔案] 對話方塊](media/asp-net-core-image8.png)

2. 將下列程式碼新增至新控制器：

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using System.Text.Encodings.Web;

    namespace Hello_ASP
    {
        public class HelloWorldController : Controller
        {
            //
            // GET: /HelloWorld/

            public string Index()
            {
                return "This is my default action...";
            }

        }
    }
    ```

3. 以滑鼠右鍵按一下 [相依性] 資料夾，然後選取 [新增套件...]，將 `Microsoft.AspNetCore.Mvc` 相依性新增至專案。

4. 使用搜尋方塊來瀏覽 NuGet 程式庫以找出 `Microsoft.AspNetCore.Mvc`，然後選取 [新增套件]。 這可能需要幾分鐘的時間來完成安裝，而且系統可能會提示您接受所需相依性的各種授權：

    ![新增 Nuget](media/asp-net-core-image9.png)

5. 在啟動類別中，移除 `app.Run` Lambda，並將 MVC 用來判斷所應叫用程式碼的 URL 路由邏輯設為下列內容：

    ```csharp
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=HelloWorld}/{action=Index}/{id?}");
    });
    ```

    請務必移除 `app.Run` Lambda，因為這會覆寫路由邏輯。

    MVC 會使用下列格式來判斷要執行的程式碼：

    `/[Controller]/[ActionName]/[Parameters]`

    當您新增上述的程式碼片段時，即是告訴應用程式預設為 `HelloWorld` 控制器及 `Index` 動作方法。

6. 將 `services.AddMvc();` 呼叫新增至 `ConfigureServices` 方法，如下所示：

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
    }
    ```

    您也可以將 URL 中的參數資訊傳遞到控制器。

7. 將另一個方法新增至 HelloWorldController，如下所示：

    ```csharp
    public string Xamarin(string name)
    {
        return HtmlEncoder.Default.Encode($"Hello {name}, welcome to Visual Studio for Mac");
    }
    ```

8. 如果您立即執行應用程式，它應該會自動開啟您的瀏覽器：

    ![在瀏覽器中執行應用程式](media/asp-net-core-image13.png)

9. 嘗試瀏覽至 `http://localhost:xxxx/HelloWorld/Xamarin?name=Amy`(將 `xxxx` 取代為正確的連接埠)，您應該會看到下列內容：

    ![使用引數在瀏覽器中執行應用程式](media/asp-net-core-image10.png)

## <a name="troubleshooting"></a>疑難排解

如果您需要在 macOS 10.12 (內部) 和更高版本上手動安裝 .NET Core，請執行下列動作：

1. 在開始安裝 .NET Core 之前，請確定所有作業系統更新已更新為最新穩定版本。 若要檢查此項，請移至應用程式市集應用程式，然後選取 [更新] 索引標籤。

2. 遵循 [.NET Core 網站](https://www.microsoft.com/net/core#macos)上所列出的步驟。

請務必順利完成所有步驟，以確保成功安裝 .NET Core。

## <a name="summary"></a>總結

本指南提供了 ASP.NET Core 的簡介。 當中描述其概念和使用時機，並提供了如何在 Visual Studio for Mac 中使用它的資訊。
如需下一個步驟的詳細資訊，請參閱下列指南：
- [ASP.NET Core](/aspnet/core/) 檔。
- [建立原生行動應用程式的後端服務](/aspnet/core/mobile/native-mobile-backend)，其示範如何使用 Xamarin.Forms 應用程式的 ASP.NET Core 來建置 REST 服務。
- [ASP.NET Core 實習實驗室](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started)。

## <a name="related-video"></a>相關影片

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Build-Your-First-App/player]