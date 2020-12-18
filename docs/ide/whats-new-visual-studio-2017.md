---
title: Visual Studio 2017 的新功能
titleSuffix: ''
description: 深入了解 Visual Studio 2017 中的新功能。
ms.date: 12/18/2018
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: ab0d5cc497709a690c88b16771f2c12651e5aed0
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668660"
---
# <a name="whats-new-in-visual-studio-2017"></a>Visual Studio 2017 的新功能

**[15.9 版](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017)的更新**

想要從舊版 Visual Studio 升級嗎？ Visual Studio 2017 提供您下列功能：適用於任何開發人員、任何應用程式和任何平台的卓越生產力。 您可使用 Visual Studio 2017 來開發適用於 Android、iOS、Windows、Linux、Web 及雲端的應用程式。 快速編碼、輕鬆偵錯及診斷、頻繁測試，然後自信地發行。 您也可以建置自己的擴充功能來擴充和自訂 Visual Studio 。 使用版本控制、變得敏捷、使用這個版本有效率地共同作業！

>[!div class="button"]
>[下載 Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

以下是自舊版 Visual Studio 2015 以來，我們所做變更的高階回顧：

* 重新 **[定義基本](#redefined-fundamentals)** 概念。 新的安裝體驗意謂著您可以安裝得更快，且可以在需要時安裝所需的項目。
* **[效能與生產力](#performance-and-productivity)**。 我們已經著重於新的和現代的行動、雲端和桌面開發功能。 而且，與以前相比，Visual Studio 的啟動速度、回應速度都變得更快，使用的記憶體也較少。
* **[使用 Azure 進行雲端應用程式開發](#cloud-app-development-with-azure)**。 一套內建的 Azure 工具套件，可讓您輕鬆建立由 Microsoft Azure 提供技術的雲端優先應用程式。 Visual Studio 可讓您在 Azure 上輕鬆設定、建置、偵錯、封裝及部署應用程式與服務。
* **[Windows 應用程式開發](#windows-app-development)**。 在 Visual Studio 2017 中，您可以使用 UWP 範本建立適用於所有 Windows 10 裝置 (電腦、平板電腦、手機、Xbox、HoloLens、Surface Hub 等) 的單一專案。
* 行動裝置 **[應用程式開發](#mobile-app-development)**。 Xamarin 將您的多平台行動需求整合到一個核心程式碼基底和一組技術，讓您能快速創新並獲得成果。
* **[跨平臺開發](#cross-platform-development)**。 將軟體順暢地提供給任何目標平台。 透過 Redgate Data Tools 將 DevOps 程序延伸到 SQL Server，並從 Visual Studio 安全地將資料庫部署自動化。 或者，使用 .NET Core 來撰寫在未修改的情況下跨 Windows、Linux 和 macOS 作業系統執行的應用程式和程式庫
* **[遊戲開發](#games-development)**。 透過 Visual Studio Tools for Unity (VSTU)，您可以在 C# 中使用 Visual Studio 來撰寫遊戲和編輯器指令碼，然後使用其強大的偵錯工具來尋找及修正錯誤。
* **[AI 開發](#ai-development)**。 有了 Visual Studio Tools for AI，您就可以使用 Visual Studio 的生產力功能來加速 AI 的創新。 建置、測試及部署與 Azure Machine Learning 無縫整合的深度學習/AI 解決方案，以獲得強固的測試功能。

> [!NOTE]
> 如需 Visual Studio 2017 中新特性和功能的完整清單，請參閱 [目前的版本](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017)資訊。 若要查看未來的功能供應專案，請參閱 [Preview 版本](/visualstudio/releasenotes/vs2017-preview-relnotes?context=visualstudio/default&contextView=vs-2017)資訊。

以下是一些最值得注意的 Visual Studio 2017 改善和新功能的詳細資訊。

## <a name="redefined-fundamentals"></a>重新定義的基本概念

### <a name="a-new-setup-experience"></a>新的安裝經驗

Visual Studio 可讓您在需要功能時，以更輕鬆、更快的方式只安裝所需的功能。 而且，它也會完全進行解除安裝。

您在安裝 Visual Studio 時要注意的最重要變更就是它的新安裝體驗。 在 [工作負載] 索引標籤上，您會看到已分組來代表通用架構、語言及平台的安裝選項。 其範圍涵蓋 Windows、Linux 及 iOS 上從 .NET 桌面開發到 C++ 應用程式開發皆包含在內的所有項目。

選擇您需要的工作負載，然後在需要時加以變更。

![Visual Studio 2017 安裝對話方塊](../install/media/install-visual-studio-enterprise.png)

此外，您還有微調安裝的選項：

* 想要選擇您自己的元件，而不是使用工作負載嗎？ 從安裝程式選取 [個別元件] 索引標籤。
* 想要安裝語言套件，同時不需要變更 Windows 語言選項嗎？ 選擇安裝程式的 [語言套件] 索引標籤。
* **15.7 的新功能**：想要變更 Visual Studio 的安裝位置嗎？ 選擇安裝程式的 [安裝選項] 索引標籤。

若要深入了解新的安裝體驗 (包括引導您執行這項作業的逐步指示)，請參閱[安裝 Visual Studio](../install/install-visual-studio.md) 頁面。

### <a name="a-focus-on-accessibility"></a>聚焦於協助工具

**15.3 的新功能**：有超過 1,700 項的目標式修正，針對 Visual Studio 與眾多客戶使用的輔助技術，改善了其間的相容性。 在數十種案例中，螢幕助讀程式、高對比佈景主題與其他輔助技術的相容性更勝以往。 偵錯工具、編輯器與殼層也都有顯著改善。

如需詳細資訊，請參閱 [Visual Studio 2017 版本 15.3 中的協助工具改善](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) \(英文\) 部落格文章。

## <a name="performance-and-productivity"></a>效能和生產力

### <a name="sign-in-across-multiple-accounts"></a>跨多個帳戶登入

我們已在 Visual Studio 中引進新的身分識別服務，可讓您在 Team Explorer、Azure Tools、Microsoft Store 發行等工具之間共用使用者帳戶。

此外，您也可以保持登入的狀態更久。 Visual Studio 將不會每隔 12 小時要求您重新登入一次。 若要深入瞭解，請參閱 [較少的 Visual Studio 登入提示](https://devblogs.microsoft.com/visualstudio/fewer-visual-studio-sign-in-prompts/) blog 文章。

### <a name="start-visual-studio-faster"></a>更快速啟動 Visual Studio

新的「Visual Studio 效能中心」可協助您將 IDE 啟動時間最佳化。 「效能中心」會列出可能讓 IDE 啟動變慢的所有擴充功能和工具視窗。 您可以使用它來改善啟動效能，方法是判斷延伸模組啟動時機，或是否在啟動時開啟工具視窗。

### <a name="faster-on-demand-loading-of-extensions"></a>依需求更快速地載入延伸模組

Visual Studio 正在移動其擴充功能 (同時也在處理協力廠商擴充功能)，讓它們變成在需要時載入，而不是在 IDE 啟動時載入。 想要知道哪些延伸模組影響啟動、解決方案載入和輸入效能嗎？ 您可以在「**協助**  >  **管理 Visual Studio 效能**」中看到此資訊。

  ![Visual Studio 2017 中的選項對話方塊](media/vs2017ide-manage-vs-perf.png)

#### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>使用漫遊延伸模組管理員來管理延伸模組

當您登入 Visual Studio 時，可以更輕鬆地使用慣用的擴充功能來設定每個開發環境。 新的「漫遊擴充功能管理員」會在雲端建立一份同步清單，來記錄您的所有慣用擴充功能。

若要在 Visual Studio 中查看延伸模組的清單，請按一下 [**工具** 延伸模組]  >  **& [更新**]，然後按一下 [**漫遊延伸模組管理員**]。

![Visual Studio 2017 - [延伸模組和更新] 對話方塊](media/vs2017ide-extensions-and-updates.png)

漫遊延伸模組管理員會追蹤您安裝的所有延伸模組，但是您可以選擇想要新增至 [漫遊] 清單的延伸模組。

![Visual Studio 2017-漫遊延伸模組管理員](media/vs2017ide-RoamingExtensionManager.png)

當您使用漫遊延伸模組管理員時，清單上會有三個圖示類型︰

* ![已漫遊圖示](media/vs2017ide-roamedicon.png) **_已漫遊_**：在漫遊清單中，但尚未安裝在電腦上的延伸模組。
  (您可以使用 [下載] 按鈕進行安裝)。
* ![已漫遊並已安裝圖示](media/vs2017ide-roamedinstalledicon.png) **_已漫遊並已安裝_**︰在漫遊清單中，並已安裝在開發環境中的所有延伸模組。
  (如果您決定不再漫遊，則可以使用 [停止漫遊] 按鈕予以移除)。
* ![已安裝圖示](media/vs2017ide-installedicon.png) **_已安裝_**︰已安裝在開發環境中，但不在漫遊清單中的所有延伸模組。
  (使用 [開始漫遊] 按鈕，即可將延伸模組新增至 [漫遊] 清單)。

您在已登入期間下載的所有延伸模組都會以 [Roamed & Installed] \(已漫遊且已安裝\) 的形式新增至您的清單。 延伸模組隨後會成為漫遊清單的一部份，使您得以從任何電腦存取。

### <a name="experience-live-unit-testing"></a>體驗 Live Unit Testing

在 Visual Studio Enterprise 2017 中，即時單元測試會在您撰寫程式碼時，在編輯器中提供即時單元測試結果和程式碼涵蓋範圍。 它可以與 .NET Framework 和 .NET Core 的 C# 和 Visual Basic 專案搭配運作，並且支援 MSTest、xUnit 及 NUnit 這三種測試架構。

![Live Unit Testing](media/lut-codewindow.png)

如需詳細資訊，請參閱 [Live Unit Testing 簡介](../test/live-unit-testing-intro.md)。 如需每個 Visual Studio Enterprise 2017 版本中新增的功能清單，請參閱 [Live Unit Testing 的新功能](../test/live-unit-testing-whats-new.md)。

### <a name="set-up-a-cicd-pipeline"></a>設定 CI/CD 管線

#### <a name="automated-testing"></a>自動化測試

自動化測試是任何 DevOps 管線的主要部分。 它可讓您在較短的循環內一致且可靠地測試和發行您的方案。 CI/CD (持續整合和持續傳遞) 流程有助於讓程序更具效率。

如需有關自動化測試的詳細資訊，請參閱 [DevOps 中自動化測試的 CI/CD 管線](/archive/blogs/visualstudioalmrangers/set-up-a-cicd-pipeline-to-run-automated-tests-efficiently) \(英文\) 部落格文章。

此外，如需 [Visual Studio 持續傳遞工具](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) DevLabs 延伸模組新功能的詳細資訊，請參閱 [Commit with confidence: Commit time code quality](https://devblogs.microsoft.com/visualstudio/committing-with-confidence-getting-code-quality-information-at-commit-time/) (有信心地認可：認可時的程式碼品質) 部落格文章。

### <a name="visual-studio-ide-enhancements"></a>Visual Studio IDE 加強功能

#### <a name="multi-caret-editing"></a>多重游標編輯

**15.8 中的新功能**：現在要在一個檔案中編輯多個位置，是輕而易舉的事。 一開始，先在一個檔案中的多個位置建立插入點和選取範圍。 接著使用多重游標編輯功能，同時對兩處以上進行相同的編輯。

如需詳細資訊，請參閱[尋找和取代文字](finding-and-replacing-text.md)頁面的[多重游標選取](finding-and-replacing-text.md#multi-caret-selection)章節。

#### <a name="keep-keybinding-profiles-consistent"></a>讓按鍵繫結關係設定檔保持一致

**15.8 中的新功能**：現在，您可以透過兩個新的鍵盤設定檔：Visual Studio Code 和 ReSharper (Visual Studio)，在工具之間保持一致的按鍵繫結關係。 您可以在 [**工具**  >  **選項**]  >  的 **[一般**  >  **鍵盤**] 和頂端下拉式功能表中找到這些架構。

  ![Visual Studio Code 和 ReSharper 的新按鍵繫結關係設定檔](media/vs-keyboard-mappings-code-resharper.png)

#### <a name="use-new-refactorings"></a>使用新的重構

重構是指撰寫程式碼之後，用以改善程式碼的程序。 重構會變更程式碼的內部結構，而不會變更其行為。 我們經常會新增重構，以下是其中一些：

* 新增參數 (從 CallSite)
* 產生覆寫
* 新增具名引數
* 新增參數的 Null 檢查
* 將數字分隔符號插入到常值中
* 變更數值常值的基底 (例如，十六進位到二進位)
* 轉換 if-to-switch
* 移除未使用的變數

如需詳細資訊，請參閱[快速動作](common-quick-actions.md)。

#### <a name="interact-with-git"></a>與 Git 互動

當您在 Visual Studio 中處理專案時，可以設定您的程式碼，然後快速認可並發行到 Git 服務。 您也可以從 IDE 右下角的按鈕中使用功能表點選，來管理您的 Git 儲存機制。

![Visual Studio 2017 與 [Git] 對話方塊互動](media/vsIDE-GitInteraction.png)

#### <a name="experience-improved-navigation-controls"></a>體驗改善的瀏覽控制項

我們已重新整理瀏覽體驗，以協助您在從 A 移到 B 時更為堅定而不易分心。

* **15.4 中的新** 功能：**移至 [定義**] (**Ctrl** + **click** 或 **F12**) &ndash; 滑鼠使用者有更簡單的方法，可按 **Ctrl** 然後按一下成員，以流覽至成員的定義。 按住 **Ctrl** 鍵並將滑鼠游標暫留在程式碼符號上，會加上底線並將它轉換成連結。 如需詳細資訊，請參閱[移至定義和查看定義](go-to-and-peek-definition.md)。

* **移至 [執行**] (**Ctrl** + **F12**) &ndash; 從任何基底類型或成員流覽至其各種不同的實作為。

* **移至所有** (**ctrl** + **T** 或 **ctrl** + **，**) &ndash; 直接流覽至任何檔案/類型/成員/符號宣告。 您可以篩選您的結果清單或使用查詢語法 (例如 "f searchTerm" 用於檔案，"t searchTerm" 用於類型等等)。

  ![已改善的 [移至全部]](media/vs2017ide-navigation-go-to.png)

* 使用語法顏色標示來 **尋找所有** 參考 (**Shift** + **F12**) &ndash; ，您可以透過專案、定義和路徑的組合，將 [尋找所有參考] 結果分組。 您也可以「鎖定」結果，如此您便可以繼續尋找其他參考，又不會遺失原始結果。

  ![新的 [尋找所有參考] 工具](media/vs2017ide-find-all-references.png)

* **結構視覺化檢視** &ndash; 灰色垂直虛線 (縮排輔助線) 在程式碼中就像是地標，可提供在您檢視框架內的內容。 您可以透過熱門的 Productivity Power Tools 辨識它們。 您可以使用它們，以視覺化方式隨時呈現您所在的程式碼區塊，而不需捲動。 將滑鼠游標暫留在程式碼行上會顯示工具提示，可讓您看到該區塊的開頭及其父代。 此功能除了在 C#、Visual Basic 及 XAML 有提供之外，所有透過 TextMate 文法支援的語言也都有此功能。

  ![Visual Studio 2017 結構視覺化檢視](media/vsIDE-StructureVisualizer.png)

如需新生產力功能的詳細資訊，請參閱 [Visual Studio 2017：生產力、效能和合作夥伴](https://devblogs.microsoft.com/visualstudio/visual-studio-2017-productivity-performance-and-partners/) 的 blog 文章。

### <a name="visual-c"></a>Visual C++

您將在 Visual Studio 中看到數項改善，例如使用 Visual Studio 來散發「C++ 核心指南」、新增增強的 C++11 和 C++ 功能支援以更新編譯器，以及新增和更新 C++ 程式庫中的功能。 我們還提升了 C++ IDE、安裝工作負載等的效能。

此外，我們已修正編譯器和工具中的 250 bug 和回報問題，許多客戶透過 [c + + 的開發人員社群](https://aka.ms/feedback/report?space=62 "適用于 c + + 的開發人員社群")提交。

如需完整的詳細資訊，請參閱 [Visual 2017 中 Visual C++ 的新功能](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio) 頁面。

### <a name="debugging-and-diagnostics"></a>偵錯與診斷

#### <a name="run-to-click"></a>執行至點選處

現在，您可以更容易在偵錯時往前跳過，而不需設定中斷點來停在您想要的程式碼行上。 當您在偵錯工具中被停止時，只需要按一下出現在程式碼行旁邊的圖示。 您的程式碼將會執行，並在下次在程式碼路徑中執行到該行時，就停在該行。

![Visual Studio 2017 偵錯 - 執行至點選處](media/vs2017ide-RunToClick.png)

#### <a name="the-new-exception-helper"></a>新的例外狀況協助程式

新的「例外狀況協助程式」可協助您快速檢視例外狀況資訊。 此資訊會以簡潔的形式呈現，其中包含內部例外狀況的快速存取方式。 當您診斷 NullReferenceException 時，在「例外狀況協助程式」內即可快速查看哪些項目為 Null。

![Visual Studio 中的新例外狀況協助程式對話方塊](media/vs2017ide-ExceptionHelper.png)

如需詳細資訊，請參閱 [Use the new Exception Helper in Visual Studio](https://devblogs.microsoft.com/devops/using-the-new-exception-helper-in-visual-studio-15-preview/) (在 Visual Studio 中使用新的例外狀況協助程式) 部落格文章。

#### <a name="snapshots-and-intellitrace-step-back"></a>快照集和 IntelliTrace 回溯

**15.5 的新功能**：IntelliTrace 回溯會自動擷取應用程式在每個中斷點和偵錯工具逐步執行事件的快照集。 記錄的快照集可讓您回溯到先前的中斷點或步驟，以檢視應用程式過去的狀態。 如果您想要查看先前的應用程式狀態，但不想要重新啟動偵錯或重新建立所需的應用程式狀態，IntelliTrace 回溯可節省您的時間。

您可以使用 **調試** 程式列中 **的 [回溯] 和 [** **下一頁**] 按鈕，流覽和查看快照集。 這些按鈕可巡覽出現在 [診斷工具] 視窗之 [事件] 索引標籤中的事件。 逐步返回或前進至某個事件會自動啟動所選事件的歷程偵錯。

![Visual Studio 中的 IntelliTrace 回溯範例](../debugger/media/intellitrace-step-back-icons-description.png  "逐步執行和向前按鈕")

如需詳細資訊，請參閱[使用 IntelliTrace 回溯檢視快照集](../debugger/view-historical-application-state.md)頁面。

### <a name="containerization"></a>容器化

容器提供您更高的應用程式密度和更低的部署成本，並提高生產力和 DevOps 彈性。

#### <a name="docker-container-tooling"></a>Docker 容器工具

**15.5 的新** 功能：

* Visual Studio 包含適用於 Docker 容器的工具，這些工具現在支援多階段 Dockerfile，以簡化最佳化容器映像的建立流程。
* 根據預設，當您開啟具有 Docker 支援的專案時，Visual Studio 會自動在背景提取、建置及執行執行必要的容器映像。 您可以在 Visual Studio 中透過 [自動在背景中啟動容器] 設定停用此選項。

## <a name="cloud-app-development-with-azure"></a>搭配 Azure 的雲端應用程式開發

### <a name="azure-functions-tools"></a>Azure Functions Tools

我們已包含工具來協助您使用先行編譯的 C# 類別庫來開發 Azure 函式，以作為「Azure 開發」工作負載的一部分。 現在您可以在本機開發電腦上進行建置、執行和偵錯，然後從 Visual Studio 直接發行至 Azure。

如需詳細資訊，請參閱 [Azure Functions tools for Visual Studio](/azure/azure-functions/functions-develop-vs) 頁面。

### <a name="debug-live-aspnet-apps-using-snappoints-and-logpoints-in-live-azure-applications"></a>使用即時 Azure 應用程式中的快照點和記錄點對即時 ASP.NET 應用程式進行偵錯

**15.5 的新功能**：快照集偵錯工具會在您感興趣的程式碼執行時，擷取實際執行應用程式的快照集。 若要指示偵錯工具擷取快照集，您可以在程式碼中設定快照點和記錄點。 偵錯工具可讓您清楚了解發生什麼問題，而不會影響實際執行應用程式的流量。 快照集偵錯工具可協助您大幅縮短為解決出現在生產環境之問題所花費的時間。

快照集合適用於 Azure App Service 中執行的下列 Web 應用程式：

* 執行 .NET Framework 4.6.1 或更新版本的 ASP.NET 應用程式。
* 在 Windows 上執行 .NET Core 2.0 或更新版本的 ASP.NET Core 應用程式。

如需詳細資訊，請參閱[使用快照點和記錄點對即時 ASP.NET 應用程式進行偵錯](../debugger/debug-live-azure-applications.md)。

## <a name="windows-app-development"></a>Windows 應用程式開發

### <a name="universal-windows-platform"></a>通用 Windows 平台

通用 Windows 平台 (UWP) 是適用於 Windows 10 的應用程式平台。 您只需要一個 API 集合、一個應用程式套件和一個觸達所有 Windows 10 裝置 (電腦、平板電腦、手機、Xbox、HoloLens、Surface Hub 等) 的 Store，就能開發 UWP app。 UWP 支援不同螢幕大小及各種互動模型，不論是觸控、滑鼠和鍵盤、遊戲控制器，還是手寫筆都沒問題。 UWP app 的核心概念是使用者想要在其「所有」裝置之間移動體驗到的事物，並想要使用最方便或最有效率的任何裝置來處理手邊的工作。

![通用 Windows 平台](../cross-platform/media/uwp_coreextensions.png)

&mdash;從 C#、Visual Basic、C++ 或 JavaScript&mdash; 中，選擇您慣用的開發語言，以建立適用於 Windows 10 裝置的通用 Windows 平台應用程式。 Visual Studio 2017 提供各種語言的 UWP app 範本，讓您可以建立適用於所有裝置的單一專案。 當工作完成時，您可以產生應用程式套件，並從 Visual Studio 提交給 Microsoft Store，以將您的應用程式提供給任何 Windows 10 裝置上的客戶。

**15.5 的新功能**：Visual Studio 2017 15.5 版提供 Windows 10 Fall Creators Update SDK (10.0.16299.0) 的最佳支援。 Windows 10 Fall Creators Update 也提供 UWP 開發人員許多增強功能。 以下是其中一些最重大的變更： 

* **針對 .NET Standard 2.0 的支援**<br/>除了簡化應用程式部署之外，Windows 10 Fall Creators Update 也是第一個提供 .NET Standard 2.0 支援的版本。 實際上，[.NET Standard](https://devblogs.microsoft.com/dotnet/introducing-net-standard/) 是任何 .NET 平台都能實作之基底類別庫的參考實作。 .NET Standard 的目標是讓 .NET 開發人員在其選擇工作的任何 .NET 平台之間，盡可能輕鬆地共用程式碼。
* **UWP 和 Win32 的最佳選擇**<br/>我們改進了 Windows 10 平台，提供[傳統型橋接器](/windows/uwp/porting/desktop-to-uwp-root)讓 Windows 10 更適用於所有 .NET 開發人員，不論其目前焦點是在 UWP、WPF、Windows Form 或 Xamarin。 透過 Visual Studio 2017 15.5 版中新增的應用程式套件專案類型，您可以像是針對 UWP 專案一樣，針對 WPF 或 Windows Forms 專案建立 Windows 應用程式套件。 封裝應用程式之後，您將享有所有 Windows 10 應用程式部署優點，並可選擇透過 Microsoft Store (適用於消費者應用程式) 或商務用 Microsoft Store 和教育用 Microsoft Store 進行散發。 由於已封裝應用程式可以存取桌面上的完整 UWP API 介面和 Win32 API，因此您現在可以使用 UWP API 和 Windows 10 功能逐漸將 WPF 和 Windows Forms 應用程式現代化。 此外，您可以將 Win32 元件加入 UWP 應用程式，在桌面上顯示所有 Win32 功能。

如需 UWP 的詳細資訊，請參閱[開發適用於通用 Windows 平台 (UWP) 的應用程式](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)頁面。

## <a name="mobile-app-development"></a>行動應用程式開發

### <a name="xamarin"></a>Xamarin

熟悉 C#、.NET 和 Visual Studio 的開發人員可以使用 Xamarin 來提供原生 Android、iOS 和 Windows 應用程式，以作為「.NET 的行動開發」工作負載的一部分。 開發人員在使用 Xamarin 開發行動應用程式時，可以不需要了解 Objective-C 或 Java 等機器碼語言，也能享有相同的功能和生產力，包括在 Android、iOS 和 Windows 裝置上進行遠端偵錯。

如需詳細資訊，請參閱 [Visual Studio 和 Xamarin](/xamarin/) 頁面。

### <a name="entitlements-editor"></a>權利編輯器

**15.3 的新功能**：針對 iOS 開發需求，我們已新增獨立權利編輯器。 它包含可輕鬆地瀏覽的使用者易記 UI。 若要啟動它，請按兩下 *plist* 檔案。

![Xamarin 的權利編輯器](media/xamarin-entitlements-editor.png)

### <a name="visual-studio-tools-for-xamarin"></a>Visual Studio Tools for Xamarin

**15.4 的新功能**：Xamarin Live 能讓開發人員直接在 iOS 和 Android 裝置上持續部署、測試及偵錯他們的應用程式。 下載 Xamarin Live Player 後 &mdash;可從 App Store 或 Google Play 取得&mdash;，您就可以配對裝置和 Visual Studio，並改革建置行動應用程式的方式。 這項功能現在已包含在 Visual Studio 中，於 [工具] > [選項] > [Xamarin] > [其他] > [啟用 Xamarin Live Player] 啟用。

![Xamarin Live Player 配對、部署和即時編輯模式的動畫](media/xamarinliveplayer.gif)

### <a name="support-for-google-android-emulator"></a>Google Android Emulator 的支援

**15.8 中的新功能**：當您使用 Hyper-V 時，現在可與其他以 Hyper-V 為基礎的技術 (例如 Hyper-V 虛擬機器、Docker 工具、HoloLens 模擬器等) 並行使用 Google 的 Android Emulator。 (此功能需要 Windows 10 2018 年 4 月更新或較新版本。)

![使用 Hyper-V 技術的 Google Android Emulator](media/xamarin-hyperv-android-emulator.png)

#### <a name="xamarinandroid-designer-split-view-editor"></a>Xamarin.Android Designer 分割檢視編輯器

也是 **15.8 中的新功能**：我們對 Xamarin.Android 的設計工具體驗進行了大幅改進。 其中一個亮點是新的分割檢視編輯器，可讓您同時建立、編輯及預覽版面配置。

![Xamarin.Android Designer 分割檢視編輯器](media/android-designer-split-view.png)

如需詳細資訊，請參閱[硬體加速以提升模擬器效能](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin)

### <a name="visual-studio-app-center"></a>Visual Studio 應用程式中心

**15.5 的新** 功能 Visual Studio App Center：適用于 &mdash; Android、iOS、macOS 和 Windows 應用程式的新功能 &mdash; ，具備管理應用程式生命週期所需的一切，包括自動化組建、在雲端中的實際裝置上進行測試、散發給搶鮮版（Beta）測試人員和應用程式商店，以及透過損毀與分析資料監視實際的使用方式。 所有功能都支援以 Objective-C、Swift、Java、C#、Xamarin 和 React Native 撰寫的應用程式。

  ![Visual Studio 應用程式中心測試環境](media/app-center-test-env.png)

如需詳細資訊，請參閱 [應用程式中心簡介：建立、測試、散發及監視雲端 blog 文章中的應用程式](https://blogs.msdn.microsoft.com/vsappcenter/introducing-visual-studio-app-center/) 。

## <a name="cross-platform-development"></a>跨平台開發

### <a name="redgate-data-tools"></a>Redgate Data Tools

為了將 DevOps 功能擴充到 SQL Server 資料庫開發，Visual Studio 現在提供 Redgate Data Tools。

隨附於 Visual Studio 2017 Enterprise：

* [Redgate ReadyRoll Core](https://www.red-gate.com/products/sql-development/sql-change-automation/?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) 可協助您開發移轉指令碼、使用原始檔控制管理資料庫變更，並且可以將 SQL Server 資料庫變更和應用程式變更的部署安全地自動化。
* [Redgate SQL Prompt Core](https://www.red-gate.com/products/sql-development/sql-prompt/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) 可協助您透過智慧型程式碼自動完成的協助，更快且更精確地撰寫 SQL。 SQL Prompt 會自動完成資料庫及系統物件和關鍵字，並在輸入期間提供資料行建議。 由於您不再需要記住所有資料行名稱或別名，這會使程式碼更加簡潔，並具有更少的錯誤。

隨附於所有版本的 Visual Studio 2017：

* [Redgate SQL Search](https://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) 可協助您跨多個資料庫快速尋找 SQL 片段和物件以提高產能。

如需詳細資訊，請參閱 [Redgate Data Tools in Visual Studio 2017](https://devblogs.microsoft.com/visualstudio/redgate-data-tools-in-visual-studio-2017/) (Visual Studio 2017 中的 Redgate Data Tools) 部落格文章。

### <a name="net-core"></a>.NET Core

.NET Core 是 .NET Standard 的一般用途、模組化、跨平台和開放原始碼實作，並且包含許多與 .NET Framework 相同的 API。

.NET Core 平台是由幾個元件所組成，其中包含 Managed 編譯器、執行階段、基底類別庫，以及許多應用程式模型 (例如 ASP.NET Core)。 .NET Core 支援三個主要作業系統：Windows、Linux 和 macOS。 您可以在裝置、雲端和內嵌/IoT 案例中使用 .NET Core。

而且，它現在包含 Docker 支援。

**15.3 的新功能**：Visual Studio 2017 版本 15.3 支援 .NET Core 2.0 開發 使用 .NET Core 2.0 需要分別下載和安裝 .NET Core 2.0 SDK。

如需詳細資訊，請參閱 [.Net Core 指南](/dotnet/core/index) 頁面。

## <a name="games-development"></a>遊戲開發

### <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity

我們已包含工具來協助開發跨平台以建立 2D 和 3D 遊戲與互動式內容，以作為「Unity 的遊戲開發」工作負載的一部分。 只需要建立一次，即可發行至 21 個平台，包含所有行動平台、WebGL、Mac、PC 和 Linux 桌面、Web 或使用 Visual Studio 2017 和 Unity 5.6 的主控台。

如需詳細資訊，請參閱 [Visual Studio Tools for Unity](/gamedev/unity/get-started/visual-studio-tools-for-unity.md) 頁面。

## <a name="ai-development"></a>AI 開發

### <a name="visual-studio-tools-for-ai"></a>Visual Studio Tools for AI

**15.5 的新功能**：立即使用 Visual Studio 的生產力功能，來加速 AI 創新。 使用內建程式碼編輯器功能，例如語法醒目顯示、IntelliSense 和文字自動格式化。 您可以透過逐步偵錯區域變數和模型，以互動方式來測試您本機環境中的深度學習應用程式。

  ![深度學習 IDE](../ai/media/about/ide.png)

如需詳細資訊，請參閱 [Visual Studio Tools for AI](../ai/about-ai-tools.md) 頁面。

## <a name="whats-next"></a>後續步驟

我們對 Visual Studio 2017 的更新通常附帶可大幅改善您開發體驗的新功能。 以下提供最值得您注意的更新回顧，目前處於實驗性預覽：

* **[Live Share](https://visualstudio.microsoft.com/services/live-share/)** 是一種新工具，可讓您透過組員共用程式碼基底和其內容，並直接從 Visual Studio 內取得即時雙向共同作業。 組員可透過 Live Share 來閱讀、瀏覽、編輯和偵錯您與其共用的專案，過程相當自然且安全。<br><br>如需詳細資訊，請參閱 [Live Share 常見問題集](/visualstudio/liveshare/faq)。<br><br>
* **[IntelliCode](https://visualstudio.microsoft.com/services/intellicode/)**：這項新功能使用了 AI 帶來更棒的內容感知程式碼完成以改善軟體開發，可引導開發人員遵循其小組的模式與風格進行編碼、找出難以發現的程式碼問題，並將程式碼檢閱聚焦於真正重要之處。 <br><br>如需詳細資訊，請參閱 [IntelliCode 常見問題集](/visualstudio/intellicode/faq)。

想深入了解 Visual Studio 2017 中還包含哪些內容嗎？ 請參閱 [Visual Studio 路程圖](/visualstudio/productinfo/vs2018-roadmap)頁面。

而且別忘了查看最新版本中， [Visual Studio 2019](whats-new-visual-studio-2019.md)。

## <a name="contact-us"></a>與我們連絡

為什麼要傳送意見反應給 Visual Studio 小組？ 我們極為重視客戶的意見反應。 它們是我們進步的動力。

如果您想為我們提供改善 Visual Studio 的建議，或是深入了解產品支援選項，請參閱[傳送意見反應給我們](feedback-options.md)頁面。

### <a name="report-a-problem"></a>回報問題

有時候，訊息並不足以表達您所遇到問題的所有影響。 如果您遇到 Visual Studio 停止回應、當機或其他效能問題的問題，您可以輕鬆地共用重現步驟和 (支援檔案（例如螢幕擷取畫面），以及使用「回報 **問題** 」工具) 的追蹤和堆積傾印檔案。 如需如何使用此工具的詳細資訊，請參閱 [如何報告問題](how-to-report-a-problem-with-visual-studio.md) 頁面。

## <a name="see-also"></a>另請參閱

* [Visual Studio 2017 版本資訊](/visualstudio/releasenotes/vs2017-relnotes)
* [Visual Studio 2017 SDK 的新功能](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md)
* [Visual C++ 的新功能](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [C# 的新功能](/dotnet/csharp/whats-new)
* [Team Foundation Server 的新功能](/azure/devops/server/whats-new)
* [Visual Studio for Mac 的新功能](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
* [Visual Studio 2019 的新功能](whats-new-visual-studio-2019.md)