---
title: Visual Studio 2019 的新功能
titleSuffix: ''
description: 了解 Visual Studio 2019 中的新功能。
ms.date: 05/28/2021
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 00bec66b-bcee-46f5-91d9-f73a2b469744
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 8664606877f5393a98a78e32c6d396e1a5bcf4c1
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687687"
---
# <a name="whats-new-in-visual-studio-2019"></a>Visual Studio 2019 的新功能

**[16.10 版](/visualstudio/releases/2019/release-notes/)的更新**

>[!div class="button"]
>[下載 Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

使用 Visual Studio 2019，您會獲得同類產品中最佳的工具和服務，任何開發人員、任何應用程式及任何平台均適用。 無論您是第一次使用 Visual Studio，還是使用了數年的時間，我們最新的版本都有很大的需要！

以下是最新功能的概要回顧：

* **[開發](#develop)**：利用改良的效能、即時程式碼清除及更好的搜尋結果，保持焦點和生產力。
* **[共同](#collaborate)** 作業：透過 Git 優先工作流程、即時編輯和偵錯工具，以及直接在 Visual Studio 中進行程式碼審核，享受自然的共同作業。
* **[Debug](#debug)**：反白顯示並流覽至特定值、優化記憶體使用量，以及取得應用程式執行的自動快照集。

如需此版本中所有新功能的完整清單，請參閱[版本資訊](/visualstudio/releases/2019/release-notes/)。

## <a name="develop"></a>開發

檢視下列影片以深入了解如何使用新功能來節省時間。 <br><br>*影片長度：3.00 分鐘*

> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>增強搜尋功能

先前稱為「快速啟動」，新的搜尋體驗將更快速且更有效。 現在，搜尋結果會隨著您的鍵入以動態方式顯示。 而且搜尋結果通常會包含命令的鍵盤快速鍵，讓您可以記住它們以供日後使用。

   ![Visual Studio 2019 中的新搜尋體驗動畫](media/vs-2019/new-search-feature.gif "Visual Studio 2019 中的新搜尋體驗。")

無論有無錯字，新的模糊搜尋邏輯都能找出您所需的任何項目。 因此，不論您要尋找命令、設定、文件或其他使用項目，新搜尋功能可讓您更輕鬆找到您要尋找的內容。

如需詳細資訊，請參閱 [使用 Visual Studio 搜尋](visual-studio-search.md)。

#### <a name="intelligent-search-service"></a>智慧型搜尋服務

**16.9 的新** 功能：使用雲端技術、人工智慧和機器學習服務，我們已改善搜尋結果。 現在，搜尋 Visual Studio 會產生更相關的結果，但也可協助您更輕鬆地探索產品功能。

如需詳細資訊，請參閱 [智慧型 Visual Studio 搜尋服務](https://devblogs.microsoft.com/visualstudio/intelligent-visual-studio-search-service/) 的 blog 文章。

### <a name="refactorings"></a>重構

C# 中有許多全新且非常有用的重構，讓您輕鬆就能組織您的程式碼。 它們顯示為燈泡中的建議，且包含動作，如將成員移動至介面或基底類別、調整命名空間以符合資料夾結構、將 foreach 迴圈轉換為 Linq 查詢等等。

   ![Visual Studio 2019 中的重構體驗動畫](media/vs-2019/refactorings.gif "Visual Studio 2019 中的重構體驗。")

只要按下 **Ctrl+.**，來叫用重構 然後選取您想要採取的動作。

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) 可使用人工智慧 (AI) 來強化您的軟體開發工作。 IntelliCode 在 GitHub 上的 2,000 個開放原始碼專案中訓練 (每個專案各有超過 100 顆星) 以產生建議。

![Visual Studio 2019 中的 IntelliCode 動畫](media/vs-2019/IntelliCode.gif "IntelliCode Visual Studio 2019。")

以下是 Visual Studio IntelliCode 可協助提高生產力的幾種方式：

* 提供內容感知的程式碼完成
* 引導開發人員遵守所屬團隊的模式與風格
* 找出難以捕捉的程式碼問題
* 將注意力放在真正重要的區域，專注在程式碼檢閱上

一開始以 Visual Studio 的延伸模組形式提供 IntelliCode 預覽時，我們僅支援 C#。 現在，我們也新增了對 C++ 和 XAML 的「內建」支援，以作為 **16.1 版的新功能** (不過，對 C++ 和 TypeScript/JavaScript 的支援目前仍為預覽狀態)。

如果您使用 C#，我們也新增了以您的程式碼訓練自訂模型的能力。

如需 IntelliCode 的詳細資訊，請參閱 [Announcing the general availability of IntelliCode plus a sneak peek](https://devblogs.microsoft.com/visualstudio/announcing-the-general-availability-of-intellicode-plus-a-sneak-peek/) (宣告 IntelliCode 正式運作與搶先預覽) 以及 [Code more, scroll less with Visual Studio IntelliCode](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/) (使用 Visual Studio IntelliCode 撰寫更多程式碼並捲動更少) 部落格文章。

### <a name="code-cleanup"></a>程式碼清除

新的程式碼清除命令會與新文件健康狀態指標搭配。 您可以使用這個新命令，以單一動作 (或按一下按鈕) ，來識別並修正警告和建議。

清除作業會設定程式碼格式，並套用由[目前的設定](code-styles-and-code-cleanup.md)和 [.editorconfig 檔案](create-portable-custom-editor-options.md)所建議的任何程式碼修正。

   ![Visual Studio 2019 中的新程式碼清除控制項螢幕擷取畫面](media/vs-2019/code-cleanup-profile.png "Visual Studio 2019 中的新程式碼清理控制項。")

您也可以將修正程式集合儲存為設定檔。 例如，如果您有一組較少的目標修正程式經常在編寫程式碼時套用，然後在程式碼檢閱之前會套用另一組完整的修正程式，您可以將設定檔設定為處理這些不同的工作。

   ![Visual Studio 2019 中設定程式碼清除控制項的螢幕擷取畫面](media/vs-2019/code-cleanup-profile-configure.png "Visual Studio 2019 中的設定程式碼清理控制項。")

### <a name="per-monitor-aware-pma-rendering"></a>個別監視器感知 (PMA) 轉譯

如果您以不同顯示比例因素設定監視器，或從遠端連線到具有不同於您主要裝置顯示比例因素的機器，您可能會發現 Visual Studio 的顯示模糊，或以錯誤的比例轉譯。

Visual Studio 2019 的發行，代表我們正著手將 Visual Studio 調整為個別監視器感知 (PMA) 應用程式。 現在，不論您使用的顯示縮放比例為何，Visual Studio 均可正確轉譯。

   ![Visual Studio 2019 中的個別監視器感知 (PMA) 轉譯](media/vs-2019/pma-dpi-scaling.png "每一監視器感知 (PMA 在 Visual Studio 2019 中) 轉譯。")

如需詳細資訊，請參閱[使用 Visual Studio 2019 獲得更好的多監視器體驗](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/) \(英文\) 部落格文章。

### <a name="test-explorer"></a>測試總管

**16.2 的新** 功能：我們已更新 Test Explorer，以提供更好的處理大型測試集、更輕鬆的篩選、更容易探索的命令、索引標籤式的播放清單，以及可自訂的欄，讓您微調顯示的測試資訊。

   ![顯示測試總管中的使用者介面改良功能的螢幕擷取畫面](media/vs-2019/test-explorer-ui.png "測試瀏覽器中的使用者介面改進。")

### <a name="net-core"></a>.NET Core

**16.3 的新** 功能：我們已包含 .net Core 3.0 的支援。 Microsoft 的跨平臺、開放原始碼 &mdash; 及完全支援。

如需詳細資訊，請參閱 [宣佈 .Net Core 3.0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/) 的 blog 文章。

## <a name="collaborate"></a>共同作業

檢視下列影片以深入了解如何進行團隊合作來解決問題。 <br><br>*影片長度：4.22 分鐘*

> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="git-first-workflow"></a>Git 優先工作流程

開啟 Visual Studio 2019 時，您會注意到新的開始視窗。

   ![Visual Studio 2019 中的新開始視窗螢幕擷取畫面](media/vs-2019/start-window-dark.png "Visual Studio 2019 中的新開始視窗。")

開始視窗會顯示數個選項，協助您快速編寫程式碼。 我們放置的選項可先複製，或從存放庫中簽出程式碼。

   ![Visual Studio 2019 中的「Git 優先」體驗動畫](media/vs-2019/git-first.gif "Visual Studio 2019 中的「Git 優先」體驗。")

開始視窗也包含開啟專案或解決方案、開啟本機資料夾，或建立新專案的選項。

如需詳細資訊，請參閱 [取得程式碼：我們如何設計新的 Visual Studio 開始視窗的](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/) blog 文章。

### <a name="git-productivity"></a>Git 生產力

**16.8** 中的新功能： Git 現在是 Visual Studio 2019 中的預設版本控制體驗。 我們已根據您在過去兩個版本中的意見反應，建立功能集並逐一查看。 所有人現在都已預設開啟新的體驗。 您可以從新的 Git 功能表複製、建立或開啟存放庫。 使用整合式 Git 工具視窗來認可和推送程式碼的變更、管理分支、隨時掌握遠端存放庫的最新狀態，以及解決合併衝突。

如需詳細資訊，請參閱 [Visual Studio 頁面中的 Git 體驗](../version-control/git-with-visual-studio.md) 。

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) 這項開發人員服務可讓您與組員共用程式碼庫和其中的內容，並直接從 Visual Stuido 中進行即時雙向共同作業。 組員可透過 Live Share 來閱讀、瀏覽、編輯和偵錯您與其共用的專案，過程相當自然且安全。

Visual Studio 2019 預設會安裝這項服務。

![顯示 Visual Studio 2019 中 Live Share 共同作業功能的動畫](media/vs-2019/live-share.gif "Visual Studio 2019 中的 Live Share 協同作業功能。")

如需詳細資訊，請參閱 [Visual Studio Live Share 提供即時程式碼檢閱與互動式教學](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) \(英文\) 部落格文章和 [Visual Studio 2019 現已包含 Live Share](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/) \(英文\) 部落格文章。

### <a name="integrated-code-reviews"></a>整合式程式碼檢閱

此次推出新的延伸模組，您可以下載並與 Visual Studio 2019 搭配使用。 使用這個新的延伸模組，您可以檢閱、執行偵錯要求，或是從您的團隊提取這些要求，而無需離開 Visual Studio。 我們支援 GitHub 和 Azure DevOps 存放庫中的程式碼。

   ![Visual Studio 2019 中新提取要求延伸模組的螢幕擷取畫面](media/vs-2019/pr-experience.png "Visual Studio 2019 中的新提取要求延伸模組。")

如需詳細資訊，請參閱 [Code reviews using the Visual Studio Pull Requests extension](https://devblogs.microsoft.com/visualstudio/code-reviews-using-the-visual-studio-pull-requests-extension/) (使用 Visual Studio 提取要求延伸模組檢閱程式碼) 部落格文章。

## <a name="debug"></a>偵錯

檢視下列影片以深入了解如何在進行偵錯時使用精確目標設定來集中精力。 <br><br>*影片長度：3.54 分鐘*

> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>效能提升

我們採用僅一次的專屬 C++ 資料中斷點，並加以修改以用於 .NET Core 應用程式。

   ![在 Visual Studio 2019 中顯示偵錯資料中斷點的動畫](media/vs-2019/debug-data-breakpoints.gif "Visual Studio 2019 中的 debug 資料中斷點。")

因此無論您在 C++ 或 .NET Core 中編寫程式碼，資料中斷點都是一般中斷點的理想替代方法。 像是尋找要修改或新增或從清單中移除的全域物件，這類情節也非常適合使用資料中斷點。

如果您是開發大型應用程式的 C++ 開發人員，Visual Studio 2019 還提供處理序外的符號，可讓您對這些應用程式偵錯，而不會發生記憶體相關的問題。

### <a name="search-while-debugging"></a>偵錯時搜尋

在 [監看式] 視窗中查看一組值中的字串，您先前可能已進行過。 在 Visual Studio 2019 中，我們在 [監看式]、[區域變數] 和 [自動變數] 視窗中新增了搜尋功能，可協助您尋找物件和值。

   ![在 Visual Studio 2019 中顯示偵錯搜尋視窗的動畫](media/vs-2019/debug-window-search.gif "Visual Studio 2019 中的 debug 搜尋視窗。")

在 [監看式]、[區域變數] 和 [自動變數] 視窗的顯示方式，您也能加以格式化。 ) 按兩下任何視窗中的其中一個專案來選取 (，然後新增逗號 ( "，" ) 以存取可能格式規範的下拉式清單，其中每個都包含其預期效果的描述。

   ![Visual Studio 2019 中的新 [監看式] 視窗和格式值功能](media/search-watch-window.png "Visual Studio 2019 中的新監看式視窗和格式值功能。")

如需詳細資訊，請參閱 [Visual Studio 2019 中的增強功能：在 [監看式]、[自動變數] 和 [區域變數] 視窗文章中搜尋物件和屬性](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) 。

### <a name="snapshot-debugger"></a>快照集偵錯工具

在雲端中取得應用程式執行的快照集，以查看確切的狀況。 (僅 Visual Studio Enterprise 提供此功能)

   ![顯示 Visual Studio 2019 Enterprise 中的快照集偵錯工具動畫](media/vs-2019/snapshot-debugger.gif "Visual Studio 2019 Enterprise 中的快照偵錯工具。")

我們也新增對 Azure VM 上執行的目標 ASP.NET (Core 與傳統型) 應用程式的支援。 此外，我們新增對Azure Kubernetes Service 中所執行應用程式的支援。 快照集偵錯工具可協助您大幅縮短為解決出現在生產環境之問題所花費的時間。

如需詳細資訊請參閱[使用快照偵錯工具針對即時 ASP.NET Azure 應用程式進行偵錯](../debugger/debug-live-azure-applications.md)頁面，以及[介紹 Visual Studio Enterprise 2019 的時間移動偵錯](https://devblogs.microsoft.com/visualstudio/introducing-time-travel-debugging-for-visual-studio-enterprise-2019/) \(英文\) 部落格文章。

### <a name="microsoft-edge-insider-support"></a>Microsoft Edge Insider 支援

**16.2 中的新** 功能：您可以在 JavaScript 應用程式中設定中斷點，並使用 [Microsoft Edge Insider](https://www.microsoftedgeinsider.com/) 瀏覽器啟動 debug 會話。 當您這樣做的時候，Visual Studio 會在已啟用偵錯功能的情況下開啟新的瀏覽器視窗，讓您可以用來在 Visual Studio 內逐步執行應用程式 JavaScript。

   ![瀏覽器中顯示 JavaScript 程式碼轉譯的螢幕擷取畫面](media/vs-2019/edge-chromium-breakpoint.png "瀏覽器中的 JavaScript 程式碼轉譯。")

### <a name="pinnable-properties-tool"></a>可釘選屬性工具

**16.4 的新** 功能：現在，使用新的可釘選屬性工具進行偵錯工具時，可更輕鬆地依屬性來識別物件。 只要將游標暫留在您要在 [監看式]、[自動變數] 和 [區域變數] 視窗的偵錯工具視窗中顯示的屬性上，選取釘選圖示，即可立即在視窗頂端看到您要尋找的資訊！

   ![顯示如何使用可釘選屬性工具在 Visual Studio 偵錯工具中釘選屬性的動畫](media/vs-2019/debugger-pinnable-properties.gif "使用可釘選屬性工具，在 Visual Studio 偵錯工具中釘選屬性。")

如需詳細資訊，請參閱 [可釘選屬性： Debug & 以您的方式將 Managed 物件顯示為您](https://devblogs.microsoft.com/visualstudio/pinnable-properties-debug-display-managed-objects-your-way/) 的 blog 文章。

## <a name="whats-next"></a>後續步驟

我們對 Visual Studio 2019 的更新通常附帶可大幅改善您開發體驗的新功能。 若要深入瞭解我們最新的創新，請參閱 [Visual Studio 的 Blog](https://devblogs.microsoft.com/visualstudio/)。 如需我們在預覽版本中發行之內容的記錄，請參閱 [Preview 版本](/visualstudio/releases/2019/release-notes-preview/)資訊。 如需我們接下來打算發行的內容清單，請參閱 [Visual Studio 藍圖](/visualstudio/productinfo/vs-roadmap)。

同時，這裡有一項新功能，目前正在運作。

- **改良 Visual Studio 2019 (Preview) 的 Git 體驗**

   雖然新的 Git 版本控制體驗現已在 Visual Studio 2019 [16.8 版](/visualstudio/releases/2019/release-notes/)中預設為開啟，但我們仍會繼續新增功能，以增強最新預覽版本的體驗。

   如需詳細資訊，請參閱 [Visual Studio 頁面中的版本控制](/visualstudio/version-control/) 。

如需 Visual Studio 2019 預覽版本的詳細資訊 &mdash; ，如果您想要試用， &mdash; 請參閱 **[Visual Studio 預覽](https://aka.ms/vspreview/)** 頁面。

> [!TIP]
> 若要深入瞭解我們的下一版，請參閱 **[Visual Studio 2022](https://devblogs.microsoft.com/visualstudio/visual-studio-2022/)** 的 blog 文章。

## <a name="give-us-feedback"></a>提供意見反應

為什麼要傳送意見反應給 Visual Studio 小組？ 我們極為重視客戶的意見反應。 它們是我們進步的動力。

* 如果您想要提出改善 Visual Studio 的建議，可以使用[建議功能](suggest-a-feature.md)工具。

* 如果您遇到 Visual Studio 停止回應、當機或其他效能問題的問題，您可以使用 [回報 [問題](how-to-report-a-problem-with-visual-studio.md) ] 工具，輕鬆地與我們分享重現步驟和支援檔案。

## <a name="see-also"></a>另請參閱

* [Visual Studio 檔中的新功能](whats-new-visual-studio-docs.md)
* [Visual Studio 2019 版本資訊](/visualstudio/releases/2019/release-notes/)
* [Visual Studio 2019 for Mac 版本資訊](/visualstudio/releasenotes/vs2019-mac-relnotes/)
* [Visual Studio 2019 SDK 的新功能](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Visual Studio 中 C++ 的新功能](/cpp/overview/what-s-new-for-visual-cpp-in-visual-studio/)
* [C # 9.0 的新功能](/dotnet/csharp/whats-new/csharp-9)
* [.NET 5 的新功能](/dotnet/core/dotnet-five)
* [.NET Framework 的新功能](/dotnet/framework/whats-new/)
* [Microsoft Build 會議](https://www.microsoft.com/build)
* [Microsoft Ignite 會議](https://www.microsoft.com/ignite)
