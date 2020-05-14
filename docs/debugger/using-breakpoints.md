---
title: 在調試器中使用中斷點 |微軟文檔
ms.custom: ''
ms.date: 10/28/2019
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
ms.openlocfilehash: a6a8ee96834fc20186ba6719a7c4f377fea45d6b
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302032"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>在視覺化工作室調試器中使用中斷點

中斷點是開發人員工具箱中最重要的調試技術之一。 無論要暫停調試器執行的任何位置，都可以設置中斷點。 例如，您可能希望查看代碼變數的狀態，或查看某個中斷點處的呼叫堆疊。  如果在使用中斷點時嘗試解決警告或問題，請參閱[Visual Studio 調試器中的"故障排除中斷點](../debugger/troubleshooting-breakpoints.md)"。

> [!NOTE]
> 如果您知道要解決的任務或問題，但需要知道要使用的中斷點類型，請參閱[查找調試任務](../debugger/find-your-debugging-task.md#pause-running-code)。

## <a name="set-breakpoints-in-source-code"></a><a name="BKMK_Overview"></a>在原始程式碼中設置中斷點

您可以在任何可執行程式碼行上設定中斷點。 例如，在以下 C# 代碼中，可以在變數聲明、`for`迴圈或迴圈中的任何代碼上`for`設置中斷點。 不能在命名空間或類聲明或方法簽名上設置中斷點。

要設置原始程式碼中的中斷點，請按一下程式碼旁邊的最左邊邊距。 您還可以選擇線並按**F9，** 選擇**調試** > **切換中斷點**，或按右鍵並選擇**中斷點** > **插入中斷點**。 中斷點在左邊距顯示為紅點。

對於大多數語言（包括 C#），中斷點和當前執行行會自動突出顯示。 對於C++代碼，您可以通過選擇 **"工具**（或**調試**）>**選項** > **調試** >  **突出顯示中斷點和當前語句（僅限C++）的整個源行**來打開中斷點和當前行的突出顯示。

![設置中斷點](../debugger/media/basicbreakpoint.png "基本中斷點")

調試時，在執行該行上的代碼之前，執行會在中斷點處暫停。 中斷點符號顯示黃色箭頭。

在下面的示例中的中斷點處，值`testInt`仍為 1。 因此，引數初始化（設置為值 1）以來，該值一直未更改，因為黃色語句尚未執行。

![中斷點執行已停止](../debugger/media/breakpointexecution.png "中斷點執行")

當調試器停止在中斷點時，可以查看應用的目前狀態，包括[變數值](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips)和[呼叫堆疊](../debugger/how-to-use-the-call-stack-window.md)。

以下是有關使用中斷點的幾條常規說明。

- 中斷點是切換。 您可以按一下它，按**F9**，或使用**調試** > **切換中斷點**刪除或重新插入它。

- 要禁用中斷點而不刪除它，請懸停在中斷點上或按右鍵它，然後選擇"**禁用中斷點**"。 禁用的中斷點在左邊距或**中斷點**視窗中顯示為空點。 要重新啟用中斷點，請懸停在中斷點上或按右鍵它，然後選擇"**啟用中斷點**"。

- 設置條件和操作、添加和編輯標籤，或通過按右鍵並選擇適當的命令匯出中斷點，或將滑鼠懸停在它上並選擇 **"設置"** 圖示。

## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a>中斷點操作和追蹤點

*追蹤點是*將消息列印到 **"輸出"** 視窗的中斷點。 追蹤點可以充當程式設計語言中的臨時跟蹤語句，並且不會暫停代碼的執行。 通過在 **"中斷點設置"** 視窗中設置特殊操作來創建追蹤點。 有關詳細說明，請參閱[在視覺化工作室調試器中使用追蹤點](../debugger/using-tracepoints.md)。

## <a name="breakpoint-conditions"></a>中斷點條件

您可以設定條件來控制中斷點執行的時機和位置。 條件可以是調試器識別的任何有效運算式。 有關有效運算式的詳細資訊，請參閱[調試器 中的運算式](../debugger/expressions-in-the-debugger.md)。

**要設置中斷點條件：**

1. 按右鍵中斷點符號並選擇 **"條件**"。 或將滑鼠懸停在中斷點符號上，選擇 **"設置"** 圖示，然後在 **"中斷點設置"** 視窗中選擇 **"條件**"。

   您還可以通過按右鍵中斷點並選擇 **"設置**"，然後選擇"條件"，在 **"中斷點**"視窗中設置**條件**。

   ![中斷點設置](../debugger/media/breakpointsettings.png "中斷點設置")

2. 在下拉清單中，選擇**條件運算式**、**命中計數**或**篩選器**，並相應地設置該值。

3. 選擇 **"關閉**"或按 **"Ctrl**+**Enter"** 以關閉**中斷點設置**視窗。 或者，從 **"中斷點"** 視窗中選擇 **"確定"** 以關閉對話方塊。

設置條件的突破點在原始程式碼和**+****中斷點**視窗中帶有符號。

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>創建條件運算式

選擇**條件運算式**時，可以在兩個條件之間進行選擇：**為 true**或**更改時**。 選擇 true 在滿足運算式時中斷，或**當運算式**的值發生更改時更改為中斷時更改為 **"true"。**

在下面的示例中，僅當 值`testInt`為**4**時才會命中中斷點：

![中斷點條件為 true](../debugger/media/breakpointconditionistrue.png "中斷點為真")

在下面的示例中，僅當`testInt`更改的值時才會命中中斷點：

![中斷點更改時](../debugger/media/breakpointwhenchanged.png "中斷點更改時")

如果使用無效的語法設定中斷點條件，警告訊息便會出現。 如果使用有效的語法，但是無效的語意指定中斷點條件，在第一次叫用中斷點時，則會出現警告訊息。 在這兩種情況下，調試器在達到不正確中斷點時會中斷。 只有在條件是有效的並且判斷值為 `false`時，才會略過中斷點。

>[!NOTE]
>[變更時]**** 欄位的行為，會隨不同的程式設計語言而異。
>- 對於本機代碼，調試器並不認為對條件的第一次評估是更改，因此不會在第一次評估時觸及中斷點。
>- 對於託管代碼，調試器在選擇**更改後**的第一次評估中命中中斷點。

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a>在條件運算式中使用物件指示（僅限 C# 和 F#）

 有時，您希望觀察特定物件的行為。 例如，您可能希望找出物件多次插入到集合中的原因。 在 C# 和 F# 中，可以為[參考型別](/dotnet/csharp/language-reference/keywords/reference-types)的特定實例創建物件 I，並在中斷點條件中使用它們。 物件 ID 是由 Common Language Runtime (CLR) 偵錯服務所產生並與物件相關聯。

**要創建物件識別碼，**

1. 在創建物件後，在代碼中的某個位置設置中斷點。

2. 開始調試，當執行在中斷點暫停時，選擇 **"調試** > **Windows** > **區域變數**"或 **"Alt**+**4"** 以打開 **"區域變數"** 視窗。

   在 **"區域變數"** 視窗中查找特定物件實例，按右鍵它，然後選擇 **"使物件識別碼**"。

   您應該在**$****"區域變數"** 視窗中看到加號。 這就是物件 ID。

3. 在要調查的點添加新的中斷點;例如，當要將物件添加到集合時。 以滑鼠右鍵按一下中斷點並選取 [條件]****。

4. 使用 [條件運算式]**** 欄位中的物件識別碼。 `item`例如，如果變數是要添加到集合的物件，請選擇 **"為 true"，** 然後鍵入項 **= $\<n>，** 其中\<n>是物件識別碼 號。

   要將該物件加入集合時，執行會在該處中斷。

   要刪除物件識別碼，請按右鍵 **"區域變數"** 視窗中的變數，然後選擇 **"刪除物件識別碼**"。

> [!NOTE]
> 物件 ID 會建立弱式參考，且不會防止記憶體回收物件。 它們僅針對目前的偵錯工作階段才有效。

### <a name="set-a-hit-count-condition"></a>設置命中計數條件

如果您懷疑代碼中的迴圈在一定數量的反覆運算後開始行為不端，則可以設置中斷點以在該命中數後停止執行，而不必重複按**F5**才能達到該反覆運算。

在 **"中斷點設置"** 視窗中**的條件**下，選擇 **"命中計數**"，然後指定反覆運算次數。 在下面的示例中，中斷點設置為在所有其他反覆運算中命中：

![中斷點命中計數](../debugger/media/breakpointhitcount.png "中斷點HitCount")

### <a name="set-a-filter-condition"></a>設置篩選器條件

您可以限制只在指定的裝置上或指定的處理序和執行緒中引發中斷點。

在 **"中斷點設置"** 視窗中**的條件**下，選擇 **"篩選**"，然後輸入以下一個或多個運算式：

- MachineName = "名稱"
- ProcessId = 值
- ProcessName ="名稱"
- ThreadId = 值
- ThreadName = "名稱"

將字串值置於雙引號中。 您可以使用這些來結合子句： `&` (AND)、 `||` (OR)、 `!` (NOT) 和括號。

## <a name="set-function-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a>設置功能中斷點

在調用函數時，可以中斷執行。 例如，當您知道函數名稱但不知道它的位置時，這非常有用。 如果您具有同名函數，並且想要斷開所有函數（如不同專案中的重載函數或函數），則它還很有用。

**要設置函數中斷點：**

1. 選擇 **"調試** > **新中斷點** > **"功能中斷點**，或按**Alt**+**F9** > **Ctrl**+**B**。

   您還可以在 **"中斷點"** 視窗中選擇 **"新功能** > **中斷點**"。

1. 在 **"新功能中斷點"** 對話方塊中，在 **"函數名稱"框中輸入函數名稱**。

   要縮小功能規格：

   - 使用完全限定的函數名稱。

     範例：`Namespace1.ClassX.MethodA()`

   - 添加重載函數的參數類型。

     範例：`MethodA(int, string)`

   - 使用"！"符號指定模組。

     範例： `App1.dll!MethodA`

   - 在本機C++中使用上下文運算子。

     `{function, , [module]} [+<line offset from start of method>]`

     範例： `{MethodA, , App1.dll}+2`

1. 在 **"語言**"下拉清單中，選擇函數的語言。

1. 選取 [確定]****。

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>使用記憶體位址設置函數中斷點（僅限本機C++）
 可以使用物件的位址在類的特定實例調用的方法上設置函數中斷點。  例如，給定類型`my_class`的物件，可以在實例調用`my_method`的方法上設置函數中斷點。

1. 在實例實例實例實例實例實例實例實例實例後，在某處設置中斷點。

2. 查找實例的位址（例如， `0xcccccccc`

3. 選擇 **"調試** > **新中斷點** > **"功能中斷點**，或按**Alt**+**F9** > **Ctrl**+**B**。

4. 將以下內容添加到 **"功能名稱**"框中，然後選擇**C++** 語言。

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="set-data-breakpoints-net-core-30-or-higher"></a><a name="BKMK_set_a_data_breakpoint_managed"></a>設置資料中斷點（.NET Core 3.0 或更高）

當特定物件的屬性發生更改時，資料中斷點會中斷執行。

**設置資料中斷點**

1. 在 .NET Core 專案中，開始調試，然後等待到達中斷點。

2. 在 **"自動**"、"**監視**"或 **"區域變數"** 視窗中，按右鍵屬性，並在內容功能表中**的值更改時選擇"中斷**"。

    ![託管資料中斷點](../debugger/media/managed-data-breakpoint.png "託管資料中斷點")

.NET Core 中的資料中斷點不適合：

- 工具提示、區域變數、自動或監看視窗中不可擴展的屬性
- 靜態變數
- 具有調試器TypeProxy屬性的類
- 結構內的欄位

::: moniker-end

## <a name="set-data-breakpoints-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>設置資料中斷點（僅限本機C++）

 當存儲在指定記憶體位址的值發生更改時，資料中斷點將中斷執行。 如果值已讀取但未變更，則不會中斷執行。

**要設置資料中斷點：**

1. 在C++專案中，開始調試，然後等待到達中斷點。 在 **"調試"** 功能表上，**選擇"新建中斷點** > **資料中斷點"**

    您還可以在 **"中斷點"** 視窗中選擇 **"新** > **資料中斷點"，** 或在 **"自動**"、"**監視**"或 **"區域變數"** 視窗中按右鍵專案，並在內容功能表中**的值更改時選擇"中斷**"。

2. 在 **"位址**"框中，鍵入記憶體位址或計算到記憶體位址的運算式。 例如，輸入當變數 `&avar` 的內容變更時要中斷的 `avar` 。

3. 在 [位元組計數] **** 下拉式清單中，選取想要偵錯工具監看的位元組數量。 例如，如果選取 **4**，則偵錯工具將從 `&avar` 開始監看四個位元組，並且在任何這些位元組的值變更時中斷。

在以下條件下，資料中斷點不起作用：
- 未進行偵錯的處理序會寫入記憶體位置。
- 記憶體位置會在兩個或多個處理序之間共用。
- 記憶體位置已在核心內更新。 例如，如果記憶體傳遞到 32 位 Windows`ReadFile`函數，則記憶體將從核心模式更新，因此調試器不會在更新時中斷。
- 監視運算式在 32 位硬體上大於 4 位元組，在 64 位硬體上大於 8 位元組。 這是 x86 體系結構的限制。

> [!NOTE]
> - 資料中斷點取決於特定的記憶體位址。 變數的位址從一個調試會話更改為下一個調試會話，因此資料中斷點在每個調試會話結束時會自動禁用。
>
> - 如果您對區域變數設定資料中斷點，則此中斷點在函式結束時會保持啟用狀態，但是此記憶體位址不再適用，因此該中斷點的行為無法預期。 如果在區域變數上設置資料中斷點，則應在函數結束之前刪除或禁用中斷點。

## <a name="manage-breakpoints-in-the-breakpoints-window"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> 在中斷點視窗中管理中斷點

 您可以使用 **"中斷點"** 視窗查看和管理解決方案中的所有中斷點。 此集中式位置在大型解決方案或關鍵中斷點的複雜調試方案中特別有用。

在 **"中斷點"** 視窗中，您可以搜索、排序、篩選、啟用/禁用或刪除中斷點。 您還可以設置條件和操作，或添加新函數或資料中斷點。

要打開**中斷點**視窗，請選擇 **"調試** > **Windows** > **中斷點**"，或按**Alt**+**F9**或**Ctrl**+**Alt**+**B**。

![中斷點視窗](../debugger/media/breakpointswindow.png "中斷點視窗")

要選擇要在 **"中斷點"** 視窗中顯示的列，請選擇"**顯示列**"。 選擇一個列標題，按該列對中斷點清單進行排序。

### <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a>中斷點標籤
您可以使用標籤對**中斷點**視窗中的中斷點清單進行排序和篩選。

1. 要向中斷點添加標籤，請按右鍵原始程式碼或**中斷點**視窗中的中斷點，然後選擇 **"編輯標籤**"。 添加新標籤或選擇現有標籤，然後選擇 **"確定**"。
2. 通過選擇 **"標籤**、**條件**"或其他列標題，對**中斷點**視窗中的中斷點清單進行排序。 您可以通過在工具列中選擇 **"顯示列**"來選擇要顯示的列。

### <a name="export-and-import-breakpoints"></a>匯出和匯入中斷點
 要保存或共用中斷點的狀態和位置，可以匯出或導入它們。

- 要將單個中斷點匯出到 XML 檔，請按右鍵原始程式碼或**中斷點**視窗中的中斷點，然後選擇"**匯出**"或 **"匯出所選**"。 選擇匯出位置，然後選擇 **"保存**"。 預設位置是解決方案資料夾。
- 要匯出多個中斷點，請在 **"中斷點"** 視窗中選擇中斷點旁邊的框，或在 **"搜索"** 欄位中輸入搜尋條件。 選擇"**匯出與當前搜尋條件匹配的所有中斷點**"圖示，然後保存該檔。
- 要匯出所有中斷點，請取消選擇所有框，並將 **"搜索"** 欄位留空。 選擇"**匯出與當前搜尋條件匹配的所有中斷點**"圖示，然後保存該檔。
- 要導入中斷點，請在 **"中斷點"** 視窗中，**從檔圖示中選擇"導入中斷點**"，導航到 XML 檔位置，然後選擇 **"打開**"。

## <a name="set-breakpoints-from-debugger-windows"></a><a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a>從調試器視窗設置中斷點

您還可以從**呼叫堆疊**和**拆卸**調試器視窗中設置中斷點。

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>在呼叫堆疊視窗中設置中斷點

 要斷開調用函數返回的指令或線路，可以在**呼叫堆疊**視窗中設置中斷點。

**要在"呼叫堆疊"視窗中設置中斷點，**

1. 要打開 **"呼叫堆疊"** 視窗，必須在調試期間暫停。 選擇**調試** > **Windows** > **呼叫堆疊**，或按**Ctrl**+**Alt**+**C**。

2. 在 **"呼叫堆疊"** 視窗中，按右鍵調用函數並**選擇中斷點** > **插入中斷點**，或按**F9**。

   在呼叫堆疊的左邊距中，函式呼叫名稱旁邊會出現中斷點符號。

呼叫堆疊中斷點在**中斷點**視窗中顯示為位址，記憶體位置對應于函數中的下一個可執行指令。

調試器在指令處中斷。

有關呼叫堆疊的詳細資訊，請參閱[：使用呼叫堆疊視窗](../debugger/how-to-use-the-call-stack-window.md)。

要在代碼執行期間直觀地跟蹤中斷點，請參閱[調試時呼叫堆疊上的 Map 方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)。

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>在拆解視窗中設置中斷點

1. 要打開 **"拆解"** 視窗，必須在調試期間暫停。 選擇 **"調試** > **Windows** > **拆解**"，或按**Alt**+**8**。

2. 在 **"拆卸"** 視窗中，按一下要斷開的指令的左邊距。 您也可以選擇它，然後按**F9**，或按右鍵並選擇**中斷點** > **插入中斷點**。

## <a name="see-also"></a>另請參閱

- [什麼是偵錯？](../debugger/what-is-debugging.md)
- [使用視覺化工作室編寫更好的 C# 代碼](../debugger/write-better-code-with-visual-studio.md)
- [首先查看調試](../debugger/debugger-feature-tour.md)
- [在視覺化工作室調試器中排除中斷點](../debugger/troubleshooting-breakpoints.md)
