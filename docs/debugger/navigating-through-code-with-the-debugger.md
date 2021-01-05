---
title: 使用偵錯工具流覽程式碼 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/12/2018
ms.topic: how-to
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
ms.openlocfilehash: 5cd7bb050204d65bb78a597c1ae3c7eea36ac184
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729349"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>使用 Visual Studio 偵錯工具流覽程式碼

Visual Studio 偵錯工具可協助您流覽程式碼來檢查應用程式的狀態，並顯示其執行流程。 您可以使用鍵盤快速鍵、偵錯工具命令、中斷點及其他功能，快速取得您想要檢查的程式碼。 熟悉偵錯工具流覽命令和快速鍵，可讓您更快速且更輕鬆地尋找和解決應用程式問題。

> [!NOTE]
> 如果這是您第一次嘗試進行程式碼的偵錯工具，您可能會想要在進行這篇文章之前，先閱讀絕對初學者和[調試](../debugger/write-better-code-with-visual-studio.md)[程式的偵錯工具](../debugger/debugging-absolute-beginners.md)。

## <a name="get-into-break-mode"></a>進入「中斷模式」

在 *中斷模式* 中，當函式、變數和物件保留在記憶體中時，會暫停應用程式執行。 當偵錯工具處於中斷模式時，您可以流覽程式碼。 快速進入中斷模式最常見的方式是：

- 按 **F10** 或 **F11** 開始程式碼逐步執行。 這可讓您快速找到應用程式的進入點，然後您可以繼續按步驟命令來流覽程式碼。

- [執行至特定位置或](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All)函式，例如，藉由 [設定中斷點](using-breakpoints.md) 並啟動您的應用程式。

   例如，在 Visual Studio 的程式碼編輯器中，您可以使用 [ **執行至游標處** ] 命令來啟動應用程式、附加偵錯工具，並進入中斷模式，然後按 **F11** 來流覽程式碼。

   ![執行至游標處並逐步執行程式碼](../debugger/media/navigate-code-code-stepping.gif "執行至游標處並逐步執行程式碼")

在中斷模式中，您可以使用各種命令來流覽程式碼。 在中斷模式中，您可以檢查變數的值，以尋找違規或錯誤。 針對某些專案類型，您也可以在中斷模式下，對應用程式進行調整。

大部分的偵錯工具視窗（例如 **模組** 和 **監看** 式視窗）只有在偵錯工具附加至您的應用程式時才可使用。 某些偵錯工具功能（例如在 [ **區域變數** ] 視窗中查看變數值，或在 [ **監看** 式] 視窗中評估運算式）只有在偵錯工具暫停時才可使用， (也就是在中斷模式中) 。

> [!NOTE]
> 如果您中斷的程式碼沒有 (*.pdb*) 載入的檔案，則偵錯工具會顯示 [找 **不到原始** 程式檔] 或 [ **找不到符號** ] 頁面，可協助您尋找和載入檔案。 請參閱 [指定符號 ( .pdb) 和來源](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)檔案。 如果您無法載入符號或原始程式檔，您仍然可以在 [反組 **解碼] 視窗** 中，偵錯工具集指令。

## <a name="step-through-code"></a>逐步執行程式碼

偵錯工具步驟命令可協助您檢查應用程式狀態，或深入瞭解其執行流程。

### <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a> 逐行執行程式碼

若要在調試時停止每個語句，請使用 **Debug**  >  **Step Into**，或按 **F11** 鍵。

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

不過，當您逐步執行這一行時，偵錯工具會將條件視為一個步驟，並將結果視為另一個步驟。 在上述範例中，條件是 true。

[ **逐步執行** ] 會在巢狀函式呼叫中逐步執行最深的巢狀函式。 例如，如果您在類似的呼叫中使用 [ **逐步** 執行] `Func1(Func2())` ，偵錯工具就會逐步執行函式 `Func2` 。

>[!TIP]
>當您執行每一行程式碼時，可以將滑鼠停留在變數上以查看其值，或使用 [ [區域變數](autos-and-locals-windows.md) ] 和 [ [監看式]](watch-and-quickwatch-windows.md) 視窗來監看這些值的變更。 您也可以在逐步執行函式時，以視覺化方式追蹤 [呼叫堆疊](how-to-use-the-call-stack-window.md) 。 只有 Visual Studio Enterprise 的 (，請參閱在偵錯工具) [時對應呼叫堆疊上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md) 。

### <a name="step-through-code-and-skip-some-functions"></a><a name="BKMK_Step_over_Step_out"></a> 逐步執行程式碼並略過某些函式

