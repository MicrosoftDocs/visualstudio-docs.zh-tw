---
title: 偵錯工具中的秘訣和訣竅
description: 瞭解 Visual Studio 偵錯工具所支援的一些較少的功能
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
ms.openlocfilehash: 92d1c327c168bfd2881ad014b7f9ab87f771b95d
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72536073"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>在 Visual Studio 中瞭解偵錯工具的生產力秘訣和訣竅

閱讀本主題以瞭解 Visual Studio 偵錯工具的一些生產力秘訣和訣竅。 如需查看偵錯工具的基本功能，請參閱[偵錯工具的第一次](../debugger/debugger-feature-tour.md)查看。 在本主題中，我們將討論一些不包含在功能導覽中的區域。

## <a name="pin-data-tips"></a>釘選資料提示

如果您經常在進行偵錯工具時將滑鼠停留在資料提示上方，您可能會想要釘選變數的資料提示，以提供您自己的快速存取。 即使在重新開機之後，變數仍會保持固定狀態。 若要釘選資料提示，請按一下釘選圖示，並將滑鼠停留在其上方。 您可以釘選多個變數。

![釘選資料提示](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>編輯您的程式碼並繼續C#進行偵錯工具C++（、VB、）

在 Visual Studio 支援的大部分語言中，您可以在偵錯工具的中間編輯您的程式碼，並繼續進行偵錯工具。 若要使用這項功能，請在偵錯工具中暫停時，按一下游標所在的程式碼，進行編輯，然後按**F5**、 **F10**或**F11**繼續進行調試。

![編輯後繼續的調試](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

如需有關使用功能和功能限制的詳細資訊，請參閱[編輯後繼續](../debugger/edit-and-continue.md)。

## <a name="edit-xaml-code-and-continue-debugging"></a>編輯 XAML 程式碼並繼續進行偵錯工具

若要在偵錯工具期間修改 XAML 程式碼，請參閱[使用 Xaml 熱重載來撰寫和](xaml-hot-reload.md)偵測執行 xaml 程式碼。

## <a name="debug-issues-that-are-hard-to-reproduce"></a>難以重現的 Debug 問題

如果在您的應用程式中重新建立特定狀態很艱難或耗時，請考慮使用條件式中斷點是否可提供協助。 您可以使用[條件式中斷點](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)和篩選中斷點，以避免中斷應用程式程式碼，直到應用程式進入所需的狀態為止（例如變數儲存錯誤資料的狀態）。 您可以使用運算式、篩選、計數等來設定條件。

#### <a name="to-create-a-conditional-breakpoint"></a>若要建立條件式中斷點

1. 以滑鼠右鍵按一下中斷點圖示（紅色球），然後選擇 [**條件**]。

2. 在 [**中斷點設定**] 視窗中，輸入運算式。

    ![條件式中斷點](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. 如果您對另一種條件類型感興趣，請在 [**中斷點設定**] 對話方塊中選取 [**篩選**] 而不是 [**條件運算式**]，然後遵循篩選提示。

## <a name="configure-the-data-to-show-in-the-debugger"></a>設定要在偵錯工具中顯示的資料

若C#為、Visual Basic 和C++ （C++僅限/cli 程式碼），您可以使用[DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)屬性告訴偵錯工具要顯示的資訊。 針對C++程式碼，您可以使用[Natvis 視覺效果](create-custom-views-of-native-objects.md)來執行相同的動作。

## <a name="change-the-execution-flow"></a>變更執行流程

當偵錯工具在一行程式碼上暫停時，使用滑鼠來抓取左邊的黃色箭號指標。 將黃色箭號指標移至程式碼執行路徑中的另一個點。 然後您可以使用 F5 或 step 命令繼續執行應用程式。

![移動執行指標](../debugger/media/dbg-tour-move-the-execution-pointer.gif "移動執行指標")

藉由變更執行流程，您可以執行一些作業，例如測試不同的程式碼執行路徑，或重新執行程式碼而不重新啟動偵錯工具。

> [!WARNING]
> 您通常需要謹慎使用這項功能，您會在工具提示中看到一則警告。 也可能會看到其他警告。 移動指標無法將您的應用程式還原為先前的應用程式狀態。

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>追蹤超出範圍的物件（C#，Visual Basic）

使用偵錯工具視窗（例如 [**監看**式] 視窗），很容易就能看到變數。 不過，當變數超出 [**監看**式] 視窗的範圍時，您可能會注意到它呈現灰色。在某些應用程式案例中，變數的值即使在變數超出範圍時也可能會變更，而且您可能會想要仔細監看（例如，變數可能會遭到垃圾收集）。 您可以在 [**監看**式] 視窗中建立物件識別碼來追蹤該變數。

#### <a name="to-create-an-object-id"></a>建立物件識別碼

1. 在您想要追蹤的變數附近設定中斷點。

2. 啟動偵錯工具（**F5**），並在中斷點停止。

3. 在 [**區域變數**] 視窗中尋找變數（**Debug > Windows > 區域變數**），以滑鼠右鍵按一下該變數，然後選取 [**建立物件識別碼**]。

    ![建立物件識別碼](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. 您應該會看到 [區域變數] **$** 視窗中顯示 **$** 視窗中設定中斷點，在進行呼叫的函式返回的指令或程式行位置中斷執行。 這個變數是物件識別碼。

5. 以滑鼠右鍵按一下 [物件識別碼] 變數，然後選擇 [**加入監看式]** 。

如需詳細資訊，請參閱[建立物件識別碼](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds)。

## <a name="view-return-values-for-functions"></a>View 函數的傳回值

若要查看函式的傳回值，請查看當您逐步執行程式碼時，出現在 [自動**變數] 視窗**中的函式。 若要查看函式的傳回值，請確定您感興趣的函式已執行（如果您目前在函式呼叫中停止，請按**F10**一次）。 如果視窗已關閉，請使用**Debug > Windows >** 自動變數來開啟 **[自動**變數] 視窗。

![自動變數視窗](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

此外，您可以**在 [即時**運算] 視窗中輸入函數來查看傳回值。 （使用**Debug > Windows > 立即**開啟）。

![即時運算視窗](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

您也可以在 [**監看**式]**和 [** 即時運算] 視窗中使用[pseudovariables](../debugger/pseudovariables.md) ，例如 `$ReturnValue`。

## <a name="string_visualizer"></a>檢查視覺化檢視中的字串

使用字串時，查看整個格式化的字串會很有説明。 若要查看純文字、XML、HTML 或 JSON 字串，請按一下放大鏡圖示![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "視覺化檢視圖示") ，並將滑鼠游標停留在包含字串值的變數上。

![開啟字串視覺化檢視](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

字串視覺化檢視可協助您找出字串的格式是否錯誤，視字串類型而定。 例如，空白**值**欄位表示視覺化檢視類型無法辨識該字串。 如需詳細資訊，請參閱[字串視覺化檢視對話方塊](../debugger/string-visualizer-dialog-box.md)。

![JSON 字串視覺化](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

若為一些其他類型，例如出現在偵錯工具視窗中的資料集和 DataTable 物件，您也可以開啟內建的視覺化檢視。

## <a name="break-into-code-on-handled-exceptions"></a>針對已處理的例外狀況中斷程式碼

偵錯工具會在未處理的例外狀況上中斷您的程式碼。 不過，已處理的例外狀況（例如在 `try/catch` 區塊內發生的例外狀況）也可以是 bug 的來源，而且您可能會想要調查發生的時間。 您也可以在 [**例外狀況設定**] 對話方塊中設定選項，以將偵錯工具設為中斷處理的例外狀況。 選擇 [偵錯工具] **> [Windows > 例外狀況設定**] 來開啟此對話方塊。

[**例外狀況設定**] 對話方塊可讓您指示偵錯工具在特定的例外狀況中，細分成程式碼。 在下面的圖例中，每當發生 `System.NullReferenceException` 時，偵錯工具就會中斷程式碼。 如需詳細資訊，請參閱[管理例外](../debugger/managing-exceptions-with-the-debugger.md)狀況。

![例外狀況設定對話方塊](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Debug 鎖死和競爭條件

如果您需要針對多執行緒應用程式的常見問題進行檢查，在進行調試時，通常可以協助您查看執行緒的位置。 您可以使用 [**在來源中顯示執行緒**] 按鈕輕鬆執行此動作。

#### <a name="to-show-threads-in-your-source-code"></a>若要在原始程式碼中顯示執行緒

1. 在調試過程中，**按一下 [在**來源中**顯示執行緒**] 按鈕 [在來源中![顯示執行緒](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker")]。

2. 查看來源視窗左邊的裝訂邊。 在這一行，您會看到類似兩個棉布執行緒的*執行緒標記*圖示![執行緒標記](../debugger/media/dbg-thread-marker.png "ThreadMarker")。 執行緒標記表示執行緒會停在這個位置上。

    請注意，中斷點可能會部分隱藏執行緒標記。

3. 將指標移到執行緒標記上。 資料提示方塊就會出現。 資料提示方塊會指出每個已停止的執行緒的名稱和執行緒 ID 編號。

    您也可以在 [[平行堆疊] 視窗](../debugger/get-started-debugging-multithreaded-apps.md)中，查看執行緒的位置。

## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>檢查 web 服務和網路資源（UWP）的承載

在 UWP 應用程式中，您可以使用 `Windows.Web.Http` API 來分析執行的網路作業。 您可以使用此工具來協助調試 web 服務和網路資源。 若要使用此工具，請選取 [ **Debug > Performance Profiler**]。 選取 [**網路**]，然後選擇 [**啟動**]。 在應用程式中，完整瀏覽使用 `Windows.Web.Http` 的案例，然後選擇 [停止收集] 以產生報表。

![網路流量分析工具](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

選取摘要檢視中的作業，以檢視更多詳細資料。

![網路使用量工具中的詳細資訊](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

如需詳細資訊，請參閱[網路使用量](../profiling/network-usage.md)。

## <a name="modules_window"></a>更熟悉偵錯工具如何附加至您的應用程式（C#、 C++、Visual Basic、 F#）

若要附加至執行中的應用程式，偵錯工具會載入為您嘗試進行偵錯工具的完全相同組建所產生的符號（.pdb）檔案。 在某些情況下，對符號檔的一些知識可能很有説明。 您可以檢查 Visual Studio 如何使用 [**模組**] 視窗載入符號檔。

藉由選取 [ **Debug > Windows > 模組**]，在進行偵錯工具時開啟 [**模組**] 視窗。 [**模組**] 視窗可讓您知道偵錯工具會將哪些模組視為使用者程式碼，或[*My Code*](../debugger/just-my-code.md)，以及模組的符號載入狀態。 在大部分情況下，偵錯工具會自動尋找使用者程式碼的符號檔，但如果您想要逐步執行（或 debug） .NET 程式碼、系統程式碼或協力廠商程式庫程式碼，則需要額外的步驟才能取得正確的符號檔。

![在 [模組] 視窗中查看符號資訊](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

您可以直接從 [**模組**] 視窗載入符號資訊，方法是以滑鼠右鍵按一下並選擇 [**載入符號**]。

有時候，應用程式開發人員會在沒有相符的符號檔的情況下傳送應用程式（以減少使用量），但要保留組建的相符符號檔複本，讓它們可以稍後再對發行的版本進行 debug。

若要瞭解偵錯工具如何將程式碼分類為使用者程式碼，請參閱[Just My Code](../debugger/just-my-code.md)。 若要瞭解符號檔的詳細資訊，請參閱[在 Visual Studio 偵錯工具中指定符號（.pdb）和來源](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)檔案。

## <a name="learn-more"></a>進一步了解

如需其他秘訣和訣竅和詳細資訊，請參閱下列的 blog 文章：

- [7個較少的已知駭客在 Visual Studio 中進行偵錯工具](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [Visual Studio 中的7個隱藏的寶物](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>請參閱

[鍵盤快速鍵](../ide/productivity-shortcuts.md)
