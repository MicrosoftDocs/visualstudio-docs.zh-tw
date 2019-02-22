---
title: 在 偵錯工具中使用中斷點 |Microsoft Docs
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
ms.openlocfilehash: 5d2d60113e3020e92d44cb45727ac1d422745f03
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54943087"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>使用 Visual Studio 偵錯工具中的中斷點
中斷點是在您的開發人員工具箱中最重要的偵錯技術之一。 每當您要暫停偵錯工具執行，您可以設定中斷點。 例如，您可能要查看程式碼變數的狀態，或查看呼叫堆疊，在特定中斷點。 如果這是您第一次嘗試偵錯程式碼，您可能需要先閱讀[適用於徹底初學者偵錯](../debugger/debugging-absolute-beginners.md)，再瀏覽本文。
  
##  <a name="BKMK_Overview"></a> 在原始程式碼中設定中斷點  
 您可以在任何可執行程式碼行上設定中斷點。 例如，在下列C#程式碼中，您無法在變數宣告中，設定中斷點`for`迴圈或任何程式碼內`for`迴圈。 您無法在命名空間或類別宣告或方法簽章上設定中斷點。  

 若要在原始程式碼中設定中斷點，按一下 程式碼行旁邊的最左邊界。 您也可以選取一行，然後按**F9**，選取**偵錯** > **切換中斷點**，或以滑鼠右鍵按一下並選取**中斷點** > **插入中斷點**。 中斷點會顯示為一個紅點的左邊界。  

在C#程式碼、 中斷點和目前執行線條會自動反白顯示。 針對 c + + 程式碼，您可以開啟反白顯示中斷點和目前行的方法是選取**工具**(或**偵錯**) >**選項** >  **偵錯** >  **反白顯示中斷點和目前的陳述式 （僅 c + +） 的整個原始程式行**。 
  
 ![設定中斷點](../debugger/media/basicbreakpoint.png "基本的中斷點")  
  
 當您偵錯時，執行的中斷點處暫停，然後才執行該行程式碼。 中斷點符號會顯示黃色箭號。 

 下列範例中，windows 7 中的中斷點處`testInt`仍然是 1。  
  
 ![中斷點執行已停止](../debugger/media/breakpointexecution.png "中斷點執行")  
  
 當偵錯工具停止於中斷點時，您可以查看應用程式，包括變數值和呼叫堆疊的目前狀態。 如需有關呼叫堆疊的詳細資訊，請參閱[How to:使用 [呼叫堆疊] 視窗](../debugger/how-to-use-the-call-stack-window.md)  

- 中斷點是切換。 您可以按一下它，請按**F9**，或使用**偵錯** > **切換中斷點**刪除，或將它重新插入。
  
- 停用中斷點而不會刪除它，將滑鼠移至或按一下滑鼠右鍵，然後選取**停用中斷點**。 已停用的中斷點會顯示為左邊界中的空點或**中斷點**視窗。 若要重新啟用中斷點，停留或按一下滑鼠右鍵，然後選取**啟用中斷點**。 
  
- 設定條件和動作、 新增和編輯標籤，或以滑鼠右鍵按一下它，然後選取適當的命令，或它暫留並選取匯出中斷點**設定**圖示。

##  <a name="BKMK_Set_a_breakpoint_in_a_function"></a> Windows 偵錯工具中設定中斷點 

您也可以設定從中斷點**呼叫堆疊**並**反組譯碼**偵錯工具視窗。  
  
### <a name="BKMK_Set_a_breakpoint_in_the_call_stack_window"></a> [呼叫堆疊] 視窗中設定中斷點  

 若要中斷的指令或呼叫的函式會傳回的列位置，您可以設定中斷點，**呼叫堆疊**視窗。 
  
**在 [呼叫堆疊] 視窗中設定中斷點：**

1. 若要開啟 [**呼叫堆疊**] 視窗中，您必須在偵錯期間暫停。 選取 **偵錯** > **Windows** > **呼叫堆疊**，或按**Ctrl** + **Alt**+**C**。  
   
