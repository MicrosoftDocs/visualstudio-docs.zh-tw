---
title: Visual Studio 中的 C# 和 ASP.NET Core 使用者入門 | Microsoft Docs
ms.custom: ''
ms.date: 12/11/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 0835c2e33dcd3c8ffa2556a406cdbd8e2d2ff265
ms.sourcegitcommit: a0a49cceb0fdc1465ddf76d131c6575018b628b8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2018
---
# <a name="getting-started-with-c-and-aspnet-in-visual-studio"></a>Visual Studio 中的 C# 和 ASP.NET 使用者入門
在利用使用 Visual Studio 的 ASP.NET Core 進行 C# 開發的這個教學課程中，您將建立 C# ASP.NET Core Web 應用程式、新增其程式碼、探索 IDE 的一些功能，以及執行應用程式。

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)頁面免費進行安裝。

## <a name="before-you-begin"></a>開始之前
以下快速常見問題集介紹一些重要概念。
### <a name="what-is-c"></a>什麼是 C#?
[C#](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework) 是一種類型安全和物件導向程式設計語言，設計成穩固且易於了解。
### <a name="what-is-aspnet-core"></a>什麼是 ASP.NET Core？
ASP.NET Core 是一個開放原始碼和跨平台架構，可建置網際網路連線應用程式，例如 Web 應用程式和服務。 ASP.NET Core 應用程式可以執行於 .NET Core 或 .NET Framework。 您可以在 Windows、Mac 和 Linux 上跨平台開發和執行 ASP.NET Core 應用程式。 ASP.NET Core 是 [GitHub](https://github.com/aspnet/home) 上的開放原始碼。
### <a name="what-is-visual-studio"></a>什麼是 Visual Studio？
Visual Studio 是開發人員生產力工具的整合式開發套件。 請將它視為可用來建立程式和應用程式的程式。  

## <a name="start-developing"></a>開始進行開發
準備好開始進行開發了嗎？ 讓我們開始吧！

### <a name="create-a-project"></a>建立專案
首先，您會建立 ASP.NET Core 專案。 在您新增任何項目之前，專案類型會隨附您需要的所有範本檔案。

1. 開啟 Visual Studio 2017。

2. 從頂端功能表列中，選擇 [檔案] > [新增] > [專案]。

3. 在 [新增專案] 對話方塊的左窗格中，依序展開 [Visual C#] 和 [Web]，然後選擇 [.NET Core]。 在中間窗格中，選擇 [ASP.NET Web 應用程式]，並將檔案命名為 *MyCoreApp*，然後選擇 [確定]。   

   ![Visual Studio IDE 的 [新增專案] 對話方塊中的 ASP.NET Core Web 應用程式專案範本](../ide/media/new-project-csharp-aspnet-mycoreapp.png)

#### <a name="add-a-workload-optional"></a>新增工作負載 (選擇性)
如果您看不到 [ASP.NET Core Web 應用程式] 專案範本，則其取得方式是新增 [ASP.NET 與網頁程式開發] 工作負載。 您可以使用下列兩種方式的其中一種來新增此工作負載，視電腦上安裝的 Visual Studio 2017 更新而定。

##### <a name="option-1-use-the-new-project-dialog-box"></a>選項 1：使用 [新增專案] 對話方塊
1. 按一下 [新增專案] 對話方塊左窗格中的 [開啟 Visual Studio 安裝程式] 連結。

  ![按一下 [新增專案] 對話方塊中的 [開啟 Visual Studio 安裝程式] 連結](../ide/media/vs-open-visual-studio-installer-generic.png)

2. Visual Studio 安裝程式即會啟動。 選擇 [ASP.NET 與網頁程式開發] 工作負載，然後選擇 [修改]。

   ![Visual Studio 安裝程式中的 .NET Core 跨平台開發工作負載](../ide/media/asp-dot-net-web-dev-workload.png)

##### <a name="option-2-use-the-tools-menu-bar"></a>選項 2：使用 [工具] 功能表列
1. 請取消 [新增專案] 對話方塊，然後從頂端功能表列中選擇 [工具] > [Get Tools and Features] (取得工具和功能)。

2. Visual Studio 安裝程式即會啟動。 選擇 [ASP.NET 與網頁程式開發] 工作負載，然後選擇 [修改]。   

#### <a name="add-a-project-template"></a>新增專案範本
1. 在 [新增 ASP.NET Core Web 應用程式] 對話方塊中，選擇 [Web 應用程式 (模型檢視控制器)] 專案範本。  

2. 從頂端下拉式功能表中，選取 [ASP.NET Core 2.0]。 (如果您在清單中看不到 [ASP.NET Core 2.0]，請遵循應該出現在接近對話方塊頂端之黃色列中的 [下載] 連結來進行安裝)。選擇 [ **確定**]。

   ![新增 ASP.NET Core Web 應用程式對話方塊](../ide/media/new-project-csharp-aspnet-web-app-mvc.png)

### <a name="about-your-solution"></a>關於方案
此方案遵循模型檢視控制器 (MVC) 架構模式，以將一個應用程式劃分成三個主要元件：

* **模型**包含代表應用程式資料的類別。 模型類別使用驗證邏輯對該資料強制執行商務規則。 通常，模型物件會在資料庫中擷取並儲存模型狀態。
* **檢視**是顯示應用程式使用者介面 (UI) 的元件。 一般而言，此 UI 會顯示模型資料。
* **控制器**包含可處理瀏覽器要求的類別。 它們會擷取模型資料，並呼叫傳回回應的檢視範本。 在 MVC 應用程式中，檢視只會顯示資訊；控制器則會處理和回應使用者輸入和互動。

MVC 模式可協助您建立比傳統整合型應用程式更容易測試和更新的應用程式。

### <a name="tour-your-solution"></a>方案導覽
1. 專案範本會建立具有單一 ASP.NET Core 專案 (名為 **MyCoreApp**) 的方案。 展開專案節點，以公開其內容。

    ![Visual Studio 中的 ASP.NET 方案總管](../ide/media/csharp-aspnet-solution-explorer-mycoreapp.png)

1. 從 **Controllers** 資料夾中，開啟 **HomeController.cs** 檔案。

      ![Visual Studio 中方案總管的 HomeController.cs 檔案](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

2. 檢視 **HomeController.cs**

  ![Visual Studio 程式碼視窗中的 HomeController.cs](../ide/media/csharp-aspnet-home-controller-code.png)

4. 專案也會有 **Views** 資料夾，內含對應至每個控制器的其他資料夾 (以及 [共用] 檢視的資料夾)。 例如，**/Home/About** 路徑的檢視 CSHTML 檔案 (副檔名為 HTML) 是在 **Views/Home/About.cshtml** 中。 開啟該檔案。

  ![Visual Studio 中方案總管的 About.cshtml 檔案](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

5. 此 CSHTML 檔案使用 Razor 語法，根據標準標記與內嵌 C# 的組合來呈現 HTML。

  ![Visual Studio 程式碼視窗中的 About.cshtml](../ide/media/csharp-aspnet-about-cshtml-code.png)

 >[!NOTE]
 > 若要深入了解此作業，請參閱[使用 Razor 語法的 C# 和 ASP.NET 使用者入門](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c)頁面。

6. 方案也包含為網站根資料夾的 **wwwroot** 資料夾。 部署網站時，您可以將 CSS、影像和 JavaScript 程式庫這類靜態網站內容直接放在您要放置它們的路徑上。

 ![Visual Studio 中方案總管的 wwwroot 資料夾](../ide/media/csharp-aspnet-solution-wwwroot.png)

7. 另外還有各種組態檔可用來在執行階段管理專案、其專案和應用程式。 例如，預設應用程式[組態](/aspnet/core/fundamentals/configuration)會儲存在 **appsettings.json** 中。 不過，您可以根據每個環境來覆寫其中一部分/所有設定，例如，透過提供**開發**環境的 **appsettings.Development.json** 檔案。

 ![Visual Studio 中方案總管的組態檔](../ide/media/csharp-aspnet-solution-explorer-config-files.png)

## <a name="run-and-debug-the-application"></a>執行和偵錯應用程式

1. 選擇 IDE 中的 [IIS Express] 按鈕，以偵錯模式建置和執行應用程式  (或者，按 **F5**，或從功能表列中選擇 [偵錯] > [開始偵錯])。

  ![按一下 Visual Studio 中的 [IIS Express] 按鈕](../ide/media/csharp-aspnet-iis-express-button.png)

  > [!NOTE]
  > 如果您收到錯誤訊息指出「無法連線到網頁伺服器 'IIS Express'」，請關閉 Visual Studio，然後使用右鍵或操作功能表中的 [以系統管理員身分執行] 選項來開啟它。 接著，再次執行應用程式。

1. Visual Studio 會啟動瀏覽器視窗。 選取 [關於]。

 ![選取應用程式的瀏覽器視窗中的 [關於]](../ide/media/csharp-aspnet-browser-page.png)

 其中，瀏覽器中的 [關於] 頁面會呈現 HomeController.cs 檔案中所設定的文字。

   ![檢視 [關於] 頁面上的文字](../ide/media/csharp-aspnet-browser-page-about.png)

1. 將瀏覽器視窗保持開啟，並回到 Visual Studio。 開啟 **Controllers/HomeController.cs** (如果尚未開啟)。

 ![從 Visual Studio 的方案總管中開啟 HomeController.cs 檔案](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

1. 在 **About** 方法的第一行中，設定中斷點。 若要這麼做，請按一下邊界，或在該行設定游標，然後按 **F9**。

  這行設定 **ViewData** 集合中的一些資料，而這些資料會呈現在 **Views/Home/About.cshtml** 的 CSHTML 頁面中。

 ![在 About.cshtml 的 About 方法的第一行中，設定中斷點。  ](../ide/media/csharp-aspnet-home-controller-code-set-breakpoint.png)

1. 回到瀏覽器，並重新整理 [關於] 頁面。 這將會在 Visual Studio 中觸發中斷點。

1. 在 Visual Studio 中，將滑鼠移至 **ViewData** 成員上方，以檢視其資料。

 ![檢視 About 方法的 ViewData 成員以查看詳細資訊](../ide/media/csharp-aspnet-home-controller-view-breakpoint-info.png)

1. 使用您用來新增應用程式中斷點的相同方法來移除應用程式中斷點。

1. 開啟 **Views/Home/About.cshtml**。

 ![在方案總管中選取 About.cshtml](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

1. 將文字 **"additional"** 變更為 **"changed"**，並儲存檔案。

 ![將文字 "additional" 變更為文字 "changed"](../ide/media/csharp-aspnet-about-cshtml-code-change.png)

1. 回到瀏覽器視窗，以查看更新的文字  (如果您看不到所變更的文字，請重新整理瀏覽器)。

  ![重新整理瀏覽器視窗，以查看變更的文字](../ide/media/csharp-aspnet-browser-page-about-changed.png)

1. 從工具列中選擇 [停止偵錯] 按鈕，以停止偵錯  (或者，按 **Shift**+**F5**，或從功能表列中選擇 [偵錯] > [開始偵錯])。

 ![按一下工具列上的 [停止偵錯] 按鈕](../ide/media/csharp-aspnet-stop-debugging.png)

## <a name="next-steps"></a>後續步驟

恭喜您完成此教學課程！ 我們希望您更了解 C#、ASP.NET Core 和 Visual Studio IDE。 若要更深入了解，請繼續下列教學課程。

 > [!div class="nextstepaction"]
 > [ASP.NET Core MVC 與 Visual Studio 使用者入門](/aspnet/core/tutorials/first-mvc-app/start-mvc?tabs=aspnetcore2x)
