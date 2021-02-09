---
title: 步驟3：使用 ASP.NET Core 應用程式中的資料
description: 使用此影片教學課程和逐步指示，開始在您的 ASP.NET Core Web 應用程式中使用 Entity Framework Core 處理資料。
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: aa3df844d5fad5dc968a9bab5d02e9a3e8e06719
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879965"
---
# <a name="step-3-work-with-data-using-entity-framework"></a>步驟3：使用 Entity Framework 處理資料

遵循這些步驟，以在您的 ASP.NET Core Web 應用程式中，開始使用 Entity Framework Core 來處理資料。

_觀看此影片並跟著操作，將資料新增到您的第一個 ASP.NET Core 應用程式。_

> [!VIDEO https://www.youtube.com/embed/dulJCwNrqhM]

## <a name="open-your-project"></a>開啟您的專案

如果您正按照此影片操作，請開啟您在上一節中建立的 Web 應用程式專案。 如果您是從這裡開始，則需要建立新專案並依序選擇 [ASP.NET Web 應用程式]、[Web 應用程式]。 維持其餘選項的預設設定。

## <a name="add-your-model"></a>新增您的模型

要在您的 ASP.NET Core 應用程式中處理資料的第一步是描述資料的外觀。 我們將此步驟稱為建立我們嘗試要解決之問題中所含項目的「模型」。 在真實應用程式中，我們會將自訂商務邏輯新增到這些模型中，它們就會進行某種行為，並為我們自動化工作。 對於此範例，我們將建立追蹤棋盤遊戲的簡單系統。 我們需要代表遊戲的類別，並包含一些我們可能想要記錄有關該遊戲的屬性，如該遊戲支援多少玩家。 此類別會位在我們於 Web 專案根建立的新資料夾內，稱為 [Models]。

```csharp
public class Game
{
    public int Id { get; set; }
    public string Title { get; set; }
    public int PublicationYear { get; set; }
    public int MinimumPlayers { get; set; }
    public int MaximumPlayers { get; set; }
}
```

## <a name="create-the-pages-to-manage-your-game-library"></a>建立頁面以管理您的遊戲庫

現在，我們已經準備好建立此頁面，我們將用它來管理遊戲庫。 這聽起來可能令人怯步，但其實非常簡單。 首先，我們需要決定此功能要位於應用程式中的何處。 開啟 Web 專案中的 [Pages] 資料夾，並在那裡新增資料夾。 將它稱為「Games」。

現在以滑鼠右鍵按一下遊戲，然後選擇 [**加入**  >  **新的 scaffold 專案**]。 選擇 [使用 Entity Framework (CRUD) 的 Razor 頁面] 選項。 CRUD 代表「建立 (Create)、讀取 (Read)、更新 (Update)、刪除 (Delete)」，而此範本會為每個這些作業都建立頁面 (包括「列出全部」和「檢視一個項目的詳細資訊」頁面)。

![Visual Studio 2019 ASP.NET Core [新增 Scaffolded] 頁面](media/vs-2019/vs2019-add-scaffold.png)

選取您的 [Game] 模型類別並使用 '+' 圖示來新增資料內容類別。 請命名為 `AppDbContext`。 維持其他預設值，再按 [新增]。

您會看到下列的 Razor Pages 新增至您的 [Games] 資料夾：

- Create.cshtml
- Delete.cshtml
- Details.cshtml
- Edit.cshtml
- Index.cshtml

![Visual Studio 2019 ASP.NET Core Scaffolded 頁面](media/vs-2019/vs2019-scaffolded-pages.png)

除了在 [Games] 資料夾中新增頁面，Scaffolding 作業還將程式碼新增至 *Startup.cs* 類別。 查看此類別中的 `ConfigureServices` 方法，您會看到已新增此程式碼：

```csharp
services.AddDbContext<AppDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("AppDbContext")));
```

您會發現 `AppDbContext` 連接字串已經新增到專案的 *appsettings.json* 檔案。

如果您現在執行應用程式，它可能會失敗，因為還沒建立資料庫。 藉由[新增一些程式碼到 Program.cs](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio&preserve-view=true#update-main)，您可以將應用程式設定為在需要時會自動建立資料庫：

```csharp
public static void Main(string[] args)
{
    var host = CreateWebHostBuilder(args).Build();

    using (var scope = host.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        try
        {
            var context = services.GetRequiredService<Data.AppDbContext>();
            context.Database.EnsureCreated();
        }
        catch (Exception ex)
        {
            var logger = services.GetRequiredService<ILogger<Program>>();
            logger.LogError(ex, "An error occurred creating the DB.");
        }
    }

    host.Run();
}
```

若要解析上述程式碼中的類型名稱，請在 *Program.cs* 中 using 陳述式的現有區塊結尾處新增下列 using 陳述式：

```csharp
using Microsoft.Extensions.DependencyInjection;
using WebApplication1.Models;
```

請務必在您的程式碼中使用專案名稱，而不是 WebApplication1。

大部分的程式碼只是用於錯誤處理，以及在應用程式執行之前提供對 EF Core `AppDbContext` 的存取。 重要的一行是顯示為 `context.Database.EnsureCreated()`，如果資料庫不存在，它就會建立資料庫。 應用程式現在已可執行。

## <a name="test-it-out"></a>立即測試

執行應用程式，並在網址列中瀏覽至 `/Games`。 您會看到空白清單頁面。 按一下 [Create New] \(建立新的\) 來將 `Game` 新增至集合。 填寫表單，然後按一下 [Create] \(建立\)。 您應該會在清單檢視中看到它。 按一下 [Details] \(詳細資料\) 來查看單一資料列詳細資料。

加入另一個資料列。 您可以按一下 [Edit] \(編輯\) 來變更資料列的詳細資料，或按一下 [Delete] \(刪除\) 來移除它，系統會在實際刪除資料列之前提示您進行確認。

![瀏覽器中的 Visual Studio 2019 ASP.NET Core Scaffolded 頁面](media/vs-2019/vs2019-game-list.png)

這就是在 ASP.NET Core 應用程式中使用 EF Core 和 Visual Studio 2019 來處理資料所需的工作。

## <a name="next-steps"></a>下一步

在下一個影片中，您將學習如何將 Web API 支援新增至您的應用程式。

[步驟4：從您的 ASP.NET Core 應用程式公開 web API](tutorial-aspnet-core-ef-step-04.md)

## <a name="see-also"></a>另請參閱

- [ASP.NET Core 中的 Entity Framework Core Razor Pages](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio&preserve-view=true)
- [ASP.NET Core Razor 頁面與 EF Core](/aspnet/core/data/?view=aspnetcore-2.1&preserve-view=true)
