---
title: 教學課程：開始使用 C# 及 ASP.NET Core
titleSuffix: ''
description: 了解如何在 Visual Studio 中使用 C# 逐步建立 ASP.NET Core Web 應用程式。
ms.custom: seodec18, get-started
ms.date: 05/29/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 00423f3affa5c882137ee19c355252acbf23c976
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402121"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>教學課程：Visual Studio 中的 C# 和 ASP.NET Core 使用者入門

在這個使用 Visual Studio 透過 ASP.NET Core 進行 C# 開發的教學課程中，您將建立 C# ASP.NET Core Web 應用程式、對其進行變更、探索 IDE 的一些功能，然後執行應用程式。

## <a name="before-you-begin"></a>開始之前

### <a name="install-visual-studio"></a>安裝 Visual Studio

::: moniker range="vs-2017"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。

::: moniker-end

::: moniker range="vs-2019"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)頁面免費進行安裝。

::: moniker-end

### <a name="update-visual-studio"></a>更新 Visual Studio 2017

如果您已經安裝 Visual Studio，請確定您執行的是最新版本。 如需如何更新安裝的詳細資訊，請參閱[將 Visual Studio 更新至最新版本](../../install/update-visual-studio.md)頁面。

### <a name="choose-your-theme-optional"></a>選擇您的佈景主題 (選擇性)

本教學課程包含使用深色佈景主題的螢幕擷取畫面。 如果您未使用深色佈景主題，但想要使用，請參閱[將 Visual Studio IDE 和編輯器個人化](../../ide/quickstart-personalize-the-ide.md)頁面以了解做法。

## <a name="create-a-project"></a>建立專案

首先，您會建立 ASP.NET Core 專案。 在您新增任何內容之前，專案類型已包含完整功能之網站所需要的所有範本檔案！

::: moniker range="vs-2017"

1. 開啟 Visual Studio 2017。

2. 從頂端功能表列中，選擇 [檔案]  > [新增]  > [專案]  。

