---
title: Visual Studio 2019 的新功能
titleSuffix: ''
description: 了解 Visual Studio 2019 中的新功能。
ms.date: 04/03/2019
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 00bec66b-bcee-46f5-91d9-f73a2b469744
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: b38f75f1172e96e3dc2576a199949fdbb0c32f68
ms.sourcegitcommit: 40393347a36779230d128f2355a911632a8d458e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58866740"
---
# <a name="whats-new-in-visual-studio-2019"></a>Visual Studio 2019 的新功能

**已針對 [16.0 版](/visualstudio/releases/2019/release-notes/)更新**

>[!div class="button"]
>[下載 Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

使用 Visual Studio 2019，您會獲得同類產品中最佳的工具和服務，任何開發人員、任何應用程式及任何平台均適用。 無論您是第一次使用 Visual Studio，或是已使用多年，這個新版本還是有許多好用的功能！

以下是新增功能的概要回顧：

* **[開發](#develop)**：透過改善的效能、即時程式碼清除及更好的搜尋結果，專注於目標並保持生產力。
* **[共同作業](#collaborate)**：透過雲端優先工作流程、即時編輯和偵錯，以及直接在 Visual Studio 中檢閱程式碼，享受自然的共同作業。
* **[偵錯](#debug)**：反白顯示並巡覽至特定值、最佳化記憶體使用，然後自動建立應用程式執行的快照集。

如需此版本中所有新功能的完整清單，請參閱[版本資訊](/visualstudio/releases/2019/release-notes/)。 

## <a name="develop"></a>開發

使用新功能節省時間。
<br><br>
> [!VIDEO https://www.youtube.com/embed/n5sJ4EewKGk]

### <a name="improved-search"></a>增強搜尋功能

先前稱為「快速啟動」，新的搜尋體驗將更快速且更有效。 現在，搜尋結果會隨著您的輸入以動態方式顯示。 此外，搜尋結果通常會包含命令的鍵盤快速鍵，讓您輕鬆記憶，以便日後使用。

   ![Visual Studio 2019 中的新搜尋體驗動畫](media/vs-2019/new-search-feature.gif)

無論有無錯字，新的模糊搜尋邏輯都能找出您所需的任何項目。 因此，不論您要尋找命令、設定、文件或其他使用項目，新搜尋功能可讓您更輕鬆找到您要尋找的內容。

### <a name="refactorings"></a>重構

新的 C# 重構可輕鬆地組織您的程式碼。 只要按下 **Ctrl+.**，來叫用重構 然後選取您想要採取的動作。 

   ![Visual Studio 2019 中的重構體驗動畫](media/vs-2019/refactorings.gif)

我們已新增許多新的重構，包括可讓您包裝方法參數的重構。

### <a name="intellicode"></a>IntelliCode

[Visual Studio IntelliCode](/visualstudio/intellicode/) 是使用人工智慧 (AI) 以改善軟體開發工作的延伸模組。 IntelliCode 在 GitHub 上的 2,000 個開放原始碼專案中訓練 (每個專案各有超過 100 顆星) 以產生建議。

 ![Visual Studio 2019 中的 IntelliCode 動畫](media/vs-2019/IntelliCode.gif)

以下是 Visual Studio IntelliCode 可協助提高生產力的幾種方式：

* 提供內容感知的程式碼完成
* 引導開發人員遵守所屬團隊的模式與風格
* 找出難以捕捉的程式碼問題
* 將注意力放在真正重要的區域，專注在程式碼檢閱上

當我們最初預覽適用於 Visual Studio 的 IntelliCode 延伸模組時，最早僅支援 C#。 現在，我們也在 Visual Studio 中新增了對 C++ 和 XAML 的支援。

如果您使用 C#，我們也新增了以您的程式碼訓練自訂模型的能力。

如需 IntelliCode 的詳細資訊，請參閱[使用 Visual Studio IntelliCode 編寫更多程式碼、捲動更少](https://devblogs.microsoft.com/visualstudio/code-more-scroll-less-with-visual-studio-intellicode/) \(英文\) 部落格文章。 

### <a name="code-cleanup"></a>程式碼清除

新的程式碼清除命令會與新文件健康狀態指標搭配。 您可以使用這個新的命令來找出警告與建議，並透過按一下按鈕進行修正。

清除作業會將程式碼格式化，並套用由[目前的設定](code-styles-and-quick-actions.md)、[.editorconfig 檔案](create-portable-custom-editor-options.md)，或 [Roslyn 分析器](../code-quality/roslyn-analyzers-overview.md)所建議的任何程式碼修正。

   ![Visual Studio 2019 中的新程式碼清除控制項螢幕擷取畫面](media/vs-2019/code-cleanup-profile.png)

您也可以將修正程式集合儲存為設定檔。 例如，如果您有一組較少的目標修正程式經常在編寫程式碼時套用，然後在程式碼檢閱之前會套用另一組完整的修正程式，您可以將設定檔設定為處理這些不同的工作。

   ![Visual Studio 2019 中的新程式碼清除控制項螢幕擷取畫面](media/vs-2019/code-cleanup-profile-configure.png)

## <a name="collaborate"></a>共同作業

團隊合作，以解決問題。
<br><br>
> [!VIDEO https://www.youtube.com/embed/dKLJsiK1QU8]

### <a name="cloud-first-workflow"></a>雲端優先工作流程

開啟 Visual Studio 2019 時，您會注意到新的開始視窗。

   ![Visual Studio 2019 中的新開始視窗螢幕擷取畫面](media/vs-2019/start-window-dark.png)

開始視窗會顯示數個選項，協助您快速編寫程式碼。 我們放置的選項可先複製，或從存放庫中簽出程式碼。  

   ![Visual Studio 2019 中的「Git 優先」體驗動畫](media/vs-2019/git-first.gif)

開始視窗也包含開啟專案或解決方案、開啟本機資料夾，或建立新專案的選項。

如需詳細資訊，請參閱 [Get to code:How we designed the new Visual Studio start window](https://devblogs.microsoft.com/visualstudio/get-to-code-how-we-designed-the-new-visual-studio-start-window/) (開始撰寫程式碼：我們如何設計新的 Visual Studio 啟動視窗) 部落格文章。

### <a name="live-share"></a>Live Share

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) 這個開發人員服務可讓您與組員共用程式碼庫和其中的內容，並直接從 Visual Stuido 中進行即時雙向共同作業。 組員可透過 Live Share 來閱讀、瀏覽、編輯和偵錯您與其共用的專案，過程相當自然且安全。

Visual Studio 2019 預設會安裝這項服務。

![顯示 Visual Studio 2019 中 Live Share 共同作業功能的動畫](media/vs-2019/live-share.gif)

如需詳細資訊，請參閱 [Visual Studio Live Share 提供即時程式碼檢閱與互動式教學](https://devblogs.microsoft.com/visualstudio/visual-studio-live-share-for-real-time-code-reviews-and-interactive-education/) \(英文\) 部落格文章和 [Visual Studio 2019 現已包含 Live Share](https://devblogs.microsoft.com/visualstudio/live-share-now-included-with-visual-studio-2019/) \(英文\) 部落格文章。

### <a name="integrated-code-reviews"></a>整合式程式碼檢閱

此次推出新的延伸模組，您可以下載並與 Visual Studio 2019 搭配使用。 使用這個新的延伸模組，您可以檢閱、執行偵錯要求，或是從您的團隊提取這些要求，而無需離開 Visual Studio。 我們支援 GitHub 和 Azure DevOps 存放庫中的程式碼。

   ![Visual Studio 2019 中的新開始視窗螢幕擷取畫面](media/vs-2019/pr-experience.png)

若要立即開始，您可以從 Visual Studio Marketplace 下載[適用於 Visual Studio 的提取要求](https://aka.ms/pr4vs)延伸模組。

## <a name="debug"></a>偵錯

精確找出目標。
<br><br>
> [!VIDEO https://www.youtube.com/embed/hr72Fs8n_9c]

### <a name="performance-gains"></a>效能提升

我們採用僅一次的專屬 C++ 資料中斷點，並加以修改以用於 .NET Core 應用程式。

   ![在 Visual Studio 2019 中顯示偵錯資料中斷點的動畫](media/vs-2019/debug-data-breakpoints.gif)

因此無論您在 C++ 或 .NET Core 中編寫程式碼，資料中斷點都是一般中斷點的理想替代方法。 像是尋找要修改或新增或從清單中移除的全域物件，這類情節也非常適合使用資料中斷點。 

如果您是開發大型應用程式的 C++ 開發人員，Visual Studio 2019 還提供處理序外的符號，可讓您對這些應用程式偵錯，而不會發生記憶體相關的問題。

### <a name="search-while-debugging"></a>偵錯時搜尋

在 [監看式] 視窗中查看一組值中的字串，您先前可能已進行過。 在 Visual Studio 2019 中，我們在 [監看式]、[區域變數] 和 [自動變數] 視窗中新增了搜尋功能，可協助您尋找物件和值。

   ![在 Visual Studio 2019 中顯示偵錯搜尋視窗的動畫](media/vs-2019/debug-window-search.gif)

您也可以設定值在 [監看式]、[區域變數] 與 [自動變數] 視窗內的顯示方式。在任一視窗中的其中一個項目上按兩下，並新增逗號 (",") 來存取可用格式指定名稱的下拉式清單，其中每一個都包含其預期效果的描述。

   ![Visual Studio 2019 中的新 [監看式] 視窗和格式值功能](media/search-watch-window.png)

如需詳細資訊，請參閱 [Enhanced in Visual Studio 2019:Search for Objects and Properties in the Watch, Autos, and Locals Windows](https://devblogs.microsoft.com/visualstudio/enhanced-in-visual-studio-2019-search-for-objects-and-properties-in-the-watch-autos-and-locals-windows/) (Visual Studio 2019 的增強功能：在監看式、自動變數和區域變數視窗中搜尋物件和屬性) 部落格文章。

### <a name="snapshot-debugger"></a>快照集偵錯工具

在雲端中取得應用程式執行的快照集，以查看確切的狀況。(僅 Visual Studio Enterprise 提供此功能)

   ![顯示 Visual Studio 2019 Enterprise 中的快照集偵錯工具動畫](media/vs-2019/snapshot-debugger.gif)

我們也新增對 Azure VM 上執行的目標 ASP.NET (Core 與傳統型) 應用程式的支援。 此外，我們新增對Azure Kubernetes Service 中所執行應用程式的支援。 快照集偵錯工具可協助您大幅縮短為解決出現在生產環境之問題所花費的時間。

如需詳細資訊，請參閱[使用快照偵錯工具偵錯即時 ASP.NET Azure 應用程式](../debugger/debug-live-azure-applications.md)頁面。

## <a name="give-us-feedback"></a>提供意見反應

為什麼要傳送意見反應給 Visual Studio 小組？ 我們極為重視客戶的意見反應。 它們是我們進步的動力。

* 如果您想要提出改善 Visual Studio 的建議，可以使用[提供建議](talk-to-us.md#i-want-to-make-a-suggestion-about-visual-studio-features)工具。

* 如果您遇到停止回應、當機或其他效能問題，則可以使用[回報問題](talk-to-us.md#i-want-to-report-a-problem-with-visual-studio)工具，輕鬆地與我們分享重現步驟和支援檔案。

## <a name="see-also"></a>另請參閱

* [隆重發表 Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/visual-studio-2019-code-faster-work-smarter-create-the-future/)
* [Visual Studio 2019 版本資訊](/visualstudio/releases/2019/release-notes/)
* [Visual Studio 2019 SDK 的新功能](../extensibility/whats-new-visual-studio-2019-sdk.md)
* [Visual Studio 2019 for Mac 現已推出](https://devblogs.microsoft.com/visualstudio/visual-studio-2019-for-mac-is-now-available/)
* [Microsoft Connect(); 2018 會議](https://www.microsoft.com/connectevent)
