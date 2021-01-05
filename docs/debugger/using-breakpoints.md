---
title: 在偵錯工具中使用中斷點 |Microsoft Docs
ms.custom: ''
ms.date: 06/30/2020
ms.topic: how-to
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
ms.openlocfilehash: 52c95749d5d7e2909fbff6da0a3a45bc36cd73c6
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729323"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>在 Visual Studio 偵錯工具中使用中斷點

中斷點是您開發人員工具箱中最重要的偵錯工具之一。 您可以在想要暫停偵錯工具執行的任何位置設定中斷點。 例如，您可能想要查看程式碼變數的狀態，或查看特定中斷點的呼叫堆疊。  如果您嘗試在使用中斷點時解決警告或問題，請參閱 [Visual Studio 偵錯工具中的中斷點疑難排解](../debugger/troubleshooting-breakpoints.md)。

> [!NOTE]
> 如果您知道您想要解決的工作或問題，但需要知道要使用哪種中斷點，請參閱 [常見問題-尋找您的偵錯工具](../debugger/find-your-debugging-task.md#pause-running-code)。

## <a name="set-breakpoints-in-source-code"></a><a name="BKMK_Overview"></a> 在原始程式碼中設定中斷點

您可以在任何可執行程式碼行上設定中斷點。 例如，在下列 c # 程式碼中，您可以在程式程式碼上設定中斷點，其具有變數指派 (`int testInt = 1`) 、 `for` 迴圈或迴圈內的任何程式碼 `for` 。 您無法在方法簽章上設定中斷點、命名空間或類別的宣告，或如果沒有指派且沒有 getter/setter，則無法設定變數宣告。

若要在原始程式碼中設定中斷點，請按一下程式程式碼旁邊的最左邊界。 您也可以選取這一行，然後按 **F9**、選取 [ **Debug**  >  **切換中斷點**]，或是以滑鼠右鍵按一下並選取 [**中斷點**  >  **插入中斷點**]。 中斷點會顯示為左邊界中的紅點。

針對大部分語言（包括 c #），會自動反白顯示中斷點和目前的執行行。 若為 c + + 程式碼，您可以選取 [**工具**] (或 [**調試** 程式]，以開啟中斷點和目前行的醒目提示) >**選項**  >  **調試** 程式  >   **反白顯示中斷點的整個原始程式列及目前的語句 (c +) +**

![設定中斷點](../debugger/media/basicbreakpoint.png "基本中斷點")

當您進行偵錯工具時，執行會在中斷點暫停，然後執行該行上的程式碼。 中斷點符號會顯示黃色箭號。

在下列範例中的中斷點，的值 `testInt` 仍然是1。 因此，因為變數已初始化，所以值不會變更 (設定為值 1) ，因為黃色的語句尚未執行。

![中斷點執行已停止](../debugger/media/breakpointexecution.png "中斷點執行")

當偵錯工具在中斷點停止時，您可以查看應用程式的目前狀態，包括 [變數值](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips) 和 [呼叫堆疊](../debugger/how-to-use-the-call-stack-window.md)。

以下是一些使用中斷點的一般指示。

- 中斷點是切換。 您可以按一下它、按 **F9**，或使用 **Debug**  >  **切換中斷點** 來刪除或重新插入。

- 若要停用中斷點而不刪除它，請將滑鼠停留在其上或按一下滑鼠右鍵，然後選取 [ **停用中斷點**]。 停用的中斷點會在左邊界或 [ **中斷點** ] 視窗中顯示為空點。 若要重新啟用中斷點，請將滑鼠停留在其上方或以滑鼠右鍵按一下，然後選取 [ **啟用中斷點**]。

- 設定條件和動作、新增和編輯標籤，或在中斷點上按一下滑鼠右鍵並選取適當的命令，或將滑鼠游標移至其上方，然後選取 [ **設定** ] 圖示。

## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> 中斷點動作和追蹤點

追蹤 *點* 是將訊息列印至 [ **輸出** ] 視窗的中斷點。 追蹤點可以像程式設計語言中的暫時追蹤語句一樣運作，而且不會暫停程式碼的執行。 您可以藉由在 [ **中斷點設定** ] 視窗中設定特殊動作來建立追蹤點。 如需詳細指示，請參閱 [Visual Studio 偵錯工具中的使用追蹤點](../debugger/using-tracepoints.md)。

## <a name="breakpoint-conditions"></a>中斷點條件

您可以設定條件來控制中斷點執行的時機和位置。 條件可以是偵錯工具所能辨識的任何有效運算式。 如需有效運算式的詳細資訊，請參閱 [偵錯工具中的運算式](../debugger/expressions-in-the-debugger.md)。

**若要設定中斷點條件：**

1. 以滑鼠右鍵按一下中斷點符號，然後選取 [ **條件**]。 或將滑鼠停留在中斷點符號上，選取 [**設定**] 圖示，然後選取 [**中斷點設定**] 視窗中的 [**條件**]。

   您也可以在 [ **中斷點** ] 視窗中設定條件，方法是以滑鼠右鍵按一下中斷點，然後選取 [ **設定**]，然後選取 [ **條件**]。

   ![中斷點設定](../debugger/media/breakpointsettings.png "BreakpointSettings")

2. 在下拉式清單中，選取 [ **條件運算式**]、[ **計數**] 或 [ **篩選**]，並據此設定值。

3. 選取 [**關閉**] 或按 **Ctrl** + **enter** ，以關閉 [**中斷點設定**] 視窗。 或者，從 [ **中斷點** ] 視窗中選取 **[確定** ] 以關閉對話方塊。

具有條件設定的中斷點會 **+** 在 [原始程式碼] 和 [ **中斷點** ] 視窗中顯示符號。

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>建立條件運算式

當您選取 [ **條件運算式**] 時，可以選擇兩個條件： [ **為 true** ] 或 [ **變更時**]。 選擇 [ **true] 會** 在滿足運算式時中斷，或是在運算式的值變更時中斷。 

在下列範例中，只有當的值為4時，才會叫用中斷點 `testInt` ： 

![中斷點條件為 true](../debugger/media/breakpointconditionistrue.png "中斷點為 true")

在下列範例中，只有在變更的值時才會叫用中斷點 `testInt` ：

![變更時的中斷點](../debugger/media/breakpointwhenchanged.png "變更時的中斷點")

如果使用無效的語法設定中斷點條件，警告訊息便會出現。 如果使用有效的語法，但是無效的語意指定中斷點條件，在第一次叫用中斷點時，則會出現警告訊息。 在任一種情況下，偵錯工具會在到達無效中斷點時中斷。 只有在條件是有效的並且判斷值為 `false`時，才會略過中斷點。

>[!NOTE]
> 在 [ **變更時** ] 欄位中，偵錯工具不會將條件的第一次評估視為變更，因此不會在第一次評估時叫用中斷點。

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a>在條件運算式中使用物件識別碼 (c # 和 F # 僅) 

 有時候您會想要觀察特定物件的行為。 例如，您可能想要找出物件插入集合的原因超過一次。 在 c # 和 F # 中，您可以針對 [參考型別](/dotnet/csharp/language-reference/keywords/reference-types)的特定實例建立物件 id，並在中斷點條件中使用它們。 物件 ID 是由 Common Language Runtime (CLR) 偵錯服務所產生並與物件相關聯。

**若要建立物件識別碼：**

1. 在建立物件之後的程式碼中設定中斷點。

2. 開始進行調試，當執行在中斷點暫停時，請選取 [ **Debug**  >  **Windows**  >  **區域變數**] 或 [ **Alt** + **4** ] 開啟 [**區域變數**] 視窗。

   在 [ **區域變數** ] 視窗中尋找特定的物件實例，以滑鼠右鍵按一下它，然後選取 [ **建立物件識別碼**]。

   您應該會 **$** 在 [ **區域變數** ] 視窗中看到一個數位加上一個數位。 這就是物件 ID。

3. 在您想要調查的點新增中斷點;例如，當物件要加入至集合時。 以滑鼠右鍵按一下中斷點並選取 [條件]。

4. 使用 [條件運算式] 欄位中的物件識別碼。 例如，如果變數 `item` 是要加入至集合中的物件，請選取 [**為 true** ]，然後輸入 **item = = \<n> $**，其中 \<n> 是物件識別碼 號碼。

   要將該物件加入集合時，執行會在該處中斷。

   若要刪除物件識別碼，請在 [ **區域變數** ] 視窗中的變數上按一下滑鼠右鍵，然後選取 [ **刪除物件 id**]。

> [!NOTE]
> 物件 ID 會建立弱式參考，且不會防止記憶體回收物件。 它們僅針對目前的偵錯工作階段才有效。

### <a name="set-a-hit-count-condition"></a>設定計數條件

如果您懷疑程式碼中的某個迴圈在經過特定數目的反復專案之後開始出現行為異常，您可以設定中斷點，以在該叫用次數之後停止執行，而不需要重複按下 **F5** 鍵來到達該反復專案。

在 [**中斷點設定**] 視窗的 [**條件**] 底下，選取 [**計數**]，然後指定反覆運算次數。 在下列範例中，中斷點設定為在每個其他反復專案上叫用：

![中斷點計數](../debugger/media/breakpointhitcount.png "BreakpointHitCount")

### <a name="set-a-filter-condition"></a>設定篩選準則

您可以限制只在指定的裝置上或指定的處理序和執行緒中引發中斷點。

在 [**中斷點設定**] 視窗的 [**條件**] 底下，選取 [**篩選**]，然後輸入下列一或多個運算式：

- MachineName = "名稱"
- ProcessId = 值
- ProcessName ="名稱"
- ThreadId = 值
- ThreadName = "名稱"

將字串值置於雙引號中。 您可以使用這些來結合子句： `&` (AND)、 `||` (OR)、 `!` (NOT) 和括號。

## <a name="set-function-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> 設定函數中斷點

您可以在呼叫函數時中斷執行。 例如，當您知道函式名稱，但不知道其位置時，這會很有用。 如果您的函式具有相同的名稱，而且您想要在其上中斷所有 (例如多載函式或不同專案中的函式) ，它也很有用。

**若要設定函數中斷點：**

1. 選取 [ **Debug**  >  **New 中斷點**  >  **函數中斷點**]，或按 **Alt** + **F9**  >  **Ctrl** + **B**。

   您也可以  >  在 [**中斷點**] 視窗中選取 [新增 **函數中斷點**]。

1. 在 [ **新增** 函式中斷點] 對話方塊中，于 [函式 **名稱** ] 方塊中輸入函數名稱。

   若要縮小函數規格：

   - 使用完整函數名稱。

     範例：`Namespace1.ClassX.MethodA()`

   - 加入多載函式的參數類型。

     範例：`MethodA(int, string)`

   - 使用 '！ ' 符號來指定模組。

     範例： `App1.dll!MethodA`

   - 在原生 c + + 中使用內容運算子。

     `{function, , [module]} [+<line offset from start of method>]`

     範例： `{MethodA, , App1.dll}+2`

1. 在 [ **語言** ] 下拉式清單中，選擇函數的語言。

1. 選取 [確定]。

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>使用記憶體位址設定函數中斷點， (僅限原生 c + +) 
 您可以使用物件的位址，在由類別之特定實例呼叫的方法上設定函式中斷點。  例如，假設有可定址的型別物件 `my_class` ，您可以在實例呼叫的方法上設定函式中斷點 `my_method` 。

1. 在具現化類別實例之後的某個位置設定中斷點。

2. 找出實例的位址 (例如 `0xcccccccc`) 。

3. 選取 [ **Debug**  >  **New 中斷點**  >  **函數中斷點**]，或按 **Alt** + **F9**  >  **Ctrl** + **B**。

4. 將下列新增至 [函式 **名稱** ] 方塊，然後選取 [ **c + +** 語言]。

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="set-data-breakpoints-net-core-30-or-higher"></a><a name="BKMK_set_a_data_breakpoint_managed"></a>將資料中斷點設定 ( .NET Core 3.0 或更高版本) 

當特定物件的屬性變更時，資料中斷點會中斷執行。

**設定資料中斷點**

1. 在 .NET Core 專案中，啟動偵錯工具，並等候直到到達中斷點為止。

2. 在 [ **自動** 變數]、 **[監看** 式] 或 [ **區域變數** ] 視窗中，以滑鼠右鍵按一下屬性，然後在內容功能表中選取 [ **值變更時中斷** ]。

    ![受控資料中斷點](../debugger/media/managed-data-breakpoint.png "受控資料中斷點")

.NET Core 中的資料中斷點無法運作：

- 在工具提示、區域變數、自動變數或監看式視窗中無法展開的屬性
- 靜態變數
- 具有 DebuggerTypeProxy 屬性的類別
- 結構內的欄位

::: moniker-end

## <a name="set-data-breakpoints-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>將資料中斷點設定 (僅限原生 c + +) 

 當儲存在指定記憶體位址的值變更時，資料中斷點會中斷執行。 如果值已讀取但未變更，則不會中斷執行。

**若要設定資料中斷點：**

1. 在 c + + 專案中，啟動偵錯工具，並等候直到到達中斷點為止。 在 [**調試**] 功能表上，選擇 [**新增中斷點**  >  **資料中斷點**]。

    您也可以  >  在 [**中斷點**] 視窗中選取 [新增 **資料中斷點**]，或 **在 [自動** 變數]、 **[監看** 式] 或 [**區域變數**] 視窗中的專案上按一下滑鼠右鍵，然後在內容功能表中選取 [**值變更**

2. 在 [ **位址** ] 方塊中，輸入記憶體位址或評估為記憶體位址的運算式。 例如，輸入當變數 `&avar` 的內容變更時要中斷的 `avar` 。

3. 在 [位元組計數]  下拉式清單中，選取想要偵錯工具監看的位元組數量。 例如，如果選取 **4**，則偵錯工具將從 `&avar` 開始監看四個位元組，並且在任何這些位元組的值變更時中斷。

在下列情況下，資料中斷點無法運作：
- 未進行偵錯的處理序會寫入記憶體位置。
- 記憶體位置會在兩個或多個處理序之間共用。
- 記憶體位置已在核心內更新。 例如，如果將記憶體傳遞給32位的 Windows 函式 `ReadFile` ，記憶體將會從核心模式進行更新，因此偵錯工具不會在更新時中斷。
- 其中的監看式運算式在32位硬體上大於4個位元組，在64位硬體上為8個位元組。 這是 x86 架構的限制。

> [!NOTE]
> - 資料中斷點取決於特定的記憶體位址。 變數的位址會從一個偵錯工具會話變更為下一個，因此在每個偵錯工具結束時，會自動停用資料中斷點。
>
> - 如果您對區域變數設定資料中斷點，則此中斷點在函式結束時會保持啟用狀態，但是此記憶體位址不再適用，因此該中斷點的行為無法預期。 如果您在本機變數上設定資料中斷點，則應該在函式結束之前刪除或停用中斷點。

## <a name="manage-breakpoints-in-the-breakpoints-window"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> 在中斷點視窗中管理中斷點

 您可以使用 [ **中斷點** ] 視窗來查看和管理方案中的所有中斷點。 這個集中的位置在大型方案中特別有用，或適用于中斷點很重要的複雜調試案例。

在 [ **中斷點** ] 視窗中，您可以搜尋、排序、篩選、啟用/停用或刪除中斷點。 您也可以設定條件和動作，或加入新的函數或資料中斷點。

若要開啟 [**中斷點**] 視窗，請選取 [ **Debug**  >  **Windows**  >  **中斷點**]，或按 **alt** + **F9** 或 **Ctrl** + **alt** + **B**。

![中斷點視窗](../debugger/media/breakpointswindow.png "中斷點視窗")

若要選取要在 [ **中斷點** ] 視窗中顯示的資料行，請選取 [ **顯示資料行**]。 選取資料行標頭，依該資料行排序中斷點清單。

### <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> 中斷點標籤
您可以在 [ **中斷點** ] 視窗中使用標籤來排序和篩選中斷點清單。

1. 若要將標籤加入至中斷點，請以滑鼠右鍵按一下 [原始程式碼] 或 [ **中斷點** ] 視窗中的中斷點，然後選取 [ **編輯標籤**]。 新增標籤或選擇現有標籤，然後選取 **[確定]**。
2. 選取標籤、**條件** 或其他資料 **行標** 頭，以排序 [**中斷點**] 視窗中的中斷點清單。 選取工具列中的 [ **顯示資料行** ]，即可選取要顯示的資料行。

### <a name="export-and-import-breakpoints"></a>匯出和匯入中斷點
 若要儲存或共用中斷點的狀態和位置，您可以將它們匯出或匯入。

- 若要將單一中斷點匯出至 XML 檔案，請以滑鼠右鍵按一下 [原始程式碼] 或 [ **中斷點** ] 視窗中的中斷點，然後選取 [ **匯出** ] 或 [ **匯出選取** 的]。 選取匯出位置，然後選取 [ **儲存**]。 預設位置是方案資料夾。
- 若要匯出數個中斷點，請在 [ **中斷點** ] 視窗中選取中斷點旁的方塊，或在 [ **搜尋** ] 欄位中輸入搜尋準則。 選取 [ **匯出所有符合目前搜尋條件的中斷點** ] 圖示，然後儲存檔案。
- 若要匯出所有中斷點，請取消選取所有的方塊，並將 [ **搜尋** ] 欄位保留空白。 選取 [ **匯出所有符合目前搜尋條件的中斷點** ] 圖示，然後儲存檔案。
- 若要匯入中斷點，請在 [ **中斷點** ] 視窗中，選取 [從檔案匯 **入中斷點** ] 圖示，流覽至 XML 檔案位置，然後選取 [ **開啟**]。

## <a name="set-breakpoints-from-debugger-windows"></a><a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a> 從偵錯工具視窗設定中斷點

您也可以從 [ **呼叫堆疊** **] 和 [** 反組解碼偵錯工具] 視窗設定中斷點。

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>在 [呼叫堆疊] 視窗中設定中斷點

 若要在呼叫函式傳回的指令或行中斷，您可以在 [ **呼叫堆疊** ] 視窗中設定中斷點。

**若要在 [呼叫堆疊] 視窗中設定中斷點：**

1. 若要開啟 [ **呼叫堆疊** ] 視窗，您必須在進行調試時暫停。 選取 [ **Debug**  >  **Windows**  >  **呼叫堆疊**]，或按 **Ctrl** + **Alt** + **C**。

2. 在 [**呼叫堆疊**] 視窗中，以滑鼠右鍵按一下呼叫函式，然後選取 [**中斷點**  >  **插入中斷點**]，或按 **F9**。

   中斷點符號會出現在呼叫堆疊左邊界中函式呼叫名稱的旁邊。

在 [ **中斷點** ] 視窗中，呼叫堆疊中斷點會顯示為位址，其記憶體位置會對應至函式中的下一個可執行指令。

偵錯工具會在指令處中斷。

如需呼叫堆疊的詳細資訊，請參閱 [如何：使用呼叫堆疊視窗](../debugger/how-to-use-the-call-stack-window.md)。

若要在程式碼執行期間以視覺化方式追蹤中斷點，請參閱在 [偵錯工具時對應呼叫堆疊上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)。

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>在 [反組解碼] 視窗中設定中斷點

1. 若要開啟 **[反** 組解碼] 視窗，您必須在進行調試時暫停。 選取 [ **Debug** Windows 反組解碼]  >    >  ****，或按 **Alt** + **8**。

2. 在 [反組 **解碼] 視窗** 中，按一下您要中斷之指令的左邊界。 您也可以選取它，然後按 **F9** 鍵，或按一下滑鼠右鍵並選取 [**中斷點**  >  **插入中斷點**]。

## <a name="see-also"></a>請參閱

- [什麼是偵錯？](../debugger/what-is-debugging.md)
- [使用 Visual Studio 撰寫更好的 c # 程式碼](../debugger/write-better-code-with-visual-studio.md)
- [先查看調試](../debugger/debugger-feature-tour.md)
- [針對 Visual Studio 偵錯工具中的中斷點進行疑難排解](../debugger/troubleshooting-breakpoints.md)
