---
title: 秘訣和訣竅，在 Visual Studio 偵錯工具
description: 了解 Visual Studio 偵錯工具的產能的秘訣
ms.custom: ''
ms.date: 06/15/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 5262d8b1-2648-429e-85d5-90fcaadfb362
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb4fb2c32f74a764e092e0e6f65685a358d64f54
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>深入了解 Visual Studio 中偵錯工具的 產能的秘訣和訣竅

閱讀本主題，了解一些產能的秘訣和訣竅 Visual Studio 偵錯工具。 以查看偵錯工具的基本功能，請參閱[偵錯工具功能導覽](../debugger/debugger-feature-tour.md)。 在本主題中，我們將討論一些不包含功能的教學課程中的區域。

## <a name="pin-data-tips"></a>固定資料提示

如果您經常將滑鼠停留在資料提示偵錯時，您可能想要釘選，讓您快速存取變數的資料提示。 變數會在重新啟動之後保持固定。 若要固定資料提示方塊，按一下 釘選圖示上方時。 您可以釘選多個變數。

![固定資料提示方塊](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>編輯程式碼，並繼續偵錯 （C#、 VB、 c + +）

在 Visual Studio 支援大部分的語言，您可以編輯您的程式碼進行偵錯工作階段，並繼續偵錯。 若要使用這項功能，按一下您的程式碼，您的游標暫停在偵錯工具，請編輯，然後按時**F5**， **F10**，或**F11**繼續偵錯。

![編輯後繼續偵錯](../debugger/media/dbg-tips-edit-and-continue.gif "/editandcontinue")

如需有關使用功能和功能限制的詳細資訊，請參閱[編輯後繼續](../debugger/edit-and-continue.md)。

## <a name="debug-issues-that-are-hard-to-reproduce"></a>偵錯難以重現的問題

如果會很難或是耗時重新建立您的應用程式中的特定狀態，請考慮是否可以幫助條件式中斷點的使用。 您可以使用[條件式中斷點](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)和篩選中斷點，以避免破壞您的應用程式程式碼，直到應用程式進入所需的狀態 （例如變數在其中儲存不正確的資料狀態）。 您可以設定使用運算式、 篩選條件、 叫用的次數，以及其他條件。

#### <a name="to-create-a-conditional-breakpoint"></a>建立條件式中斷點

1. 以滑鼠右鍵按一下中斷點圖示 （紅色圓球），然後選擇 **條件**。

2. 在**中斷點設定** 視窗中，輸入運算式。

    ![條件式中斷點](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. 如果您想要在另一種情況中，選取**篩選**而不是**條件運算式**中**中斷點設定**對話方塊，然後再依照篩選器的秘訣。

## <a name="change-the-execution-flow"></a>變更執行流程

偵錯工具暫停的程式碼行上，使用滑鼠來抓取左側的黃色箭頭指標。 黃色箭號將指標移至程式碼執行路徑中的不同點。 然後您會使用 F5 或逐步執行 命令，以繼續執行應用程式。

![執行將指標移至](../debugger/media/dbg-tour-move-the-execution-pointer.gif "執行將指標移至")

藉由變更執行流程，您可以執行一些作業，例如測試不同的程式碼執行路徑，或執行程式碼並不會重新啟動偵錯工具。

> [!WARNING]
> 通常需要謹慎使用這項功能，您會看到工具提示中的警告。 您可能會太看到其他警告。 移動指標無法還原成先前的應用程式狀態的應用程式。

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>追蹤超出範圍的物件 （C#、 Visual Basic）

所以可以輕鬆地檢視變數使用偵錯工具視窗，例如**監看式**視窗。 不過，當變數超出範圍中**監看式**視窗中，您可能會注意到，它會變成灰色。在某些應用程式案例中，即使變數超出範圍，而且您可能想要密切，可能會變更變數的值 （例如，變數可能會收到記憶體回收）。 您可以為它在建立物件 ID 來追蹤變數**監看式**視窗。

#### <a name="to-create-an-object-id"></a>若要建立的物件識別碼

1.  設定中斷點靠近您想要追蹤的變數。

2.  開始偵錯工具 (**F5**)，並會在中斷點停止。

3. 尋找中的變數**區域變數**視窗 (**偵錯 > Windows > [區域變數]**)，以滑鼠右鍵按一下變數，並選取**設定物件 ID**。

    ![建立物件 ID](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")
  
4.  您應該會看到 [區域變數] **$** 視窗中顯示 **$** 視窗中設定中斷點，在進行呼叫的函式返回的指令或程式行位置中斷執行。 此變數是物件識別碼。
  
5.  以滑鼠右鍵按一下 物件識別碼變數，然後選擇 **加入監看式**。

如需詳細資訊，請參閱[建立物件 ID](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds)。

## <a name="view-return-values-for-functions"></a>檢視函式的傳回值

若要檢視您的函式的傳回值，請查看出現在函式**自動變數**時您逐步執行程式碼 視窗。 若要查看函式的傳回值，請確定您有興趣的函式已經執行 (按**F10**一次，如果您目前已停止在函式呼叫)。 如果視窗已關閉，使用**偵錯 > Windows > [自動變數]** 開啟**自動變數**視窗。

![[自動變數] 視窗](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

此外，您可以輸入中的函式**即時運算**視窗來檢視傳回的值。 (使用開啟**偵錯 > Windows > 即時運算**。)

![即時運算視窗](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

您也可以使用[虛擬變數](../debugger/pseudovariables.md)中**監看式**和**即時運算**視窗中，例如`$ReturnValue`。

## <a name="string_visualizer"></a>檢查在視覺化檢視中的字串

當使用字串，可能很有幫助，若要檢視整個格式化的字串。 若要檢視的純文字、 XML、 HTML 或 JSON 字串，請按一下放大鏡圖示![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "視覺化檢視圖示")游標變數，其中包含字串值。

![開啟字串視覺化檢視](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

字串視覺化檢視可以協助您了解字串是格式不正確，根據字串類型。 例如，空白**值**欄位指出視覺化檢視類型無法辨識字串。 如需詳細資訊，請參閱[字串視覺化檢視對話方塊](../debugger/string-visualizer-dialog-box.md)。

![JSON 字串視覺化檢視](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

偵錯工具視窗中顯示 WPF 物件等其他一些類型，您也可以開啟視覺化檢視。

## <a name="break-into-code-on-handled-exceptions"></a>中斷程式碼上處理的例外狀況

偵錯工具會中斷您的程式碼未處理的例外狀況。 不過，處理的例外狀況 (例如內發生的例外狀況`try/catch`區塊) 也可以是錯誤的來源，您可能想要調查發生的時機。 您可以設定偵錯工具處理的例外狀況的程式碼藉由設定中的選項**例外狀況設定** 對話方塊。 開啟此對話方塊選擇**偵錯 > Windows > 例外狀況設定**。

**例外狀況設定**對話方塊可讓您告知偵錯工具中斷特定的例外狀況的程式碼。 在下圖中，偵錯工具會中斷您的程式碼時`System.NullReferenceException`，就會發生。 如需詳細資訊，請參閱[管理例外狀況](../debugger/managing-exceptions-with-the-debugger.md)。

![例外狀況設定 對話方塊](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>偵錯死結和競爭情形

如果您需要偵錯通用於多執行緒應用程式的問題類型，這通常有助於偵錯時檢視執行緒的位置。 您可以輕鬆地使用**在來源中顯示執行緒** 按鈕。

#### <a name="to-show-threads-in-your-source-code"></a>若要在您的原始程式碼中顯示執行緒

1.  偵錯時，按一下 **在來源中顯示執行緒**按鈕![在來源中顯示執行緒](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker")中**偵錯**工具列。
  
2.  查看來源視窗左邊的裝訂邊。 在這行中，您會看到*執行緒標記*圖示![執行緒標記](../debugger/media/dbg-thread-marker.png "ThreadMarker")類似於兩條布條。 執行緒標記表示執行緒會停在這個位置上。

    請注意，可能會在中斷點部分隱藏執行緒標記。
  
3.  將指標移到執行緒標記上。 資料提示方塊就會出現。 資料提示方塊會指出每個已停止的執行緒的名稱和執行緒 ID 編號。

    您也可以檢視中的執行緒位置[平行堆疊 視窗](../debugger/get-started-debugging-multithreaded-apps.md)。

## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>檢查裝載的 web 服務和網路資源 (UWP)

在 UWP 應用程式，您可以分析執行使用的網路作業`Windows.Web.Http`應用程式開發介面。 您可以使用此工具可協助偵錯 web 服務和網路資源。 若要使用此工具，請選取**偵錯 > 效能分析工具**。 選取**網路**，然後選擇 **啟動**。 在應用程式中，完整瀏覽使用 `Windows.Web.Http` 的案例，然後選擇 [停止收集] 以產生報表。

![網路使用量分析工具](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

選取摘要檢視中的作業，以檢視更多詳細資料。

![詳細資訊，在 [網路使用量] 工具](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

如需詳細資訊，請參閱[網路使用量](../profiling/network-usage.md)。

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app"></a>讓您更熟悉的偵錯工具會將附加至您的應用程式

若要將附加至執行的應用程式，偵錯工具會載入您嘗試偵錯應用程式的完全相同的組建產生的符號 (.pdb) 檔案。 在某些情況下，極小知識的符號檔可能很有用。 您可以檢查 Visual Studio 如何載入符號檔使用**模組**視窗。

開啟**模組**選取偵錯時的視窗**偵錯 > Windows > 模組**。 **模組**視窗可以告訴您哪些模組中偵錯工具會視為使用者程式碼，或[ *My Code*](../debugger/just-my-code.md)，和符號載入模組的狀態。 在大部分情況下，偵錯工具會自動尋找符號檔，使用者程式碼，但如果您想要逐步執行 （或偵錯） 的.NET framework 程式碼、 系統程式碼或協力廠商程式庫程式碼，額外的步驟，才能取得正確的符號檔。

![在 [模組] 視窗中檢視符號資訊](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

您可以載入的符號資訊直接**模組**視窗上按一下滑鼠右鍵，然後選擇**載入符號**。

某些情況下，應用程式開發人員未出貨應用程式比對符號檔 （若要減少使用量），但保留一份相符的符號，讓他們稍後可以偵錯發行的版本組建檔案。

若要找出偵錯工具會為使用者程式碼的程式碼的分類，請參閱[Just My Code](../debugger/just-my-code.md)。 若要了解有關符號檔的詳細資訊，請參閱[Visual Studio debugger 中指定符號 (.pdb) 和原始程式檔](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。

## <a name="learn-more"></a>進一步了解

其他秘訣和訣竅及更詳細的資訊，請參閱下列部落格文章：

- [在 Visual Studio 中偵錯的較小者已知的 hack 7](https://blogs.msdn.microsoft.com/visualstudio/2017/06/26/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [在 Visual Studio 中的 7 隱藏的珍貴](https://blogs.msdn.microsoft.com/visualstudio/2017/10/05/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>另請參閱
[鍵盤快速鍵](../ide/tips-and-tricks-for-visual-studio.md)
