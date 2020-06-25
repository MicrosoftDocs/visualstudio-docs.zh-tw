---
title: 在偵錯工具中查看反組解碼程式碼 |Microsoft Docs
ms.custom: seodec18
ms.date: 10/30/2018
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0570aec5e8571e75cf64418a2c8c7c95cf507d31
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348700"
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>在 Visual Studio 偵錯工具中查看反組解碼程式碼（c #、c + +、Visual Basic、F #）

[反組譯碼]**** 視窗會顯示對應到編譯器所建立之指令的組譯程式碼。 如果您正在對 managed 程式碼進行偵錯工具，這些元件指令會對應至即時（JIT）編譯器所建立的機器碼，而不是 Visual Studio 編譯器所建立的 Microsoft 中繼語言（MSIL）。

> [!NOTE]
> 若要充分**利用 [反**組解碼] 視窗，請瞭解或瞭解[元件語言程式設計](https://wikipedia.org/wiki/Assembly_language)的基本概念。

只有在啟用位址層級的調試時，才可以使用此功能。 它不適用於腳本或 SQL 的偵錯工具。

除了反組譯碼指令外，[反組譯碼]**** 視窗也可以顯示下列選擇性資訊：

- 每一指令所在的記憶體位址。 若是原生應用程式，則是實際的記憶體位址。 針對 Visual Basic 或 c #，這是從函式開頭算起的位移。

- 從組譯程式碼衍生的來源原始程式碼。

- 程式碼位元組，也就是實際機器或 MSIL 指令的位元組標記法。

- 記憶體位址的符號名稱。

- 原始程式碼的對應行號。

元件語言指示包含*助憶鍵*，這是指令名稱的縮寫，以及變數、暫存器和常數的*符號*。 每個電腦語言指令都會以一個組合語言助憶鍵來表示，並選擇性地以一個或多個符號。

元件程式碼高度依賴處理器暫存器，或適用于 managed 程式碼，也就是通用語言執行時間註冊。 您可以**使用 [反**組解碼] 視窗和 [暫存器 **] 視窗，** 讓您檢查暫存器的內容。

若要以原始數值格式（而非元件語言）來查看機器程式碼指令，請使用 [**記憶體**] 視窗，或從 [反組解碼 **] 視窗**中的快捷方式功能表選取 [程式**代碼位元組**]。

## <a name="use-the-disassembly-window"></a>使用反組譯碼視窗

若要啟用 **[反**組解碼] 視窗，請在 [**工具**  >  **選項**] （或 [**工具**  >  **選項**]）下 > [偵測]，選取 [**啟用位址層級** **Debugging**

若**要在調試期間開啟 [反**組解碼] 視窗，請選取 [ **Windows**反組解碼]  >  **Disassembly**或按**Alt** + **8**

> [!NOTE]
> 您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。 若要變更您的設定，請在 [工具]**** 功能表上選擇 [匯入和匯出設定]****。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

若要開啟或關閉選擇性資訊，請以滑鼠右鍵按一下 [反組**解碼] 視窗**，然後在快捷方式功能表中設定或清除所需的選項。

左邊界的黃色箭號會標示目前的執行點。 針對機器碼，執行點會對應至 CPU 的程式計數器。 這個位置顯示出下一個要執行的程式指令。

## <a name="see-also"></a>另請參閱

* [在記憶體中向上或向下翻頁](../debugger/how-to-page-up-or-down-in-memory.md)
* [在偵錯工具中查看資料](../debugger/viewing-data-in-the-debugger.md)
* [如何：使用暫存器視窗](../debugger/how-to-use-the-registers-window.md)