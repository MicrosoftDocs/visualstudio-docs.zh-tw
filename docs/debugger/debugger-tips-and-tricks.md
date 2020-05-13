---
title: 調試器中的提示和技巧
description: 瞭解 Visual Studio 調試器支援的一些鮮為人知的功能
ms.custom: seodec18
ms.date: 06/15/2018
ms.topic: conceptual
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 5262d8b1-2648-429e-85d5-90fcaadfb362
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf8d6df020694bb10fe4f3f051551056549d5673
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302214"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>在視覺化工作室中學習調試器的生產力提示和技巧

閱讀本主題，瞭解 Visual Studio 調試器的一些工作效率提示和技巧。 有關調試器的基本功能，請參閱[首先查看調試器](../debugger/debugger-feature-tour.md)。 在本主題中，我們將介紹功能教程中未包括的一些區域。

## <a name="pin-data-tips"></a>固定資料提示

如果在調試時經常將滑鼠懸停在資料提示上，則可能需要為變數固定資料提示，以便自己快速訪問。 即使在重新開機後，該變數也會保持固定狀態。 要固定資料提示，請在懸停在資料提示上時按一下引腳圖示。 您可以固定多個變數。

![固定資料提示](../debugger/media/dbg-tips-data-tips-pinned.png "固定資料提示")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>編輯代碼並繼續調試（C#、VB、C++）

在大多數由 Visual Studio 支援的語言中，您可以在調試會話中編輯代碼並繼續調試。 要使用此功能，請在調試器中暫停時使用游標按一下代碼，進行編輯，然後按**F5、F10**或**F11**繼續調試。 **F5**

![編輯並繼續調試](../debugger/media/dbg-tips-edit-and-continue.gif "編輯並繼續")

有關使用該功能和功能限制的詳細資訊，請參閱[編輯並繼續](../debugger/edit-and-continue.md)。

## <a name="edit-xaml-code-and-continue-debugging"></a>編輯 XAML 代碼並繼續調試

要在調試會話期間修改 XAML 代碼，請參閱[使用 XAML 熱重載入 編寫和調試運行 XAML 代碼](../xaml-tools/xaml-hot-reload.md)。

## <a name="debug-issues-that-are-hard-to-reproduce"></a>難以重現的調試問題

如果在應用中重新創建特定狀態很困難或耗時，請考慮使用條件中斷點是否會有所説明。 您可以使用[條件中斷點](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)和篩選器中斷點，以避免在應用進入所需狀態（例如變數存儲不良資料的狀態）之前侵入應用代碼。 您可以使用運算式、篩選器、命中計數等設置條件。

#### <a name="to-create-a-conditional-breakpoint"></a>創建條件中斷點

1. 按右鍵中斷點圖示（紅色球）並選擇 **"條件**"。

2. 在 **"中斷點設置"** 視窗中，鍵入運算式。

    ![條件中斷點](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "條件中斷點")

3. 如果您對其他類型的條件感興趣，請在 **"中斷點設置"** 對話方塊中選擇 **"篩選**"而不是 **"條件運算式**"，然後按照篩選器提示操作。

## <a name="configure-the-data-to-show-in-the-debugger"></a>配置要在調試器中顯示的資料

對於 C#、Visual Basic 和C++（僅限C++/CLI 代碼），您可以使用[DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)屬性告訴調試器要顯示哪些資訊。 對於C++代碼，您可以使用[Natvis 視覺化進行相同的操作](create-custom-views-of-native-objects.md)。

## <a name="change-the-execution-flow"></a>變更執行流程

當調試器在程式碼上暫停後，使用滑鼠抓取左側的黃色箭頭指標。 將黃色箭頭指標移動到代碼執行路徑中的不同點。 然後，使用 F5 或步驟命令繼續運行應用。

![移動執行指標](../debugger/media/dbg-tour-move-the-execution-pointer.gif "移動執行指標")

藉由變更執行流程，您可以執行一些作業，例如測試不同的程式碼執行路徑，或重新執行程式碼而不重新啟動偵錯工具。