在進行偵錯工具時，您可能不在意函式，或您知道它的運作方式，就像是經過妥善測試的程式庫程式碼。 您可以使用下列命令，在程式碼逐步執行時略過程式碼。 函數仍會執行，但偵錯工具會略過這些函式。

|鍵盤命令|偵錯功能表命令|描述|
|----------------------|------------------|-----------------|
|**F10**|**逐程序**|如果目前的行包含函式呼叫，[不進入函式] **會執行程式** 代碼，然後在呼叫的函式傳回之後，于第一行程式碼上暫停執行。|
|**Shift** +**F11**|**跳出**|**跳出** 執行程式碼，並在目前的函式傳回時暫停執行。 偵錯工具會略過目前的函式。|

## <a name="run-to-a-specific-location-or-function"></a><a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> 執行至特定位置或函數

當您確切知道想要檢查的程式碼時，或知道您想要從何處開始進行偵錯工具時，您可能會想要直接執行至特定的位置或函數。

### <a name="run-to-a-breakpoint-in-code"></a>在程式碼中執行至中斷點

若要在您的程式碼中設定簡單的中斷點，請按一下您要暫停執行的程式程式碼旁邊的最左邊界。 您也可以選取這一行，然後按 **F9**、選取 [ **Debug**  >  **切換中斷點**]，或是以滑鼠右鍵按一下並選取 [**中斷點**  >  **插入中斷點**]。 中斷點會在程式程式碼旁邊的左邊界中顯示為紅色點。 偵錯工具會在執行行之前暫停執行。

![設定中斷點](../debugger/media/dbg_basics_setbreakpoint.png "設定中斷點")

Visual Studio 的中斷點提供一組豐富的其他功能，例如條件式中斷點和追蹤點。 如需詳細資訊，請參閱 [使用中斷點](../debugger/using-breakpoints.md)。

### <a name="run-to-a-function-breakpoint"></a>執行至函數中斷點

您可以告訴偵錯工具執行，直到它到達指定的函式為止。 您可以依名稱來指定函式，或是在呼叫堆疊中選擇函式。

**依名稱指定函數中斷點**

1. 選取 **Debug**  >  **New 中斷點**  >  **函數中斷點**

1. 在 [ **新增** 函式中斷點] 對話方塊中，輸入函數的名稱，然後選取其語言。

   ![新增函數中斷點對話方塊](../debugger/media/dbg_execution_newbreakpoint.png "新增函數中斷點")

1. 選取 [確定]。

如果函式已多載或在多個命名空間中，您可以在 [ **中斷點** ] 視窗中選擇您想要的函數。

![多載函數中斷點](../debugger/media/dbg_execution_overloadedbreakpoints.png "多載函數中斷點")

**從呼叫堆疊選取函數中斷點**

1. 在進行偵錯工具時，請選取 [ **Debug**   >  **Windows**  >  **呼叫堆疊**] 來開啟 [呼叫堆疊] 視窗。

1. 在 [**呼叫堆疊**] 視窗中，以滑鼠右鍵按一下函式，然後選取 [**執行至游標處**]，或按 **Ctrl** + **F10**。

若要以視覺化方式追蹤呼叫堆疊，請參閱在 [調試過程中對應呼叫堆疊上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)。

### <a name="run-to-a-cursor-location"></a>執行至游標位置

若要執行至游標位置，請在 [原始程式碼] 或 [**呼叫堆疊**] 視窗中，選取您要中斷的行，按一下滑鼠右鍵並選取 [**執行至游標** 處]，或按 **Ctrl** + **F10**。 選取 [ **執行至游標處** ] 就像設定暫存中斷點一樣。

### <a name="run-to-click"></a>執行至點選處

在偵錯工具中暫停時，您可以將滑鼠停留 **在 [原始程式碼] 或** [反組解碼] 視窗中的語句上方，然後選取 [在 **這裡執行執行到這裡** ] 綠色箭號圖示。 使用 [ **執行] 按一下即可** 免除設定暫存中斷點的需求。

![執行至點選處](../debugger/media/dbg-run-to-click.png "執行至點選處")

> [!NOTE]
> 從開始，可按 [**執行**] [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] 。

### <a name="manually-break-into-code"></a>手動中斷程式碼

若要在執行中的應用程式中中斷下一個可用的程式碼，請選取 [全部 **調試** 程式  >  **中斷**]，或按 **Ctrl** + **Alt** + **break**。

## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a> 移動指標以變更執行流程