3. 在 [新增專案]  對話方塊的左窗格中，依序展開 [Visual C#]  和 [Web]  ，然後選擇 [.NET Core]  。 在中間窗格中，選擇 [ASP.NET Core Web 應用程式]  。 接著將檔案命名為 *MyCoreApp*，然後選擇 [確定]  。

   ![Visual Studio IDE 的 [新增專案] 對話方塊中的 ASP.NET Core Web 應用程式專案範本](media/csharp-aspnet-choose-template-name-razor-mycoreapp-file.png)

### <a name="add-a-workload-optional"></a>新增工作負載 (選擇性)

如果您看不到 [ASP.NET Core Web 應用程式]  專案範本，則其取得方式是新增 [ASP.NET 與網頁程式開發]  工作負載。 您可以使用下列兩種方式的其中一種來新增此工作負載，視電腦上安裝的 Visual Studio 2017 更新而定。

#### <a name="option-1-use-the-new-project-dialog-box"></a>選項 1：使用 [新增專案] 對話方塊

1. 選取 [新增專案]  對話方塊左窗格中的 [開啟 Visual Studio 安裝程式]  連結。 (根據您的顯示設定，您可能必須捲動才能看到它。)

   ![從 [新增專案] 對話方塊中選取 [開啟 Visual Studio 安裝程式] 連結](../media/open-visual-studio-installer-mycoreapp.png)

1. Visual Studio 安裝程式即會啟動。 選擇 [ASP.NET 與網頁程式開發]  工作負載，然後選擇 [修改]  。

   ![Visual Studio 安裝程式中的 .NET Core 跨平台開發工作負載](../media/tutorial-aspnet-workload.png)

   (您可能必須關閉 Visual Studio 才能繼續安裝新的工作負載)。

#### <a name="option-2-use-the-tools-menu-bar"></a>選項 2：使用 [工具] 功能表列

1. 取消 [新增專案]  對話方塊。 然後從功能表列選擇 [工具]   > [取得工具與功能]  。

1. Visual Studio 安裝程式即會啟動。 選擇 [ASP.NET 與網頁程式開發]  工作負載，然後選擇 [修改]  。

   (您可能必須關閉 Visual Studio 才能繼續安裝新的工作負載)。

### <a name="add-a-project-template"></a>新增專案範本

1. 在 [新增 ASP.NET Core Web 應用程式]  對話方塊中，選擇 [Web 應用程式]  專案範本。

1. 確認 [ASP.NET Core 2.1]  出現在頂端的下拉式功能表中。 然後選擇 [確定]  。

   ![新增 ASP.NET Core Web 應用程式對話方塊](media/new-project-csharp-aspnet-razor-web-app.png)

   > [!NOTE]
   > 如果您在頂端的下拉式功能表中沒有看到 **ASP.NET Core 2.1**，請確定您執行的是最新版 Visual Studio。 如需如何更新安裝的詳細資訊，請參閱[將 Visual Studio 更新至最新版本](../../install/update-visual-studio.md)頁面。

::: moniker-end

::: moniker range="vs-2019"

1. 在開始視窗中，選擇 [建立新專案]  。

   ![檢視 [建立新專案] 視窗](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. 在 [建立新專案]  視窗中，在搜尋方塊內輸入或鍵入 *ASP.NET*。 接下來，從語言清單中選擇 **C#** ，然後從平台清單中選擇 **Windows**。

   在您套用語言和平台的篩選後，請選擇 [ASP.NET Core Web 應用程式]  範本，然後選擇 [下一步]  。

   ![為 ASP.NET Core Web 應用程式選擇 C# 範本](./media/vs-2019/csharp-create-new-project-search-aspnet-core-filtered.png)

   > [!NOTE]
   > 如果您沒有看到 [ASP.NET Core Web 應用程式]  範本，可以從 [建立新專案]  視窗加以安裝。 在 [找不到你要尋找的項目嗎?]  訊息中，選擇 [安裝更多工具和功能]  連結。
   >
   > ![[建立新專案] 視窗中「找不到您要尋找的項目嗎?」訊息的 [安裝更多工具和功能] 連結](../../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > 然後，在 Visual Studio 安裝程式中選擇 [ASP.NET 與網頁程式開發]  工作負載。
   >
   > ![Visual Studio 安裝程式中的 .NET Core 跨平台開發工作負載](../../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > 接著，選擇Visual Studio 安裝程式中的 [修改]  按鈕。 如果系統出現提示，請儲存您的工作。 接下來，選擇 [繼續]  以安裝工作負載。 然後，返回這個「[建立專案](#create-a-project)」程序中的第 2 步。

1. 在 [設定新專案]  視窗中，於 [專案名稱]  方塊中鍵入或輸入 *MyCoreApp*。 接著，選擇 [建立]  。

   ![在 [設定新專案] 視窗中，將專案命名為 'MyCoreApp'](./media/vs-2019/csharp-name-your-aspnet-mycoreapp-project.png)

1. 在 [建立新的 ASP.NET Core Web 應用程式]  視窗中，確認頂端的下拉式功能表出現 **ASP.NET Core 2.1**。 然後，請選擇包含範例 Razor Pages 的 [Web 應用程式]  。 接著，選擇 [建立]  。

   ![[建立新的 ASP.NET Core Web 應用程式] 視窗](./media/vs-2019/csharp-create-aspnet-core-razor-pages-app.png)

   Visual Studio 會開啟您的新專案。

::: moniker-end

### <a name="about-your-solution"></a>關於方案

此方案遵循 **Razor 頁面**設計模式。 它和 [Model-View-Controller (MVC)](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x) 設計模式的不同在於它簡化成 Razor 頁面本身即包含模型和控制器程式碼。

## <a name="tour-your-solution"></a>方案導覽

 1. 專案範本會建立具有單一 ASP.NET Core 專案 (名為 _MyCoreApp_) 的方案。 選擇 [方案總管]  索引標籤以檢視其內容。

    ![Visual Studio 中的 ASP.NET 方案總管顯示名為 MyCoreApp 的 Razor Pages 方案](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. 展開 [Pages]  資料夾，然後展開 [About.cshtml]  。

     ![Visual Studio 的 [方案總管] 中的 About.cshtml 檔案](media/csharp-aspnet-razor-solution-explorer-aboutcshtml.png)

 1. 在程式碼編輯器中檢視 **About.cshtml** 檔案。

     ![在 Visual Studio 程式碼編輯器中檢視 About.cshtml 檔案](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code.png)

 1. 選擇 [About.cshtml.cs]  檔案。

     ![在 Visual Studio 程式碼編輯器中選擇 About.cshtml.cs 檔案](media/csharp-aspnet-razor-solution-explorer-aboutcshtmlcs.png)

 1. 在程式碼編輯器中檢視 **About.cshtml.cs** 檔案。

     ![在 Visual Studio 程式碼編輯器中檢視 About.cshtml 檔案](media/csharp-aspnet-razor-aboutcshtmlcs-mycoreapp-code.png)

 1. 專案包含 [wwwroot]  資料夾，即為網站的根資料夾。 展開資料夾可檢視其內容。

     ![Visual Studio 中方案總管的 wwwroot 資料夾](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    您可以直接在想要的路徑中放置靜態網站內容，像是 CSS、影像及 JavaScript 程式庫。

 1. 專案也包含在執行階段管理 Web 應用程式的組態檔。 預設應用程式[設定](/aspnet/core/fundamentals/configuration)是儲存在 *appsettings.json* 中。 不過，您可以使用 *appsettings.Development.json*來覆寫這些設定。 展開 **appsettings.json** 檔案以檢視 **appsettings.Development.json** 檔案。

     ![Visual Studio 中方案總管的組態檔](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>執行、偵錯及進行變更

1. 選擇 IDE 中的 [IIS Express]  按鈕，以偵錯模式建置和執行應用程式 (或者，按下 **F5**，或從功能表列中選擇 [偵錯]   > [開始偵錯]  。)

     ![選取 Visual Studio 中的 [IIS Express] 按鈕](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > 如果您收到錯誤訊息指出「無法連線到網頁伺服器 'IIS Express'」  ，請關閉 Visual Studio，然後使用右鍵或操作功能表中的 [以系統管理員身分執行]  選項來開啟它。 接著，再次執行應用程式。
     >
     > 您也可能會收到訊息，詢問您是否要接受 IIS SSL Express 憑證。 若要在網頁瀏覽器中檢視程式碼，請選擇 [是]  ，如果您收到後續的安全性警告訊息，請再次選擇 [是]  。

1. Visual Studio 會啟動瀏覽器視窗。 您應該會在功能表列中看到 [首頁]  、[關於]  和 [連絡人]  頁面。 (如果沒有看到，請選擇「漢堡」功能表項目來檢視它們)。

    ![在 Web 應用程式的功能表列上選取「漢堡」功能表項目](media/csharp-aspnet-razor-browser-page.png)

1. 從功能表列選擇 [關於]  。

   ![在應用程式的瀏覽器視窗功能表列中選取 [關於]](media/csharp-aspnet-razor-browser-page-about-menu.png)

   其中，瀏覽器中的 [關於]  頁面會呈現 *About.cshtml* 檔案中所設定的文字。

   ![檢視 [關於] 頁面上的文字](media/csharp-aspnet-razor-browser-page-about.png)

1. 返回 Visual Studio，然後按 **Shift+F5**，停止偵錯模式。 這也會關閉瀏覽器視窗中的專案。

1. 在 Visual Studio 中，選擇 [About.cshtml]  。 然後，刪除文字 _additional_，並在其位置新增文字 _file and directory_。

    ![變更 About.cshtml 檔案中的文字](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code-changed.png)

1. 選擇 [About.cshtml.cs]  。 然後，使用下列快速鍵清除檔案頂端的 `using` 指示詞：

   選擇任何呈現灰色的 `using` 指示詞，而且[快速動作燈泡](../../ide/quick-actions.md)會顯示在插入點正下方或左邊界中。 選擇燈泡，然後選擇 [移除不必要的 Using]  。

   ![移除 About.cshtml.cs 檔案中不必要的 Using](media/csharp-aspnet-razor-remove-unnecessary-usings.png)

     Visual Studio 會將不必要的 `using` 指示詞從檔案中刪除。

1. 接下來，在 `OnGet()` 方法中，將主體變更為下列程式碼：

     ```csharp
     public void OnGet()
     {
         string directory = Environment.CurrentDirectory;
     Message = String.Format("Your directory is {0}.", directory);
     }
    ```

1. 請注意，**Environment** 和 **String** 底下會出現兩個波浪底線。 因為這些類型不在範圍內，所以會顯示波浪底線。

   ![OnGet 方法中以波浪底線標示的錯誤](media/csharp-aspnet-razor-add-new-on-get-method.png)

    開啟 [錯誤清單]  工具列，以查看該處所列的相同錯誤 (如果您看不到 [錯誤清單]  工具列，請從頂端功能表列中選擇 [檢視]   > [錯誤清單]  )。

   ![Visual Studio 中的錯誤清單](media/csharp-aspnet-razor-error-list.png)

1. 讓我們來修正此錯誤。 在程式碼編輯器中，將游標放在包含錯誤的任一行上，然後選擇左邊界的快速動作燈泡。 接著，從下拉式功能表中，選擇 **using System;** ，以將此指示詞新增至檔案頂端並解決錯誤。

   ![新增 "using System;" 指示詞](media/csharp-aspnet-razor-add-usings.png)

1. 按下 **Ctrl**+**S** 以儲存變更，然後按下 **F5**，在網頁瀏覽器中開啟您的專案。

1. 在網站頂端，選擇 [關於]  來檢視您所做的變更。

   ![檢視包含您所做變更的 [關於] 頁面](media/csharp-aspnet-razor-browser-page-about-changed.png)

1. 關閉網頁瀏覽器，按下 **Shift**+**F5** 以停止偵錯模式，然後關閉 Visual Studio。

## <a name="quick-answers-faq"></a>常見問題集快問快答

以下提供常見問題集的快問快答，來強調幾個重要概念。

### <a name="what-is-c"></a>什麼是 C#?

[C#](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework) 是一種類型安全和物件導向程式設計語言，設計成穩固且易於了解。

### <a name="what-is-aspnet-core"></a>什麼是 ASP.NET Core？

ASP.NET Core 是一個開放原始碼和跨平台架構，可建置網際網路連線應用程式，例如 Web 應用程式和服務。 ASP.NET Core 應用程式可以執行於 .NET Core 或 .NET Framework。 您可以在 Windows、Mac 和 Linux 上跨平台開發和執行 ASP.NET Core 應用程式。 ASP.NET Core 是 [GitHub](https://github.com/aspnet/home) 上的開放原始碼。

### <a name="what-is-visual-studio"></a>什麼是 Visual Studio？

Visual Studio 是開發人員生產力工具的整合式開發套件。 請將它視為可用來建立程式和應用程式的程式。

## <a name="next-steps"></a>後續步驟

恭喜您完成此教學課程！ 我們希望您更了解 C#、ASP.NET Core 和 Visual Studio IDE。 若要深入了解如何使用 C# 和 ASP.NET 建立 Web 應用程式或網站，請繼續進行下列教學課程：

> [!div class="nextstepaction"]
> [使用 ASP.NET Core 建立 Razor 頁面 Web 應用程式](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)

## <a name="see-also"></a>另請參閱

[使用 Visual Studio 將 Web 應用程式發行到 Azure App Service](../../deployment/quickstart-deploy-to-azure.md)
