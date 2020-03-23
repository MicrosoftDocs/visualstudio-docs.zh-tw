---
title: 使用調試器導航代碼 |微軟文檔
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
ms.openlocfilehash: 6dfffdf0c12ea2a8f14769f26bb40a3943579248
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302116"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>使用視覺化工作室調試器流覽代碼

Visual Studio 調試器可以説明您流覽代碼以檢查應用的狀態並顯示其執行流。 您可以使用鍵盤快速鍵、調試命令、中斷點和其他功能快速訪問要檢查的代碼。 熟悉調試器導航命令和快捷方式，可以更快、更輕鬆地查找和解決應用問題。  如果這是您第一次嘗試調試代碼，則可能需要在閱讀本文之前閱讀[絕對初學者](../debugger/debugging-absolute-beginners.md)調試以及[調試技術和工具](../debugger/write-better-code-with-visual-studio.md)。

## <a name="get-into-break-mode"></a>進入"中斷模式"

在*中斷模式下*，當函數、變數和物件保留在記憶體中時，應用執行將掛起。 調試器處於中斷模式後，即可流覽代碼。 快速進入中斷模式的最常見方式是：

- 通過按**F10**或**F11**開始代碼步進。 這允許您快速查找應用的進入點，然後可以繼續按步驟命令來導航代碼。

- [運行到特定位置或函數](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All)，例如，通過[設置中斷點](using-breakpoints.md)並啟動應用。

   例如，從 Visual Studio 中的代碼編輯器中，可以使用 **"運行到游標"** 命令啟動應用、附加調試器並進入中斷模式，然後**F11**來導航代碼。

   ![運行到游標並踏入代碼](../debugger/media/navigate-code-code-stepping.gif "運行到游標並踏入代碼")

進入中斷模式後，可以使用各種命令流覽代碼。 在中斷模式下，可以檢查變數的值以查找衝突或 Bug。 對於某些專案類型，您還可以在中斷模式下對應用進行調整。

大多數調試器視窗（如 **"模組**"和 **"監視"** 視窗）僅在調試器附加到應用時才可用。 某些調試器功能（如在 **"區域變數"** 視窗中查看變數值或"**監視"** 視窗中的評估運算式）僅在調試器暫停時（即處於中斷模式）可用。

