---
title: Visual Studio 2017 的概觀
ms.date: 02/05/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- MSDNSTART
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0fdc6acd2c14331d34ccb3f3435b1ee5fcc44a14
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
---
# <a name="visual-studio-ide-overview"></a>Visual Studio IDE 概觀

Visual Studio 是一個互動式開發環境 (IDE)；這是一個有創意的啟動控制板，可供您用來檢視和編輯幾乎任何類型的程式碼，然後偵錯、組建及發佈適用於 Android、iOS、Windows、Web 和雲端的應用程式。 針對 Mac 和 Windows 都有適用的版本。 本主題將為您介紹 Visual Studio IDE 的功能。 我們將逐步解說您可以運用 Visual Studio 來進行的一些操作及如何安裝和使用它、建立簡單的專案、取得進行程式碼偵錯和部署時的指標，以及介紹各種工具視窗。

## <a name="what-can-you-do-with-the-visual-studio-ide"></a>您可以運用 Visual Studio IDE 來做什麼？

您是否想要建立適用於 Android 手機的應用程式？ 您可以辦得到。 使用 C++ 來建立最頂尖的遊戲，如何？ 您也可以辦得到，而且還能做得更多。 Visual Studio 可提供範本來協助您建立網站、遊戲、傳統型應用程式、行動應用程式、適用於 Office 的應用程式等等。

![Visual Studio 專案](../ide/media/VSIDE_Tour_Projects_List.png)

或者，您可以直接開啟從幾乎任何來源取得的一些程式碼並開始工作。 在 GitHub 上看到您喜歡的專案嗎？ 只要直接複製該儲存機制、在 Visual Studio 中開啟它，然後開始撰寫程式碼即可！

### <a name="create-mobile-apps"></a>建立行動應用程式

您可以使用 C# 和 Xamarin 或 Visual C++ 為不同的平台建立原生行動應用程式，或是使用 JavaScript 搭配 Apache Cordova 來建立混合式應用程式。 您可以為 Unity、Unreal、DirectX、Cocos 等撰寫行動裝置遊戲。 Visual Studio 包含一個 Android 模擬器，可協助您執行 Android 應用程式及針對這些應用程式進行偵錯。

