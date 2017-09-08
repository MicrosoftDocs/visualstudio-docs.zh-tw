---
title: "Visual Studio 2017 的新功能 | Microsoft Docs"
ms.custom: 
ms.date: 08/22/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 3cd705d703b3d745c502290422e29b3c6da39ee5
ms.openlocfilehash: 5bf00b7e5ed79f8679b837d0dcabf03550d2b849
ms.contentlocale: zh-tw
ms.lasthandoff: 09/06/2017

---
# <a name="what39s-new-in-visual-studio-2017"></a>Visual Studio 2017 的新功能
#### <a name="updated-for-the-153-release"></a>已針對 15.3 版本更新
適用於任何開發人員、任何應用程式及任何平台的卓越生產力。 您可使用 Visual Studio 2017 來開發適用於 Android、iOS、Windows、Linux、Web 及雲端的應用程式。 快速編碼、輕鬆偵錯及診斷、頻繁測試，然後自信地發行。 您也可以建置自己的擴充功能來擴充和自訂 Visual Studio 。 使用版本控制、變得敏捷、使用這個版本有效率地共同作業！

以下是我們所做變更的高階回顧︰

* **重新定義基本概念**。 新的安裝體驗意謂著您可以安裝得更快，且可以在需要時安裝所需的項目。 不論您是要載入大型方案與專案，還是要使用程式碼資料夾或甚至是單一程式碼檔案，Visual Studio 的啟動速度都更快。 而且，Visual Studio 可協助您將焦點放在主要目標，特別適用於採用 DevOps 的小組。
* **效能和生產力**。 我們已經著重於新的和現代的行動、雲端和桌面開發功能。 而且，我們也已改善整體擷取、效能和一般開發人員生產力體驗。 與以前相比，Visual Studio 的啟動速度、回應速度都變得更快，且使用的記憶體也更少。
* **搭配 Azure 的雲端應用程式開發**。 一套內建的 Azure 工具套件，可讓您輕鬆建立由 Microsoft Azure 提供技術的雲端優先應用程式。 Visual Studio 可讓您在 Azure 上輕鬆設定、建置、偵錯、封裝及部署應用程式與服務。
* **行動應用程式開發**。 在 Visual Studio 2017 中，您可以透過 Xamarin 快速創新並獲得結果，它使用一個核心程式碼基底和一組技術來統一您的多平台行動需求。 利用您現有的小組、技術投資及 C# 程式碼即可撰寫行動應用程式，讓您不僅能夠提前還能以低於預算的方式，提供消費者等級的體驗。 您可以加速行動應用程式生命週期的每個步驟，以提供世界級的消費者體驗，或是提供生產力應用程式組合來提升工作人員能力。
* **跨平台開發**：將軟體順暢地提供給任何目標平台。 透過 Redgate Data Tools 將 DevOps 程序延伸到 SQL Server，並從 Visual Studio 安全地將資料庫部署自動化。 使用 Visual Studio Tools for Unity，開發和發行多平台遊戲。 或者，使用 .NET Core 來撰寫在未修改的情況下跨 Windows、Linux 和 macOS 作業系統執行的應用程式和程式庫 (15.3 的新功能：取得 .NET Core 2.0 SDK 的並存支援)。

> [!NOTE]
> 如需 Visual Studio 2017 中新功能的完整清單，請參閱[版本資訊](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes)。

以下是一些最值得注意的 Visual Studio 2017 改善和新功能的詳細資訊。

## <a name="redefined-fundamentals"></a>重新定義的基本概念
### <a name="a-new-setup-experience"></a>新的安裝經驗

[下載 Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) 或[查看 Visual Studio 系統需求](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)

 Visual Studio 可讓您在需要功能時，以更輕鬆、更快的方式只安裝所需的功能。 而且，它也會完全進行解除安裝。

 您在安裝 Visual Studio 時要注意的最重要變更就是它的新安裝體驗。 在 [工作負載] 索引標籤上，您會看到已分組來代表通用架構、語言及平台的安裝選項。 其範圍涵蓋 Windows、Linux 及 iOS 上從 .NET 桌面開發到 C++ 應用程式開發皆包含在內的所有項目。

