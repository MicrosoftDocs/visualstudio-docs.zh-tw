---
title: "巡覽程式碼與 Visual Studio 中偵錯工具 |Microsoft 文件"
ms.custom: H1Hack27Feb2017
ms.date: 02/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
caps.latest.revision: "42"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2c45f6cfa37ee8593da08d59071d8244b08feac7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="navigate-code-with-the-visual-studio-debugger"></a>巡覽程式碼與 Visual Studio 偵錯工具
熟悉命令和快速鍵來巡覽偵錯工具中的程式碼，也會讓更快且更容易尋找和解決您的應用程式中的問題。 當您巡覽程式碼偵錯工具中的時，您可以檢查您的應用程式的狀態，或深入了解它的執行流程。  
  
## <a name="start-debugging"></a>開始偵錯  
 通常，您可以開始偵錯工作階段使用**F5** (**偵錯** > **開始偵錯**)。 此命令會啟動您的應用程式附加偵錯工具。  
  
 綠色箭號也會啟動偵錯工具 (與相同**F5**)。  
  
 ![DBG &#95;基本概念 &#95;開始 &#95; 偵錯](../debugger/media/dbg_basics_start_debugging.png "DBG_Basics_Start_Debugging")  
  
 您可以附加偵錯工具啟動應用程式的其他幾種方式包含**F11** ([逐步執行程式碼](#BKMK_Step_into__over__or_out_of_the_code))， **F10** ([不進入函式程式碼](#BKMK_Step_over_Step_out))，或由使用**執行至游標處**。  有關這些選項執行之操作，請參閱本主題的資訊的其他章節。  
  
 當您偵錯時，黃色列會顯示您接下來執行的程式碼。  
  
 ![DBG &#95;基本概念 &#95;中斷 &#95;模式](../debugger/media/dbg_basics_break_mode.png "DBG_Basics_Break_Mode")  
  
 偵錯時，您可以切換等命令**F5**， **F11**及使用其他功能 （例如中斷點） 本主題說明若要快速取得您想要查看程式的碼。  
  
 大部分的偵錯工具功能，例如在 [區域變數] 視窗中檢視變數的值，或在 [監看式] 視窗中評估運算式，則使用只偵錯工具已暫停 (也稱為*中斷模式*)。 偵錯工具暫停時，應用程式狀態已暫停時函式、 變數，而物件保留在記憶體中。 在中斷模式時，您可以檢查項目的位置和狀態，以尋找違規或錯誤。 針對某些專案類型，您也可以進行調整應用程式處於中斷模式時。 若要觀看視訊，其中顯示這些功能，請參閱[偵錯工具使用者入門](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6)。
  
##  <a name="BKMK_Step_into__over__or_out_of_the_code"></a>逐步執行程式碼中，一行一行地  
 若要停止偵錯時每一行程式碼 （每個陳述式），使用**F11**鍵盤快速鍵 (或**偵錯** > **逐步執行**功能表上)。  
  
> [!TIP]
>  當您執行每一行程式碼，您可以將滑鼠停留在變數，以查看其值，或使用[區域變數](../debugger/autos-and-locals-windows.md)和[監看式](../debugger/autos-and-locals-windows.md)windows 監看變更其值。  
  
 以下是一些詳細的行為**逐步執行**:  
  
-   [ **逐步執行** ] 會在巢狀函式呼叫中逐步執行最深的巢狀函式。 如果您在類似 **的呼叫中使用 [逐步執行]**`Func1(Func2())`，偵錯工具就會逐步執行函式 `Func2`。  
  
-   偵錯工具實際上逐步執行程式碼陳述式，而不是實際程式碼行。 例如 `if` 子句可撰寫在一行上：  
  
    ```CSharp  
    int x = 42;  
    string s = "Not answered";  
    if( int x == 42) s = "Answered!";  
    ```  
  
    ```VB  
    Dim x As Integer = 42  
    Dim s As String = "Not answered"  
    If x = 42 Then s = "Answered!"  
    ```  
  
     當您逐步執行至這一行時，偵錯工具會將條件視為一個步驟並將結果視為另一個步驟 (在此範例中，條件是 true)。  
  
 若要以視覺方式追蹤呼叫堆疊時逐步執行函式，請參閱[偵錯時對應呼叫堆疊上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)。  
  
##  <a name="BKMK_Step_over_Step_out"></a>逐步執行程式碼中，略過函式  
 當偵錯工具中執行程式碼，通常您會發現，您不需要看到特定函式中發生的事 (不在意或您知道它如何運作，要經過完整測試的程式庫程式碼)。 若要跳過程式碼中使用這些命令 （函式仍在執行，當然，但偵錯工具會略過它們）。  
  
|鍵盤命令|功能表命令|描述|  
|----------------------|------------------|-----------------|  
|**F10**|**不進入函式**|如果目前的行包含函式呼叫，**不進入函式**執行的程式碼，然後之後暫止執行的程式碼的第一行呼叫的函式傳回。|  
|**Shift + F11**|**跳離函式**|**跳離函式**仍然會繼續執行程式碼和目前的函式會傳回 （偵錯工具會略過透過目前的函式） 時，暫停執行。|  
  
> [!TIP]
>  如果您需要找出應用程式的進入點，以啟動**F10**或**F11**。 當您檢查應用程式狀態或嘗試了解有關其執行流程的詳細資訊，這些命令通常是很有幫助。  
  
##  <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a>執行至特定位置或函式  
 通常偵錯程式碼的慣用的方法，這些方法可用於當您知道實際程式的碼內容您想要檢查，或至少您知道您要開始偵錯。  
  
-   **在程式碼中設定中斷點**  
  
     若要在程式碼中設定簡單的中斷點，請在 Visual Studio 編輯器中開啟原始程式檔。 將游標放在一行程式碼要暫止執行，並以滑鼠右鍵按一下要查看內容功能表，然後選擇 程式碼視窗**中斷點 > 插入中斷點**(或按**F9**)。 在執行該行之前，偵錯工具暫停執行權限。  
  
     ![設定中斷點](../debugger/media/dbg_basics_setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     Visual Studio 的中斷點提供一組豐富的其他功能，例如條件式中斷點和追蹤點。 請參閱[使用中斷點](../debugger/using-breakpoints.md)。  
  
-   **執行至游標位置**  
  
     若要執行至游標位置，請將游標置於來源視窗中的一行可執行的程式碼。 在編輯器的操作功能表 （右鍵在編輯器中），選擇 **執行至游標處**。 這就像設定暫時中斷點。

-   **按一下以執行** 

    若要執行的點暫停偵錯工具時，程式碼中，選取**執行這裡**綠色箭號圖示 （您將看到游標一行程式碼圖示）。 這樣就不需要設定暫時中斷點。

    ![偵錯工具的執行按一下](../debugger/media/dbg-run-to-click.png "DbgRunToClick") 

    > [!NOTE]
    > **按一下以執行**新[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]。
  
-   **手動中斷程式碼**  
  
     若要中斷執行中應用程式的下一行程式碼，請選擇 [ **偵錯**]、[ **全部中斷** ] (鍵盤： **Ctrl+Alt+Break**)。 
  
     如果您在執行沒有對應原始程式檔或符號檔 (.pdb) 的程式碼時中斷，偵錯工具會顯示 [找不到原始程式檔]  或 [找不到符號]  頁面，協助您找出適當的檔案。 請參閱[指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。 如果您無法存取支援檔案，您仍然可以在 [反組譯碼] 視窗中偵錯組譯碼指令。  
  
-   **執行至呼叫堆疊上的函式**  
  
     在**呼叫堆疊**視窗 （偵錯時可用），選取函式，以滑鼠右鍵按一下並選擇**執行至游標處**。 若要以視覺方式追蹤呼叫堆疊，請參閱[偵錯時對應呼叫堆疊上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)。  
  
-   **執行至名稱所指定的函式**  
  
     您可以通知偵錯工具執行您的應用程式直至指定的函式。 您可以依名稱來指定函式，或是在呼叫堆疊中選擇函式。  
  
     若要依名稱指定函式，選擇 [ **偵錯**]、[ **新增中斷點**]、[ **在函式中斷**]，然後輸入函式名稱和其他識別資訊。  
  
     ![新中斷點對話方塊](../debugger/media/dbg_execution_newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     如果函式已多載或在多個命名空間中，您可以在 [ **選擇中斷點** ] 對話方塊中選擇想要的函式。  
  
     ![選擇中斷點對話方塊](../debugger/media/dbg_execution_overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
##  <a name="BKMK_Set_the_next_statement_to_execute"></a>將指標移至變更執行流程  
 當偵錯工具暫停時，您可以移動指令指標來設定要執行的程式碼的下一個陳述式。 來源或 [反組譯碼] 視窗邊界中的黃色箭頭，將會標記出下一個要執行的陳述式之位置。 您可以移動這個箭頭以略過一部分的程式碼或是返回先前執行的行。 可以在某些情形中使用這項功能，例如略過包含已知錯誤的程式碼區段。  
  
 ![將指標移](../debugger/media/dbg_basics_example3.gif "DBG_Basics_Example3")
  
 若要設定下一個要執行的陳述式，請使用下列其中一項程序：  
  
-   在來源視窗中，將黃色箭頭拖曳至想要設定下一個陳述式的位置 (在相同的原始程式檔中)  
  
-   在來源視窗中，將游標放在您想要執行接下來，以滑鼠右鍵按一下，然後選擇行**設定下一個陳述式**。  
  
-   在 反組譯碼 視窗中，將游標放在您想要執行接下來，以滑鼠右鍵按一下組譯碼指令，然後選擇 **設定下一個陳述式**。  
  
> [!CAUTION]
>  設定下一個陳述式會導致程式計數器直接跳至新的位置。 使用這個命令時請務必要注意：  
>   
>  -   不會執行舊與新執行點之間的指令  
> -   如果將執行點向後移，並不會復原中間的指令  
> -   將下一個陳述式移至其他函式或範圍通常會造成呼叫堆疊損毀，導致執行階段錯誤或例外狀況。 如果嘗試將下一個陳述式移至其他範圍，偵錯工具會開啟警告對話方塊，讓您有機會取消作業。 在 Visual Basic，您無法將下一個陳述式移至其他範圍或函式  
> -   在原生 C++ 中，如果啟用執行階段檢查，設定下一個陳述式會導致在執行到方法結尾時擲回例外狀況  
> -   啟用 [編輯後繼續] 時，如果您進行了 [編輯後繼續] 無法立即重新對應的編輯作業，[ **設定下一個陳述式** ] 就會失敗。 舉例來說，如果您編輯了 catch 區塊內的程式碼，就會發生這種情況。 當發生這種情況時，您會看到錯誤訊息，告訴您此作業都不支援。  
  
> [!NOTE]
>  在 Managed 程式碼中，您無法在下列情況中移動下一個陳述式：  
>   
>  -   下一個陳述式是在與目前陳述式不同的方法中  
> -   使用 Just-In-Time 偵錯啟動偵錯。  
> -   呼叫堆疊回溯進行中  
> -   擲回 System.StackOverflowException 或 System.Threading.ThreadAbortException 例外狀況  
  
 應用程式正在執行時，不能設定下一個陳述式。 若要設定下一個陳述式，偵錯工具必須處於中斷模式下。  
  
## <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>逐步執行非使用者程式碼  
 根據預設，偵錯工具會嘗試顯示您只有您的應用程式程式碼偵錯時，是由偵錯工具稱為決定*Just My Code*。 (請參閱[Just My Code](../debugger/just-my-code.md)以查看這適用於不同的專案類型和語言的方式以及您如何自訂行為。)不過，有時候您會偵錯時，您可能想要看看 framework 程式碼、 協力廠商程式庫程式碼或呼叫作業系統 （系統呼叫）。  
  
 您可以關閉 Just My Code，請前往**工具** > **選項** > **偵錯**清除**啟用 Just My Code**核取方塊。  
  
 停用 Just My Code 時，偵錯工具可以逐步執行至非使用者程式碼和非使用者程式碼會出現在偵錯工具視窗。  
  
> [!NOTE]
>  裝置專案不支援 Just My Code。  
  
 **逐步執行系統呼叫**  
  
 如果您已載入系統程式碼的偵錯符號，而且沒有啟用 Just My Code，您可以逐步執行系統呼叫其他任何呼叫一樣。  
  
 若要存取 Microsoft 符號檔，請參閱[使用符號伺服器尋找不在您本機電腦上的符號檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine)中[指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)主題。  
  
 若要在偵錯時載入特定系統元件的符號：  
  
1.  開啟 [模組] 視窗 (鍵盤： **Ctrl + Alt + U**)。  
  
2.  選取您要載入其符號的模組。  
  
     您可以透過查看 [ **符號狀態** ] 欄來判斷哪些模組已經載入符號。  
  
3.  選擇內容功能表上的 [ **載入符號** ]。  
  
##  <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> 逐步執行 Managed 程式碼中的屬性及運算子  
 偵錯工具預設為不進入 Managed 程式碼中的屬性及運算子。 在大部分情況下，這會產生比較令人滿意的偵錯經驗。 若要啟用逐步執行屬性或運算子，請選擇**偵錯** > **選項**。 在**偵錯** > **一般**頁面上，清除**不進入屬性和運算子 (僅限 Managed)**核取方塊