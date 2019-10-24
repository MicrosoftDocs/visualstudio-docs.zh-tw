---
title: 使用偵錯工具流覽程式碼 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/12/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e07e2612e01453115cf4cd6120d92bfd5b0168bd
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "70222648"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>使用 Visual Studio 偵錯工具流覽程式碼

Visual Studio 偵錯工具可協助您流覽程式碼，以檢查應用程式的狀態，並顯示其執行流程。 您可以使用鍵盤快速鍵、偵錯工具命令、中斷點和其他功能，快速取得您想要檢查的程式碼。 熟悉偵錯工具導覽命令和快捷方式可讓您更快速且更輕鬆地尋找和解決應用程式問題。  如果這是您第一次嘗試偵錯工具代碼，您可能會想要在進行本文之前，先閱讀適用于徹底初學者和[偵錯工具技術和工具](../debugger/write-better-code-with-visual-studio.md) [的偵錯工具](../debugger/debugging-absolute-beginners.md)。

## <a name="basic-debugging"></a>基本偵錯

若要在附加偵錯工具的情況下啟動應用程式，請按**F5**、選取 [ **Debug** ]  >  [**開始調試**]，或選取 [Visual Studio] 工具列中的綠色箭號。

 ![DBG&#95;基本&#95;概念&#95;開始調試](../debugger/media/dbg_basics_start_debugging.png "DBG_Basics_Start_Debugging")

當您正在進行偵錯工具時，黃色醒目提示會顯示接下來要執行的程式程式碼。

 ![DBG&#95;基本&#95;中斷&#95;模式](../debugger/media/dbg_basics_break_mode.png "中斷模式")

大部分的偵錯工具視窗（例如**模組**和**監看**式視窗）只有在偵錯工具執行時才可使用。 某些偵錯工具功能（例如在 [**區域變數**] 視窗中查看變數值或在 [**監看**式] 視窗中評估運算式）只有在偵錯工具于中斷點暫停（也稱為*中斷模式*）時才可以使用。

在中斷模式中，應用程式執行會在函式、變數和物件保留在記憶體中時暫停。 您可以檢查元素的位置和狀態，以尋找違規或 bug。 針對某些專案類型，您也可以在中斷模式中進行應用程式的調整。 如需顯示這些功能的影片，請參閱[使用偵錯工具消費者入門](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6)。

如果您在未載入來源或符號（ *.pdb*）檔案的程式碼中中斷，偵錯工具會顯示 [找**不到原始**程式檔] 或 [找**不到符號**] 頁面，協助您尋找和載入檔案。 請參閱[指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。 如果您無法載入符號檔或原始程式檔，您仍然可以在 [反組解碼 **] 視窗中，對元件**指令進行 debug。

您不一定都需要在一開始就啟動應用程式來啟動偵錯工具。 您也可以按**F11**逐步執行程式碼，按**F10**以不[進入](#BKMK_Step_into__over__or_out_of_the_code)程式[代碼](#BKMK_Step_over_Step_out)，或[執行至特定位置或功能](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All)。

## <a name="step-through-code"></a>逐步執行程式碼

偵錯工具步驟命令可協助您檢查應用程式狀態，或深入瞭解其執行流程。

如果您需要在應用程式中尋找進入點，請從**F10**或**F11**開始。

### <a name="BKMK_Step_into__over__or_out_of_the_code"></a>逐行逐步執行程式碼

若要在偵錯工具時停止每一行程式碼或語句，請使用**Debug**  > **逐步**執行，或按**F11**鍵。

偵錯工具會逐步執行程式碼語句，而不是實體行。 例如 `if` 子句可以寫在一行上：

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

不過，當您逐步執行這一行時，偵錯工具會將條件視為一個步驟，並將結果視為另一個。 在上述範例中，條件為 true。

[ **逐步執行** ] 會在巢狀函式呼叫中逐步執行最深的巢狀函式。 例如，如果您在 `Func1(Func2())` 之類的呼叫中使用 [**逐步**執行]，偵錯工具就會逐步執行 `Func2` 的函式。

>[!TIP]
>當您執行每一行程式碼時，您可以將滑鼠停留在變數上以查看其值，或使用 [[區域變數](autos-and-locals-windows.md)] 和[[監看](watch-and-quickwatch-windows.md)式] 視窗來監看這些值的變更。 您也可以在逐步執行函式時，以視覺化方式追蹤呼叫堆疊。 請參閱在進行[調試時，呼叫堆疊上的對應方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)。

### <a name="BKMK_Step_over_Step_out"></a>逐步執行程式碼並略過一些功能

在進行偵錯工具時，您可能不在意函式，或者您知道它的運作方式，就像是經過妥善測試的程式庫程式碼。 您可以使用下列命令來略過程式碼。 函式仍會執行，但偵錯工具會略過它們。

|鍵盤命令|[調試] 功能表命令|描述|
|----------------------|------------------|-----------------|
|**F10**|**不進入函式**|如果目前這一行包含函式呼叫，不進入函式**會執行程式**代碼，然後在呼叫的函式傳回之後，在程式碼的第一行暫停執行。|
|**Shift**+**F11**|**跳離函式**|[**跳出**] 會繼續執行程式碼，並在目前的函式傳回時暫停執行。 偵錯工具會略過目前的函式。|

## <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a>執行至特定位置或函數

當您確切知道想要檢查的程式碼時，或您知道要開始進行的偵錯工具時，您可能會想要直接執行至特定位置或功能。

### <a name="run-to-a-breakpoint-in-code"></a>在程式碼中執行至中斷點

若要在程式碼中設定簡單的中斷點，請按一下您要暫停執行之程式程式碼旁邊的最左邊界。 您也可以選取該行並按**F9**、選取  **Debug**   > **切換中斷點**，或按一下滑鼠右鍵，然後選取 **中斷點**  > **插入中斷點**。 中斷點會在程式程式碼旁的左邊界中顯示為紅點。 偵錯工具會在執行這行之前暫停執行。

![設定中斷點](../debugger/media/dbg_basics_setbreakpoint.png "設定中斷點")

Visual Studio 的中斷點提供一組豐富的其他功能，例如條件式中斷點和追蹤點。 如需詳細資訊，請參閱[使用中斷點](../debugger/using-breakpoints.md)。

### <a name="run-to-a-function-breakpoint"></a>執行至函數中斷點

您可以指示偵錯工具執行直到到達指定的函式為止。 您可以依名稱來指定函式，或是在呼叫堆疊中選擇函式。

**依名稱指定函數中斷點**

1. 選取 [ **Debug** ]  > **新中斷點** > **函數中斷點**

1. 在 [**新增**函式中斷點] 對話方塊中，輸入函數的名稱，然後選取其語言。

   ![[新增函式中斷點] 對話方塊](../debugger/media/dbg_execution_newbreakpoint.png "新增函式中斷點")

1. 選取 [確定]。

如果函式已多載或在一個以上的命名空間中，您可以在 [**中斷點**] 視窗中選擇您要的一個。

![多載函式中斷點](../debugger/media/dbg_execution_overloadedbreakpoints.png "多載函式中斷點")

**從呼叫堆疊選取函數中斷點**

1. 在偵錯工具中，選取 [ **Debug**  > **Windows**  > **呼叫堆疊**] 來開啟 [**呼叫堆疊**] 視窗。

1. 在 [**呼叫堆疊**] 視窗中，以滑鼠右鍵按一下函數，然後選取 [**執行至游標處**]，或按**Ctrl** +**F10**。

若要以視覺化方式追蹤呼叫堆疊，請參閱在進行[調試時，在呼叫堆疊上對應方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)。

### <a name="run-to-a-cursor-location"></a>執行至游標位置

若要執行至游標位置，請在 [原始程式碼] 或 [**呼叫堆疊**] 視窗中，選取您要中斷的行，按一下滑鼠右鍵，然後選取 [**執行至游標**處]，或按**Ctrl** +**F10**。 選取 [**執行至游標處**] 就像設定暫時中斷點。

### <a name="run-to-click"></a>執行至點選處

在偵錯工具中暫停時，您**可以將滑鼠**停留在 [原始程式碼] 或 [反組解碼] 視窗中的語句上方，然後選取 [執行**到這裡**綠色箭號] 圖示。 使用 [**執行至] 按一下**就不需要設定暫時中斷點。

![執行以按一下](../debugger/media/dbg-run-to-click.png "執行至點選處")

> [!NOTE]
> 從 [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] 開始 **，即可按一下 [執行**]。

### <a name="manually-break-into-code"></a>手動中斷程式碼

若要在執行中應用程式中的下一個可用程式程式碼中中斷，請選取 [ **Debug** ]  >  [**全部中斷**]，或按**Ctrl** +**Alt** +**break**。

## <a name="BKMK_Set_the_next_statement_to_execute"></a>移動指標以變更執行流程

當偵錯工具暫停時，[原始程式碼 **] 或 [** 反組解碼] 視窗邊界的黃色箭頭會標示要執行的下一個語句的位置。 您可以藉由移動此箭頭來變更下一個要執行的語句。 您可以略過部分程式碼，或回到前一行。 移動指標對於像是略過包含已知 bug 之程式碼區段的情況很有用。

 ![移動指標](../debugger/media/dbg_basics_example3.gif "移動指標")

若要變更下一個要執行的語句，偵錯工具必須處於中斷模式。 在 [**原始程式碼] 或**[反組解碼] 視窗中，將黃色箭頭拖曳至另一行，或以滑鼠右鍵按一下您要執行的下一行，然後選取 [**設定下一個語句]** 。

程式計數器會直接跳到新的位置，而不會執行舊和新執行點之間的指示。 不過，如果您向後移動執行點，則不會復原中間的指示。

>[!CAUTION]
>- 將下一個陳述式移至其他函式或範圍通常會造成呼叫堆疊損毀，導致執行階段錯誤或例外狀況。 如果嘗試將下一個陳述式移至其他範圍，偵錯工具會開啟警告對話方塊，讓您有機會取消作業。
>- 在 Visual Basic，您無法將下一個陳述式移至其他範圍或函式
>- 在原生 C++ 中，如果啟用執行階段檢查，設定下一個陳述式會導致在執行到方法結尾時擲回例外狀況
>- 啟用 [編輯後繼續] 時，如果您進行了 [編輯後繼續] 無法立即重新對應的編輯作業，[ **設定下一個陳述式** ] 就會失敗。 舉例來說，如果您編輯了 catch 區塊內的程式碼，就會發生這種情況。 發生這種情況時，會出現一則錯誤訊息，告訴您作業不受支援。
>- 在 managed 程式碼中，如果是下列情況，則無法移動下一個語句：
>   - 下一個陳述式是在與目前陳述式不同的方法中
>   - 偵錯工具是由即時的偵錯工具啟動。
>   - 呼叫堆疊回溯正在進行中。
>   - 擲回 System.StackOverflowException 或 System.Threading.ThreadAbortException 例外狀況

## <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>非使用者程式碼的 Debug

根據預設，偵錯工具會藉由啟用名為*Just My Code*的設定，來嘗試僅進行應用程式程式碼的驗證。 如需有關這項功能適用于不同專案類型和語言的詳細資訊，以及如何進行自訂的詳細資料，請參閱[Just My Code](../debugger/just-my-code.md)。

若要查看在進行偵錯工具時的架構程式碼、協力廠商程式庫程式碼或系統呼叫，您可以停用 Just My Code。 在 **工具** （或  **Debug** **）中 >** **選項**  >  偵測，清除 **啟用 Just My Code**  核取方塊。 停用 Just My Code 時，非使用者程式碼會出現在偵錯工具視窗中，而偵錯工具可以逐步執行非使用者程式碼。

> [!NOTE]
> 裝置專案不支援 Just My Code。

### <a name="debug-system-code"></a>Debug 系統程式碼

如果您已載入 Microsoft 系統程式碼的偵錯工具符號，並已停用 Just My Code，就可以逐步執行系統呼叫，就像任何其他呼叫一樣。

若要載入 Microsoft 符號，請參閱[設定符號位置和載入選項](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options)。

**若要載入特定系統元件的符號：**

1. 當您正在進行偵錯工具時，請選取 [ **Debug**  > **Windows**  > **模組**]，或按**Ctrl** +**Alt** +**U**，以開啟 [**模組**] 視窗。

1. 在 [**模組**] 視窗中，您可以分辨哪些模組在 [**符號狀態**] 欄中已載入符號。 以滑鼠右鍵按一下您要載入其符號的模組，然後選取 [**載入符號**]。

## <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> 逐步執行 Managed 程式碼中的屬性及運算子
 偵錯工具預設為不進入 Managed 程式碼中的屬性及運算子。 在大部分情況下，這會產生比較令人滿意的偵錯經驗。 若要啟用逐步執行屬性或運算子，請選擇 [ **Debug**  > **選項**]。 在 [偵錯] > [一般] 頁面上，清除 [不進入屬性和運算子 (僅限受控)] 核取方塊。

## <a name="see-also"></a>請參閱
- [什麼是偵錯？](../debugger/what-is-debugging.md)
- [偵錯技術和工具](../debugger/write-better-code-with-visual-studio.md)
- [第一次查看調試](../debugger/debugger-feature-tour.md)
