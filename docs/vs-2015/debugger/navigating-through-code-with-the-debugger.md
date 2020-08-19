---
title: 使用偵錯工具流覽程式碼 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f79ece781db19f2483ef1dd6cb0a81ff7cf78e06
ms.sourcegitcommit: 4be64917e4224fd1fb27ba527465fca422bc7d62
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "88608935"
---
# <a name="navigating-through-code-with-the-debugger"></a>使用偵錯工具巡覽程式碼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

熟悉命令和快捷方式，以在偵錯工具中流覽程式碼，並可讓您更快速且更輕鬆地尋找和解決應用程式中的問題。 當您在偵錯工具中流覽程式碼時，您可以 [檢查應用程式的狀態](https://msdn.microsoft.com/library/mt243867.aspx#BKMK_Inspect_Variables) ，或深入瞭解其執行流程。  
  
## <a name="start-debugging"></a>開始偵錯  
 通常，您會使用**F5** (**Debug**  /  **開始調試**) 來啟動調試會話。 此命令會啟動已附加偵錯工具的應用程式。  
  
 綠色箭號也會啟動偵錯工具 (與 **F5**) 相同。  
  
 ![DBG&#95;基本概念&#95;開始&#95;的調試](../debugger/media/dbg-basics-start-debugging.png "DBG_Basics_Start_Debugging")  
  
 您可以使用附加偵錯工具來啟動應用程式的其他一些方法包括 **F11** ([逐步](#BKMK_Step_into__over__or_out_of_the_code) 執行程式碼) 、  **F10** (不進入程式 [代碼](#BKMK_Step_over_Step_out)) ，或使用 [ **執行至游標處**]。  請參閱本主題中的其他章節，以取得這些選項的用途資訊。  
  
 當您進行偵錯工具時，黃色線會顯示接下來將執行的程式碼。  
  
 ![DBG&#95;基本概念&#95;中斷&#95;模式](../debugger/media/dbg-basics-break-mode.png "DBG_Basics_Break_Mode")  
  
 在進行偵錯工具時，您可以在命令（例如 **F5**、 **F11** 和使用本主題中所述的其他功能）之間切換 (例如中斷點) ，以快速取得您想要查看的程式碼。  
  
 大部分的偵錯工具功能（例如在 [區域變數] 視窗中查看變數值，或在監看式視窗中評估運算式）都只有在偵錯工具暫停 (也稱為 *中斷模式*) 時才可使用。 當偵錯工具暫停時，您的應用程式狀態會被擱置，而函式、變數和物件仍會保留在記憶體中。 在中斷模式中，您可以檢查元素的位置和狀態，以尋找違規或錯誤。 針對某些專案類型，您也可以在中斷模式下，對應用程式進行調整。  
  
## <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a> 逐步執行程式碼，逐行  
 若要在每一行程式碼上停止 (在進行偵錯工具時) 每個語句，請使用**F11**鍵盤快速鍵 (或在**Debug**  /  **Step Into**功能表) 上的 [偵錯工具]。  
  
> [!TIP]
> 當您執行每一行程式碼時，可以將滑鼠停留在變數上以查看其值，或使用 [ [區域變數](../debugger/autos-and-locals-windows.md) ] 和 [ [監看式]](../debugger/autos-and-locals-windows.md) 視窗來監看其值變更。  
  
 以下是 **逐步**執行行為的一些詳細資料：  
  
- [ **逐步執行** ] 會在巢狀函式呼叫中逐步執行最深的巢狀函式。 如果您在類似 **的呼叫中使用 [逐步執行]**`Func1(Func2())`，偵錯工具就會逐步執行函式 `Func2`。  
  
- 偵錯工具實際上逐步執行程式碼陳述式，而不是實際程式碼行。 例如 `if` 子句可撰寫在一行上：  
  
  ```csharp  
  int x = 42;  
  string s = "Not answered";  
  if( int x == 42) s = "Answered!";  
  ```  
  
  ```vb  
  Dim x As Integer = 42  
  Dim s As String = "Not answered"  
  If x = 42 Then s = "Answered!"  
  ```  
  
   當您逐步執行至這一行時，偵錯工具會將條件視為一個步驟並將結果視為另一個步驟 (在此範例中，條件是 true)。  
  
  若要在逐步執行函式時以視覺方式追蹤呼叫堆疊，請參閱在 [調試過程中對應呼叫堆疊上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)。  
  
## <a name="step-through-code-skipping-functions"></a><a name="BKMK_Step_over_Step_out"></a> 逐步執行程式碼，略過函式  
 在偵錯工具中執行程式碼時，通常您會發現，您不需要查看特定函式中發生什麼事 (您不在意它或您知道它是否正常運作，像是經過妥善測試的程式庫程式碼) 。 當然，您可以使用這些命令略過程式碼 (函式仍會執行，但偵錯工具會略過這些函式) 。  
  
|鍵盤命令|功能表命令|描述|  
|----------------------|------------------|-----------------|  
|**F10**|**逐程序**|如果目前的行包含函式呼叫，[不進入函式] 會執行程式碼，然後在呼叫的函式傳回 **之後，于** 第一行程式碼上暫停執行。|  
|**Shift + F11**|**跳出**|當目前的函式傳回 (偵錯工具略過目前的函式) 時，**會繼續執行**程式碼並暫停執行。|  
  
> [!TIP]
> 如果您需要在應用程式中尋找進入點，請以 **F10** 或 **F11**開始。 當您檢查您的應用程式狀態，或嘗試進一步瞭解其執行流程時，這些命令通常很有説明。  
  
## <a name="run-to-a-specific-location-or-function"></a><a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> 執行至特定位置或函數  
 當您確切知道想要檢查的程式碼時，或至少您知道要在何處開始進行偵錯工具時，這些方法通常是偵錯工具代碼的慣用方法。  
  
- **在程式碼中設定中斷點**  
  
     若要在程式碼中設定簡單的中斷點，請在 Visual Studio 編輯器中開啟原始程式檔。 將游標放在您要暫停執行的程式程式碼，然後以滑鼠右鍵按一下程式碼視窗，以查看操作功能表並選擇 [中斷點] **/[插入中斷點** ] (或按 **F9**) 。 偵錯工具會在執行程式程式碼之前暫停執行。  
  
     ![設定中斷點](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     Visual Studio 的中斷點提供一組豐富的其他功能，例如條件式中斷點和追蹤點。 請參閱 [使用中斷點](../debugger/using-breakpoints.md)。  
  
- **執行至游標位置**  
  
     若要執行至游標位置，請將游標置於來源視窗中的一行可執行的程式碼。 在編輯器的內容功能表上 (以滑鼠右鍵按一下編輯器) ，然後選擇 [ **執行至游標處**]。 這就像是設定暫時中斷點。  
  
- **手動中斷程式碼**  
  
     若要中斷執行中應用程式的下一行程式碼，請選擇 [ **偵錯**]、[ **全部中斷** ] (鍵盤： **Ctrl+Alt+Break**)。  
  
     如果您在執行沒有對應原始程式檔或符號檔 (.pdb) 的程式碼時中斷，偵錯工具會顯示 [找不到原始程式檔] **** 或 [找不到符號] **** 頁面，協助您找出適當的檔案。 請參閱 [指定符號 ( .pdb) 和來源](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)檔案。 如果您無法存取支援檔案，您仍然可以在 [反組譯碼] 視窗中偵錯組譯碼指令。  
  
- **執行至呼叫堆疊上的函式**  
  
     在 [ **呼叫堆疊** ] 視窗中， (在調試) 時可用，請選取函數，再按一下滑鼠右鍵，然後選擇 [ **執行至游標處**]。 若要以視覺化方式追蹤呼叫堆疊，請參閱在 [調試過程中對應呼叫堆疊上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)。  
  
- **執行至名稱所指定的函式**  
  
     您可以告訴偵錯工具執行您的應用程式，直到它到達指定的函式為止。 您可以依名稱來指定函式，或是在呼叫堆疊中選擇函式。  
  
     若要依名稱指定函式，選擇 [ **偵錯**]、[ **新增中斷點**]、[ **在函式中斷**]，然後輸入函式名稱和其他識別資訊。  
  
     ![[新增中斷點] 對話方塊](../debugger/media/dbg-execution-newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     如果函式已多載或在多個命名空間中，您可以在 [ **選擇中斷點** ] 對話方塊中選擇想要的函式。  
  
     ![選擇中斷點對話方塊](../debugger/media/dbg-execution-overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a> 移動指標以變更執行流程  
 當偵錯工具暫停時，您可以移動指令指標以設定下一個要執行的程式碼語句。 來源或 [反組譯碼] 視窗邊界中的黃色箭頭，將會標記出下一個要執行的陳述式之位置。 您可以移動這個箭頭以略過一部分的程式碼或是返回先前執行的行。 可以在某些情形中使用這項功能，例如略過包含已知錯誤的程式碼區段。  
  
 ![Example2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")  
  
 若要設定下一個要執行的陳述式，請使用下列其中一項程序：  
  
- 在來源視窗中，將黃色箭頭拖曳至想要設定下一個陳述式的位置 (在相同的原始程式檔中)  
  
- 在來源視窗中，將游標放在您接下來要執行的程式列上，按一下滑鼠右鍵，然後選擇 [ **設定下一個語句]**。  
  
- 在 [反組解碼] 視窗中，將游標放在您接下來要執行的元件指令上，以滑鼠右鍵按一下，然後選擇 [ **設定下一個語句]**。  
  
> [!CAUTION]
> 設定下一個陳述式會導致程式計數器直接跳至新的位置。 使用這個命令時請務必要注意：  
> 
> - 不會執行舊與新執行點之間的指令  
>   - 如果將執行點向後移，並不會復原中間的指令  
>   - 將下一個陳述式移至其他函式或範圍通常會造成呼叫堆疊損毀，導致執行階段錯誤或例外狀況。 如果嘗試將下一個陳述式移至其他範圍，偵錯工具會開啟警告對話方塊，讓您有機會取消作業。 在 Visual Basic，您無法將下一個陳述式移至其他範圍或函式  
>   - 在原生 C++ 中，如果啟用執行階段檢查，設定下一個陳述式會導致在執行到方法結尾時擲回例外狀況  
>   - 啟用 [編輯後繼續] 時，如果您進行了 [編輯後繼續] 無法立即重新對應的編輯作業，[ **設定下一個陳述式** ] 就會失敗。 舉例來說，如果您編輯了 catch 區塊內的程式碼，就會發生這種情況。 當發生這種情況時，您將會看到一則錯誤訊息，說明不支援此作業。  
> 
> [!NOTE]
> 在 Managed 程式碼中，您無法在下列情況中移動下一個陳述式：  
> 
> - 下一個陳述式是在與目前陳述式不同的方法中  
>   - 使用 Just-In-Time 偵錯啟動偵錯。  
>   - 呼叫堆疊回溯進行中  
>   - 擲回 System.StackOverflowException 或 System.Threading.ThreadAbortException 例外狀況  
  
 應用程式正在執行時，不能設定下一個陳述式。 若要設定下一個陳述式，偵錯工具必須處於中斷模式下。  
  
## <a name="step-into-non-user-code"></a>逐步執行非使用者程式碼  
 根據預設，偵錯工具只會在進行偵錯工具時，只顯示您的應用程式程式碼，這是由稱為 *Just My Code*的偵錯工具設定所決定。  (查看 [Just My Code](../debugger/just-my-code.md) 來瞭解這對不同專案類型和語言的運作方式，以及您可能自訂行為的方式。 ) 不過，有時候您正在進行偵錯工具時，您可能會想要查看 framework 程式碼、協力廠商程式庫程式碼，或 (系統呼叫的作業系統呼叫) 。  
  
 您可以前往 [**工具**選項] 偵錯工具來關閉 Just My Code  /  **Options**  /  **Debugging** ，並清除 [**啟用 Just My Code** ] 核取方塊。  
  
 當 Just My Code 停用時，偵錯工具可以逐步執行非使用者程式碼，而非使用者程式碼會出現在偵錯工具視窗中。  
  
> [!NOTE]
> 裝置專案不支援 Just My Code。  
  
 **逐步執行系統呼叫**  
  
 如果您已載入系統程式碼的偵錯工具符號，但未啟用 Just My Code，您可以逐步執行系統呼叫，就像您可以進行任何其他呼叫一樣。  
  
 若要存取 Microsoft 符號檔，請參閱[指定符號 ( .pdb) 和原始](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)程式檔主題中的[使用符號伺服器尋找不在本機電腦上的符號](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine)檔。  
  
 若要在偵錯時載入特定系統元件的符號：  
  
1. 開啟 [模組] 視窗 (鍵盤： **Ctrl+Alt+U**)。  
  
2. 選取您要載入其符號的模組。  
  
     您可以透過查看 [ **符號狀態** ] 欄來判斷哪些模組已經載入符號。  
  
3. 選擇內容功能表上的 [ **載入符號** ]。  
  
## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> 逐步執行 Managed 程式碼中的屬性及運算子  
 偵錯工具預設為不進入 Managed 程式碼中的屬性及運算子。 在大部分情況下，這會產生比較令人滿意的偵錯經驗。 若要啟用逐步執行屬性或運算子，請選擇 [ **Debug**  /  **選項**]。 在 [**調試**  /  **一般**] 頁面上，清除 [不進入**屬性和運算子] ([僅限 Managed) ** ] 核取方塊
