---
title: 步驟4：從您的 ASP.NET Core 應用程式公開 web API
description: 使用此影片教學課程和逐步指示，向您的 ASP.NET Core Web 應用程式新增 Web API。
ms.custom: get-started
ms.date: 02/13/2020
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
ms.openlocfilehash: 9625ce43d94158732c2d6af738a1f1abc84f666e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878769"
---
# <a name="step-4-expose-a-web-api-from-your-aspnet-core-app"></a>步驟4：從您的 ASP.NET Core 應用程式公開 web API

請遵循下列步驟將 Web API 新增至現有的 ASP.NET Core 應用程式中。

_觀看並遵循這段影片，向您的第一個 ASP.NET Core 應用程式新增 Web API 支援。_

> [!VIDEO https://www.youtube.com/embed/o_fYPOsAXts]

## <a name="open-your-project"></a>開啟您的專案

在 Visual Studio 2019 中開啟您的 ASP.NET Core 應用程式。 該應用程式應該已經使用 EF Core 來管理您的模型類型，如[本系列教學課程的步驟 3](tutorial-aspnet-core-ef-step-03.md) 中所設定。

## <a name="add-an-api-controller"></a>新增 API 控制器

以滑鼠右鍵按一下專案並加入一個名為 *Api* 的新資料夾。 然後，以滑鼠右鍵按一下此資料夾，然後選擇 [**加入**  >  **新的 scaffold 專案**]。 選擇 [使用 Entity Framework 執行動作的 API 控制器]。 現在選擇現有的模型類別，然後按一下 [新增]。

![Visual Studio 2019 ASP.NET Core Scaffolded API 控制器](media/vs-2019/vs2019-add-scaffold-api.png)

## <a name="reviewing-the-generated-controller"></a>檢閱產生的控制器

產生的程式碼包含新的控制器類別。 在類別定義的頂端是兩個屬性。

```csharp
[Route("api/[controller]")]
[ApiController]
public class GamesController : ControllerBase
```

第一個指定此控制器中的動作路由為 `api/[controller]`，這表示如果控制器名為 `GamesController`，則路由將為 `api/Games`。

第二個屬性 `[ApiController]` 為類別新增了一些實用的驗證，例如確保每個動作方法都包含它自己的 `[Route]` 屬性。

```csharp
public class GamesController : ControllerBase
{
    private readonly AppDbContext _context;

    public GamesController(AppDbContext context)
    {
        _context = context;
    }
```

控制器會使用現有的 `AppDbContext`，傳遞給它的建構函式。 每個動作都將使用此欄位來處理應用程式的資料。

```csharp
// GET: api/Games
[HttpGet]
public IEnumerable<Game> GetGame()
{
    return _context.Game;
}
```

第一種方法是使用 `[HttpGet]` 屬性指定的簡單 GET 要求。 它不接受任何參數，並傳回資料庫中所有遊戲的清單。

```csharp
// GET: api/Games/5
[HttpGet("{id}")]
public async Task<IActionResult> GetGame([FromRoute] int id)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    var game = await _context.Game.FindAsync(id);

    if (game == null)
    {
        return NotFound();
    }

    return Ok(game);
}
```

下一個方法會在路由中指定 `{id}`，它將被新增至 `/` 之後的路由中，因此完整路由將類似於 `api/Games/5`，如頂端註解中所示。 `id` 輸入會對應至方法上的 `id` 參數。 在方法中，如果模型無效，則傳回 `BadRequest` 結果。 否則，EF 會嘗試尋找與提供的 `id` 符合的記錄。 如果不能則傳回 `NotFound` 結果，否則傳回適當的 `Game` 記錄。

```csharp
// PUT: api/Games/5
[HttpPut("{id}")]
public async Task<IActionResult> PutGame([FromRoute] int id, [FromBody] Game game)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    if (id != game.Id)
    {
        return BadRequest();
    }

    _context.Entry(game).State = EntityState.Modified;

    try
    {
        await _context.SaveChangesAsync();
    }
    catch (DbUpdateConcurrencyException)
    {
        if (!GameExists(id))
        {
            return NotFound();
        }
        else
        {
            throw;
        }
    }

    return NoContent();
}
```

接下來，向 API 提出的 `[HttpPut]` 要求會用來執行更新。 新的 `Game` 記錄會在要求主體中提供。 會執行一些驗證和錯誤檢查，如果一切都成功，則使用要求主體中提供的值來更新資料庫中的記錄。 否則會傳回適當的錯誤回應。

```csharp
// POST: api/Games
[HttpPost]
public async Task<IActionResult> PostGame([FromBody] Game game)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    _context.Game.Add(game);
    await _context.SaveChangesAsync();

    return CreatedAtAction("GetGame", new { id = game.Id }, game);
}
```

`[HttpPost]` 要求用來向系統新增新記錄。 如同 `[HttpPut]` 一樣，記錄將新增至要求主體中。 如果它是有效的，則 EF Core 會將記錄加入到資料庫，並且動作將傳回更新的記錄 (及其產生的資料庫識別碼) 以及指向 API 中記錄的連結。

```csharp
// DELETE: api/Games/5
[HttpDelete("{id}")]
public async Task<IActionResult> DeleteGame([FromRoute] int id)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    var game = await _context.Game.FindAsync(id);
    if (game == null)
    {
        return NotFound();
    }

    _context.Game.Remove(game);
    await _context.SaveChangesAsync();

    return Ok(game);
}
```

最後，`[HttpDelete]` 路由會與識別碼一起使用以刪除記錄。 如果要求有效，且存在具有指定識別碼的記錄，則 EF Core 會從資料庫中刪除它。

## <a name="adding-swagger"></a>新增 Swagger

Swagger 是一個 API 文件和測試工具，可以作為一組服務與中介軟體新增至 ASP.NET Core 應用程式中。 若要這樣做，請以右鍵按一下專案，然後選擇 [管理 NuGet 套件]。 然後，按一下 **[流覽]**、搜尋 `Swashbuckle.AspNetCore` 及安裝4.0.1 版本。

![Visual Studio 2019 從 Nuget 新增 Swashbuckle](media/vs-2019/vs2019-nuget-swashbuckle.png)

安裝後，開啟 `Startup.cs` 並將下列內容新增至 `ConfigureServices` 方法的結尾：

```csharp
services.AddSwaggerGen(c =>
{
    c.SwaggerDoc("v1", new Info { Title = "My API", Version = "v1" });
});
```

您還需要在檔案頂端新增 `using Swashbuckle.AspNetCore.Swagger;`。

接下來，在 `UseMvc` 之前的 `Configure` 方法中加入下列內容：

```csharp
// Enable middleware to serve generated Swagger as a JSON endpoint.
app.UseSwagger();

// Enable middleware to serve swagger-ui (HTML, JS, CSS, etc.),
// specifying the Swagger JSON endpoint.
app.UseSwaggerUI(c =>
{
    c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
});
```

現在您應該能夠建置並執行您的應用程式。 在瀏覽器中，瀏覽至網址列中的 `/swagger`。 您應該會看到應用程式的 API 端點和模型清單。

![瀏覽器中的 Visual Studio 2019 Swagger 頁面](media/vs-2019/vs2019-swagger-browser.png)

按一下 [遊戲] 下的端點，然後按一下 `Try it out` 和 `Execute` 以查看不同端點的行為方式。

## <a name="next-steps"></a>下一步

在下一個影片中，您將學習如何將應用程式部署至 Azure。

[步驟5：將您的 ASP.NET Core 應用程式部署至 Azure](tutorial-aspnet-core-ef-step-05.md)

## <a name="see-also"></a>另請參閱

- [開始使用 Swashbuckle 及 ASP.NET Core](/aspnet/core/tutorials/getting-started-with-swashbuckle?view=aspnetcore-2.2&tabs=visual-studio&preserve-view=true)
- [使用 Swagger/OpenAPI 的 ASP.NET Core Web API 說明頁面](/aspnet/core/tutorials/web-api-help-pages-using-swagger?view=aspnetcore-2.2&preserve-view=true)