2. 在 **呼叫堆疊**視窗中，以滑鼠右鍵按一下呼叫函式，然後選取**中斷點** > **插入中斷點**，或按**F9**.  
   
   中斷點符號會出現在左邊界的呼叫堆疊函式呼叫名稱旁邊。
   
此呼叫堆疊中斷點會出現在**中斷點**為位址，伴隨著對應於函式中下一個可執行指令的記憶體位置的視窗。 

偵錯工具會在指令處中斷。  

如需有關呼叫堆疊的詳細資訊，請參閱[How to:使用 [呼叫堆疊] 視窗](../debugger/how-to-use-the-call-stack-window.md) 

若要在程式碼執行期間的可用空間以視覺化方式追蹤中斷點，請參閱[偵錯時對應呼叫堆疊上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)。 
  
### <a name="set-a-breakpoint-in-the-disassembly-window"></a>在反組譯碼視窗中設定中斷點  
   
1. 若要開啟 [**反組譯碼**] 視窗中，您必須在偵錯期間暫停。 選取 **偵錯** > **Windows** > **反組譯碼**，或按**Alt** + **8**。  
   
2. 在 **反組譯碼**視窗中，按一下您想要在中斷的指令的左邊界中。 您也可以選取它，並按下**F9**，或以滑鼠右鍵按一下並選取**中斷點** > **插入中斷點**。 

##  <a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> 設定函式中斷點  

  呼叫函式時，您可以中斷執行。 

**若要設定函式中斷點：**
  
1. 選取 **偵錯** > **新中斷點** > **函式中斷點**，或按**Alt** +**F9** > **Ctrl**+**B**。 
   
   您也可以選取**的新** > **函式中斷點**中**中斷點**視窗。
   
1. 在 **新增函式中斷點** 對話方塊中，輸入中的函式名稱**函式名稱** 方塊中。 

   若要縮小函式規格：
   
   - 使用完整函式名稱。 
     
     範例：`Namespace1.ClassX.MethodA()`
     
   - 新增多載的函式的參數類型。 
     
     範例：`MethodA(int, string)`
     
   - 使用 '！' 指定模組的符號。
     
     範例：`App1.dll!MethodA`
     
   - 原生 c + + 中使用內容運算子。
     
     `{function, , [module]} [+<line offset from start of method>]`
     
     範例：`{MethodA, , App1.dll}+2`
   
1. 在 **語言**下拉式清單中，選擇 函式的語言。
   
1. 選取 [確定]。
  
### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>設定使用的記憶體位址 （原生 c + + 只） 的函式中斷點  
 您可以使用物件的位址來設定類別的特定執行個體所呼叫的方法上的函式中斷點。  例如，假設定址的物件型別的`my_class`，您可以設定函式中斷點上`my_method`執行個體呼叫的方法。 
  
1.  類別的執行個體具現化之後，某處設定中斷點。  
    
2.  尋找執行個體的位址 (例如`0xcccccccc`)。 
    
3.  選取 **偵錯** > **新中斷點** > **函式中斷點**，或按**Alt** +**F9** > **Ctrl**+**B**。  
    
4.  將下列內容加入**函式名稱**方塊，然後選取**c + +** 語言。  
    
    ```C++  
    ((my_class *) 0xcccccccc)->my_method  
    ```  

## <a name="BKMK_set_a_data_breakpoint_native_cplusplus_only"></a>設定資料中斷點 （原生 c + + 只） 
 
 資料中斷點會中斷執行時儲存在指定的記憶體位址會變更的值。 如果值已讀取但未變更，則不會中斷執行。  
  
**若要設定資料中斷點：**

1.  在 c + + 專案中，啟動偵錯，並等待直到達到中斷點為止。 在 **偵錯**功能表上，選擇**新中斷點** > **資料中斷點** 

    您也可以選取**的新** > **資料中斷點**中**中斷點**視窗。
  