當偵錯工具暫停時，[原始程式碼 **] 或 [** 反組解碼] 視窗邊界的黃色箭頭會標示下一個要執行之語句的位置。 您可以藉由移動此箭頭來變更下一個要執行的語句。 您可以略過某部分的程式碼，或回到前一行。 移動指標對於略過包含已知 bug 之程式碼區段的情況很有用。

 ![移動指標](../debugger/media/dbg_basics_example3.gif "移動指標")

若要變更下一個要執行的語句，偵錯工具必須處於中斷模式。 在 [ **原始程式碼] 或** [反組解碼] 視窗中，將黃色箭頭拖曳至另一行，或以滑鼠右鍵按一下要執行的下一行，然後選取 [ **設定下一個語句]**。

程式計數器會直接跳到新位置，而且不會執行舊的和新執行點之間的指示。 但是，如果您將執行點向後移動，則不會復原中間的指示。

>[!CAUTION]
>- 將下一個陳述式移至其他函式或範圍通常會造成呼叫堆疊損毀，導致執行階段錯誤或例外狀況。 如果嘗試將下一個陳述式移至其他範圍，偵錯工具會開啟警告對話方塊，讓您有機會取消作業。
>- 在 Visual Basic，您無法將下一個陳述式移至其他範圍或函式
>- 在原生 C++ 中，如果啟用執行階段檢查，設定下一個陳述式會導致在執行到方法結尾時擲回例外狀況
>- 啟用 [編輯後繼續] 時，如果您進行了 [編輯後繼續] 無法立即重新對應的編輯作業，[ **設定下一個陳述式** ] 就會失敗。 舉例來說，如果您編輯了 catch 區塊內的程式碼，就會發生這種情況。 發生這種情況時，會出現錯誤訊息，告訴您作業不受支援。
>- 在 managed 程式碼中，您無法在下列情況下移動下一個語句：
>   - 下一個陳述式是在與目前陳述式不同的方法中
>   - 偵錯工具是由即時偵測啟動。
>   - 正在回溯呼叫堆疊。
>   - 擲回 System.StackOverflowException 或 System.Threading.ThreadAbortException 例外狀況

## <a name="debug-non-user-code"></a><a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>非使用者程式碼的偵錯工具

根據預設，偵錯工具會嘗試啟用稱為 *Just My Code* 的設定，只會將您的應用程式程式碼進行偵錯工具。 如需此功能對於不同專案類型和語言的運作方式，以及如何進行自訂的詳細資訊，請參閱 [Just My Code](../debugger/just-my-code.md)。

若要查看架構程式碼、協力廠商程式庫程式碼或在進行偵錯工具時的系統呼叫，您可以停用 Just My Code。 在 [**工具**] (或 [ **Debug** ]) >**選項**  >  **調試**] 中，清除 [**啟用 Just My Code** ] 核取方塊。 當 Just My Code 停用時，[偵錯工具] 視窗中會顯示非使用者程式碼，而偵錯工具可以逐步執行非使用者程式碼。

> [!NOTE]
> 裝置專案不支援 Just My Code。

### <a name="debug-system-code"></a>偵錯工具系統程式碼

如果您已載入 Microsoft 系統程式碼的偵錯工具符號，而停用的 Just My Code，就可以逐步執行系統呼叫，就像您可以進行任何其他呼叫一樣。

若要載入 Microsoft 符號，請參閱 [設定符號位置和載入選項](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options)。

**若要載入特定系統元件的符號：**

1. 當您正在進行偵錯工具時 ，請選取 [ **Debug**  >  **Windows**  >  **模組**]，或按 **Ctrl** + **Alt** + **U** 來開啟 [模組] 視窗。

1. 在 [ **模組** ] 視窗中，您可以分辨哪些模組在 [ **符號狀態** ] 資料行中有已載入的符號。 以滑鼠右鍵按一下您要載入符號的模組，然後選取 [ **載入符號**]。

## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> 逐步執行 Managed 程式碼中的屬性及運算子
 偵錯工具預設為不進入 Managed 程式碼中的屬性及運算子。 在大部分情況下，這會產生比較令人滿意的偵錯經驗。 若要啟用逐步執行屬性或運算子，請選擇 [ **Debug**  >  **選項**]。 在 [**調試**  >  **一般**] 頁面上，清除 [不進入 **屬性和運算子] ([僅限 Managed)** ] 核取方塊。

## <a name="see-also"></a>請參閱
- [什麼是偵錯？](../debugger/what-is-debugging.md)
- [偵錯技術和工具](../debugger/write-better-code-with-visual-studio.md)
- [先查看調試](../debugger/debugger-feature-tour.md)
