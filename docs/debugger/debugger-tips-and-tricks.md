---
title: 祕訣和訣竅，偵錯工具
description: 了解一些 Visual Studio 偵錯工具支援鮮為人知的功能
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
ms.openlocfilehash: bb47aa94dbf444e27fd149e2e16c723677f973eb
ms.sourcegitcommit: cd91a8a4f6086cda9ba6948be25864fc7d6b8e44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59537555"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>了解 Visual Studio 中偵錯工具的產能的秘訣和訣竅

閱讀本主題以了解 Visual Studio 偵錯工具的幾個產能的秘訣和訣竅。 在偵錯工具的基本功能，請參閱[第一次查看偵錯工具](../debugger/debugger-feature-tour.md)。 在本主題中，我們將討論功能教學課程中不包含某些區域。

## <a name="pin-data-tips"></a>釘選資料提示

如果您經常暫留在資料提示進行偵錯時，您可能想要釘選到快速存取變數的資料提示。 變數會重新啟動之後保持固定。 若要釘選的資料提示，請按一下釘選圖示將滑鼠移到它。 您可以釘選多個變數。

![固定資料提示](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>編輯您的程式碼，並繼續偵錯 (C#，VB， C++)

在大部分的語言支援的 Visual Studio 中，您可以編輯您的程式碼在偵錯工作階段中央，並繼續偵錯。 若要使用這項功能，可按一下以進入您的程式碼，將游標暫停偵錯工具，請編輯，然後按下時使用**F5**， **F10**，或**F11**繼續偵錯。

![編輯後繼續偵錯](../debugger/media/dbg-tips-edit-and-continue.gif "/editandcontinue")

如需使用此功能及功能限制的詳細資訊，請參閱 <<c0> [ 編輯後繼續](../debugger/edit-and-continue.md)。

## <a name="debug-issues-that-are-hard-to-reproduce"></a>偵錯難以重現的問題

如果很難或耗時重新建立您的應用程式中的特定狀態，請考慮是否可以協助使用條件式中斷點。 您可以使用[條件式中斷點](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)和篩選中斷點使用，以避免中斷您的應用程式程式碼，直到應用程式便會進入所需的狀態 （例如，變數會將不正確的資料儲存所在的狀態）。 您可以設定使用運算式、 篩選、 叫用的次數和等等的條件。

#### <a name="to-create-a-conditional-breakpoint"></a>若要建立條件式中斷點

1. 以滑鼠右鍵按一下中斷點圖示 （紅色圓球），然後選擇 **條件**。

2. 在 **中斷點設定**視窗中，輸入的運算式。

    ![條件式中斷點](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. 如果您有興趣在另一種條件，請選取**篩選條件**而不是**條件運算式**中**中斷點設定**對話方塊，然後再依照篩選器的秘訣。

## <a name="configure-the-data-to-show-in-the-debugger"></a>設定要在偵錯工具中顯示的資料

針對C#，Visual Basic 和C++(C++僅限 /CLI 程式碼)，您可以告知偵錯工具来示範如何使用資訊[DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)屬性。 針對C++程式碼中，您可以執行相同的 using [Natvis 視覺化](create-custom-views-of-native-objects.md)。

## <a name="change-the-execution-flow"></a>變更執行流程

偵錯工具暫停程式碼行上，使用滑鼠按住左邊的黃色箭號指標。 黃色箭號將指標移至程式碼執行路徑中的不同點。 然後您會使用 F5 或逐步執行 命令，以繼續執行應用程式。

![將執行指標](../debugger/media/dbg-tour-move-the-execution-pointer.gif "執行將指標移至")

藉由變更執行流程，您可以執行一些作業，例如測試不同的程式碼執行路徑，或重新執行程式碼而不重新啟動偵錯工具。

> [!WARNING]
> 您通常需要謹慎使用這項功能，您會在工具提示中看到一則警告。 也可能會看到其他警告。 將指標移無法還原成先前的應用程式狀態的應用程式。

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>追蹤範圍外的物件 （C#、 Visual Basic）

就可以輕鬆地檢視變數使用偵錯工具視窗，例如**監看式**視窗。 不過，當變數超出範圍內**監看式** 視窗中，您可能會注意到，它會呈現灰色。在某些應用程式案例中，即使變數超出範圍，以及要密切，可能會變更變數的值 （例如，變數可能會收到回收）。 您可以在建立物件識別碼來追蹤變數**監看式**視窗。

#### <a name="to-create-an-object-id"></a>若要建立的物件識別碼

1.  設定中斷點，靠近您想要追蹤的變數。

2.  開始偵錯工具 (**F5**)，並在中斷點停止。

3. 尋找在變數**區域變數** 視窗 (**偵錯 > Windows > 區域變數**)，以滑鼠右鍵按一下變數，然後選取**設定物件 ID**。

    ![建立物件 ID](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4.  您應該會看到 [區域變數] **$** 視窗中顯示 **$** 視窗中設定中斷點，在進行呼叫的函式返回的指令或程式行位置中斷執行。 此變數是物件識別碼。

5.  以滑鼠右鍵按一下 物件識別碼變數，然後選擇 **新增監看式**。

如需詳細資訊，請參閱 <<c0> [ 建立物件 ID](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds)。

## <a name="view-return-values-for-functions"></a>檢視函式的傳回值

若要檢視您的函式的傳回值，查看 函式中出現**自動變數**時您會逐步執行程式碼的視窗。 若要查看函式的傳回值，請確定您有興趣的函式已執行 (按下**F10**一次，如果您目前已停止在函式呼叫)。 如果視窗已關閉，使用**偵錯 > Windows > [自動變數]** 來開啟**自動變數**視窗。

![[自動變數] 視窗](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

此外，您可以在其中輸入中的函式**Immediate**視窗來檢視傳回的值。 (使用開啟**偵錯 > Windows > 即時運算**。)

![即時運算視窗](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

您也可以使用[虛擬變數](../debugger/pseudovariables.md)中**監看式**並**即時運算**視窗中，例如`$ReturnValue`。

## <a name="string_visualizer"></a>檢查視覺化檢視中的字串

當使用字串，很有幫助，若要檢視完整的格式化的字串。 若要檢視純文字、 XML、 HTML 或 JSON 字串，請按一下 放大鏡圖示![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "視覺化檢視圖示")將滑鼠移到包含字串值的變數。

![開啟字串視覺化檢視](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

字串視覺化檢視可協助您了解字串是格式不正確，根據的字串類型。 比方說，空白**值** 欄位表示的視覺化檢視型別無法辨識字串。 如需詳細資訊，請參閱 <<c0> [ 字串視覺化檢視對話方塊](../debugger/string-visualizer-dialog-box.md)。

![JSON 字串視覺化檢視](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

例如會出現在偵錯工具視窗的 DataSet 和 DataTable 物件其他一些類型，您也可以開啟內建的視覺化檢視。

## <a name="break-into-code-on-handled-exceptions"></a>中斷程式碼上處理的例外狀況

偵錯工具會中斷您的程式碼，在未處理的例外狀況。 不過，處理例外狀況 (例如內發生的例外狀況`try/catch`區塊) 也可以是錯誤的來源，而且您可能想要調查發生。 您可以設定偵錯工具處理的例外狀況的程式碼藉由設定中的選項**例外狀況設定** 對話方塊。 開啟此對話方塊中，選擇**偵錯 > Windows > 例外狀況設定**。

**例外狀況設定**對話方塊可讓您告訴偵錯工具中斷程式碼在特定的例外狀況。 在下圖中，偵錯工具會中斷您的程式碼只要`System.NullReferenceException`，就會發生。 如需詳細資訊，請參閱 <<c0> [ 管理例外狀況](../debugger/managing-exceptions-with-the-debugger.md)。

![例外狀況設定 對話方塊](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>偵錯死結和競爭情形

如果您需要偵錯的通用於多執行緒應用程式的問題類型，這通常有助於偵錯時檢視執行緒的位置。 您可以輕鬆地**在來源中顯示執行緒** 按鈕。

#### <a name="to-show-threads-in-your-source-code"></a>若要在您的原始程式碼中顯示執行緒

1.  偵錯時，按一下**在來源中顯示執行緒** 按鈕![在來源中顯示執行緒](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker")中**偵錯**工具列。

2.  查看來源視窗左邊的裝訂邊。 在這一行，您會看到*執行緒標記*圖示![執行緒標記](../debugger/media/dbg-thread-marker.png "ThreadMarker") ，類似於兩條布條。 執行緒標記表示執行緒會停在這個位置上。

    請注意，可能會在中斷點部分隱藏執行緒標記。

3.  將指標移到執行緒標記上。 資料提示方塊就會出現。 資料提示方塊會指出每個已停止的執行緒的名稱和執行緒 ID 編號。

    您也可以檢視的位置中的執行緒[平行堆疊 視窗](../debugger/get-started-debugging-multithreaded-apps.md)。

## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>檢查裝載 web 服務和網路資源 (UWP)

在 UWP 應用程式，您可以分析執行使用的網路作業`Windows.Web.Http`API。 您可以使用這項工具，以協助偵錯 web 服務和網路資源。 若要使用的工具，請選取**偵錯 > 效能 Profiler**。 選取 **網路**，然後選擇**開始**。 在應用程式中，完整瀏覽使用 `Windows.Web.Http` 的案例，然後選擇 [停止收集] 以產生報表。

![網路使用量分析工具](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

選取摘要檢視中的作業，以檢視更多詳細資料。

![中的網路使用量工具的詳細資訊](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

如需詳細資訊，請參閱[網路使用量](../profiling/network-usage.md)。

## <a name="modules_window"></a> 更熟悉的偵錯工具會將附加至您的應用程式 (C#， C++，Visual Basic 中， F#)

若要附加至您執行的應用程式，偵錯工具會載入針對您嘗試偵錯的應用程式的完全相同的組建產生的符號 (.pdb) 檔。 在某些情況下，符號檔的一些知識可以很有幫助。 您可以檢查 Visual Studio 會使用的符號檔的載入**模組**視窗。

開啟**模組**視窗中的選取偵錯時**偵錯 > Windows > 模組**。 **模組**視窗可以告訴您哪些模組偵錯工具會視為使用者程式碼，或[ *My Code*](../debugger/just-my-code.md)，和符號載入模組的狀態。 在大部分情況下，偵錯工具會自動尋找符號檔的使用者程式碼，但如果您想要逐步執行 （或偵錯）.NET framework 程式碼、 系統程式碼或協力廠商程式庫程式碼，需要額外的步驟，以取得正確的符號檔。

![在 [模組] 視窗中檢視符號資訊](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

您可以載入符號資訊，直接從**模組**視窗中的按一下滑鼠右鍵，然後選擇**載入符號**。

有時候，應用程式開發人員會交付應用程式，如果沒有相符符號檔案 （以減少磁碟使用量），但保留一份相符的符號檔案的組建，讓他們稍後可以偵錯發行的版本。

若要了解如何偵錯工具會分類為使用者程式碼的程式碼，請參閱[Just My Code](../debugger/just-my-code.md)。 若要深入了解符號檔，請參閱[在 Visual Studio debugger 中指定符號 (.pdb) 和原始程式檔](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。

## <a name="learn-more"></a>進一步了解

其他祕訣和訣竅與更多詳細的資訊，請參閱這些部落格文章：

- [在 Visual Studio 中偵錯的較小者已知的駭客 7](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [在 Visual Studio 中隱藏的寶藏 7](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>另請參閱
[鍵盤快速鍵](../ide/tips-and-tricks-for-visual-studio.md)