2.  在 [位址] 方塊中，鍵入記憶體位址或評估為記憶體位址的運算式。 例如，輸入當變數 `&avar` 的內容變更時要中斷的 `avar` 。  
  
3.  在 [位元組計數]  下拉式清單中，選取想要偵錯工具監看的位元組數量。 例如，如果選取 **4**，則偵錯工具將從 `&avar` 開始監看四個位元組，並且在任何這些位元組的值變更時中斷。  

在下列情況下，不適用資料中斷點：  
-   未進行偵錯的處理序會寫入記憶體位置。  
-   記憶體位置會在兩個或多個處理序之間共用。  
-   記憶體位置已在核心內更新。 例如，如果記憶體已傳遞至 32 位元 Windows`ReadFile`函式，記憶體將更新從核心模式，因此偵錯工具不會在更新時中斷。  

>[!NOTE]
>- 資料中斷點會相依於特定記憶體位址。 變數的位址變成一個偵錯工作階段的下一步，以便在每個偵錯工作階段結束時自動停用資料中斷點。  
>  
>- 如果您對區域變數設定資料中斷點，則此中斷點在函式結束時會保持啟用狀態，但是此記憶體位址不再適用，因此該中斷點的行為無法預期。 如果您對區域變數設定資料中斷點，您應該刪除或停用函式結束前的中斷點。  

##  <a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> 在中斷點視窗中管理中斷點 

 您可以使用**中斷點**地查看和管理您的方案中的所有中斷點 視窗。 這個集中式的位置是在大型解決方案中，或針對複雜非常重視中斷點的偵錯案例特別有用。 

在 [**中斷點**] 視窗中，您可以搜尋、 排序、 篩選、 啟用/停用或刪除中斷點。 您也可以設定條件和動作，或新增新的函式或資料中斷點。
  
若要開啟 **中斷點**視窗中，選取**偵錯** > **Windows** > **中斷點**，或按**Alt**+**F9**或是**Ctrl**+**Alt**+**B**。
  
![中斷點視窗](../debugger/media/breakpointswindow.png "中斷點視窗")  
  
若要選取要顯示在資料行**中斷點**視窗中，選取**顯示行**。 選取資料行標頭以便排序依據該資料行的中斷點清單。 

###  <a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> 中斷點標籤  
您可以使用標籤來排序和篩選清單中的中斷點**中斷點**視窗。 

1. 若要新增標籤至中斷點，請以滑鼠右鍵按一下中斷點的原始程式碼中或**中斷點** 視窗中，，然後選取**編輯標籤**。 新增新的標籤或選擇現有的帳戶，然後按**確定**。
2. 排序中的中斷點清單**中斷點**視窗中的選取**標籤**，**條件**，或其他資料行標頭。 您可以選取要顯示所選取的資料行**顯示的資料行**工具列中。 
  
### <a name="export-and-import-breakpoints"></a>匯出和匯入中斷點  
 若要儲存或共用的狀態和您的中斷點的位置，您可以匯出或匯入它們。 

- 若要將單一中斷點匯出至 XML 檔案，以滑鼠右鍵按一下中斷點的原始程式碼中或**中斷點** 視窗中，然後選取**匯出**或是**匯出所選**。 選取的匯出位置，然後選取**儲存**。 預設位置是方案資料夾。 
- 若要匯出多個中斷點，**中斷點** 視窗中，選取中斷點，旁邊的方塊，或輸入中的搜尋準則**搜尋**欄位。 選取 **匯出符合目前搜尋條件的所有中斷點**圖示，然後儲存檔案。 
- 要匯出的所有中斷點，請取消選取所有的方塊，並將**搜尋**欄位保留空白。 選取 **匯出符合目前搜尋條件的所有中斷點**圖示，然後儲存檔案。  
- 要匯入中斷點**中斷點**視窗中，選取**從檔案匯入中斷點**圖示，瀏覽至 XML 檔案位置，然後選取**開啟**。 