您可以藉由建立 Azure 應用程式服務，將雲端的強大功能運用在您的行動應用程式上。 Azure 應用程式服務可讓您的應用程式將資料儲存在雲端、安全地驗證使用者，以及自動相應增加或減少其資源以配合您應用程式和業務的需求。 若要深入了解，請參閱[行動應用程式開發](https://www.visualstudio.com/vs/mobile-app-development/)。

### <a name="create-cloud-apps-for-azure"></a>建立適用於 Azure 的雲端應用程式

Visual Studio 提供一套工具，可讓您輕鬆建立由 Microsoft Azure 提供技術之支援雲端的應用程式。 您可以直接從 IDE，在 Microsoft Azure 上設定、建置、偵錯、封裝及部署應用程式和服務。 若要取得「適用於 .NET 的 Azure 工具」，請在安裝 Visual Studio 時，選取 [Azure 開發] 工作負載。 如需詳細資訊，請參閱 [Visual Studio Tools for Azure](https://www.visualstudio.com/vs/azure-tools/)。

您可以使用「已連線的服務」，將 Azure 服務運用到您的應用程式，例如：

- [Azure 行動服務](http://azure.microsoft.com/documentation/services/mobile-services/)

- [Azure 儲存體](http://azure.microsoft.com/documentation/services/storage/)

[HockeyApp (英文)](https://www.visualstudio.com/hockey-app/) 可協助您散發搶鮮版 (Beta)、收集即時當機報告，以及取得實際使用者的意見反應。 此外，您可以將 Office 365 REST API 與您自己的應用程式進行整合，以連接儲存在雲端的資料。 如需詳細資訊，請參閱[下列 GitHub 範例](https://github.com/OfficeDev/?utf8=%E2%9C%93&query=o365)。

[Application Insights](https://marketplace.visualstudio.com/items?itemName=VisualStudioOnlineApplicationInsights.application-insights) 可協助您偵測和診斷應用程式和 Web 服務中的品質問題。 Application Insights 也可協助您了解使用者實際上使用應用程式進行何種作業，以將使用者體驗最佳化。

### <a name="create-apps-for-the-web"></a>建立適用於 Web 的應用程式

Web 推動我們的現代化世界，而 Visual Studio 則可協助您撰寫適用於 Web 的應用程式。 您可以使用 ASP.NET、Node.js、Python、JavaScript 及 TypeScript 來建立 Web 應用程式。 Visual Studio 了解 Angular、jQuery、Express 等 Web 架構。 ASP.NET Core 和 .NET Core 可在 Windows、Mac 及 Linux 作業系統上執行。 [ASP.NET Core](http://www.asp.net/core/overview) 是 MVC、WebAPI 及 SignalR 的重大更新，可以在 Windows、Mac 及 Linux 上執行。  ASP.NET Core 是全新的設計，提供您可組合的簡式 .NET 堆疊，讓您建置現代化的雲端架構 Web 應用程式和服務。

如需詳細資訊，請參閱[新式 Web 工具](https://www.visualstudio.com/vs/modern-web-tooling/)。

### <a name="build-cross-platform-apps-and-games"></a>建置跨平台應用程式和遊戲

您可以使用 Visual Studio 建置 macOS、Linux、Windows、Android、iOS 和其他行動裝置用的應用程式和遊戲。

- 建置在 Windows、macOS 和 Linux 上執行的 [.NET Core](/dotnet/core/) 應用程式。

- 使用 [Xamarin](https://developer.xamarin.com/guides/cross-platform/windows/visual-studio/) 以 C# 和 F# 建置 iOS、Android 和 Windows 用的行動應用程式。

- 透過 [Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/)，使用標準 Web 技術 &mdash;HTML、CSS 和 JavaScript&mdash; 建置 iOS、Android 和 Windows 用的行動應用程式。

- 使用 [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) 以 C# 建置 2D 和 3D 遊戲。

- 以[適用於跨平台開發的 C++](../cross-platform/visual-cpp-for-cross-platform-mobile-development.md) 建置 iOS、Android 和 Windows 裝置用的原生 C++ 應用程式，以及在為 iOS、Android 和 Windows 建置的程式庫中共用通用程式碼。

- 使用 [Android 模擬器](../cross-platform/visual-studio-emulator-for-android.md)部署、測試及偵錯 Android 應用程式。

Visual Studio 還可協助您進行更多的工作。 如需更完整的清單，請參閱 [www.visualstudio.com](https://www.visualstudio.com/vs/)。

## <a name="install-the-visual-studio-ide"></a>安裝 Visual Studio IDE

若要開始，請下載 Visual Studio 並將它安裝在您的系統上。 您可以從 [Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) 下載它。

Visual Studio 現在比以往更輕巧！ 模組安裝程式可讓您選擇並安裝「工作負載」，這些通常是您慣用的程式設計語言或平台所需的幾組功能。 此策略有助於將 Visual Studio 安裝項的資源使用量降到比以往低，這意謂著它的安裝和更新速度也更快。 除改善安裝效能，Visual Studio 2017 的 IDE 啟動和解決方案載入時間也較短。

若要深入了解如何在您的系統上設定 Visual Studio，請參閱 [Install Visual Studio 2017](../install/install-visual-studio.md)。 若要遵循[建立程式](#create-a-program)的步驟，請務必在安裝期間選取 **.NET Core 跨平台開發**工作負載。

![Visual Studio 安裝程式](../ide/media/overview-net-core-workload.png)

## <a name="sign-in"></a>登入

當您第一次啟動 Visual Studio 時，可以視需要使用您的 Microsoft 帳戶或是工作或學校帳戶來登入。 登入可讓您跨多個裝置同步 Visual Studio 設定，例如視窗配置。 此外，還可自動將您連線到您可能需要的服務，例如 Azure 訂用帳戶和 [Visual Studio Team Services](/vsts/)。

## <a name="create-a-program"></a>建立程式

有一個了解東西的好方法，就是去使用它！ 讓我們來深入探討並建立一個新的簡單程式。

1. 開啟 Visual Studio。 在功能表上，選擇 [檔案] > [新增] > [專案]。

  ![功能表列上的 [檔案] > [新增專案]](../ide/media/VSIDE_Tour_NewProject1.png)

1. [新增專案] 對話方塊會顯示數個專案範本。 選擇 [Visual C#] 下的 [.NET Core] 類別，然後選擇 [主控台應用程式 (.NET Core)] 範本。 在 [名稱] 文字方塊中，鍵入 "HelloWorld"。 選取 [確定] 按鈕。

  ![.NET Core 應用程式範本](../ide/media/overview-new-project-dialog.png)

  > [!NOTE]
  > 如果您未看到 [.NET Core] 類別，則需要安裝 [.NET Core 跨平台開發] 工作負載。 若要安裝，請選擇 [新增專案] 對話方塊左下角的 [開啟 Visual Studio 安裝程式] 連結。 在 [Visual Studio 安裝程式] 開啟後，請向下捲動並選取 [.NET Core 跨平台開發] 工作負載，然後選擇 [修改]。

   Visual Studio 使用範本建立專案。 其為簡單的 "Hello World" 應用程式，會呼叫 <xref:System.Console.WriteLine> 方法來顯示常值字串 "Hello World!" 。

1. 不久後，您應該就會看到類似如下所示的螢幕擷取畫面：

  ![Visual Studio IDE](../ide/media/overview-ide-console-app.png)

   您應用程式的 C# 程式碼會顯示在編輯器視窗中，其占據了大部分的空間。 請注意，系統會將程式碼語法自動標示色彩，以表示不同的程式碼類型，例如關鍵字或類型。 此外，程式碼中的垂直小虛線會指出那些大括號彼此成對，而行號則可協助您稍後找出程式碼。 您可以選擇帶方框的小負號來摺疊或展開程式碼。 此程式碼大綱功能可讓您隱藏您不需要的程式碼，有助於讓畫面變得較為簡潔。

   專案檔會列在右邊稱作 [方案總管] 的視窗中。

  ![具有紅色方塊的 Visual Studio IDE](../ide/media/overview-ide-console-app-red-boxes.png)

  還有其他可用的功能表和工具視窗，但讓我們目前先繼續進行操作。

1. 現在，啟動應用程式。 您可以藉由從功能表列上的 [偵錯] 功能表選擇 [啟動但不偵錯]，來執行此動作。 您也可以按 **Ctrl**+**F5**。

  ![[偵錯] > [啟動但不偵錯] 功能表](../ide/media/overview-start-without-debugging.png)

  Visual Studio 會建置應用程式，然後主控台視窗會開啟並顯示 "Hello World!"。 您現在已有一個執行中的應用程式！

  ![主控台視窗](../ide/media/overview-console-window.png)

1. 若要關閉主控台視窗，請在鍵盤上按下任意鍵。

1. 讓我們將一些其他程式碼新增至應用程式。 在 `Console.WriteLine("Hello World!");` 行前新增下列 C# 程式碼：

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   此程式碼會在主控台中顯示「What is your name?」， 然後等待使用者輸入某些文字並按下 **ENTER** 鍵。

1. 現在將 `Console.WriteLine("Hello World!");` 行變更為下列程式碼：

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. 選取 偵錯 > 啟動但不偵錯 或按 **Ctrl**+**F5**，再次執行應用程式。

   Visual Studio 會重建應用程式，然後主控台視窗會開啟並提示您輸入您的名稱。

1. 請在主控台視窗中輸入您的名稱，並按下 **ENTER**。

   ![主控台視窗輸入](media/overview-console-input.png)

1. 按任意鍵以關閉主控台視窗。

## <a name="debug-test-and-improve-your-code"></a>偵錯、測試及改善您的程式碼

沒有任何程式碼會始終以完美狀態執行。 當您撰寫程式碼時，必須執行它並測試它，以找出錯誤 (bug) 及改善效能。 Visual Studio 先進的偵錯系統讓您可對在遠端裝置或模擬器 (例如 [Android 裝置的模擬器](../cross-platform/visual-studio-emulator-for-android.md)) 上執行的程式碼進行偵錯。 您可以以一次一個陳述式的方式逐步偵錯程式碼，並一邊檢查變數。 您可以將中斷點設定成只在指定的條件為 true 時才叫用。 您可以在程式碼執行時，監視變數的值等等。 這些全部都可以在程式碼編輯器本身中管理，如此您就不需要離開您的程式碼。 如需有關 Visual Studio 中之 偵錯的更多詳細資料，請參閱[偵錯工具功能導覽](../debugger/debugger-feature-tour.md)。

在測試方面，Visual Studio 提供單元測試、IntelliTest、負載和效能測試等。 若要深入了解測試，請參閱[測試工具與案例](../test/developer-testing-scenarios.md)。 若要深入了解如何改善您應用程式的效能，請參閱[分析功能導覽](../profiling/profiling-feature-tour.md)。

## <a name="deploy-your-finished-application"></a>部署已完成的應用程式

當您的應用程式已準備就緒而可部署到使用者或客戶時，Visual Studio 會提供工具來執行部署，不論您是要部署到 Microsoft Store、SharePoint 網站，還是透過 InstallShield 或 Windows Installer 技術來部署，都可以。 全部都可透過 IDE 來存取。 如需詳細資訊，請參閱[部署應用程式、服務和元件](../deployment/deploying-applications-services-and-components.md)。

## <a name="quick-tour-of-the-ide"></a>IDE 快速導覽

為了提供您一個概要的 Visual Studio 視覺總覽，下圖顯示已開啟一個專案及數個您最可能使用之重要工具視窗的 Visual Studio：

- [方案總管](../ide/solutions-and-projects-in-visual-studio.md)可讓您檢視、瀏覽及管理您的程式碼檔案。 方案總管透過將程式碼的檔案分組到方案和專案，以協助組織程式碼。

- [編輯器](../ide/writing-code-in-the-code-and-text-editor.md)視窗 (您可能大多數時間都花費在這裡) 會顯示程式碼，並可讓您編輯原始程式碼及設計 UI。

- [[輸出]](../ide/reference/output-window.md) 視窗就是 Visual Studio 傳送其通知的位置，例如偵錯和錯誤訊息、編譯器警告、發行狀態訊息等。 每個訊息來源都有自己的索引標籤。

- [Team Explorer (VSTS)](/vsts/user-guide/work-team-explorer) 可讓您追蹤工作項目，並使用版本控制技術 (例如 [Git](https://git-scm.com/) 和 [Team Foundation 版本控制 (TFVC)](/vsts/tfvc/overview)) 與其他人共用程式碼。

- [Cloud Explorer](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) 可讓您檢視和管理 Azure 資源，例如虛擬機器、資料表、SQL 資料庫等。 如果特定作業需要 Azure 入口網站，Cloud Explorer 會提供連結，將您帶到 Azure 入口網站中您所需前往的位置。

![Visual Studio IDE](../ide/media/visualstudioide.png)

以下是 Visual Studio 中一些其他常見的生產力功能：

- [快速啟動](../ide/reference/quick-launch-environment-options-dialog-box.md)搜尋方塊是一個可讓您在 Visual Studio 中快速找到所需項目的絕佳方式。 只要開始輸入您要尋找的任何項目的名稱，Visual Studio 會列出結果將您引導至您確實想要去的地方。 [快速啟動] 也會顯示連結，這些連結可啟動任何工作負載或個別元件的 Visual Studio 安裝程式。

  ![[快速啟動] 搜尋方塊](../ide/media/VSIDE_Tour_QuickLaunch.png)

- [重構](../ide/refactoring-in-visual-studio.md)包含一些作業，例如智慧型的變數重新命名、將選取的多行程式碼移動到個別函式、將程式碼移到其他位置、重新排序函式參數等等。

 ![重構](../ide/media/VSIDE_refactor.png)

- **IntelliSense** 為一種涵蓋一組常用功能的概括性詞彙，會直接在編輯器中顯示有關您程式碼的類型資訊，而在某些情況下會為您撰寫一些程式碼。 就像內嵌在編輯器中的基本文件，讓您無需在個別的 [說明] 視窗中查閱類型資訊。 IntelliSense 功能會因語言而異。 如需詳細資訊，請參閱 [C# IntelliSense](../ide/visual-csharp-intellisense.md)、[Visual C++ IntelliSense](../ide/visual-cpp-intellisense.md)、[JavaScript IntelliSense](../ide/javascript-intellisense.md) 和 [Visual Basic IntelliSense](../ide/visual-basic-specific-intellisense.md)。 下圖顯示一些可用的 IntelliSense 功能：

  ![Visual Studio 成員清單](../ide/media/vs2017_Intellisense.png)

- 「波浪線」是紅色的波浪底線，可在您輸入程式碼時，針對錯誤或潛在的問題即時提出警示。 這可讓您立即修正它們，而不需等到編譯或執行階段才發現錯誤。 如果您將滑鼠停留在波浪線，則您會看到有關此錯誤的其他資訊。 左邊界也可能會出現燈泡與修正錯誤的建議。 如需詳細資訊，請參閱[快速動作](../ide/quick-actions.md)。

 ![波浪線](../ide/media/vs2017_squiggle.png)

- 您可以在文字編輯器操作功能表上開啟[呼叫階層](../ide/reference/call-hierarchy.md)視窗，以顯示呼叫插入點 (caret) 底下方法及被該方法呼叫的方法。

 ![呼叫階層視窗](../ide/media/VSIDE_call_hierarchy.png)

- [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) 可讓您尋找程式碼、已連結的 Bug、工作項目、程式碼檢閱和單元測試的參考和變更，而不需離開編輯器。

 ![CodeLens](../ide/media/codelensoverview.png)

- [[查看定義]](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) 視窗會顯示方法或類型的定義內嵌，而不用離開您目前的內容。

 ![查看定義](../ide/media/VSIDE_peek_definition.png)

- [移至定義]  內容功能表選項會讓您直接進入定義函式或物件的位置。 以滑鼠右鍵在編輯器中按一下，還有其他巡覽命令可供使用。

 ![移至定義](../ide/media/VSIDE_go_to_definition.png)

## <a name="manage-your-source-code-and-collaborate-with-others"></a>管理您的原始程式碼並與其他人共同作業

您可以在任何提供者所裝載的 Git 儲存機制 (包括 GitHub) 中管理您的原始程式碼。 或是使用 [Visual Studio Team Services (VSTS)](/vsts/index) 來一邊管理整個專案的程式碼，一邊管理錯誤 (bug) 與工作項目。 若要深入了解如何在 Visual Studio 中使用 Team Explorer 來管理 Git 存放庫，請參閱 [Git 與 Team Services (VSTS) 使用者入門](/vsts/git/gitquickstart?tabs=visual-studio)。 Visual Studio 也有其他內建原始檔控制功能。 如需詳細資訊，請參閱 [New Git Features in Visual Studio 2017 (blog)](https://blogs.msdn.microsoft.com/visualstudioalm/2017/03/06/new-git-features-in-visual-studio-2017/) (Visual Studio 2017 的新 Git 功能 (部落格))。

Visual Studio Team Services 是一項雲端式服務，可用來裝載軟體專案及允許以小組進行共同作業。 VSTS 支援 Git 和 Team Foundation 原始檔控制系統，以及 Scrum、CMMI 和 Agile 開發方法。 Team Foundation 版本控制 (TFVC) 使用單一且集中式伺服器儲存機制來追蹤和版本化檔案。 在其他開發人員取得最新變更的地方，一律將本機變更簽入中央伺服器。

Team Foundation Server (TFS) 是 Visual Studio 的應用程式生命週期管理中樞。 其可讓所有人使用單一方案參與開發流程。 TFS 也適合用來管理異質小組和專案

如果您在網路上有 Visual Studio Team Services 帳戶或 Team Foundation Server，便可以透過 Visual Studio 中的 [Team Explorer] 視窗與其連接。 在這個視窗中，您可以在原始檔控制簽入或簽出程式碼、管理工作項目、啟動建置和存取小組聊天室及工作區。 您可以從 [快速啟動] 方塊開啟 [Team Explorer]，也可以從主功能表的 [檢視] > [Team Explorer] 或從 [小組] > [管理連線] 來開啟它。

下圖顯示裝載於 VSTS 中之方案的 [Team Explorer] 視窗。

![Visual Studio Team Explorer](../ide/media/vs2017_teamexplorer.png)

您也可以自動化建置流程，來建置您小組開發人員已簽入版本控制的程式碼。 例如，您可以每晚或在每次簽入程式碼時建置一或多個專案。 如需詳細資訊，請參閱[建置及發行 (VSTS 和 TFS)](/vsts/build-release/index)。

## <a name="connect-to-services-databases-and-cloud-based-resources"></a>連接至服務、資料庫及雲端式資源

雲端對現今的線上世界至關重要，而 Visual Studio 則提供您運用雲端的方法。 例如，「已連接服務」功能可讓您將應用程式連接至服務。 此外，您的應用程式還可以使用它來將其資料儲存在 Azure 儲存體上。

![已連接服務](../ide/media/VSIDE_Tour_Connected_Services.png)

選擇 [已連線的服務] 頁面上的服務會啟動 [已連線的服務精靈]，此精靈會設定您的專案並下載必要的 NuGet 套件，以協助您開始編寫服務的程式碼。

您可以在 Visual Studio 內使用 [Cloud Explorer](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) 來檢視和管理 Azure 型雲端資源。 Cloud Explorer 會顯示在您所登入 Azure 訂用帳戶下管理之所有帳戶中的 Azure 資源。 您可以在 Visual Studio 安裝程式中選取 **Azure 開發**工作負載，來取得 **Cloud Explorer**。

![Cloud Explorer](../ide/media/VSIDE_CloudExplorer.png)

[伺服器總管] 可協助您在本機、從遠端瀏覽和管理 Azure、Salesforce.com、Office 365 及網站上的 SQL Server 執行個體和資產。 若要開啟 [伺服器總管]，請選擇主功能表上的 [檢視] > [伺服器總管]。 如需有關使用 [伺服器總管] 的詳細資訊，請參閱[新增連線 (英文)](../data-tools/add-new-connections.md)。

[SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt) 是一個適用於 SQL Server、Azure SQL Database 及「Azure SQL 資料倉儲」的強大開發環境。 它可讓您建置、偵錯、維護及重構資料庫。 您可以使用資料庫專案，或直接使用內部或外部所連接的資料庫執行個體。

Visual Studio 中的 [SQL Server 物件總管] 提供與 SQL Server Management Studio 類似的資料庫物件檢視。 [SQL Server 物件總管] 可讓您執行輕型的資料庫管理和設計工作，包括編輯資料表資料、比較結構描述、直接從 [SQL Server 物件總管] 使用內容功能表來執行查詢等。

![SQL Server 物件總管](../ide/media/vs2015_sqlobjectexplorer.png)

## <a name="extend-visual-studio"></a>擴充 Visual Studio

如果 Visual Studio 沒有您所需的確切功能，您可以新增功能！ 您可以根據您的工作負載和風格將 IDE 個人化、針對尚未與 Visual Studio 整合的外部工具新增支援，以及修改現有的功能以提升您的生產力。 若要尋找最新版本的 Visual Studio 擴充性工具 (VS SDK)，請參閱 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。

您可以使用 .NET 編譯器平台 ("Roslyn") 來撰寫自己的程式碼分析器和程式碼產生器。 前往 [Roslyn](https://github.com/dotnet/Roslyn)尋找您所需要的各項資源。

尋找由 Microsoft 開發人員和開發社群所建立的 Visual Studio [現有延伸模組](https://marketplace.visualstudio.com/vs)。

若要深入了解如何擴充 Visual Studio，請參閱[擴充 Visual Studio IDE](https://www.visualstudio.com/vs/extend/)。

## <a name="learn-more-and-find-out-whats-new"></a>深入了解並找出新功能

如果您從來沒有使用過 Visual Studio，請參閱 [Visual Studio 使用者開發入門](../ide/get-started-developing-with-visual-studio.md) 或查看 [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!index=2&lang=1033) 上提供的免費 Visual Studio 課程。 如果您想要查看 Visual Studio 2017 的新功能，請參閱 [Visual Studio 2017 的新功能](../ide/whats-new-in-visual-studio.md)。

恭喜您完成 Visual Studio IDE 的導覽！ 希望您已了解有關其部分主要功能一些實用資訊。

## <a name="see-also"></a>另請參閱

* [Visual Studio IDE](https://www.visualstudio.com/vs/)
* [Visual Studio 下載](https://www.visualstudio.com/downloads/)
* [Visual Studio 部落格](https://blogs.msdn.microsoft.com/visualstudio/)
* [Visual Studio 論壇](https://social.msdn.microsoft.com/Forums/vstudio/home?category=visualstudio%2Cvsarch%2Cvsdbg%2Cvstest%2Cvstfs%2Cvsdata%2Cvsappdev%2Cvisualbasic%2Cvisualcsharp%2Cvisualc)
* [Microsoft Virtual Academy](https://mva.microsoft.com/)