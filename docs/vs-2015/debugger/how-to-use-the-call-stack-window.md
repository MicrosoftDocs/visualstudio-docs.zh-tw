---
title: HOW TO：使用 [呼叫堆疊] 視窗 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.callstack
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 65dafa09035e937e9ee48005c4f29c441d983c37
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430291"
---
# <a name="how-to-use-the-call-stack-window"></a>HOW TO：使用 [呼叫堆疊] 視窗
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 [呼叫堆疊] 視窗來檢視目前堆疊上的函式或程序呼叫。  
  
 **呼叫堆疊**視窗會顯示每個函式和程式設計語言中所寫入的名稱。 函式或程序名稱可能還會伴隨選擇性資訊，例如模組名稱、行號，以及參數名稱、類型和值。 您可以選擇開啟或關閉這個選擇性資訊。  
  
 執行指標目前所在的堆疊框架位置會以黃色箭頭識別。 根據預設，這是在來源中，不會顯示其資訊的框架**反組譯碼**，**區域變數**，**監看式**，以及**自動變數**windows。 如果您想要將內容變更為另一個框架在堆疊上，您可以這麼做**呼叫堆疊**視窗。  
  
 當偵錯符號沒有可用的呼叫堆疊的一部分**呼叫堆疊**視窗可能無法顯示該部分呼叫堆疊的正確資訊。 就會出現下列標記法：  
  
 [下面的框架可能錯誤及/或遺失，未載入 name.dll 的符號]  
  
 在 managed 程式碼，根據預設。 **呼叫堆疊** 視窗會隱藏非使用者程式碼的資訊。 會出現下列標記法，而不是隱藏的資訊：  
  
 **[\<External Code>]**  
  
 非使用者程式碼是指任何不是 "My Code" 的程式碼。您可以使用捷徑功能表選擇顯示非使用者程式碼的呼叫堆疊資訊。  
  
 您可以使用捷徑功能表選擇是否要檢視執行緒之間的呼叫。  
  
> [!NOTE]
> 根據目前使用的設定與版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中所描述的不同。 若要變更設定，請選取 [工具] 功能表上的 [匯入和匯出設定]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-display-the-call-stack-window-in-break-mode-or-in-run-mode"></a>在中斷模式或執行模式中顯示呼叫堆疊視窗  
  
- 在 **偵錯**功能表上，選取**Windows** ，然後按一下 **呼叫堆疊**。  
  
### <a name="to-change-the-optional-information-displayed"></a>若要變更所顯示的選擇性資訊  
  
- 以滑鼠右鍵按一下**呼叫堆疊** 視窗，然後設定或清除**顯示\<** _您想要的資訊_**>**.  
  
### <a name="to-display-non-user-code-frames-in-the-call-stack-window"></a>若要在呼叫堆疊視窗中顯示非使用者程式碼框架  
  
- 以滑鼠右鍵按一下 [呼叫堆疊] 視窗，然後選取 [顯示外部程式碼]。  
  
### <a name="to-switch-to-another-stack-frame"></a>若要切換到另一個堆疊框架  
  
1. 在 [**呼叫堆疊**] 視窗中，以滑鼠右鍵按一下框架之程式碼和您想要檢視的資料。  
  
2. 選取 [切換至框架]。  
  
     在您選取的框架旁邊會出現尾端彎曲的綠色箭號。 執行指標會留在原來的框架中，並仍以黃色箭頭標示。 如果您從 [偵錯] 功能表中選取 [逐步執行] 或 [繼續]，則會從原本框架而非選取的框架繼續執行。  
  
### <a name="to-display-calls-to-or-from-another-thread"></a>若要顯示與另一個執行緒之間的往來呼叫  
  
- 以滑鼠右鍵按一下 [呼叫堆疊] 視窗，然後選取 [包含至/從其他執行緒的呼叫]。  
  
### <a name="to-view-the-source-code-for-a-function-on-the-call-stack"></a>若要檢視呼叫堆疊上的函式的原始程式碼  
  
- 在 [呼叫堆疊] 視窗，以滑鼠右鍵按一下您要查看原始程式碼的函式，然後選取 [移至原始程式碼]。  
  
### <a name="to-visually-trace-the-call-stack"></a>若要以視覺化方式追蹤呼叫堆疊  
  
1. 在 [呼叫堆疊] 視窗中，開啟捷徑功能表。 選擇**Code Map 上顯示呼叫堆疊**。 (鍵盤：**CTRL** + **SHIFT** + **`**)  
  
     請參閱[偵錯時對應呼叫堆疊上的方法](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)。  
  
### <a name="to-view-the-disassembly-code-for-a-function-on-the-call-stack"></a>若要檢視呼叫堆疊上的函式的反組譯程式碼  
  
- 在 [呼叫堆疊] 視窗中，以滑鼠右鍵按一下您要查看反組譯程式碼的函式，然後選取 [移至反組譯碼]。  
  
### <a name="to-run-to-a-specific-function-from-the-call-stack-window"></a>若要從 [呼叫堆疊] 視窗執行至特定函式  
  
- 在 [**呼叫堆疊**] 視窗中，選取的函式，以滑鼠右鍵按一下，然後選擇**執行至游標處**。  
  
### <a name="to-set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>若要在函式呼叫的結束點設定中斷點  
  
- 請參閱[在呼叫堆疊函式設定中斷點](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window)。  
  
### <a name="to-load-symbols-for-a-module"></a>若要載入模組的符號  
  
- 在 **呼叫堆疊** 視窗中，以滑鼠右鍵按一下 顯示模組的符號的框架您想要重新載入，並選取**載入符號**。  
  
## <a name="loading-symbols"></a>載入符號  
 在 [呼叫堆疊] 視窗中，您可以載入目前尚未載入符號之程式碼的偵錯符號。 這些符號可能是從 Microsoft 公用符號伺服器下載的 .NET Framework 或系統符號，或是您所偵錯之電腦上符號路徑中的符號。  
  
 請參閱[指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols"></a>若要載入符號  
  
1. 在 **呼叫堆疊**視窗中，以滑鼠右鍵按一下未載入符號的框架。 該框架隨即變成暗灰色。  
  
2. 指向**載入符號來源**，然後按一下**Microsoft 符號伺服器**或是**符號路徑**。  
  
#### <a name="to-set-the-symbol-path"></a>若要設定符號路徑  
  
1. 在 [呼叫堆疊] 視窗中，從捷徑功能表選擇 [符號設定]。  
  
     [選項] 對話方塊隨即開啟，並顯示 [符號] 頁面。  
  
2. 按一下 **符號設定**。  
  
3. 在 [選項] 對話方塊中，按一下資料夾圖示。  
  
     游標隨即出現在 [符號檔 (.pdb) 位置] 方塊中。  
  
4. 輸入您要偵錯之電腦上符號位置的目錄路徑名稱。 在本機偵錯中，這是您的本機電腦； 在遠端偵錯中，則是遠端電腦。  
  
5. 按一下 [確定] 關閉 [選項] 對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [混合程式碼和遺失的資訊，在 [呼叫堆疊] 視窗](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)   
 [如何：變更 Windows 偵錯工具的數字格式](http://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)   
 [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)   
 [指定符號 (.pdb) 和來源檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [使用中斷點](../debugger/using-breakpoints.md)
