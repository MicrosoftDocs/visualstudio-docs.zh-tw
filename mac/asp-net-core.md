---
title: 開始使用 ASP.NET Core
description: 本文說明如何在 Visual Studio for Mac 中開始使用 ASP.NET，包括安裝及建立新的專案。
author: conceptdev
ms.author: crdun
ms.date: 07/13/2017
ms.assetid: 6E8B0C90-33D6-4546-8207-CE0787584565
ms.openlocfilehash: 694f6f10a482318f6c6a1c40e6796e09daac0913
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942942"
---
# <a name="getting-started-with-aspnet-core"></a>開始使用 ASP.NET Core

 Visual Studio for Mac 可藉由支援最新的 ASP.NET Core Web 程式開發平台，讓您輕鬆地開發應用程式的服務。 ASP.NET Core 在 .NET Core 上執行，而 .NET Core 是 .NET Framework 和執行階段的最新演進。 它已針對快速效能進行調整、分解成小型安裝大小，並重新設想為在 Linux 與 macOS 及 Windows 上執行。

## <a name="installing-net-core"></a>安裝 .NET Core

當您安裝 Visual Studio for Mac 時，即會自動安裝 .NET Core 1.1。

## <a name="creating-an-aspnet-core-app-in-visual-studio-for-mac"></a>在 Visual Studio for Mac 中建立 ASP.NET Core 應用程式

開啟 Visual Studio for Mac。 在歡迎頁面上選取 [新增專案...]

![[新增專案] 對話方塊](media/asp-net-core-image1.png)

這會顯示 [新增專案] 對話方塊，可讓您選取範本來建立應用程式。

有許多專案可為您提供預先建立的範本，以開始建置 ASP.NET Core 應用程式。 這些是：

- **.NET Core > ASP.NET Core 空白 Web 應用程式**
- **.NET Core > ASP.NET Core Web 應用程式**
- **.NET Core > ASP.NET Core Web API**
- **多平台 > 應用程式 > 連線的應用程式**

![ASP.NET 專案選項](media/asp-net-core-image11.png)

選取 [ASP.NET Core 空白 Web 應用程式]，然後按 [下一步]。 提供專案名稱，然後按 [建立]。 這會建立新的 ASP.NET Core 應用程式，看起來應該類似下面的影像：

![新的 ASP.NET Core 空白專案檢視](media/asp-net-core-image4.png)

ASP.NET Core 空白 Web 應用程式建立的 Web 應用程式含有兩個預設檔案：**Program.cs** 和 **Startup.cs**，其說明如下。 它也會建立相依性資料夾，其中包含專案的 NuGet 套件相依性，例如 ASP.NET Core、.NET Core 架構和用來建置專案的 MSBuild 目標：

![顯示相依性的 Solution Pad](media/asp-net-core-image12.png)

### <a name="programcs"></a>Program.cs

在專案中開啟並檢查 **Program.cs** 檔案。 請注意 `Main` 方法中發生兩件事 - 對應用程式的輸入：