##  <a name="breakpoint-conditions"></a>中斷點條件  
 您可以設定條件來控制中斷點執行的時機和位置。 條件可以是偵錯工具會辨識的任何有效運算式。 如需有效運算式的詳細資訊，請參閱[偵錯工具中的運算式](../debugger/expressions-in-the-debugger.md)。  

**若要設定中斷點條件：**

1. 以滑鼠右鍵按一下中斷點符號，然後選取**條件**。 或將滑鼠停在中斷點符號，選取**設定**圖示，然後再選取**條件**中**中斷點設定**視窗。  

   您也可以設定條件**中斷點**視窗中的以滑鼠右鍵按一下中斷點，然後選取**設定**，然後選取**條件**。 
  
   ![中斷點設定](../debugger/media/breakpointsettings.png "BreakpointSettings")  
  
2. 在下拉式清單中，選取**條件運算式**，**叫用次數**，或**篩選**，並據此設定的值。 
  
3. 選取 **關閉** 或按**Ctrl**+**Enter**以關閉 **中斷點設定**視窗。 或從**中斷點**視窗中，選取**確定**以關閉對話方塊。 

顯示具有條件設定中斷點**+** 原始程式碼中的符號和**中斷點**windows。 

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="conditional-expression"></a>條件運算式

當您選取**條件運算式**，您可以選擇兩個條件：**成立**或是**時變更**。 選擇**成立**滿足運算式時中斷或**變更時**以運算式的值變更時中斷。  
  
 在下列範例中，叫用中斷點時，才的值`testInt`已**4**:  
  
 ![中斷點條件為真](../debugger/media/breakpointconditionistrue.png "中斷點是 true")  
  
 在下列範例中，叫用中斷點時，才值`testInt`變更：  
  
 ![變更時的中斷點](../debugger/media/breakpointwhenchanged.png "中斷點時變更")  
  
 如果使用無效的語法設定中斷點條件，警告訊息便會出現。 如果使用有效的語法，但是無效的語意指定中斷點條件，在第一次叫用中斷點時，則會出現警告訊息。 在任一情況下，當它叫用無效的中斷點會中斷偵錯工具。 只有在條件是有效的並且判斷值為 `false`時，才會略過中斷點。  
  
 >[!NOTE]
 >[變更時] 欄位的行為，會隨不同的程式設計語言而異。 
 >- 原生程式碼，偵錯工具不會視為變更，因此不會叫用第一次評估中斷點條件的第一次評估。 
 >- Managed 程式碼，偵錯工具叫用中斷點之後的第一個評估**變更時**已選取。  
  
### <a name="using-object-ids-in-conditional-expressions-c-and-f-only"></a>使用條件式運算式中的物件識別碼 (C#和F#只)  
 有些的時候，當您想要觀察特定物件的行為。 比方說，您可能會想了解為什麼物件插入至集合一次以上。 在 C# 和 F# 中，您可以針對[參考類型](/dotnet/csharp/language-reference/keywords/reference-types)的特定執行個體建立物件識別碼，並用於中斷點條件中。 物件 ID 是由 Common Language Runtime (CLR) 偵錯服務所產生並與物件相關聯。  

**若要建立的物件識別碼：** 
  
1. 設定中斷點的程式碼中的某個地方建立物件之後。  
   
2. 開始偵錯，以及時的中斷點處暫停執行，選取**偵錯** > **Windows** > **區域變數**或**Alt**+ **4**以開啟**區域變數**視窗。
   
   尋找在中斷點**區域變數** 視窗中，按一下滑鼠右鍵，然後選取**設定物件 ID**。  
   
   您應該會看到 [區域變數] **$** 視窗中顯示 **$** 視窗中設定中斷點，在進行呼叫的函式返回的指令或程式行位置中斷執行。 這就是物件 ID。  
   