> [!WARNING]
> 您通常需要謹慎使用這項功能，您會在工具提示中看到一則警告。 也可能會看到其他警告。 移動指標無法將應用還原到較早的應用程式狀態。

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>跟蹤範圍外物件（C#，可視基本）

使用調試器視窗（如**Watch**視窗）輕鬆查看變數。 但是，當變數超出 **"監視"** 視窗中的範圍時，您可能會注意到該變數已灰顯。在某些應用方案中，即使變數已出範圍，變數的值也可能更改，您可能需要密切監視它（例如，變數可能會收集垃圾）。 您可以通過在 **"監視"** 視窗中為其創建物件識別碼 來跟蹤該變數。

#### <a name="to-create-an-object-id"></a>創建物件識別碼

1. 在要跟蹤的變數附近設置中斷點。

2. 啟動調試器 （**F5**）， 並在中斷點停止。

3. 在 **"區域變數"** 視窗中查找變數（**調試> Windows >區域變數**），按右鍵該變數，然後選擇 **"使物件識別碼**"。

    ![創建物件識別碼](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. 您應該在**$****"區域變數"** 視窗中看到加號。 此變數是物件識別碼。

5. 按右鍵物件識別碼 變數並選擇 **"添加監視**"。

有關詳細資訊，請參閱[創建物件識別碼](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds)。

## <a name="view-return-values-for-functions"></a>查看函數的傳回值

要查看函數的傳回值，請查看在單一步驟代碼時顯示在 **"自動"** 視窗中的函數。 要查看函數的傳回值，請確保感興趣的函數已執行（如果當前在函式呼叫時已停止，請按**F10）。** 如果視窗已關閉，請使用**調試> Windows >自動**"打開 **"自動"** 視窗。

![自動視窗](../debugger/media/dbg-tips-autos-window.png "自動視窗")

此外，您可以在 **"立即"** 視窗中輸入函數以查看傳回值。 （使用**調試> Windows > 立即**打開它。

![即時視窗](../debugger/media/dbg-tips-immediate-window.png "即時視窗")

您還可以在 **"監視"** 和 **"立即"** 視窗中使用`$ReturnValue`[偽變數](../debugger/pseudovariables.md)，例如 。

## <a name="inspect-strings-in-a-visualizer"></a><a name="string_visualizer"></a>檢查視覺化檢視中的字串

使用字串時，查看整個格式化字串會很有説明。 要查看純文字、XML、HTML 或 JSON 字串，請按一下放大鏡圖示![VisualizerIcon，](../debugger/media/dbg-tips-visualizer-icon.png "視覺化檢視圖示")同時懸停在包含字串值的變數上。

![打開字串視覺化檢視](../debugger/media/dbg-tips-string-visualizers.png "OpenString視覺化器")

字串視覺化檢視可以説明您根據字串類型找出字串是否格式錯誤。 例如，空白**值**欄位指示視覺化檢視類型無法識別字串。 有關詳細資訊，請參閱[字串視覺化器對話方塊](../debugger/string-visualizer-dialog-box.md)。

![JSON 字串視覺化器](../debugger/media/dbg-tips-string-visualizer-json.png "JSONString視覺化器")

對於在調試器視窗中顯示的一些其他類型的類型（如 DataSet 和 DataTable 物件），您還可以打開內置視覺化檢視。

## <a name="break-into-code-on-handled-exceptions"></a>在已處理的異常上侵入代碼

調試器會侵入未處理的異常代碼。 但是，處理的異常（如`try/catch`塊內發生的異常）也可以是 Bug 的來源，您可能需要在它們發生時進行調查。 通過將調試器配置為分解處理的異常的代碼，還可以通過在 **"例外設置"** 對話方塊中配置選項來設置調試器。 通過選擇 **"調試> Windows >異常設置**"來打開此對話方塊。

"**例外設置"** 對話方塊允許您告訴調試器在特定異常上侵入代碼。 在下圖中，每當發生 時`System.NullReferenceException`，調試器都會侵入您的代碼。 有關詳細資訊，請參閱[管理異常](../debugger/managing-exceptions-with-the-debugger.md)。

![例外設置對話方塊](../debugger/media/dbg-tips-exception-settings.png "例外設置對話方塊")

## <a name="debug-deadlocks-and-race-conditions"></a>調試鎖死和競爭條件

如果需要調試多執行緒應用常見的問題類型，則在調試時查看執行緒的位置通常有助於查看執行緒的位置。 您可以使用"**源中顯示執行緒**"按鈕輕鬆執行此操作。

#### <a name="to-show-threads-in-your-source-code"></a>在原始程式碼中顯示執行緒

1. 調試時，按一下"**源"中的"顯示執行緒****"按鈕"在調試**工具列![中顯示源中的執行緒](../debugger/media/dbg-multithreaded-show-threads.png "執行緒標記")"。

2. 查看來源視窗左邊的裝訂邊。 在這條線上，您會看到類似于兩個布螺紋的*螺紋標記*圖示![執行緒標記](../debugger/media/dbg-thread-marker.png "執行緒標記")。 執行緒標記表示執行緒會停在這個位置上。

    請注意，執行緒標記可能被中斷點部分隱藏。

3. 將指標移到執行緒標記上。 資料提示方塊就會出現。 資料提示方塊會指出每個已停止的執行緒的名稱和執行緒 ID 編號。

    您還可以在["並行堆疊"視窗中](../debugger/get-started-debugging-multithreaded-apps.md)查看執行緒的位置。

::: moniker range="vs-2017"
## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>檢查 Web 服務和網路資源 （UWP） 的有效負載

在 UWP 應用中，您可以分析使用`Windows.Web.Http`API 執行的網路操作。 您可以使用此工具來説明調試 Web 服務和網路資源。 要使用該工具，請選擇 **"調試>性能探測器**"。 選擇 **"網路**"，然後選擇 **"開始**"。 在應用程式中，完整瀏覽使用 `Windows.Web.Http` 的案例，然後選擇 [停止收集]**** 以產生報表。

![網路使用方式分析工具](../profiling/media/prof-tour-network-usage.png "網路使用工具")

選取摘要檢視中的作業，以檢視更多詳細資料。

![網路使用工具中的詳細資訊](../profiling/media/prof-tour-network-usage-details.png "詳細查看網路使用方式")

如需詳細資訊，請參閱[網路使用量](../profiling/network-usage.md)。
::: moniker-end

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app-c-c-visual-basic-f"></a><a name="modules_window"></a>更熟悉調試器如何附加到應用（C#、C++、視覺化基本、F#）

要附加到正在運行的應用，調試器將載入為嘗試調試的應用完全相同的生成生成的符號 （.pdb） 檔。 在某些情況下，對符號檔稍加瞭解可能會有所説明。 您可以使用 **"模組"** 視窗檢查 Visual Studio 如何載入符號檔。

通過選擇**Modules****"調試> Windows > 模組，** 在調試時打開模組視窗。 **"模組"** 視窗可以告訴您調試器將哪些模組視為使用者代碼，或[*"我的代碼*](../debugger/just-my-code.md)"，以及模組的符號載入狀態。 在大多數情況下，調試器會自動查找使用者代碼的符號檔，但如果要進入（或調試）.NET代碼、系統代碼或協力廠商庫代碼，需要額外的步驟才能獲取正確的符號檔。

![在"模組"視窗中查看符號資訊](../debugger/media/dbg-tips-modules-window.png "查看符號資訊")

您可以通過按右鍵和選擇 **"載入符號**"直接從 **"模組"** 視窗載入符號資訊。

有時，應用開發人員在沒有匹配符號檔的情況下發布應用（以減少佔用空間），但保留生成匹配符號檔的副本，以便以後可以調試發佈的版本。

要瞭解調試器如何將代碼分類為使用者代碼，請參閱["我的代碼](../debugger/just-my-code.md)"。 要瞭解有關符號檔的更多內容，請參閱[在 Visual Studio 調試器中指定符號 （.pdb） 和原始檔案](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。

## <a name="learn-more"></a>深入了解

有關其他提示和技巧以及更多詳細資訊，請參閱以下博客文章：

- [在視覺工作室中調試的 7 個鮮為人知的駭客](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [視覺工作室中的 7 顆隱藏的寶石](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>另請參閱

[鍵盤快速鍵](../ide/productivity-shortcuts.md)
