---
title: "在 Visual Studio 偵錯工具中檢視呼叫堆疊 |Microsoft 文件"
ms.custom: H1Hack27Feb2017
ms.date: 04/06/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.callstack
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
caps.latest.revision: "40"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e10b81ff07b77e2fd6202d2f5fb27392fe8134c2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-visual-studio-debugger"></a>檢視呼叫堆疊，並使用 Visual Studio 偵錯工具中 [呼叫堆疊] 視窗

使用**呼叫堆疊**視窗中，您可以檢視目前堆疊上函式或程序呼叫。 **呼叫堆疊** 視窗會顯示方法和函式會取得呼叫所在的順序。 呼叫堆疊是很好的方式來檢查，並了解應用程式的執行流程。
  
當[偵錯符號](#bkmk_symbols)不適用於部分呼叫堆疊，**呼叫堆疊**視窗可能無法顯示該部分呼叫堆疊的正確資訊。 如果發生此情況，就會出現下列標記法：  
  
`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

>  [!NOTE]
> **呼叫堆疊**視窗是類似於偵錯觀點來看，某些像 Eclipse Ide 中。 

> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與此處所描述的不同。 若要變更您的設定，請選取**匯入和匯出設定**上**工具**功能表。  請參閱[個人化 IDE](../ide/personalizing-the-visual-studio-ide.md)
  
## <a name="view-the-call-stack-while-in-the-debugger"></a>檢視呼叫堆疊偵錯工具中 
  
-   在偵錯時**偵錯**功能表上，選取**Windows > 呼叫堆疊**。

 ![[呼叫堆疊] 視窗](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

執行指標目前所在的堆疊框架位置會以黃色箭頭識別。 根據預設，這是在來源中，會顯示其資訊的堆疊框架**區域變數**，**自動變數**，**監看式**，和**反組譯碼**windows. 如果您想要將偵錯工具內容變更為另一個堆疊框架時，您可以達成[切換至另一個堆疊框架](#bkmk_switch)。   
  
## <a name="display-non-user-code-in-the-call-stack-window"></a>在 [呼叫堆疊] 視窗中顯示非使用者程式碼  
  
-   以滑鼠右鍵按一下**呼叫堆疊**視窗，然後選取**顯示外部程式碼**。

非使用者程式碼是不會顯示時的任何程式碼[Just My Code](../debugger/just-my-code.md)已啟用。 在 managed 程式碼，預設會隱藏非使用者程式碼框架。 而非使用者程式碼框架不是，會出現下列標記法：  
  
**[\<外部程式碼 >]**  
  
## <a name="bkmk_switch"></a>切換至另一個堆疊框架 （變更偵錯工具內容）
  
1.  在**呼叫堆疊**視窗中，以滑鼠右鍵按一下堆疊框架之程式碼和您想要檢視的資料。

    或者，您可以按兩下框架**呼叫堆疊**視窗切換至所選取畫面格。 
  
2.  選取**切換至框架**。  
  
     您所選取的堆疊框架旁邊，會出現尾端彎曲的綠色箭號。 執行指標會留在原來的框架中，並仍以黃色箭頭標示。 如果您選取**步驟**或**繼續**從**偵錯** 功能表中，原本的框架中，會繼續執行，您所選取非框架。  
  
## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>檢視呼叫堆疊上函式的原始程式碼  
  
-   在**呼叫堆疊**視窗中，以滑鼠右鍵按一下原始程式碼函式您想要看到和選取**移至原始程式碼**。

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>從 [呼叫堆疊] 視窗執行至特定函式  
  
-  在**呼叫堆疊**視窗中，選取函式，以滑鼠右鍵按一下，然後選擇**執行至游標處**。  
  
## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>函式呼叫的結束點上設定中斷點  
  
-   請參閱[呼叫堆疊函式處設定中斷點](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window)。

## <a name="display-calls-to-or-from-another-thread"></a>顯示或另一個執行緒的呼叫  
  
-   以滑鼠右鍵按一下**呼叫堆疊**視窗，然後選取**包含至/從其他執行緒的呼叫**。   
  
## <a name="visually-trace-the-call-stack"></a>以視覺方式追蹤呼叫堆疊  

如果您使用 Visual Studio Enterprise （僅限），您可以檢視呼叫堆疊 code map 偵錯時。

- 在**呼叫堆疊**視窗中，開啟捷徑功能表。 選擇**Code Map 上顯示呼叫堆疊**。 (鍵盤： **CTRL** + **SHIFT** + **`**)  
  
    如需詳細資訊，請參閱[偵錯時對應呼叫堆疊上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)。

![Code Map 上顯示呼叫堆疊](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")
  
## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack"></a>檢視呼叫堆疊上的函式的反組譯碼程式碼  
  
-   在**呼叫堆疊**視窗中，以滑鼠右鍵按一下函式的反組譯程式碼，您想要看到和選取**移至反組譯碼**。    

## <a name="change-the-optional-information-displayed"></a>變更顯示的選擇性資訊  
  
-   以滑鼠右鍵按一下**呼叫堆疊**視窗並設定或清除**顯示\<** *您想要的資訊* **>** .  
  
## <a name="bkmk_symbols"></a>模組載入符號
在**呼叫堆疊**視窗中，您可以載入偵錯目前沒有載入的符號的程式碼的符號。 這些符號可能是從 Microsoft 公用符號伺服器下載的 .NET Framework 或系統符號，或是您所偵錯之電腦上符號路徑中的符號。  
  
請參閱[指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
### <a name="to-load-symbols"></a>若要載入符號  
  
1.  在**呼叫堆疊**視窗中，以滑鼠右鍵按一下未載入符號的堆疊框架。 該框架隨即變成暗灰色。  
  
2.  指向**載入符號**，然後按一下  **Microsoft 符號伺服器**（如果有的話） 或瀏覽至的符號路徑。  
  
### <a name="to-set-the-symbol-path"></a>若要設定符號路徑  
  
1.  在**呼叫堆疊**視窗中，選擇**符號設定**從捷徑功能表。  
  
     **選項**對話方塊隨即開啟並**符號**頁面隨即顯示。  
  
2.  按一下**符號設定**。  
  
3.  在**選項**對話方塊方塊中，按一下資料夾圖示。  
  
     在**符號檔 (.pdb) 位置**方塊中，游標隨即出現。  
  
4.  輸入您要偵錯之電腦上符號位置的目錄路徑名稱。 進行本機和遠端偵錯，這是本機電腦上的路徑。
  
5.  按一下 [確定] 關閉 [選項] 對話方塊。  
  
## <a name="see-also"></a>請參閱  
 [呼叫堆疊視窗內的混合程式碼和遺失的資訊](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)  
 [在 偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)   
 [指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [使用中斷點](../debugger/using-breakpoints.md)