3. 在您想要調查; 加入新的中斷點例如，當物件是要加入至集合。 以滑鼠右鍵按一下中斷點並選取 [條件]。  
   
4. 使用 [條件運算式] 欄位中的物件識別碼。 比方說，如果變數`item`是要加入至集合中，選取的物件**成立**並輸入**item = = $\<n >**，其中\<n > 是物件 ID 號碼.  
   
   要將該物件加入集合時，執行會在該處中斷。  
   
   若要刪除的物件識別碼，以滑鼠右鍵按一下中的變數**區域變數**視窗，然後選取**刪除物件 ID**。  

>[!NOTE]
>物件 ID 會建立弱式參考，且不會防止記憶體回收物件。 它們僅針對目前的偵錯工作階段才有效。  
  
### <a name="hit-count"></a>叫用次數  
 如果您懷疑您的程式碼中的迴圈開始出現行為異常特定數目的反覆項目之後，您可以設定中斷點以停止執行之後的點擊數，而不需要重複按數字**F5**觸達該反覆項目。  
  
 底下**條件**中**中斷點設定**視窗中，選取**叫用次數**，然後指定反覆項目數目。 在下列範例中，會叫用每一個反覆項目上設定中斷點：  
  
 ![中斷點叫用次數](../debugger/media/breakpointhitcount.png "BreakpointHitCount")  
  
### <a name="filter"></a>篩選器  
您可以限制只在指定的裝置上或指定的處理序和執行緒中引發中斷點。  
  
底下**條件**中**中斷點設定**視窗中，選取**篩選**，然後輸入一或多個下列運算式：  
  
-   MachineName = "名稱"  
-   ProcessId = 值  
-   ProcessName ="名稱"  
-   ThreadId = 值  
-   ThreadName = "名稱"  

將字串值置於雙引號中。 您可以使用這些來結合子句： `&` (AND)、 `||` (OR)、 `!` (NOT) 和括號。  
  
##  <a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> 中斷點動作和追蹤點  
 「追蹤點」是將訊息列印至 [輸出] 視窗的中斷點。 追蹤點在程式語言中的行為可以像是暫存追蹤陳述式。  
  
**若要設定追蹤點：**

1. 以滑鼠右鍵按一下中斷點，然後選取**動作**。 或者，在**中斷點設定** 視窗中，將滑鼠停在中斷點上，選取**設定**圖示，然後再選取**動作**。  
   
1. 輸入中的訊息**將訊息記錄到輸出視窗**欄位。 訊息可以包含一般文字字串、 變數或運算式括在大括號和格式規範的值 ([ C# ](../debugger/format-specifiers-in-csharp.md)並[c + +](../debugger/format-specifiers-in-cpp.md)) 的值。
   
   您也可以在訊息中使用下列特殊關鍵字：  
   
   - **$ADDRESS** -目前的指令  
   - **$CALLER** -呼叫函式名稱  
   - **$CALLSTACK** -呼叫堆疊 
   - **$FUNCTION** -目前的函式名稱  
   - **$PID** -處理序識別碼  
   - **$PNAME** -處理序名稱  
   - **$TID** -執行緒識別碼  
   - **$TNAME** -執行緒名稱  
   - **$TICK** -滴答計數 (從 Windows `GetTickCount`)  
   
1. 若要列印的訊息**輸出**而不會中斷選取的視窗**繼續執行**核取方塊。 若要列印在追蹤點的訊息，並中斷執行，請清除核取方塊。 

追蹤點會顯示為原始程式碼的左邊界中的紅色方塊並**中斷點**windows。 
  
## <a name="see-also"></a>另請參閱

- [什麼是偵錯？](../debugger/what-is-debugging.md)
- [撰寫更好C#使用 Visual Studio 程式碼](../debugger/write-better-code-with-visual-studio.md)
- [率先一睹偵錯](../debugger/debugger-feature-tour.md)
- [疑難排解 Visual Studio 偵錯工具中的中斷點](../debugger/troubleshooting-breakpoints.md)