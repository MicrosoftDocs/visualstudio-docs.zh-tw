---
title: 使用 Visual Studio 偵錯工具巡覽程式碼 |Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 11/12/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 865fbca5092378af044d6121862119ecba8625a2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51748673"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Visual Studio 偵錯工具巡覽程式碼

Visual Studio 偵錯工具可協助您瀏覽程式碼來檢查應用程式的狀態，並顯示其執行流程。 若要快速取得您想要檢查的程式碼，您可以使用鍵盤快速鍵、 偵錯 命令、 中斷點及其他功能。 熟悉偵錯工具巡覽命令和快速鍵可以更快速且輕易地尋找和解決應用程式的問題。  
  
## <a name="basic-debugging"></a>基本偵錯  

若要附加偵錯工具啟動應用程式，請按**F5**，選取**偵錯** > **開始偵錯**，或在 Visual Studio 工具列中選取的綠色箭頭。  
  
 ![DBG&#95;Basics&#95;Start&#95;Debugging](../debugger/media/dbg_basics_start_debugging.png "DBG_Basics_Start_Debugging")  
  
當您偵錯時，黃色反白顯示就會顯示的一行程式碼會執行下一步。  
  
 ![DBG&#95;基本概念&#95;Break&#95;模式](../debugger/media/dbg_basics_break_mode.png "中斷模式")  
  
大部分偵錯工具視窗，例如**模組**並**監看式**windows 中，有，只會執行偵錯工具時。 有些偵錯工具功能，例如檢視中的變數值**區域變數**視窗或在中評估運算式**監看式**視窗中，只有當偵錯工具已暫停於中斷點的行，也稱為時，才可使用*中斷模式*。 

在中斷模式中，函式中，變數時，會暫停應用程式執行，並保留在記憶體中的物件。 您可以檢查項目的位置和狀態，以尋找違規或錯誤。 針對某些專案類型，您也可以進行調整應用程式處於中斷模式時。 示範這些功能的影片，請參閱 < [Getting Started with 偵錯工具](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6)。

如果中斷在沒有原始檔或符號的程式碼中 (*.pdb*) 載入的檔案，偵錯工具會顯示**檔案找不到來源**或是**找不到符號**可協助您的頁面尋找並載入檔案。 請參閱[指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。 如果您無法載入符號或原始程式檔，您仍然可以偵錯中的組件指令**反組譯碼**視窗。 

您不一定要開始偵錯啟動應用程式的開頭。 您也可以按下**F11**要[逐步執行程式碼](#BKMK_Step_into__over__or_out_of_the_code)，按下**F10**至[略過程式碼](#BKMK_Step_over_Step_out)，或[執行至特定位置或函式](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All)。    

##  <a name="step-through-code"></a>逐步執行程式碼

偵錯工具逐步執行命令，可協助您檢查應用程式狀態，或深入了解其執行流程。 

如果您要尋找應用程式中的進入點，以啟動**F10**或是**F11**。  

### <a name="BKMK_Step_into__over__or_out_of_the_code"></a> 逐步執行逐行程式碼  

若要停止程式碼或在偵錯時的陳述式的每一行，使用**偵錯** > **逐步**，或按**F11**。  

偵錯工具會逐步引導您程式碼陳述式，而不實際程式碼行。 比方說，`if`子句可以撰寫在一行上：  
  
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

不過，當您逐步執行這一行，偵錯工具會將條件視為一個步驟中，並將結果視為另一個。 在上述範例中，條件為 true。  
  
[ **逐步執行** ] 會在巢狀函式呼叫中逐步執行最深的巢狀函式。 例如，如果您使用**逐步**的呼叫，例如`Func1(Func2())`，偵錯工具逐步執行函式`Func2`。  

>[!TIP]
>當您執行每一行程式碼時，您可以暫留變數，以查看其值，或是使用[區域變數](autos-and-locals-windows.md)並[監看式](watch-and-quickwatch-windows.md)監看變更值的 windows。 同時逐步執行函式中，您可以也以視覺化方式追蹤呼叫堆疊。 請參閱[偵錯時對應呼叫堆疊上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)。 

###  <a name="BKMK_Step_over_Step_out"></a> 逐步執行程式碼，並略過某些函式  

您可能不在意函式偵錯時，或您知道它的運作方式，例如通過完善測試的程式庫程式碼。 您可以使用下列命令，可以跳過的程式碼。 函式仍在執行，但偵錯工具會略過它們。  
  
|鍵盤命令|偵錯 功能表命令|描述|  
|----------------------|------------------|-----------------|  
|**F10**|**不進入函式**|如果目前這一行包含函式呼叫**不進入函式**執行的程式碼，然後在第一行程式碼中暫止執行之後呼叫的函式會傳回。|  
|**Shift**+**F11**|**跳離函式**|**跳離函式**會繼續執行程式碼和目前的函式傳回時，會暫停執行。 偵錯工具會略過透過目前的函式。|  
  
##  <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> 執行至特定位置或函式  

您可能會想要知道確切您要檢查哪些程式的碼時，直接向特定的位置或函式執行，或您知道您要開始偵錯。  
  
### <a name="run-to-a-breakpoint-in-code"></a>執行程式碼中的中斷點  
  
若要設定簡單的中斷點，在您的程式碼中，按一下您要暫停執行的最左邊的界的程式碼行旁邊。 您也可以選取一行，然後按**F9**，選取**偵錯** > **切換中斷點**，或以滑鼠右鍵按一下並選取**中斷點** > **插入中斷點**。 中斷點會顯示為一個紅點，程式碼行旁邊的左邊界。 偵錯工具會在執行該行之前暫停執行。
  
![設定中斷點](../debugger/media/dbg_basics_setbreakpoint.png "設定中斷點")  
  
Visual Studio 的中斷點提供一組豐富的其他功能，例如條件式中斷點和追蹤點。 如需詳細資訊，請參閱 <<c0> [ 使用中斷點](../debugger/using-breakpoints.md)。  
  
### <a name="run-to-a-function-breakpoint"></a>執行至函式中斷點  

您可以告知偵錯工具執行，直到它到達指定的函式。 您可以指定函式名稱，或您可以在呼叫堆疊中選擇它。  
  
**依名稱指定函式中斷點**

1. 選取 **偵錯** > **新中斷點** > **函式中斷點**
   
1. 在 [**新的函式中斷點**] 對話方塊中，輸入函式的名稱，然後選取其語言。
   
   ![[新增函式中斷點] 對話方塊](../debugger/media/dbg_execution_newbreakpoint.png "新增函式中斷點")  
   
1. 選取 [確定]。 

如果函式已多載或在一個以上的命名空間中，您可以選擇您想的要在**中斷點**視窗。  

![多載函式中斷點](../debugger/media/dbg_execution_overloadedbreakpoints.png "多載函式中斷點")  
  
**若要在呼叫堆疊中選取函式中斷點** 
  
1. 偵錯時，開啟**呼叫堆疊**視窗中的選取**偵錯** > **Windows** > **呼叫堆疊**。 
   
1. 在 **呼叫堆疊**視窗中，以滑鼠右鍵按一下函式，然後選取**執行至游標處**，或按下**Ctrl**+**F10**。  

若要以視覺方式追蹤呼叫堆疊，請參閱[偵錯時對應呼叫堆疊上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)。  
  
### <a name="run-to-a-cursor-location"></a>執行至游標位置  

若要執行至游標位置，在原始程式碼中或**呼叫堆疊** 視窗中，選取您想要在分頁，以滑鼠右鍵按一下並選取的該行**執行至游標處**，或按下**Ctrl** +**F10**。 選取**執行至游標處**就像設定暫時中斷點。

### <a name="run-to-click"></a>執行至點選處 

當偵錯工具暫停時，您可以將滑鼠移至原始程式碼中的陳述式或**反組譯碼** 視窗中，然後選取**執行到這裡**綠色箭號圖示。 使用**執行至點選處**就不需要設定暫時中斷點。

![執行至點選處](../debugger/media/dbg-run-to-click.png "執行至點選處") 

> [!NOTE]
> **執行至點選處**的新[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]。
  
### <a name="manually-break-into-code"></a>手動中斷程式碼  
  
若要中斷執行中應用程式中的程式碼的下一行中，選取**偵錯** > **全部中斷**，或按**Ctrl**+**Alt** +**中斷**。 
  
##  <a name="BKMK_Set_the_next_statement_to_execute"></a> 將指標移至要變更執行流程  

當偵錯工具暫停時，來源程式碼界的黃色箭頭或**反組譯碼**視窗會將標示要執行下一個陳述式的位置。 您可以變更下一個陳述式，來執行移動這個箭頭。 您可以略過的部分程式碼，或返回先前的行。 將指標移適合的情況下，例如略過包含已知的錯誤的程式碼區段。  

 ![將指標移](../debugger/media/dbg_basics_example3.gif "移動指標")
  
若要變更要執行的下一個陳述式，偵錯工具必須處於中斷模式。 在原始程式碼中或**反組譯碼**視窗中，將黃色箭頭拖曳到不同的一行，或以滑鼠右鍵按一下您想要執行接下來，選取的線條**設定下一個陳述式**。 

程式計數器直接跳到新的位置，並指示不會執行點的舊和新的執行之間。 不過，如果您向後移動執行點，中間的指令不會復原。  

>[!CAUTION]
>- 將下一個陳述式移至其他函式或範圍通常會造成呼叫堆疊損毀，導致執行階段錯誤或例外狀況。 如果嘗試將下一個陳述式移至其他範圍，偵錯工具會開啟警告對話方塊，讓您有機會取消作業。 
>- 在 Visual Basic，您無法將下一個陳述式移至其他範圍或函式  
>- 在原生 C++ 中，如果啟用執行階段檢查，設定下一個陳述式會導致在執行到方法結尾時擲回例外狀況  
>- 啟用 [編輯後繼續] 時，如果您進行了 [編輯後繼續] 無法立即重新對應的編輯作業，[ **設定下一個陳述式** ] 就會失敗。 舉例來說，如果您編輯了 catch 區塊內的程式碼，就會發生這種情況。 當發生這種情況時，則會出現錯誤訊息，告訴您不支援此作業。  
>- 在 managed 程式碼，您無法移動下一個陳述式，如果：  
>   - 下一個陳述式是在與目前陳述式不同的方法中  
>   - 偵錯的 Just In Time 啟動偵錯。  
>   - 呼叫堆疊回溯正在進行中。  
>   - 擲回 System.StackOverflowException 或 System.Threading.ThreadAbortException 例外狀況  
  
## <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>非使用者程式碼進行偵錯  

根據預設，偵錯工具會嘗試藉由啟用設定，稱為，只有您的應用程式程式碼進行偵錯*Just My Code*。 如需進一步瞭解不同專案類型和語言，這項功能的運作方式以及如何自訂它的詳細資訊，請參閱[Just My Code](../debugger/just-my-code.md)。 

若要查看架構程式碼、 協力廠商程式庫程式碼或系統呼叫，偵錯時，您可以停用 Just My Code。 在 [**工具**(或**偵錯**) >**選項** > **偵錯**，清除**啟用 Just My Code** ] 核取方塊。 停用 Just My Code 時，非使用者程式碼會出現在 [偵錯工具] 視窗中，而且偵錯工具可以在非使用者程式碼。  

> [!NOTE]
> 裝置專案不支援 Just My Code。  
  
### <a name="debug-system-code"></a>偵錯系統程式碼

如果您已載入偵錯符號的 Microsoft 系統程式碼，並停用 Just My Code，您可以逐步執行系統呼叫就像其他任何呼叫。  
  
若要載入 Microsoft 符號，請參閱[設定符號位置和載入選項](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options)。  
  
**若要載入特定系統元件的符號：**

1. 當您偵錯時，開啟**模組**視窗中的選取**偵錯** > **Windows** > **模組**，或按下**Ctrl**+**Alt**+**U**。  
  
1. 在 [**模組**] 視窗中，您所見的模組已經載入的符號**符號狀態**資料行。 以滑鼠右鍵按一下您想要載入符號，然後選取模組**載入符號**。  
  
##  <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> 逐步執行 Managed 程式碼中的屬性及運算子  
 根據預設，偵錯工具不進入屬性和運算子，在 managed 程式碼。 不進入屬性和運算子通常可提供更有效偵錯體驗。 若要啟用逐步執行屬性和運算子，在**工具**(或**偵錯**) >**選項** > **偵錯** > **一般**，清除**不進入屬性和運算子 （僅限受控）** 核取方塊。