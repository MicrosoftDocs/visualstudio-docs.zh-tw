---
title: 在 Visual Studio for Mac 中建置 ASP.NET Core 應用程式
description: 本文說明如何在 Visual Studio for Mac 中開始使用 ASP.NET，包括安裝及建立新的專案。
author: sayedihashimi
ms.author: sayedha
ms.date: 05/30/2019
ms.assetid: 771C2F8E-46BC-4280-AFE8-ED9D5C7790CE
ms.openlocfilehash: f0a2e8433877b3eb61228a886280707f3b4a37fe
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67693133"
---
# <a name="building-aspnet-core-applications-in-visual-studio-for-mac"></a>在 Visual Studio for Mac 中建置 ASP.NET Core 應用程式 

ASP.NET Core 是一個開放原始碼和跨平台架構，可建置現代雲端架構的網際網路連線應用程式，例如 Web 應用程式和服務、IoT 應用程式和行動後端。 ASP.NET Core 應用程式可以在 [.NET Core](https://www.microsoft.com/net/core/platform) \(英文\) 或 .NET Framework 執行階段上執行。 它被設計成可為部署至雲端或在內部部署上執行的應用程式，提供最佳化的開發架構。 它包含具有最少額外負荷的模組化元件，讓您在建構方案時能保持彈性。 您可以在 Windows、Mac 和 Linux 上跨平台開發和執行 ASP.NET Core 應用程式。 ASP.NET Core 是 [GitHub](https://github.com/aspnet/home) 上的開放原始碼。

在本實驗室中，您將會搭配 Visual Studio for Mac 建立並探索 ASP.NET Core 應用程式。

## <a name="objectives"></a>目標

> [!div class="checklist"]
> * 建立 ASP.NET Core Web 應用程式
> * 探索 ASP.NET Core 裝載、設定及中介軟體模型
> * 對 ASP.NET Core Web 應用程式進行偵錯

## <a name="prerequisites"></a>必要條件

- [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac)

## <a name="intended-audience"></a>適用對象

本實驗適用於熟悉 C# 的開發人員，但不需要深度經驗。

## <a name="task-1-creating-a-new-aspnet-core-application"></a>工作 1：建立新的 ASP.NET Core 應用程式

1. 啟動 **Visual Studio for Mac**。

2. 選取 [檔案] > [新增方案]  。

3. 選取 [.NET Core] > [應用程式]  類別，然後選取 [ASP.NET Core Web 應用程式 (C#)]  範本。 按 [ **下一步**]。

    ![](media/netcore-image1.png)

4. 輸入 **"CoreLab"** 作為名稱，然後按一下 [建立]  來建立專案。 這需要花費一點時間才能完成。

    ![](media/netcore-image2.png)

## <a name="task-2-touring-the-solution"></a>工作 2：瀏覽方案

1. 預設範本將會產生具有名為 **CoreLab** 的單一 ASP.NET Core 專案的方案。 展開專案節點，以公開其內容。

    ![](media/netcore-image3.png)

2. 此專案會遵循 Model-View-Controller (MVC) 架構，以在資料 (模型)、呈現 (檢視) 及功能 (控制器) 之間提供清楚的職責區隔。 從 **Controllers** 資料夾中，開啟 **HomeController.cs** 檔案。

    ![](media/netcore-image4.png)

3. **HomeController** 類別依照慣例會處理以 **/Home** 為開頭的所有傳入要求。 **Index** 方法會處理針對根目錄 (例如 `http://site.com/Home`) 的要求，而其他方法則會依慣例處理針對其具名路徑的要求 (例如 **About()** 會處理針對 `http://site.com/Home/About` 的要求)。 當然，這全都是可以加以設定的。 其中一個值得注意的地方是 **HomeController** 為新專案的預設控制器，因此針對網站根目錄 (`http://site.com`) 的要求將會通過 **HomeController** 的 **Index()** ，就像針對 `http://site.com/Home` 或 `http://site.com/Home/Index` 的要求一樣。

    ![](media/netcore-image5.png)

4. 專案也會有 **Views** 資料夾，內含對應至每個控制器的其他資料夾 (以及 [共用]  檢視的資料夾)。 例如， **/Home/About** 路徑的檢視 CSHTML 檔案 (副檔名為 HTML) 是在 **Views/Home/About.cshtml** 中。 開啟該檔案。

    ![](media/netcore-image6.png)

5. 此 CSHTML 檔案使用 Razor 語法，根據標準標記與內嵌 C# 的組合來呈現 HTML。 您可以在[線上文件](https://docs.microsoft.com/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c) \(部分機器翻譯\) 中深入了解這點。

    ![](media/netcore-image7.png)

6. 方案也包含將會成為網站根目錄的 **wwwroot** 資料夾。 部署網站時，您可以將 CSS、影像和 JavaScript 程式庫這類靜態網站內容直接放在您要放置它們的路徑上。

    ![](media/netcore-image8.png)

7. 另外還有各種組態檔可用來在執行階段管理專案、其專案和應用程式。 例如，預設應用程式[組態](https://docs.microsoft.com/aspnet/core/fundamentals/configuration)會儲存在 **appsettings.json** 中。 不過，您可以根據每個環境來覆寫其中一部分/所有設定，例如，透過提供**開發**環境的 **appsettings.Development.json** 檔案。

    ![](media/netcore-image9.png)

## <a name="task-3-understanding-how-the-application-is-hosted"></a>工作 3：了解應用程式的裝載方式

1. 從 [方案總管]  中，開啟 **Program.cs**。 這是將會執行您應用程式的啟動載入器。

    ![](media/netcore-image10.png)

2. 雖然這裡只有兩行程式碼，它們都相當重要。 讓我們仔細釐清它們。 首先，系統會建立新的 **WebHostBuilder**。 ASP.NET Core 應用程式需要主機，以在其中執行。 主機必須實作 **IWebHost** 介面，其會公開功能與服務的集合，以及 **Start** 方法。 主機通常是使用 **WebHostBuilder** 的執行個體來建立，其會建置並傳回 **WebHost** 執行個體。 **WebHost** 會參考將處理要求的伺服器。

    ![](media/netcore-image11.png)

3. 雖然 **WebHostBuilder** 會負責建立將會為應用程式啟動伺服器的主機，它需要您提供能實作 **IServer** 的伺服器。 根據預設，這會是 **[Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel)** ，此為以 **libuv** (跨平台的非同步 I/O 程式庫) 為基礎，適用於 ASP.NET Core 的跨平台網頁伺服器。

    ![](media/netcore-image12.png)

4. 接下來，將會設定伺服器的內容根目錄。 這會決定它搜尋內容檔的位置，例如 MVC 檢視檔案。 預設的內容根目錄是應用程式執行所在的資料夾。

    ![](media/netcore-image13.png)

5. 如果應用程式必須搭配 Internet Information Services (IIS) 網頁伺服器運作，便應該先呼叫 **UseIISIntegration** 方法作為建置主機的一部分。 這不會像 **UseKestrel** 那樣設定伺服器。 若要搭配 ASP.NET Core 使用 IIS，您必須同時指定 **UseKestrel** 和 **UseIISIntegration**。 **Kestrel** 是設計來在 Proxy 後方執行，且不應該直接部署為面對網際網路。 **UseIISIntegration** 會將 IIS 指定為反向 Proxy 伺服器，但這只會在具有 IIS 的電腦上具相關性。 如果您是將應用程式部署至 Windows，請保留它。 它並不會有任何負面影響。

    ![](media/netcore-image14.png)

6. 將設定的載入與應用程式的啟動載入分開，是較為簡潔的作法。 若要輕鬆地這麼做，請呼叫 **UseStartup** 來指定要針對載入設定及其他啟動工作 (例如將中介軟體插入至 HTTP 管線) 呼叫 **Startup** 類別。 您可能會有多個 **UseStartup** 呼叫，並預期每個新設定都會視需求覆寫上一個設定。

    ![](media/netcore-image15.png)

7. 最後一個步驟是建立 **IWebHost** 來呼叫 **Build**。

    ![](media/netcore-image16.png)

8. 雖然需要 **IWebHost** 類別來實作非封鎖 **Start**，ASP.NET Core 專案具有稱為 **Run** 的擴充方法，其能搭配封鎖程式碼來包裝 **Start**，使您不需要手動防止方法立即結束。

    ![](media/netcore-image17.png)

## <a name="task-4-running-and-debugging-the-application"></a>工作 4：執行應用程式並對其進行偵錯

1. 在 [方案總管]  中，以滑鼠右鍵按一下 [CoreLab]  專案節點，然後選取 [選項]  。

    ![](media/netcore-image18.png)

2. [專案選項]  對話方塊包含調整應用程式的建置及執行方法的所有必要內容。 從左側面板選取 [執行] > [設定] > [預設]  節點。

3. 核取 [在外部主控台上執行]  並取消核取 [暫停主控台輸出]  。 自我裝載應用程式的主控台通常不會可見，而會改為將結果記錄到 [輸出]  索引頁。 基於本實驗室的目的，我們也會在個別的視窗中顯示它，不過您在一般的開發期間並不需要那麼做。

4. 按一下 [確定]  。

    ![](media/netcore-image19.png)

5. 按 **F5** 鍵建置並執行應用程式。 或者，您可以選取 [執行] > [開始偵錯]  。

6. Visual Studio for Mac 將會啟動兩個視窗。 第一個是主控台視窗，其能提供針對自我裝載伺服器應用程式的檢視。

    ![](media/netcore-image20.png)

7. 第二個是一般的瀏覽器視窗，可用來測試該網站。 對瀏覽器來說，此應用程式可能被裝載在任何地方。 按一下 [關於]  來瀏覽至該頁面。

    ![](media/netcore-image21.png)

8. 除了其他工作之外，[關於] 頁面會呈現在控制器中所設定的一些文字。

    ![](media/netcore-image22.png)

9. 將兩個視窗保持開啟，並返回 Visual Studio for Mac。 開啟 **Controllers/HomeController.cs** (如果尚未開啟)。

    ![](media/netcore-image23.png)

10. 在 **About** 方法的第一行中，設定中斷點。 若要這麼做，您可以按一下邊界，或將游標暫留在線上並按下 **F9**。 這行設定 **ViewData** 集合中的一些資料，而這些資料會呈現在 **Views/Home/About.cshtml** 的 CSHTML 頁面中。

    ![](media/netcore-image24.png)

11. 回到瀏覽器，並重新整理 [關於] 頁面。 這將會觸發 Visual Studio for Mac 中的中斷點。

12. 將滑鼠移至 **ViewData** 成員上方，以檢視其資料。 您可以展開其子成員以查看巢狀資料。

    ![](media/netcore-image25.png)

13. 使用您用來新增應用程式中斷點的相同方法來移除應用程式中斷點。

14. 開啟 **Views/Home/About.cshtml**。

15. 將文字 **"additional"** 變更為 **"changed"** ，並儲存檔案。

    ![](media/netcore-image26.png)

16. 按 [繼續]  按鈕以繼續執行。

    ![](media/netcore-image27.png)

17. 回到瀏覽器視窗，以查看更新的文字 此變更可以在任何時候進行，且不需要偵錯工具中斷點。 如果您未看見變更立即反映，請重新整理瀏覽器。

    ![](media/netcore-image28.png)

18. 關閉測試瀏覽器視窗和應用程式主控台。 這同時也會停止偵錯。

## <a name="task-5-application-startup-configuration"></a>工作 5：應用程式啟動設定

1. 從 [方案總管]  開啟 **Startup.cs**。 在系統於背景還原 NuGet 套件，且 Roslyn 編譯器正在編譯專案相依性的完整面貌時，您一開始可能會看見一些紅色波浪線。

    ![](media/netcore-image29.png)

2. 找出 **Startup** 方法。 此區段會定義應用程式的初始設定，且具有非常多的內容。 讓我們仔細釐清它。

    ![](media/netcore-image30.png)

3. 該方法會先初始化 **ConfigurationBuilder** 並設定其基底路徑。

    ![](media/netcore-image31.png)

4. 接下來，它會載入必要的 **appsettings.json** 檔案。

    ![](media/netcore-image32.png)

5. 在那之後，它會嘗試載入環境特定的 **appsettings.json** 檔案，其將會覆寫現有設定。 例如，以下是針對該特定環境所提供的 **appsettings.Development.json** 檔案。 若要深入了解 ASP.NET Core 中的設定，請參閱[相關文件](https://docs.microsoft.com/aspnet/core/fundamentals/configuration)。

    ![](media/netcore-image34.png)

6. 最後，會將環境變數新增至設定建立器以建置設定並使其可供使用。

    ![](media/netcore-image35.png)

## <a name="task-6-inserting-application-middleware"></a>工作 6：插入應用程式中介軟體

1. 找出 **Startup** 類別中的 **Configure** 方法。 這是設定所有中介軟體以將其插入至 HTTP 管線，並用來處理針對伺服器之所有要求的位置。 雖然此方法只會被呼叫一次，每個要求都可能會執行方法的內容 (例如 **UseStaticFiles**)。

    ![](media/netcore-image36.png)

2. 您也可以加入其他中介軟體，以作為管線的一部分執行。 在 **app.UseStaticFiles** 之後加入下列程式碼，以自動將 **X-Test** 標頭加入至每個傳出的回應。 IntelliSense 將會在您輸入時協助完成程式碼。

    ```csharp
    app.Use(async (context, next) =>
    {
        context.Response.Headers.Add("X-Test", new[] { "Test value" });
        await next();
    });
    ```

3. 按 **F5** 鍵建置並執行專案。

4. 我們可以使用瀏覽器來檢查標頭，以確認它們是否已被加入。 下列的指示適用於 Safari，但您可以在 [Chrome](https://stackoverflow.com/questions/4423061/view-http-headers-in-google-chrome) \(英文\) 或 [Firefox](https://stackoverflow.com/questions/33974595/in-firefox-how-do-i-see-http-request-headers-where-in-web-console) \(英文\) 中執行相同的工作。

5. 在瀏覽器載入網站之後，請選取 [Safari] > [偏好設定]  。

6. 在 [進階]  索引標籤上，核取 [在選單列中顯示「開發」選單]  ，然後關閉對話方塊。

    ![](media/netcore-image37.png)

7. 選取 [開發] > [顯示網頁資源]  。

8. 重新整理瀏覽器視窗來讓新開啟的開發人員工具能追蹤及分析流量和內容。

9. 由伺服器轉譯的 localhost HTML 頁面將會是系統預設選取的項目。

    ![](media/netcore-image38.png)

10. 展開 [詳細資訊]  側邊欄。

    ![](media/netcore-image39.png)

11. 捲動至側邊欄的底部，以查看稍早加入至程式碼的回應標頭。

    ![](media/netcore-image40.png)

12. 確認完畢後，請關閉瀏覽器視窗和主控台。

## <a name="summary"></a>總結

在本實驗室中，您已了解如何開始搭配 Visual Studio for Mac 開發 ASP.NET Core 應用程式。 如果您想了解如何開發更為完整的電影資料庫應用程式，請參閱[開始使用 ASP.NET Core MVC](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/start-mvc) 教學課程。