選擇您需要的工作負載，然後在需要時加以變更。

 ![Visual Studio 2017 安裝對話方塊](../install/media/install-visual-studio-enterprise.png "Visual Studio 2017 安裝畫面")

想要選擇您自己的元件，而不是使用工作負載嗎？ 從安裝程式選取 [個別元件] 索引標籤。 想要安裝語言套件，同時不需要變更 Windows 語言選項嗎？ 選擇安裝程式的 [語言套件] 索引標籤。  

若要深入了解新的安裝體驗 (包括引導您執行這項作業的逐步指示)，請參閱[安裝 Visual Studio](../install/install-visual-studio.md) 頁面。

## <a name="performance-and-productivity"></a>效能和生產力
### <a name="sign-in-across-multiple-accounts"></a>跨多個帳戶登入  
我們已在 Visual Studio 中導入新的身分識別服務，可讓您在 Team Explorer、Azure Tools、Windows 市集發行等工具之間共用使用者帳戶。

此外，您也可以保持登入的狀態更久。 Visual Studio 將不會每隔 12 小時要求您重新登入一次。 若要深入了解，請參閱 [Fewer Visual Studio Sign-in Prompts](https://blogs.msdn.microsoft.com/visualstudio/2016/08/15/fewer-visual-studio-sign-in-prompts/) (較少的 Visual Studio 登入提示) 部落格文章。

### <a name="start-visual-studio-faster"></a>更快速啟動 Visual Studio
新的「Visual Studio 效能中心」可協助您將 IDE 啟動時間最佳化。 「效能中心」會列出可能讓 IDE 啟動變慢的所有擴充功能和工具視窗。 您可以使用它來改善啟動效能，方法是判斷延伸模組啟動時機，或是否在啟動時開啟工具視窗。

### <a name="decrease-solution-load-time"></a>減少解決方案載入時間
處理包含大量專案的方案並不意謂著您必須一次處理所有的檔案或專案。 您現在可以進行編輯和偵錯，而不需要等待 Visual Studio 載入每個專案。 若要使用 Managed 專案進行試用，請從 [工具] -> [選項] -> [專案和方案] 中開啟 [輕量型解決方案載入]。

  ![Visual Studio 2017 中的 [選項] 對話方塊](../ide/media/vs2017ide-lightweight-solution-load.png "Visual Studio 2017 - [選項] 對話方塊 - [對所有解決方案使用輕量型解決方案載入]")

### <a name="faster-on-demand-loading-of-extensions"></a>依需求更快速地載入延伸模組
Visual Studio 正在移動其擴充功能 (同時也在處理協力廠商擴充功能)，讓它們變成在需要時載入，而不是在 IDE 啟動時載入。 想要知道哪些延伸模組影響啟動、解決方案載入和輸入效能嗎？ 您可以在 [說明] -> [管理 Visual Studio 效能] 中查看這項資訊。

  ![Visual Studio 2017 中的 [選項] 對話方塊](../ide/media/vs2017ide-manage-vs-perf.png "Visual Studio [說明] 對話方塊 - 效能管理")

#### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>使用漫遊延伸模組管理員來管理延伸模組
當您登入 Visual Studio 時，可以更輕鬆地使用慣用的擴充功能來設定每個開發環境。 新的「漫遊擴充功能管理員」會在雲端建立一份同步清單，來記錄您的所有慣用擴充功能。  

若要查看 Visual Studio 中的延伸模組清單，請按一下 [工具] > [延伸模組和更新]，然後按一下 [漫遊延伸模組管理員]。

![Visual Studio 2017 - [延伸模組和更新] 對話方塊](../ide/media/vs2017ide-extensions-and-updates.png "Visual Studio 2017 - [工具] > [延伸模組和更新] 對話方塊")

漫遊延伸模組管理員會追蹤您安裝的所有延伸模組，但是您可以選擇想要新增至 [漫遊] 清單的延伸模組。

![Visual Studio 2017 - [延伸模組和更新] 對話方塊](../ide/media/vs2017ide-RoamingExtensionManager.png "Visual Studio 2017 - 漫遊延伸模組管理員")

當您使用漫遊延伸模組管理員時，清單上會有三個圖示類型︰
* ![[已漫遊] 圖示](../ide/media/vs2017ide-roamedicon.png "[已漫遊] 圖示") 已漫遊：在此「漫遊清單」中但未安裝在您電腦上的擴充功能。
  (您可以使用 [下載] 按鈕進行安裝)。
* ![[已漫遊並已安裝] 圖示](../ide/media/vs2017ide-roamedinstalledicon.png "[已漫遊並已安裝] 圖示") 已漫遊並已安裝︰所有在此「漫遊清單」中並已安裝在您開發環境中的擴充功能。
  (如果您決定不再漫遊，則可以使用 [停止漫遊] 按鈕予以移除)。
* ![[已安裝] 圖示](../ide/media/vs2017ide-installedicon.png "[已安裝] 圖示") 已安裝︰所有已安裝在此環境中但不在「漫遊清單」中的擴充功能。
  (使用 [開始漫遊] 按鈕，即可將延伸模組新增至 [漫遊] 清單)。

您在登入後下載的任何擴充功能都會新增到您的清單中並顯示為「已漫遊並已安裝」，而且會包含在您的「漫遊清單」中，讓您從任何電腦都可以存取它。

### <a name="experience-live-architecture-dependency-validation-and-live-unit-testing"></a>體驗即時架構相依性驗證和即時單元測試
當您在文字編輯器中鍵入程式碼時，如果違反架構相依性規則，Visual Studio 可以使用「相依性驗證」圖表 (也稱為 分層圖) 來即時通知您。

錯誤會出現在 [錯誤清單] 中，而且文字編輯器中的波浪線會顯示違規的確切位置。 如此較不容易引進您不想要的相依性。

![即時驗證架構](../ide/media/vs2017ide-LiveArchitectureDepedendencyValidation.png "即時驗證架構相依性")

#### <a name="live-unit-testing"></a>即時單元測試
在 Visual Studio Enterprise 2017 中，即時單元測試會在您撰寫程式碼時，在編輯器中提供即時單元測試結果和程式碼涵蓋範圍。 它可以與 .NET Framework 和 .NET Core 的 C# 和 Visual Basic 專案搭配運作，並且支援 MSTest、xUnit 及 NUnit 這三種測試架構。

![即時單元測試](../ide/media/lut-codewindow.png "Visual Studio Enterprise 版中新「即時單元測試」功能的範例")

如需詳細資訊，請參閱 [Live Unit Testing in Visual Studio 2017 Enterprise](https://blogs.msdn.microsoft.com/visualstudio/2017/03/09/live-unit-testing-in-visual-studio-2017-enterprise/) (Visual Studio 2017 Enterprise 中的 Live Unit Testing) 部落格文章。

#### <a name="set-up-a-cicd-pipeline-to-run-automated-tests-efficiently"></a>設定 CI/CD 管線，有效率地執行自動化測試
自動化測試是任何 DevOps 管線的主要部分。 它可讓您在較短的循環內一致且可靠地測試和發行您的方案。 CI/CD (持續整合和持續傳遞) 流程有助於讓程序更具效率。

如需有關自動化測試的詳細資訊，請參閱 [DevOps 中自動化測試的 CI/CD 管線](https://blogs.msdn.microsoft.com/visualstudioalmrangers/2017/04/20/set-up-a-cicd-pipeline-to-run-automated-tests-efficiently/) \(英文\) 部落格文章。

此外，針對 [Visual Studio 的持續傳遞工具](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) \(英文\) DevLabs 擴充功能的新功能，如需相關詳細資訊，請參閱[有信心地認可：認可時的程式碼品質](https://blogs.msdn.microsoft.com/visualstudio/2017/08/21/committing-with-confidence-commit-time-code-quality-information-updated/) \(英文\) 部落格文章。

### <a name="a-focus-on-accessibility"></a>聚焦於協助工具
在 15.3 中有超過 1,700 項的標的式修正，針對 Visual Studio 與眾多客戶使用的輔助技術，改善了其間的相容性。 在數十種案例中，螢幕助讀程式、高對比佈景主題與其他輔助技術的相容性更勝以往。 偵錯工具、編輯器與 shell 也都有顯著的改善。

如需詳細資訊，請參閱 [Visual Studio 2017 版本 15.3 中的協助工具改善](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/) \(英文\) 部落格文章。

### <a name="visual-studio-ide-enhancements"></a>Visual Studio IDE 加強功能
#### <a name="use-new-refactorings"></a>使用新的重構
在 15.3 中，我們已新增少數新的重構，包含：
*   解決合併衝突
*   新增參數 (從 CallSite)
*   產生覆寫
*   新增具名引數
*   新增參數的 Null 檢查
*   將數字分隔符號插入到常值中
*   變更數值常值的基底 (例如，十六進位到二進位)
*   轉換 if-to-switch
*   移除未使用的變數

如需詳細資訊，請參閱 [Visual Studio 中的重構、程式碼產生和快速動作](refactoring-code-generation-quick-actions.md)頁面。


#### <a name="interact-with-git"></a>與 Git 互動
當您在 Visual Studio 中處理專案時，可以設定您的程式碼，然後快速認可並發行到 Git 服務。 您也可以從 IDE 右下角的按鈕中使用功能表點選，來管理您的 Git 儲存機制。

![Visual Studio 2017 與 Git 互動對話方塊](../ide/media/vsIDE-GitInteraction.png "Visual Studio IDE 中的 Git 工具")

#### <a name="view-and-navigate-code-with-structure-visualizer"></a>使用結構視覺化檢視來檢視和巡覽程式碼
「結構視覺化檢視」會在您的程式碼上繪製結構輔助線 (也稱為 縮排輔助線)。 您可以使用它們，以視覺化方式隨時呈現您所在的程式碼區塊，而不需捲動。 將滑鼠游標暫留在程式碼行上會顯示工具提示，可讓您看到該區塊的開頭及其父代。 此功能除了在 C#、Visual Basic 及 XAML 有提供之外，所有透過 TextMate 文法支援的語言也都有此功能。

![Visual Studio 2017 結構視覺化檢視](../ide/media/vsIDE-StructureVisualizer.png "Visual Studio 中的結構視覺化檢視")

#### <a name="experience-improved-navigation-controls"></a>體驗改善的瀏覽控制項
我們已重新整理瀏覽體驗，以協助您在從 A 移到 B 時更為堅定而不易分心。

* **移至** (Ctrl+F12) &ndash; 會從任何基底類型或成員瀏覽至其各種實作。

* **移至全部** (Ctrl+T 或 Ctrl+,) &ndash; 會直接瀏覽至任何檔案/類型/成員/符號宣告。 您可以篩選您的結果清單或使用查詢語法 (例如 "f searchTerm" 用於檔案，"t searchTerm" 用於類型等等)。

 ![已改進的 [移至全部]](../ide/media/vs2017ide-navigation-go-to.png "已改進的 [移至全部] 功能範例")

* **尋找所有參考 (Shift+F12)** &ndash; 包含語法色彩標示，您可以依據專案、定義及路徑的組合，將 [尋找所有參考] 結果分組。 您也可以「鎖定」結果，如此您便可以繼續尋找其他參考，又不會遺失原始結果。

 ![新的 [尋找所有參考] 工具](../ide/media/vs2017ide-find-all-references.png "新的 [尋找所有參考] 工具範例")

* **縮排輔助線** &ndash; 灰色垂直虛線在程式碼中就像是地標，可提供在您檢視框架內的內容。 您可以透過熱門的 Productivity Power Tools 辨識它們。

如需有關我們新生產力功能的詳細資訊，請參閱 Mark Wilson-Thomas 所撰寫的 [Visual Studio 2017 中的生產力 (英文)](https://blogs.msdn.microsoft.com/visualstudio/2016/11/28/productivity-in-visual-studio-2017-rc/) 部落格文章。

### <a name="visual-c"></a>Visual C++
您將在 Visual Studio 中看到數項改善，例如使用 Visual Studio 來散發「C++ 核心指南」、新增增強的 C++11 和 C++ 功能支援以更新編譯器，以及新增和更新 C++ 程式庫中的功能。 我們還提升了 C++ IDE、安裝工作負載等的效能。

此外，我們修正了編譯器及工具中超過 250 個錯誤 (bug) 與回報的問題，其中許多是客戶透過 [Microsoft Connect](https://connect.microsoft.com/VisualStudio "Microsoft Connect") 所提交。

如需完整的詳細資料，請參閱 [Visual Studio 2017 中 Visual C++ 的新功能](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)頁面。  

### <a name="debugging-and-diagnostics"></a>偵錯和診斷
#### <a name="run-to-click"></a>執行至點選處：
現在，您可以更容易在偵錯時往前跳過，而不需設定中斷點來停在您想要的程式碼行上。 當您在偵錯工具中被停止時，只需要按一下出現在程式碼行旁邊的圖示。 您的程式碼將會執行，並在下次在程式碼路徑中執行到該行時，就停在該行。

![Visual Studio 2017 偵錯 - 執行至點選處](../ide/media/vs2017ide-RunToClick.png "Visual Studio 偵錯和診斷中的 [執行至點選處]")

#### <a name="the-new-exception-helper"></a>新的例外狀況協助程式：
新的「例外狀況協助程式」可協助您快速檢視例外狀況資訊。 此資訊會以簡潔的形式呈現，其中包含內部例外狀況的快速存取方式。 當您診斷 NullReferenceException 時，在「例外狀況協助程式」內即可快速查看哪些項目為 Null。

![Visual Studio 中新的「例外狀況協助程式」對話方塊](../ide/media/vs2017ide-ExceptionHelper.png "新的「例外狀況協助程式」對話方塊")

如需詳細資訊，請參閱 [Using the New Exception Helper in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/) (在 Visual Studio 中使用新的例外狀況協助程式) 部落格文章。

## <a name="cloud-app-development-with-azure"></a>搭配 Azure 的雲端應用程式開發
### <a name="azure-functions-tools"></a>Azure Functions Tools
我們已包含工具來協助您使用先行編譯的 C# 類別庫來開發 Azure 函式，以作為「Azure 開發」工作負載的一部分。 現在您可以在本機開發電腦上進行建置、執行和偵錯，然後從 Visual Studio 直接發行至 Azure。

如需詳細資訊，請參閱 [Azure Functions Tools for Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-develop-vs) 頁面。

## <a name="mobile-app-development"></a>行動應用程式開發
### <a name="xamarin"></a>Xamarin
熟悉 C#、.NET 和 Visual Studio 的開發人員可以使用 Xamarin 來提供原生 Android、iOS 和 Windows 應用程式，以作為「.NET 的行動開發」工作負載的一部分。 開發人員在使用 Xamarin 開發行動應用程式時，可以不需要了解 Objective-C 或 Java 等機器碼語言，也能享有相同的功能和生產力，包括在 Android、iOS 和 Windows 裝置上進行遠端偵錯。

如需詳細資訊，請參閱 [Visual Studio 和 Xamarin](../cross-platform/visual-studio-and-xamarin.md) 頁面。

### <a name="entitlements-editor"></a>權利編輯器
**15.3 的新功能**：針對 iOS 開發需求，我們已新增獨立權利編輯器。 它包含可輕鬆地瀏覽的使用者易記 UI。 若要啟動它，請按兩下 entitlements.plist 檔案。

![Xamarin 的權利編輯器](../ide/media/xamarin-entitlements-editor.png "Xamarin 的權利編輯器")

## <a name="cross-platform-development"></a>跨平台開發
### <a name="redgate-data-tools"></a>Redgate Data Tools
為了將 DevOps 功能擴充到 SQL Server 資料庫開發，下列 Visual Studio 2017 版本現在會提供 Redgate Data Tools。

隨附於 Visual Studio 2017 Enterprise：
- [Redgate ReadyRoll Core](http://www.red-gate.com/products/sql-development/readyroll/entrypage/microsoft-and-readyroll?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) 可協助您開發移轉指令碼、使用原始檔控制管理資料庫變更，並且可以將 SQL Server 資料庫變更和應用程式變更的部署安全地自動化。
- [Redgate SQL Prompt Core](http://www.red-gate.com/products/sql-development/sql-prompt/entrypage/microsoft-and-sql-prompt?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) 可協助您透過智慧型程式碼自動完成的協助，更快且更精確地撰寫 SQL。 SQL Prompt 會自動完成資料庫及系統物件和關鍵字，並在輸入期間提供資料行建議。 由於您不再需要記住所有資料行名稱或別名，這會使程式碼更加簡潔，並具有更少的錯誤。

隨附於所有版本的 Visual Studio 2017：
- [Redgate SQL Search](http://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) 可協助您跨多個資料庫快速尋找 SQL 片段和物件以提高產能。

如需詳細資訊，請參閱我們的 [Redgate Data Tools in Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2017/03/07/redgate-data-tools-in-visual-studio-2017/) (Visual Studio 2017 中的 Redgate Data Tools) 部落格文章。

### <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity
我們已包含工具來協助開發跨平台以建立 2D 和 3D 遊戲與互動式內容，以作為「Unity 的遊戲開發」工作負載的一部分。 只需要建立一次，即可發行至 21 個平台，包含所有行動平台、WebGL、Mac、PC 和 Linux 桌面、Web 或使用 Visual Studio 2017 和 Unity 5.6 的主控台。

如需詳細資訊，請參閱 [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) 頁面。

### <a name="net-core"></a>.NET 核心
.NET Core 是 .NET Standard 的一般用途、模組化、跨平台和開放原始碼實作，並且包含許多與 .NET Framework 相同的 API。

.NET Core 平台是由幾個元件所組成，其中包含 Managed 編譯器、執行階段、基底類別庫，以及許多應用程式模型 (例如 ASP.NET Core)。 .NET Core 支援三個主要作業系統：Windows、Linux 和 macOS。 您可以在裝置、雲端和內嵌/IoT 案例中使用 .NET Core。

而且，它現在包含 Docker 支援。

**15.3 的新功能**：Visual Studio 2017 版本 15.3 支援 .NET Core 2.0 開發 (在 15.3 中，使用 .NET Core 2.0 需要分別下載和安裝 .NET Core 2.0 SDK)。

如需詳細資訊，請參閱 [.NET Core 指南](https://docs.microsoft.com/dotnet/core/index)頁面。

## <a name="talk-to-us"></a>告訴我們  
 為什麼要傳送意見反應給 Visual Studio 小組？ 我們極為重視客戶的意見反應：它可以讓我們更有動力進行改善。

如果您想要建議我們如何改善 Visual Studio，或回報問題，請參閱[告訴我們](../ide/talk-to-us.md)頁面來取得詳細資訊。

### <a name="report-a-problem"></a>回報問題  
 訊息有時無法完整傳達您所發生問題的完整影響。 如果您遇到停止回應、當機或其他效能問題，則可以使用 [回報問題] 工具，輕鬆地與我們分享重現步驟和支援檔案 (例如螢幕擷取畫面以及追蹤和堆積傾印檔案)。 如需如何使用此工具的詳細資訊，請參閱[如何回報問題](how-to-report-a-problem-with-visual-studio-2017.md)頁面。

### <a name="track-your-issue-in-connect"></a>使用 Connect 追蹤您的問題  
 如果您想要追蹤 Visual Studio 意見反應的狀態，請前往 [Connect](http://connect.microsoft.com/) 並回報 Bug。 回報 Bug 之後，就可以回到 Connect 來追蹤其狀態。

## <a name="see-also"></a>另請參閱
* [Visual Studio 2017 版本資訊](https://www.visualstudio.com/news/vs2015-vs)
* [Visual C++ 的新功能](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [C# 的新功能](https://docs.microsoft.com/dotnet/csharp/csharp-7)  
* [Team Foundation Server 的新功能](https://www.visualstudio.com/docs/whats-new)
* [Visual Studio for Mac 的新功能](https://www.visualstudio.com/vs/visual-studio-mac/)

