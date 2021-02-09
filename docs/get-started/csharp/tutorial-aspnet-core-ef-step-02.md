---
title: 步驟2：建立您的第一個 ASP.NET Core Web 應用程式
description: 使用此影片教學課程和逐步指示，建立您的第一個 ASP.NET Core Web 應用程式。
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
ms.openlocfilehash: e560d9028a7c2044964f5a2ec54e8daefea26372
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922818"
---
# <a name="step-2-create-your-first-aspnet-core-web-app"></a>步驟2：建立您的第一個 ASP.NET Core web 應用程式

使用此影片教學課程和逐步指示，建立您的第一個 ASP.NET Core Web 應用程式。

_觀看此影片並跟著操作，建立您的第一個 ASP.NET Core 應用程式。_

> [!VIDEO https://www.youtube.com/embed/-79RkpyFB6E]

## <a name="start-visual-studio-2019-and-create-a-new-project"></a>啟動 Visual Studio 2019 並建立新專案

啟動 Visual Studio 2019 並按一下 [建立新專案]。 選擇 [ASP.NET Core Web 應用程式]。 選擇 [Web 應用程式] 範本，保留預設的專案名稱和位置。 在具有 ASP.NET Core 版本的下拉式清單中，選擇 **ASP.NET Core 2.1** 或 **ASP.NET Core 2.2**。 按一下頁面底部的 [新增]  。 如需詳細指示，請參閱[本教學課程系列的上一段影片](tutorial-aspnet-core-ef-step-01.md)。

![Visual Studio 2019 選擇 ASP.NET Core 專案選項](media/vs-2019/vs2019-choose-aspnetcore-project.png)

> [!WARNING]
> 請確定您選擇的是 ASP .NET Core 2.1 或 ASP.NET Core 2.2。 本教學課程與 ASP.NET Core 3.x 不相容。

## <a name="explore-the-new-project"></a>探索新專案

在右側的方案總管視窗中，您可以檢視新專案的內容。 其於此描述。

![Visual Studio 2019 ASP.NET Core 專案](media/vs-2019/vs2019-solution-explorer.png)

### <a name="wwwroot"></a>wwwroot

*wwwroot* 資料夾存放的靜態檔案，可從 Web 應用程式公開存取。 它通常存放樣式表、用戶端指令碼檔案和影像。

### <a name="pages"></a>頁面

*Pages* 資料夾存放網站的 Razor 頁面。 預設範本提供數個頁面，包括應用程式首頁的 *Index.cshtml* 頁面，以及 [關於]、[連絡人] 等等。

### <a name="appsettingsjson"></a>appsettings.json

此檔案存放 JSON 格式的網站組態設定。

### <a name="programcs"></a>Program.cs

此檔案作為應用程式的進入點使用。 執行應用程式時，其 Main 方法是執行的第一個方法，負責建立會包含應用程式的 Web 主機。

### <a name="startupcs"></a>Startup.cs

在 *Program.cs* 中建立的 Web 主機會參考啟動類別，並呼叫其方法以設定應用程式。 ConfigureServices 方法負責設定應用程式要使用的任何服務。 `Configure` 方法會設定應用程式的 HTTP 要求管線。 每個要求都會經由此管線，在如此做時與「中介軟體」的每個片段互動。

### <a name="indexcshtml"></a>Index.cshtml

網站首頁包含一些 HTML 標記和一些伺服器端的 Razor 程式碼。 它使用 Razor 來指定頁面模型 `IndexModel`，其位於相關聯的 *Index.cshtml.cs* 檔案中。 它也會在 ViewData 中設定值來設定頁面標題。 這個 ViewData 值是在配置 *\_ . cshtml* 檔案中讀取，該檔案位於 Pages 資料夾內的共用資料夾中。 Layout 檔案為許多 Razor 頁面共用，並為應用程式提供共同的外觀與風格。 每個頁面內容都會在 Layout 檔案的 HTML 中轉譯。

## <a name="run-the-application"></a>執行應用程式

現在執行應用程式，並在瀏覽器中檢視它。 您可以使用 **Ctrl** F5 來執行應用程式， + 或  >  從 Visual Studio 的功能表中選擇 [Debug **啟動但不進行調試** 程式]。

## <a name="customize-the-application"></a>自訂應用程式

將屬性新增至 *Index.cshtml.cs* 檔案，並在 `OnGet` 處理常式中將其值設定為目前的時間：

```csharp
public string Time { get; set; }
public void OnGet()
{
    Time = DateTime.Today.ToShortTimeString();
}
```

使用這個標記取代 *Index.cshtml* 中的 `<div>` 內容：

```cshtml
<h2>It's @Model.Time right now on the server!</h2>
```

再次執行應用程式。 您現在應該會看到頁面顯示目前的時間，但一律為午夜！ 這樣不對。

![瀏覽器視窗中應用程式首頁的螢幕擷取畫面。 頁面的內容會顯示：「目前正于伺服器上的 12:00 AM！」。](media/vs-2019/vs2019-app-in-browser.png)

## <a name="debug-the-application"></a>偵錯應用程式

在 `OnGet` 方法中新增中斷點，我們會在此方法中將值指派給 `Time`，並在此時開始偵錯應用程式。

執行會在此行停止，您可以看到 `DateTime.Today` 包含日期，但時間一直停留在午夜，因為它不包含時間資料。

![顯示 Visual Studio 中 Index.cshtml.cs 程式碼的螢幕擷取畫面。 中斷點設定在行 ' Time = DateTime. ToShortTimeString ( # A1; '。](media/vs-2019/vs2019-breakpoint.png)

將它變更為使用 `DateTime.Now` 並繼續執行。 `OnGet` 的新程式碼應該是：

```csharp
public void OnGet()
{
    Time = DateTime.Now.ToShortTimeString();
}
```

當您瀏覽至應用程式時，現在應會看到瀏覽器中實際的伺服器時間。

> [!NOTE]
> 您的輸出可能會與圖片不同，因為 ToShortDateTimeString 的輸出格式取決於目前的文化特性設定。 請參閱 <xref:System.DateTime.ToShortTimeString>。

![瀏覽器視窗中應用程式首頁的螢幕擷取畫面。 頁面的內容會顯示：「目前正于伺服器上的 1:46 AM！」。](media/vs-2019/vs2019-app-fixed-in-browser.png)

## <a name="next-steps"></a>下一步

在下段影片中，您會了解如何將資料支援新增至您的應用程式。

[教學課程：使用 ASP.NET Core 應用程式中的資料](tutorial-aspnet-core-ef-step-03.md)

## <a name="see-also"></a>另請參閱

- [教學課程：使用 ASP.NET Core 建立 Razor Pages web 應用程式](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1&preserve-view=true)