```csharp
public static void Main(string[] args)
{
    var host = new WebHostBuilder()
        .UseKestrel()
        .UseContentRoot(Directory.GetCurrentDirectory())
        .UseIISIntegration()
        .UseStartup<Startup>()
        .Build();

    host.Run();
}
```
ASP.NET Core 應用程式會透過 [`WebHostBuilder`](https://docs.microsoft.com/aspnet/core/fundamentals/hosting) 的執行個體設定和啟動主機，在其 Main 方法中建立 Web 伺服器。 這個建立器提供了一些方法來允許設定主機。 在範本應用程式中會使用下列組態：

* `UseKestrel`：指定應用程式將使用的 Kestrel 伺服器
* `UseContentRoot(Directory.GetCurrentDirectory())`：當應用程式從 Web 專案的根資料夾啟動時，使用這個資料夾作為應用程式的內容根目錄
* `.UseIISIntegration()`：指定應用程式應該使用 IIS。 若要搭配使用 IIS 與 ASP.NET Core，必須同時指定 `UseKestrel` 和 `UseIISIntegration`。
* `.UseStartup<Startup>()`：指定啟動類別。

  Build 和 Run 方法會建置裝載應用程式的 IWebHost，並使其開始接聽傳入的 HTTP 要求。

### <a name="startupcs"></a>Startup.cs

應用程式的啟動類別是在 `WebHostBuilder` 的 `UseStartup()` 方法中指定。 在這個類別中，您將指定要求處理管線，並在其中設定任何服務。

在專案中開啟並檢查 **Startup.cs** 檔案：

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
    }

    public void Configure(IApplicationBuilder app, IHostingEnvironment env, ILoggerFactory loggerFactory)
    {
        loggerFactory.AddConsole();

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

`Configure` 可讓您使用[中介軟體](https://docs.microsoft.com/aspnet/core/fundamentals/middleware)撰寫要求管線。 這些是 ASP.NET 應用程式管線中用來處理要求和回應的元件。 HTTP 管線包含許多要求委派，這些委派將依順序呼叫。 每個委派可以選擇處理要求本身，或將它傳遞至下一個委派。

您可以在 `IApplicationBuilder` 上使用 `Run`、`Map` 和 `Use` 方法來設定委派，但 `Run` 方法永遠不會呼叫下一個委派，因此應該一律在管線結尾處使用。

預先建立範本的 `Configure` 方法是為了執行一些作業而建立的。 首先，它會設定例外狀況處理頁面以供開發期間使用。 然後，它會以簡單的 "Hello World" 傳送回應給要求網頁。

現在，無需新增任何其他程式碼，即可執行這個簡單的 Hello, World 專案。 若要執行應用程式，並在瀏覽器中檢視它，請按工具列中的 [播放] (三角形) 按鈕：

![執行應用程式](media/asp-net-core-image5.png)

Visual Studio for Mac 會使用隨機的連接埠來啟動您的 Web 專案。 若要找出這個連接埠，請開啟應用程式輸出，其列在 [檢視] > [板] 底下。 您應該尋找的輸出類似如下：

![顯示接聽連接埠的應用程式輸出](media/asp-net-core-image6.png)

開啟您選擇的瀏覽器，然後輸入 `http://localhost:5000/`，並將 `5000` 取代為 Visual Studio 在應用程式輸出中輸出的連接埠。 您應該會看到文字 `Hello World!`：

![顯示文字的瀏覽器](media/asp-net-core-image7.png)

## <a name="adding-a-controller"></a>新增控制器

ASP.NET Core 應用程式使用「模型-檢視-控制器 (MVC)」設計模式，為應用程式的每個部分提供責任的邏輯分隔。 MVC 包含下列項目：

- **模型**：代表應用程式資料的類別。
- **檢視**：顯示應用程式的使用者介面 (這通常是模型資料)。
- **控制器**：用來處理瀏覽器要求、回應使用者輸入和互動的類別。

如需使用 MVC 的詳細資訊，請參閱 [ASP.NET Core MVC 的概觀](https://docs.microsoft.com/aspnet/core/mvc/overview)指南。

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

如果您需要在 Mac OS 10.11 (El Capitan) 和更高版本上手動安裝 .NET Core ，請執行下列作業：

1. 在開始安裝 .NET Core 之前，請確定所有作業系統更新已更新為最新穩定版本。 若要檢查此項，請移至應用程式市集應用程式，然後選取 [更新] 索引標籤。

2. 遵循 [.NET Core 網站](https://www.microsoft.com/net/core#macos)上所列出的步驟。

請務必先順利完成所有四個步驟，以確保已順利安裝 .NET Core。

## <a name="summary"></a>總結

本指南提供了 ASP.NET Core 的簡介。 當中描述其概念和使用時機，並提供了如何在 Visual Studio for Mac 中使用它的資訊。
如需其下一個步驟的詳細資訊，請參閱下列指南：
- [ASP.NET Core](https://docs.microsoft.com/aspnet/core/?view=aspnetcore-2.1#build-web-ui-and-web-apis-using-aspnet-core-mvc) 文件。
- [建立原生行動應用程式的後端服務](https://docs.microsoft.com/aspnet/core/mobile/native-mobile-backend)，其示範如何使用 Xamarin.Forms 應用程式的 ASP.NET Core 來建置 REST 服務。
- [ASP.NET Core 實習實驗室](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started)。