> [!NOTE]
> 如果闖入的代碼沒有載入源或符號 *（.pdb*） 檔，調試器將顯示 **"未找到的原始檔案**"或 **"未找到符號"** 頁面，以説明您查找和載入這些檔。 請參閱[指定符號 （.pdb） 和原始檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。 如果無法載入符號或原始檔案，仍可以在 **"拆解"** 視窗中偵錯工具集指令。

## <a name="step-through-code"></a>逐步執行程式碼

調試器步驟命令可説明您檢查應用狀態或瞭解有關其執行流的更多資訊。

### <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a>逐行執行代碼

要在調試時停止每個語句，請使用**調試** > **步驟輸入**， 或按**F11**。

調試器通過代碼語句，而不是物理行。 例如 `if` 子句可以寫在一行上：

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

但是，當您踏入此行時，調試器將條件視為一個步驟，並將結果視為另一個步驟。 在前面的示例中，條件為 true。

[ **逐步執行** ] 會在巢狀函式呼叫中逐步執行最深的巢狀函式。 例如，如果在調用（如`Func1(Func2())`）上使用 **"步進**"，則調試器將踏`Func2`入函數。

>[!TIP]
>執行每行代碼時，可以將滑鼠懸停在變數上以查看其值，或使用["區域變數](autos-and-locals-windows.md)"和["監視"](watch-and-quickwatch-windows.md)視窗監視值更改。 您還可以在步進函數時直觀地跟蹤[呼叫堆疊](how-to-use-the-call-stack-window.md)。 （僅適用于視覺化工作室企業版，請參閱[調試時呼叫堆疊上的映射方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)。

### <a name="step-through-code-and-skip-some-functions"></a><a name="BKMK_Step_over_Step_out"></a>單一步驟代碼並跳過一些函數

調試時可能不關心函數，或者知道它有效，就像經過良好測試的庫代碼一樣。 在代碼執行期間，可以使用以下命令跳過代碼。 函數仍在執行，但調試器跳過它們。

|鍵盤命令|偵錯功能表命令|描述|
|----------------------|------------------|-----------------|
|**F10**|**不進入函數**|如果當前行包含函式呼叫，**則"單一步驟**"將運行代碼，然後在被調用的函數返回後在第一行代碼暫停執行。|
|**換檔**+**F11**|**走出來**|**"退出"** 將繼續運行代碼，並在當前函數返回時暫停執行。 調試器跳過當前函數。|

## <a name="run-to-a-specific-location-or-function"></a><a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a>運行到特定位置或功能

當您確切知道要檢查的代碼或知道要從何處開始調試時，您可能更喜歡直接運行到特定位置或函數。

### <a name="run-to-a-breakpoint-in-code"></a>運行到代碼中的中斷點

要在代碼中設置一個簡單的中斷點，請按一下要掛起執行的程式碼旁邊的最左邊邊距。 您還可以選擇線並按**F9，** 選擇 **"調試** > **切換中斷點**"，或按右鍵並選擇**中斷點** > **插入中斷點**。 中斷點在程式碼旁邊的左邊距顯示為紅點。 調試器在行執行之前暫停執行。

![設置中斷點](../debugger/media/dbg_basics_setbreakpoint.png "設定中斷點")

Visual Studio 的中斷點提供一組豐富的其他功能，例如條件式中斷點和追蹤點。 有關詳細資訊，請參閱[使用中斷點](../debugger/using-breakpoints.md)。

### <a name="run-to-a-function-breakpoint"></a>運行到函數中斷點

您可以告訴調試器運行，直到它到達指定的函數。 您可以依名稱來指定函式，或是在呼叫堆疊中選擇函式。

**按名稱指定函數中斷點**

1. 選擇**調試** > **新中斷點** > **函數中斷點**

1. 在 **"新建函數中斷點"** 對話方塊中，鍵入函數的名稱並選擇其語言。

   ![新增功能中斷點對話方塊](../debugger/media/dbg_execution_newbreakpoint.png "新功能中斷點")

1. 選取 [確定]****。

如果函數超載或有多個命名空間，則可以在 **"中斷點"** 視窗中選擇所需的函數。

![重載功能中斷點](../debugger/media/dbg_execution_overloadedbreakpoints.png "重載功能中斷點")

**從呼叫堆疊中選擇函數中斷點**

1. 調試時，通過選擇 **"調試** > **Windows** > **呼叫堆疊**"打開**呼叫堆疊**視窗。

1. 在 **"呼叫堆疊"** 視窗中，按右鍵函數並**選擇"運行到游標**"，或按**Ctrl**+**F10**。

要直觀地跟蹤呼叫堆疊，請參閱[調試時呼叫堆疊上的 Map 方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)。

### <a name="run-to-a-cursor-location"></a>運行到游標位置

要運行到游標位置，請在原始程式碼或**呼叫堆疊**視窗中選擇要中斷的行，按右鍵並選擇"**運行到游標**"，或按**Ctrl**+**F10**。 選擇 **"運行到游標"** 類似于設置臨時中斷點。

### <a name="run-to-click"></a>執行至點選處

在調試器中暫停時，可以將滑鼠懸停在原始程式碼或 **"拆解"** 視窗中的語句上，然後選擇"**運行執行"到此處**的綠色箭頭圖示。 使用 **"運行"按一下**無需設置臨時中斷點。

![執行至點選處](../debugger/media/dbg-run-to-click.png "執行至點選處")

> [!NOTE]
> **運行到按一下**可從 中[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]開始。

### <a name="manually-break-into-code"></a>手動中斷程式碼

要在正在運行的應用中斷開下一行可用代碼，請選擇 **"全部調試** > **中斷**"，或按**Ctrl**+**Alt**+**中斷**。

## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a>移動指標以更改執行流

當調試器暫停時，原始程式碼或**拆解**視窗的邊距中黃色箭頭標記要執行的下一個語句的位置。 您可以通過移動此箭頭更改要執行的下一個語句。 您可以跳過部分代碼，或返回到上一行。 移動指標對於跳過包含已知 Bug 的代碼部分等情況非常有用。

 ![移動指標](../debugger/media/dbg_basics_example3.gif "移動指標")

要更改要執行的下一個語句，調試器必須處於中斷模式。 在原始程式碼或**拆解**視窗中，將黃色箭頭拖動到其他行，或按右鍵要執行的下一行，然後選擇"**設置下一個語句**"。

程式計數器直接跳轉到新位置，並且不會執行新舊執行點之間的指令。 但是，如果向後移動執行點，則中間指令不會撤銷。

>[!CAUTION]
>- 將下一個陳述式移至其他函式或範圍通常會造成呼叫堆疊損毀，導致執行階段錯誤或例外狀況。 如果嘗試將下一個陳述式移至其他範圍，偵錯工具會開啟警告對話方塊，讓您有機會取消作業。
>- 在 Visual Basic，您無法將下一個陳述式移至其他範圍或函式
>- 在原生 C++ 中，如果啟用執行階段檢查，設定下一個陳述式會導致在執行到方法結尾時擲回例外狀況
>- 啟用 [編輯後繼續] 時，如果您進行了 [編輯後繼續] 無法立即重新對應的編輯作業，[ **設定下一個陳述式** ] 就會失敗。 舉例來說，如果您編輯了 catch 區塊內的程式碼，就會發生這種情況。 發生這種情況時，一條錯誤訊息告訴您不支援該操作。
>- 在託管代碼中，如果以下情況：則無法移動下一個語句：
>   - 下一個陳述式是在與目前陳述式不同的方法中
>   - 調試由即時調試啟動。
>   - 呼叫堆疊展開正在進行中。
>   - 擲回 System.StackOverflowException 或 System.Threading.ThreadAbortException 例外狀況

## <a name="debug-non-user-code"></a><a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>調試非使用者代碼

預設情況下，調試器嘗試通過啟用名為 *"僅我的代碼"* 的設置來僅調試應用代碼。 有關此功能如何適用于不同的專案類型和語言以及如何自訂它的詳細資訊，請參閱["我的代碼](../debugger/just-my-code.md)"。

要查看調試時的框架代碼、協力廠商庫代碼或系統調用，可以禁用"僅我的代碼"。 在 **"工具**（或**調試**）>**選項** > **調試**中，清除"**僅啟用我的代碼"** 核取方塊。 禁用"僅我的代碼"時，調試器視窗中將顯示非使用者代碼，調試器可以單步進入非使用者代碼。

> [!NOTE]
> 裝置專案不支援 Just My Code。

### <a name="debug-system-code"></a>調試系統代碼

如果已載入了 Microsoft 系統代碼的調試符號，並禁用了"僅我的代碼"，則可以像任何其他調用一樣進入系統調用。

要載入 Microsoft 符號，請參閱[配置符號位置和載入選項](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options)。

**要載入特定系統元件的符號，**

1. 調試時，通過選擇**調試** > **Windows** > **模組**或按**Ctrl**+**Alt**+**U**打開 **"模組"** 視窗。

1. 在 **"模組"** 視窗中，您可以分辨哪些模組在 **"符號狀態"** 列中載入了符號。 按右鍵要為其載入符號的模組，然後選擇 **"載入符號**"。

## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> 逐步執行 Managed 程式碼中的屬性及運算子
 偵錯工具預設為不進入 Managed 程式碼中的屬性及運算子。 在大部分情況下，這會產生比較令人滿意的偵錯經驗。 要啟用單一步驟到屬性或運算子，請選擇**調試** > **選項**。 在 **"調試** > **常規"** 頁上，清除 **"對屬性和運算子（僅限託管）"核取方塊**。

## <a name="see-also"></a>另請參閱
- [什麼是偵錯？](../debugger/what-is-debugging.md)
- [偵錯技術和工具](../debugger/write-better-code-with-visual-studio.md)
- [首先查看調試](../debugger/debugger-feature-tour.md)
