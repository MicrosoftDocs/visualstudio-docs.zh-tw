---
title: 偵錯工具中的秘訣和訣竅
description: 瞭解 Visual Studio 偵錯工具所支援的一些較低的已知功能
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d5b934c0e9532bd3bc1f53d9b00d1cc8273f4120
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872985"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>瞭解 Visual Studio 中偵錯工具的生產力秘訣和訣竅

閱讀本主題以瞭解 Visual Studio 偵錯工具的一些生產力秘訣和訣竅。 若要查看偵錯工具的基本功能，請參閱 [偵錯工具的第一次查看](../debugger/debugger-feature-tour.md)。 在本主題中，我們將討論一些不包含在功能導覽中的區域。

## <a name="pin-data-tips"></a>釘選資料提示

如果您經常在進行偵錯工具時將滑鼠停留在資料提示上方，您可能會想要釘選變數的資料提示，以提供您自己的快速存取權。 即使在重新開機後，變數仍會保持固定。 若要釘選資料提示，請在滑鼠停留時按一下釘選圖示。 您可以釘選多個變數。

![釘選資料提示](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>編輯您的程式碼並繼續進行 (c #、VB、c + +) 的偵錯工具

在 Visual Studio 所支援的大部分語言中，您可以在偵錯工具的過程中編輯程式碼，並繼續進行偵錯工具。 若要使用這項功能，請在偵錯工具中暫停時，按一下您的程式碼，並進行編輯，然後按 **F5**、 **F10** 或 **F11** 以繼續進行偵錯工具。

![編輯後繼續調試](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

如需使用功能和功能限制的詳細資訊，請參閱 [編輯後繼續](../debugger/edit-and-continue.md)。

## <a name="edit-xaml-code-and-continue-debugging"></a>編輯 XAML 程式碼並繼續進行偵錯工具

若要在偵錯工具期間修改 XAML 程式碼，請參閱 [使用 XAML 熱重新載入撰寫和](../xaml-tools/xaml-hot-reload.md)偵測執行中的 xaml 程式碼。

## <a name="debug-issues-that-are-hard-to-reproduce"></a>難以重現的問題

如果在您的應用程式中重新建立特定狀態是很困難或耗時的，請考慮使用條件式中斷點是否可提供協助。 您可以使用 [條件式中斷點](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) 和篩選中斷點來避免中斷應用程式程式碼，直到應用程式進入預期狀態 (例如變數儲存錯誤資料) 的狀態。 您可以使用運算式、篩選器、計數等來設定條件。

#### <a name="to-create-a-conditional-breakpoint"></a>若要建立條件式中斷點

1. 以滑鼠右鍵按一下中斷點圖示 (紅色球形) 然後選擇 [ **條件**]。

2. 在 [ **中斷點設定** ] 視窗中，輸入運算式。

    ![條件中斷點](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. 如果您對其他類型的條件有興趣，請在 [**中斷點設定**] 對話方塊中選取 [**篩選**]，而不要選取 [**條件運算式**]，然後依照篩選提示進行。

## <a name="configure-the-data-to-show-in-the-debugger"></a>設定要在偵錯工具中顯示的資料

針對 c #、Visual Basic 和 c + + (c + +/CLI 程式碼僅) ，您可以使用 [DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md) 屬性告訴偵錯工具要顯示的資訊。 針對 c + + 程式碼，您可以使用 [Natvis 視覺效果](create-custom-views-of-native-objects.md)來進行相同的動作。

## <a name="change-the-execution-flow"></a>變更執行流程

當偵錯工具在程式程式碼上暫停時，請使用滑鼠抓取左側的黃色箭號指標。 將黃色箭號指標移至程式碼執行路徑中的不同點。 然後，您可以使用 F5 或 step 命令繼續執行應用程式。

![移動執行指標](../debugger/media/dbg-tour-move-the-execution-pointer.gif "移動執行指標")

藉由變更執行流程，您可以執行一些作業，例如測試不同的程式碼執行路徑，或重新執行程式碼而不重新啟動偵錯工具。

> [!WARNING]
> 您通常需要謹慎使用這項功能，您會在工具提示中看到一則警告。 也可能會看到其他警告。 移動指標無法將您的應用程式還原為先前的應用程式狀態。

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>追蹤超出範圍的物件 (c #、Visual Basic) 

您可以使用偵錯工具視窗（例如 [ **監看** 式] 視窗）輕鬆地查看變數。 不過，當變數超出 [ **監看** 式] 視窗中的範圍時，您可能會注意到它呈現灰色。在某些應用程式案例中，變數的值即使在變數超出範圍時也可能會變更，而且您可能會想要緊密地觀看 (例如，變數可能會遭到垃圾收集) 。 您可以在 [ **監看** 式] 視窗中為它建立物件識別碼來追蹤變數。

#### <a name="to-create-an-object-id"></a>若要建立物件識別碼

1. 在您想要追蹤的變數附近設定中斷點。

2. 啟動偵錯工具 (**F5**) 並在中斷點停止。

3. 在 [ **區域變數** ] 視窗中尋找變數 (**Debug > Windows > 區域變數**) ，以滑鼠右鍵按一下變數，然後選取 [ **建立物件識別碼**]。

    ![建立物件識別碼](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. 您應該會 **$** 在 [ **區域變數** ] 視窗中看到一個數位加上一個數位。 此變數是物件識別碼。

5. 以滑鼠右鍵按一下物件識別碼變數，然後選擇 [ **加入監看式]**。

如需詳細資訊，請參閱 [建立物件識別碼](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds)。

## <a name="view-return-values-for-functions"></a>查看函數的傳回值

若要查看函式的傳回值，請在逐步執行程式碼時，查看 [自動 **變數] 視窗** 中出現的函式。 若要查看函式的傳回值，請確定您感興趣的函式已執行 (按下 **F10** 一次，如果您目前已停止函式呼叫) 。 如果視窗已關閉，請使用 **Debug > Windows >** 自動變數來開啟 **[自動** 變數] 視窗。

![自動變數視窗](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

此外，您可以 **在 [即時** 運算] 視窗中輸入函數來查看傳回值。  (使用 **Debug > Windows > Immediate** 來開啟它。 ) 

![即時運算視窗](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

您也可以在 [**監看** 式] 和 [即時 **運算] 視窗** 中使用 [下](../debugger/pseudovariables.md)，例如 `$ReturnValue` 。

## <a name="inspect-strings-in-a-visualizer"></a><a name="string_visualizer"></a>在視覺化視覺化中檢查字串

使用字串時，查看整個格式化的字串可能會很有説明。 若要查看純文字、XML、HTML 或 JSON 字串，請在將滑鼠停留在包含字串值的變數上時，按一下放大鏡圖示 ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "視覺化檢視圖示") 。

![開啟字串視覺化](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

字串視覺化檢視可協助您找出字串是否格式不正確，視字串類型而定。 例如，空白 **值** 欄位表示視覺化程式類型無法辨識字串。 如需詳細資訊，請參閱 [字串視覺化程式對話方塊](../debugger/string-visualizer-dialog-box.md)。

![JSON 字串視覺化](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

對於出現在偵錯工具視窗中的其他一些類型，例如資料集和 DataTable 物件，您也可以開啟內建的視覺化檢視。

## <a name="break-into-code-on-handled-exceptions"></a>中斷處理例外狀況的程式碼

偵錯工具會在未處理的例外狀況時中斷程式碼。 不過，處理例外狀況 (例如在區塊中發生的例外狀況 `try/catch`) 也可能是錯誤的來源，而您可能想要在發生錯誤時進行調查。 您也可以在 [ **例外狀況設定** ] 對話方塊中設定選項，將偵錯工具設定為中斷處理例外狀況的程式碼。 選擇 [ **Debug > Windows > 例外狀況設定**]，即可開啟此對話方塊。

[ **例外狀況設定** ] 對話方塊可讓您告訴偵錯工具在特定例外狀況時中斷程式碼。 在下圖中，偵錯工具會在每次發生時中斷程式碼 `System.NullReferenceException` 。 如需詳細資訊，請參閱 [管理例外](../debugger/managing-exceptions-with-the-debugger.md)狀況。

![例外狀況設定對話方塊](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>偵測鎖死和競爭條件

如果您需要對多執行緒應用程式常見的問題類型進行偵錯工具，則在進行偵錯工具時，通常有助於查看執行緒的位置。 您可以使用 [ **在來源中顯示執行緒** ] 按鈕，輕鬆地完成這項作業。

#### <a name="to-show-threads-in-your-source-code"></a>在原始程式碼中顯示執行緒

1. 在調試過程中，按一下 [**在來源中顯示執行緒**] 按鈕會在 **調試** 的工具列中 ![顯示來源](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker")中的執行緒。

2. 查看來源視窗左邊的裝訂邊。 在此行中，您會看到類似兩個抹布執行緒的 *執行緒標記* 圖示  ![執行緒標記](../debugger/media/dbg-thread-marker.png "ThreadMarker") 。 執行緒標記表示執行緒會停在這個位置上。

    請注意，中斷點可能會部分隱藏執行緒標記。

3. 將指標移到執行緒標記上。 資料提示方塊就會出現。 資料提示方塊會指出每個已停止的執行緒的名稱和執行緒 ID 編號。

    您也可以在 [ [平行堆疊] 視窗](../debugger/get-started-debugging-multithreaded-apps.md)中，查看執行緒的位置。

::: moniker range="vs-2017"
## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>檢查 (UWP) 的 web 服務和網路資源承載

在 UWP 應用程式中，您可以使用 API 來分析執行的網路作業 `Windows.Web.Http` 。 您可以使用此工具來協助您進行 web 服務和網路資源的調試。 若要使用此工具，請選取 [ **Debug >] 效能分析工具**。 選取 [ **網路**]，然後選擇 [ **啟動**]。 在應用程式中，完整瀏覽使用 `Windows.Web.Http` 的案例，然後選擇 [停止收集] 以產生報表。

![網路流量分析工具](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

選取摘要檢視中的作業，以檢視更多詳細資料。

![網路使用量工具中的詳細資訊](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

如需詳細資訊，請參閱[網路使用量](../profiling/network-usage.md)。
::: moniker-end

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app-c-c-visual-basic-f"></a><a name="modules_window"></a> 深入瞭解偵錯工具如何附加至您的應用程式 (c #、c + +、Visual Basic、F # ) 

若要附加至執行中的應用程式，偵錯工具會將符號 ( .pdb 載入至您嘗試要進行偵錯工具之完全相同組建的相同組建) 檔案。 在某些情況下，對符號檔的一些知識可能很有説明。 您可以使用 [ **模組** ] 視窗檢查 Visual Studio 載入符號檔的方式。

在偵錯工具中選取 [ **Debug > Windows > 模組**] 來開啟 [**模組**] 視窗。 [ **模組** ] 視窗可以告訴您偵錯工具視為使用者程式碼的模組，或 [*My Code*](../debugger/just-my-code.md)，以及模組的符號載入狀態。 在大部分的情況下，偵錯工具會自動尋找使用者程式碼的符號檔，但如果您想要逐步執行 (或 debug) .NET 程式碼、系統程式碼或協力廠商程式庫程式碼，則需要額外的步驟才能取得正確的符號檔。

![在 [模組] 視窗中查看符號資訊](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

您可以直接從 [ **模組** ] 視窗載入符號資訊，方法是以滑鼠右鍵按一下並選擇 [ **載入符號**]。

有時候，應用程式開發人員會在沒有相符符號檔 (的情況下提供應用程式，以降低) 的使用量，但保留組建的相符符號檔複本，讓它們可以稍後再進行發行的發行版本。

若要瞭解偵錯工具如何將程式碼分類為使用者程式碼，請參閱 [Just My Code](../debugger/just-my-code.md)。 若要瞭解符號檔的詳細資訊，請參閱 [Visual Studio 偵錯工具中的指定符號 ( .pdb) 和原始程式](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)檔。

## <a name="learn-more"></a>深入了解

如需其他秘訣和訣竅和詳細資訊，請參閱下列 blog 文章：

- [7個較少的已知駭客在 Visual Studio 中的偵錯工具](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [Visual Studio 中的7個隱藏 gem](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>另請參閱

[鍵盤快速鍵](../ide/productivity-shortcuts.md)
