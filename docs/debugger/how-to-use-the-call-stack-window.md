---
title: 檢視呼叫堆疊偵錯工具 |Microsoft Docs
ms.custom: seodec18
ms.date: 10/29/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.callstack
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
- aspx
helpviewer_keywords:
- threading [Visual Studio], displaying calls to or from
- functions [debugger], viewing code on call stack
- disassembly code
- breakpoints, Call Stack window
- debugging [Visual Studio], switching to another stack frame
- debugging [Visual Studio], Call Stack window
- Call Stack window, viewing source code for functions on the call stack
- stack, switching stack frames
- Call Stack window, viewing disassembly code for functions on the call stack
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2673ed9a69a80b2e9ab9275ff54909e33e4434f4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62906342"
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-debugger"></a>檢視呼叫堆疊，並使用偵錯工具中的 [呼叫堆疊] 視窗

您可以使用 [呼叫堆疊] 視窗來檢視目前堆疊上的函式或程序呼叫。 [呼叫堆疊] 視窗會顯示方法和函式的呼叫順序。 呼叫堆疊是檢查並了解應用程式執行流程的好方法。

當[偵錯符號](#bkmk_symbols)沒有可用的呼叫堆疊的一部分**呼叫堆疊**視窗可能無法顯示正確的呼叫堆疊，並改為顯示該部分的資訊：

`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

> [!NOTE]
> [呼叫堆疊] 視窗類似於某些 IDE (例如 Eclipse) 中的 [偵錯] 檢視方塊。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與此處所描述的不同。 若要變更設定，請選取 [工具] 功能表上的 [匯入和匯出設定]。  請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

## <a name="view-the-call-stack-while-in-the-debugger"></a>檢視呼叫堆疊偵錯工具中

- 偵錯時，在**偵錯**功能表上，選取**Windows > 呼叫堆疊**。

  ![呼叫堆疊 視窗](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

執行指標目前所在的堆疊框架位置會以黃色箭頭識別。 根據預設，此堆疊框架的資訊會出現在來源中，**區域變數**，**自動變數**，**監看式**，以及**反組譯碼**windows。 若要將偵錯工具內容變更為另一個框架在堆疊上，[切換至另一個堆疊框架](#bkmk_switch)。

## <a name="display-non-user-code-in-the-call-stack-window"></a>在 [呼叫堆疊] 視窗中顯示非使用者程式碼

- 以滑鼠右鍵按一下 [呼叫堆疊] 視窗，然後選取 [顯示外部程式碼]。

非使用者程式碼是不會顯示時的任何程式碼[Just My Code](../debugger/just-my-code.md)已啟用。 在 managed 程式碼，預設會隱藏非使用者程式碼框架。 下列標記法會出現的非使用者程式碼框架取代：

`[<External Code>]`

## <a name="bkmk_switch"></a> 切換至另一個堆疊框架 （變更偵錯工具內容）

1. 在 **呼叫堆疊**視窗中，以滑鼠右鍵按一下堆疊框架之程式碼和您想要檢視的資料。

    或者，您可以按兩下框架**呼叫堆疊**視窗切換至該範圍內。

2. 選取 [切換至框架]。

     旁邊所選取之堆疊框架，會出現尾端彎曲的綠色箭號。 執行指標會留在原來的框架中，並仍以黃色箭頭標示。 如果您從 [偵錯] 功能表中選取 [逐步執行] 或 [繼續]，則會從原本框架而非選取的框架繼續執行。

## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>檢視呼叫堆疊上的函式的原始程式碼

- 在 [呼叫堆疊] 視窗，以滑鼠右鍵按一下您要查看原始程式碼的函式，然後選取 [移至原始程式碼]。

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>從 [呼叫堆疊] 視窗執行至特定函式

- 在 **呼叫堆疊**視窗中，選取的函式，以滑鼠右鍵按一下，然後選擇**執行至游標處**。

## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>函式呼叫的結束點上設定中斷點

- 請參閱[在呼叫堆疊函式設定中斷點](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window)。

## <a name="display-calls-to-or-from-another-thread"></a>顯示呼叫，或從另一個執行緒

- 以滑鼠右鍵按一下 [呼叫堆疊] 視窗，然後選取 [包含至/從其他執行緒的呼叫]。

## <a name="visually-trace-the-call-stack"></a>以視覺方式追蹤呼叫堆疊

在 Visual Studio Enterprise （僅限），您可以檢視呼叫堆疊的 code map 偵錯時。

- 在 [呼叫堆疊] 視窗中，開啟捷徑功能表。 選擇**Code Map 上顯示呼叫堆疊**(**Ctrl** + **Shift** + **`**)。

    如需詳細資訊，請參閱 <<c0> [ 偵錯時對應呼叫堆疊上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)。

![Code Map 上顯示呼叫堆疊](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")

## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack-c-c-visual-basic-f"></a>檢視呼叫堆疊上的函式的反組譯碼程式碼 (C#， C++，Visual Basic 中， F#)

- 在 [呼叫堆疊] 視窗中，以滑鼠右鍵按一下您要查看反組譯程式碼的函式，然後選取 [移至反組譯碼]。

## <a name="change-the-optional-information-displayed"></a>變更顯示的選擇性資訊

- 以滑鼠右鍵按一下**呼叫堆疊** 視窗，然後設定或清除**顯示\<** _您想要的資訊_**>**.

## <a name="bkmk_symbols"></a> 載入模組的符號 (C#， C++，Visual Basic 中， F#)

在 [呼叫堆疊] 視窗中，您可以載入目前尚未載入符號之程式碼的偵錯符號。 這些符號可能是從 Microsoft 公用符號伺服器下載的 .NET Framework 或系統符號，或是您所偵錯之電腦上符號路徑中的符號。

請參閱[指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。

### <a name="to-load-symbols"></a>若要載入符號

1. 在 **呼叫堆疊**視窗中，以滑鼠右鍵按一下未載入符號的堆疊框架。 該框架隨即變成暗灰色。

2. 指向**載入符號**，然後選取**Microsoft 符號伺服器**（如果有的話），或瀏覽至符號路徑。

### <a name="to-set-the-symbol-path"></a>若要設定符號路徑

1. 在 [呼叫堆疊] 視窗中，從捷徑功能表選擇 [符號設定]。

     [選項] 對話方塊隨即開啟，並顯示 [符號] 頁面。

2. 選取 **符號設定**。

3. 在 [選項] 對話方塊中，按一下資料夾圖示。

     游標隨即出現在 [符號檔 (.pdb) 位置] 方塊中。

4. 輸入您要偵錯的電腦上符號位置的目錄路徑名稱。 本機和遠端偵錯，這是您的本機電腦上的路徑。

5. 選取 [ **[確定]** 以關閉**選項**] 對話方塊。

## <a name="see-also"></a>另請參閱

- [呼叫堆疊視窗內的混合程式碼和遺失的資訊](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)
- [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)
- [指定符號 (.pdb) 和來源檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [使用中斷點](../debugger/using-breakpoints.md)