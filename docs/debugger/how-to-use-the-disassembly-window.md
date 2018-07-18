---
title: 在 Visual Studio 中偵錯工具中檢視反組譯碼的程式碼 |Microsoft 文件
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.disassembly
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 46c0ae689a9d514983aeb747bebc6cb9905c6e11
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31475531"
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger"></a>Visual Studio 偵錯工具中檢視反組譯碼程式碼
這項功能會啟用位址層級偵錯時，才可以使用**選項**對話方塊中，**偵錯**節點。 它並不能用來偵錯指令碼或 SQL。  
  
 **反組譯碼** 視窗會顯示對應到編譯器所建立之指令的組譯程式碼。 如果您正在偵錯 Managed 程式碼，這些組譯碼 (Assembly) 指令相當於 Just-in-Time (JIT) 編譯器所建立的機器碼，而非 Visual Studio 編譯器所產生的 Microsoft Intermediate Language (MSIL)。  
  
 組譯碼指令，除了**反組譯碼**視窗可以顯示下列選擇性資訊：  
  
-   每一指令所在的記憶體位址。 原生應用程式的實際記憶體位址。 Visual Basic、C# 或 Managed 程式碼的函式開頭位移。  
  
-   從組譯程式碼衍生的來源原始程式碼。  
  
-   程式碼位元組，實際電腦或 MSIL 指令的代表位元組。  
  
-   記憶體位址的符號名稱。  
  
-   原始程式碼的對應行號。  
  
 組合語言指令包含了助憶鍵 (Mnemonics) (也就是指令名稱的縮寫)，以及可代表變數、暫存器和常數的符號。 每個機器語言指令都會用一個組合語言助憶鍵來表示，後面通常跟著一個或多個變數、暫存器或常數。  
  
 如果您看不懂組合語言，但想好好利用 [反組譯碼] 視窗，請參閱一本組合語言程式設計的好書。 組合語言程式設計實在已經超過這份 [反組譯碼] 視窗簡要說明的討論範圍。  
  
 因為撰寫組譯程式碼需要大量用到處理器暫存器，而撰寫 Managed 程式碼需要大量用到 Common Language Runtime 暫存器，所以通常使用 [反組譯碼] 視窗時，再搭配使用 [暫存器] 視窗來檢查暫存器的內容，將會很方便。  
  
 您可能永遠不希望或不需要用不是組合語言形式的原始、數值形式，來檢視機器碼指令。 不過，如果您要這麼做，您可以使用 [記憶體] 視窗，或從 [反組譯碼] 視窗的捷徑功能表選擇 [程式碼位元組]，來達到目的。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
### <a name="to-display-the-disassembly-window"></a>若要顯示反組譯碼視窗  
  
-   當您偵錯時，選取 **偵錯 > Windows** ，然後按一下 **反組譯碼**。
  
### <a name="to-turn-optional-information-on-or-off"></a>若要開啟或關閉選擇性資訊  
  
-   以滑鼠右鍵按一下**反組譯碼**視窗中，並設定或清除想要的選項中的捷徑功能表。  
  
     左邊界中的黃色箭頭將標示出目前執行點的位置。 它對應機器碼的 CPU 程式計數器。 這個位置顯示出下一個要執行的程式指令。  
  
     如需詳細資訊，請參閱[分頁向上或向下，在記憶體中的](../debugger/how-to-page-up-or-down-in-memory.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在 偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)   
 [如何：使用暫存器視窗](../debugger/how-to-use-the-registers-window.md)