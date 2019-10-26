---
title: 在偵錯工具中使用中斷點 |Microsoft Docs
ms.custom: seodec18
ms.date: 10/15/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpointswin
- vs.debug.disassembly.insert
- vs.debug.sourcewin.edit
- vs.debug.file
- vs.debug.breakpt.new
- vs.debug.whenbreakpointishit
- vs.debug.breakpt.location.address
- vs.debug.breakpt.constraints
- vs.debug.breakpoints.delete
- vs.debug.breakpt.location.data
- vc.breakpoints
- vs.debug.breakpt.condition
- vs.debug.breakpt.location.function
- vs.debug.breakpoints
- vs.debug.menu.insert
- vs.debug.filenames
- vs.debug.breakpt.action
- vs.debug.sourcewin.insert
- vs.debug.address
- vs.debug.data
- vs.debug.func
- vs.debug.breakpt.location.file
helpviewer_keywords:
- breakpoints, about breakpoints
ms.assetid: 020b2e97-3b3e-4b2c-872d-b5c6025e120e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 985369a052a8a7d00b55c45844562af9f0491cc2
ms.sourcegitcommit: 4f82de3fb0cfae226aef1abb40c47e63d2036a5c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919014"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>在 Visual Studio 偵錯工具中使用中斷點

中斷點是開發人員工具箱中最重要的偵錯工具技術之一。 您可以在想要暫停偵錯工具執行的任何位置設定中斷點。 例如，您可能想要查看程式碼變數的狀態，或在特定中斷點查看呼叫堆疊。 如果您知道您想要解決的工作或問題，但您需要知道要使用的中斷點類型，請參閱[尋找您的偵錯工具](../debugger/find-your-debugging-task.md#pause-running-code)。 如果這是您第一次嘗試偵錯程式碼，您可能需要先閱讀[適用於徹底初學者偵錯](../debugger/debugging-absolute-beginners.md)，再瀏覽本文。 

## <a name="BKMK_Overview"></a>在原始程式碼中設定中斷點
 您可以在任何可執行程式碼行上設定中斷點。 例如，在下列C#程式碼中，您可以在變數宣告、`for`迴圈或`for`迴圈內的任何程式碼上設定中斷點。 您無法在命名空間或類別宣告上，或在方法簽章上設定中斷點。

 若要在原始程式碼中設定中斷點，請按一下程式程式碼旁邊的最左邊界。 您也可以選取該行並按**F9**、選取  **Debug**  > **切換中斷點**，或按一下滑鼠右鍵，然後選取 **中斷點** > **插入中斷點**。 中斷點會在左邊界中顯示為紅點。

在C#程式碼中，會自動反白顯示中斷點和目前的執行行。 針對C++程式碼，您可以藉由選取 [**工具**] （或 [ **Debug**]） >**選項** >  >  **調試**程式來開啟反白顯示中斷點和目前的行 **。語句（C++僅限）** 。

 ![設定中斷點](../debugger/media/basicbreakpoint.png "基本中斷點")

 當您進行 debug 時，執行會在中斷點上暫停，然後才執行該行上的程式碼。 中斷點符號會顯示黃色箭號。

 在下列範例的中斷點，`testInt` 的值仍然是1。

 ![中斷點執行已停止](../debugger/media/breakpointexecution.png "中斷點執行")

 當偵錯工具在中斷點停止時，您可以查看應用程式的目前狀態，包括變數值和呼叫堆疊。 如需此呼叫堆疊的詳細資訊，請參閱[如何：使用呼叫堆疊視窗](../debugger/how-to-use-the-call-stack-window.md)。

- 中斷點是切換。 您可以按一下它、按**F9**，或使用**Debug** > **切換中斷點**來刪除或重新插入它。

- 若要停用中斷點而不刪除它，請將滑鼠停留在其上或以滑鼠右鍵按一下，然後選取 [**停用中斷點**]。 停用的中斷點會在左邊界或 [**中斷點**] 視窗中顯示為空的點。 若要重新啟用中斷點，請將滑鼠停留在其上或在其上按一下滑鼠右鍵，然後選取 [**啟用中斷點**]。

- 設定條件和動作、新增和編輯標籤，或以滑鼠右鍵按一下中斷點並選取適當的命令，或將滑鼠停留在其上方，然後選取 [**設定**] 圖示來匯出。

## <a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a>從偵錯工具視窗設定中斷點

您也可以從 [**呼叫堆疊** **] 和 [** 反組解碼偵錯工具] 視窗中設定中斷點。

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>在 [呼叫堆疊] 視窗中設定中斷點

 若要在呼叫函式返回的指令或程式列中斷，您可以在 [**呼叫堆疊**] 視窗中設定中斷點。

**若要在 [呼叫堆疊] 視窗中設定中斷點：**

1. 若要開啟 [**呼叫堆疊**] 視窗，您必須在進行調試過程中暫停。 選取 [ **Debug** > **Windows** > **呼叫堆疊**]，或按**Ctrl**+**Alt**+**C**。

2. 在 **呼叫堆疊** 視窗中，以滑鼠右鍵按一下呼叫函式，然後選取 **中斷點** > **插入中斷點**，或按**F9**。

   中斷點符號會出現在呼叫堆疊左邊界的函式呼叫名稱旁邊。

呼叫堆疊中斷點會在 [**中斷點**] 視窗中顯示為位址，其記憶體位置會對應至函式中的下一個可執行指令。

偵錯工具會在指令處中斷。

如需此呼叫堆疊的詳細資訊，請參閱[如何：使用呼叫堆疊視窗](../debugger/how-to-use-the-call-stack-window.md)。

若要在程式碼執行期間以視覺化方式追蹤中斷點，請參閱在[偵錯工具時對應呼叫堆疊上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)。

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>在 [反組解碼] 視窗中設定中斷點

1. 若要開啟 **[反**組解碼] 視窗，您必須在進行調試過程中暫停。 選取 [ **Debug** > Windows ** > 反**組解碼]，或按**Alt**+**8**。

2. 在 [反組解碼] 視窗中，按一下您想要**在其上**中斷之指令的左邊界。 您也可以選取它並按下**F9**鍵，或按一下滑鼠右鍵，然後選取 **中斷點** > **插入中斷點**。

## <a name="BKMK_Set_a_breakpoint_in_a_source_file"></a>設定函式中斷點

  呼叫函數時，您可以中斷執行。

**若要設定函數中斷點：**

1. 選取 [ **Debug** ] > **新中斷點** > 函式**中斷點**，或按**Alt**+**F9** > **Ctrl**+**B**。

   您也可以在 [**中斷點**] 視窗中選取 [**新增** > **函數中斷點**]。

1. 在 [**新增**函式中斷點] 對話方塊的 [函式**名稱**] 方塊中，輸入函數名稱。

   若要縮小函數規格：

   - 使用完整的函數名稱。

     範例：`Namespace1.ClassX.MethodA()`

   - 加入多載函式的參數類型。

     範例：`MethodA(int, string)`

   - 請使用 '！ ' 符號來指定模組。

     範例：`App1.dll!MethodA`

   - 在原生C++中使用內容運算子。

     `{function, , [module]} [+<line offset from start of method>]`

     範例：`{MethodA, , App1.dll}+2`

1. 在 [**語言**] 下拉式清單中，選擇函數的語言。

1. 選取 [確定]。

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>使用記憶體位址設定函數中斷點（僅限原C++生）
 您可以使用物件的位址，在類別的特定實例所呼叫的方法上設定函式中斷點。  例如，假設 `my_class`類型的可定址物件，您可以在實例呼叫的 `my_method` 方法上設定函式中斷點。

1. 在具現化類別的實例之後的某處設定中斷點。

2. 尋找實例的位址（例如，`0xcccccccc`）。

3. 選取 [ **Debug** ] > **新中斷點** > 函式**中斷點**，或按**Alt**+**F9** > **Ctrl**+**B**。

4. 將下列新增至 [**函數名稱**] 方塊，然後**C++** 選取 [語言]。

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="BKMK_set_a_data_breakpoint_managed"></a>設定資料中斷點（.NET Core 3.0 或更高版本）

當特定物件的屬性變更時，資料中斷點會中斷執行。

**若要設定資料中斷點**

1. 在 .NET Core 專案中，開始進行調試，並等候直到到達中斷點為止。

2. 在 [**自動**變數]、 **[監看**式] 或 [**區域變數**] 視窗中，以滑鼠右鍵按一下屬性，然後選取內容功能表中的 [**值變更時中斷**]。

    ![受控資料中斷點](../debugger/media/managed-data-breakpoint.png "受控資料中斷點")

.NET Core 中的資料中斷點不適用於：

- [工具提示]、[區域變數]、[自動變數] 或 [監看式視窗] 中無法展開的屬性
- 靜態變數
- 具有 DebuggerTypeProxy 屬性的類別
- 結構內的欄位

::: moniker-end

## <a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>設定資料中斷點（ C++僅限機器碼）

 當儲存在指定的記憶體位址的值變更時，資料中斷點會中斷執行。 如果值已讀取但未變更，則不會中斷執行。

**若要設定資料中斷點：**

1. 在C++專案中，開始進行調試，並等候直到到達中斷點為止。 在 [**調試**] 功能表上，選擇 [**新增中斷點**] > **資料中斷點**

    您也可以在 **中斷點** 視窗中選取 **新增** > **資料中斷點**，或以滑鼠右鍵按一下 自動變數、 **監看**式 或 **區域變數** 視窗**中的專案**，然後選取內容功能表中的 **值變更時中斷**

2. 在 [位址] 方塊中，鍵入記憶體位址或評估為記憶體位址的運算式。 例如，輸入當變數 `&avar` 的內容變更時要中斷的 `avar` 。

3. 在 [位元組計數] 下拉式清單中，選取想要偵錯工具監看的位元組數量。 例如，如果選取 **4**，則偵錯工具將從 `&avar` 開始監看四個位元組，並且在任何這些位元組的值變更時中斷。

在下列情況下，資料中斷點無法正常執行：
- 未進行偵錯的處理序會寫入記憶體位置。
- 記憶體位置會在兩個或多個處理序之間共用。
- 記憶體位置已在核心內更新。 例如，如果將記憶體傳遞至32位 Windows `ReadFile` 函式，記憶體將會從核心模式更新，因此偵錯工具不會在更新時中斷。
- 其中，監看式運算式在32位硬體上大於4個位元組，64位硬體上則為8個位元組。 這是 x86 架構的限制。

> [!NOTE]
> - 資料中斷點取決於特定的記憶體位址。 變數的位址會從一個調試會話變更為下一個，因此在每個調試階段結束時，會自動停用資料中斷點。
>
> - 如果您對區域變數設定資料中斷點，則此中斷點在函式結束時會保持啟用狀態，但是此記憶體位址不再適用，因此該中斷點的行為無法預期。 如果您在本機變數上設定資料中斷點，您應該在函式結束之前刪除或停用中斷點。

## <a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> 在中斷點視窗中管理中斷點

 您可以使用 [**中斷點**] 視窗來查看和管理方案中的所有中斷點。 這個集中式位置在大型解決方案中特別有用，或適用于中斷點非常重要的複雜的偵錯工具案例。

在 [**中斷點**] 視窗中，您可以搜尋、排序、篩選、啟用/停用或刪除中斷點。 您也可以設定條件和動作，或加入新的函數或資料中斷點。

若要開啟 [**中斷點**] 視窗，請選取 [ **Debug** > **Windows** > **中斷點**]，或按**Alt**+**F9**或**Ctrl**+**alt**+**B**。

![中斷點視窗](../debugger/media/breakpointswindow.png "中斷點視窗")

若要選取要在 [**中斷點**] 視窗中顯示的資料行，請選取 [**顯示資料行**]。 選取資料行標頭，依該資料行排序中斷點清單。

### <a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> 中斷點標籤
您可以在 [**中斷點**] 視窗中使用標籤來排序和篩選中斷點清單。

1. 若要將標籤加入至中斷點，請以滑鼠右鍵按一下原始程式碼或 [**中斷點**] 視窗中的中斷點，然後選取 [**編輯標籤**]。 新增新標籤或選擇現有標籤，然後選取 **[確定]** 。
2. 選取**卷**標、**條件**或其他欄標題，以排序 [**中斷點**] 視窗中的中斷點清單。 選取工具列中的 [**顯示資料行**]，即可選取要顯示的資料行。

### <a name="export-and-import-breakpoints"></a>匯出和匯入中斷點
 若要儲存或共用中斷點的狀態和位置，您可以將它們匯出或匯入。

- 若要將單一中斷點匯出至 XML 檔案，請以滑鼠右鍵按一下 [原始程式碼] 或 [**中斷點**] 視窗中的中斷點，然後選取 [**匯出**] 或 [**匯出選取**]。 選取匯出位置，然後選取 [**儲存**]。 預設位置為 [方案] 資料夾。
- 若要匯出數個中斷點，請在 [**中斷點**] 視窗中選取中斷點旁的方塊，或在 [**搜尋**] 欄位中輸入搜尋準則。 選取 [**匯出符合目前搜尋條件的所有中斷點**] 圖示，然後儲存檔案。
- 若要匯出所有中斷點，請取消選取所有的方塊，並將 [**搜尋**] 欄位保留空白。 選取 [**匯出符合目前搜尋條件的所有中斷點**] 圖示，然後儲存檔案。
- 若要匯入中斷點，請在 [**中斷點**] 視窗中，選取 [從檔案匯**入中斷點**] 圖示，流覽至 XML 檔案位置，然後選取 [**開啟**]。

## <a name="breakpoint-conditions"></a>中斷點條件
 您可以設定條件來控制中斷點執行的時機和位置。 條件可以是偵錯工具可識別的任何有效運算式。 如需有效運算式的詳細資訊，請參閱[偵錯工具中的運算式](../debugger/expressions-in-the-debugger.md)。

**若要設定中斷點條件：**

1. 以滑鼠右鍵按一下中斷點符號，然後選取 [**條件**]。 或將滑鼠停留在中斷點符號上，選取 [**設定**] 圖示，然後選取 [**中斷點設定**] 視窗中的 [**條件**]。

   您也可以在 [**中斷點**] 視窗中設定條件，方法是以滑鼠右鍵按一下中斷點，然後選取 [**設定**]，然後選取 [**條件**]。

   ![中斷點設定](../debugger/media/breakpointsettings.png "BreakpointSettings")

2. 在下拉式清單中，選取 [**條件運算式**]、[**計數**] 或 [**篩選**]，並據以設定值。

3. 選取 [**關閉**] 或按**Ctrl**+**Enter** ，以關閉 [**中斷點設定**] 視窗。 或者，在 [**中斷點**] 視窗中，選取 **[確定**] 以關閉對話方塊。

具有條件集的中斷點會在 [原始程式碼] 和 [**中斷點**] 視窗中以 **+** 符號顯示。

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="conditional-expression"></a>條件運算式

當您選取 [**條件運算式**] 時，您可以選擇兩個條件： [**是 true** ] 或 [**變更時**]。 選擇 [**是 true] 會**在滿足運算式時中斷，或**在**運算式的值變更時中斷。

 在下列範例中，只有當 `testInt` 的值為**4**時，才會叫用中斷點：

 ![中斷點條件為 true](../debugger/media/breakpointconditionistrue.png "中斷點為 true")

 在下列範例中，只有當 `testInt` 的值變更時，才會叫用中斷點：

 ![變更時的中斷點](../debugger/media/breakpointwhenchanged.png "變更時的中斷點")

 如果使用無效的語法設定中斷點條件，警告訊息便會出現。 如果使用有效的語法，但是無效的語意指定中斷點條件，在第一次叫用中斷點時，則會出現警告訊息。 在任一情況下，偵錯工具會在到達不正確中斷點時中斷。 只有在條件是有效的並且判斷值為 `false`時，才會略過中斷點。

 >[!NOTE]
 >[變更時] 欄位的行為，會隨不同的程式設計語言而異。
 >- 針對機器碼，偵錯工具不會將條件的第一個評估視為變更，因此不會在第一次評估時叫用中斷點。
 >- 對於 managed 程式碼，偵錯工具會在選取 [**變更時**] 之後，于第一次評估時叫用中斷點。

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="using-object-ids-in-conditional-expressions-c-and-f-only"></a>在條件運算式中使用物件識別碼C# （ F#僅限和）
 有時候您會想要觀察特定物件的行為。 例如，您可能會想要找出物件多次插入集合的原因。 在 C# 和 F# 中，您可以針對[參考類型](/dotnet/csharp/language-reference/keywords/reference-types)的特定執行個體建立物件識別碼，並用於中斷點條件中。 物件 ID 是由 Common Language Runtime (CLR) 偵錯服務所產生並與物件相關聯。

**若要建立物件識別碼：**

1. 在建立物件之後的程式碼中設定中斷點。

2. 開始進行調試，並于中斷點暫停執行時，選取 [ **Debug** > **Windows** > **區域變數**] 或 [ **Alt**+**4** ] 以開啟 [**區域變數**] 視窗。

   在 [**區域變數**] 視窗中找出特定的物件實例，以滑鼠右鍵按一下它，然後選取 [**建立物件識別碼**]。

   您應該會看到 [區域變數] **$** 視窗中顯示 **$** 視窗中設定中斷點，在進行呼叫的函式返回的指令或程式行位置中斷執行。 這就是物件 ID。

3. 在您要調查的時間點新增中斷點;例如，當物件要加入至集合時。 以滑鼠右鍵按一下中斷點並選取 [條件]。

4. 使用 [條件運算式] 欄位中的物件識別碼。 例如，如果變數 `item` 是要加入至集合的物件，請選取 [**是 true** ]，然後輸入**item = = $\<n >** ，其中 \<n > 是物件識別碼。

   要將該物件加入集合時，執行會在該處中斷。

   若要刪除物件識別碼，請在 [**區域變數**] 視窗中的變數上按一下滑鼠右鍵，然後選取 [**刪除物件識別碼**]。

>[!NOTE]
>物件 ID 會建立弱式參考，且不會防止記憶體回收物件。 它們僅針對目前的偵錯工作階段才有效。

### <a name="hit-count"></a>叫用次數
 如果您懷疑程式碼中的迴圈在經過特定數目的反復專案之後開始出現行為異常，您可以設定中斷點，以在該叫用次數之後停止執行，而不需要重複按**F5**鍵來到達該反覆運算。

 在 [**中斷點設定**] 視窗的 [**條件**] 底下，選取 [**計數**]，然後指定反覆運算次數。 在下列範例中，中斷點設定為在每個反復專案上叫用：

 ![中斷點計數](../debugger/media/breakpointhitcount.png "BreakpointHitCount")

### <a name="filter"></a>篩選
您可以限制只在指定的裝置上或指定的處理序和執行緒中引發中斷點。

在 [**中斷點設定**] 視窗的 [**條件**] 底下，選取 [**篩選**]，然後輸入下列一個或多個運算式：

- MachineName = "名稱"
- ProcessId = 值
- ProcessName ="名稱"
- ThreadId = 值
- ThreadName = "名稱"

將字串值置於雙引號中。 您可以使用這些來結合子句： `&` (AND)、 `||` (OR)、 `!` (NOT) 和括號。

## <a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> 中斷點動作和追蹤點
 「追蹤點」是將訊息列印至 [輸出] 視窗的中斷點。 追蹤點在程式語言中的行為可以像是暫存追蹤陳述式。

**若要設定追蹤點：**

1. 以滑鼠右鍵按一下中斷點，然後選取 [**動作**]。 或者，在 [**中斷點設定**] 視窗中，將滑鼠停留在中斷點上，選取 [**設定**] 圖示，然後選取 [**動作**]。

1. 在 [將**訊息記錄到輸出視窗]** 欄位中輸入訊息。 訊息可以包含一般文字字串、以大括弧括住的變數或運算式的值，以及值的[C#](../debugger/format-specifiers-in-csharp.md)格式[C++](../debugger/format-specifiers-in-cpp.md)規範（和）。

   您也可以在訊息中使用下列特殊關鍵字：

   - **$ADDRESS** -目前的指令
   - **$CALLER**呼叫函數名稱
   - **$CALLSTACK**呼叫堆疊
   - **$FUNCTION** -目前的函式名稱
   - **$PID** -處理序識別碼
   - **$PNAME** -進程名稱
   - **$TID** -執行緒識別碼
   - **$TNAME** -執行緒名稱
   - **$TICK** -滴答計數（來自 Windows `GetTickCount`）

1. 若要將訊息列印到 [**輸出**] 視窗而不中斷，請選取 [**繼續執行**] 核取方塊。 若要列印訊息並在追蹤點中斷執行，請清除此核取方塊。

追蹤點會在 [原始程式碼] 和 [**中斷點**] 視窗的左邊界中顯示為紅色菱形。

## <a name="see-also"></a>請參閱

- [什麼是偵錯？](../debugger/what-is-debugging.md)
- [使用 Visual Studio C#撰寫更好的程式碼](../debugger/write-better-code-with-visual-studio.md)
- [第一次查看調試](../debugger/debugger-feature-tour.md)
- [疑難排解 Visual Studio 偵錯工具中的中斷點](../debugger/troubleshooting-breakpoints.md)
