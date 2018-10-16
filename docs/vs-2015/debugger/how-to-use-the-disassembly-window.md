---
title: 如何： 使用反組譯碼視窗 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.disassembly
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa414aacc8b7ffc39132157686abee860cac994c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287751"
---
# <a name="how-to-use-the-disassembly-window"></a>如何：使用反組譯碼視窗
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

這項功能才會提供啟用位址層級偵錯**選項** 對話方塊中，**偵錯**節點。 它並不能用來偵錯指令碼或 SQL。  
  
 **反組譯碼**視窗會顯示對應到編譯器所建立之指令的組件程式碼。 如果您正在偵錯 Managed 程式碼，這些組譯碼 (Assembly) 指令相當於 Just-in-Time (JIT) 編譯器所建立的機器碼，而非 Visual Studio 編譯器所產生的 Microsoft Intermediate Language (MSIL)。  
  
 除了組譯碼指令**反組譯碼**視窗可以顯示下列選擇性資訊：  
  
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
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-display-the-disassembly-window"></a>若要顯示反組譯碼視窗  
  
-   在上**偵錯**功能表上，選擇**Windows**，然後按一下**反組譯碼**。  
  
     偵錯工具必須正在執行或處於中斷模式。  
  
### <a name="to-turn-optional-information-on-or-off"></a>若要開啟或關閉選擇性資訊  
  
-   以滑鼠右鍵按一下**反組譯碼** 視窗中，並設定或清除想要的選項，在快顯功能表中。  
  
     左邊界中的黃色箭頭將標示出目前執行點的位置。 它對應機器碼的 CPU 程式計數器。 這個位置顯示出下一個要執行的程式指令。  
  
     如需詳細資訊，請參閱 <<c0> [ 分頁] 或 [在記憶體中的向下](../debugger/how-to-page-up-or-down-in-memory.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在 偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)   
 [如何：使用暫存器視窗](../debugger/how-to-use-the-registers-window.md)





