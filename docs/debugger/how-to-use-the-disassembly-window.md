---
title: 在 偵錯工具中檢視反組譯碼的程式碼 |Microsoft Docs
ms.custom: seodec18
ms.date: 10/30/2018
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
ms.openlocfilehash: c35432bdd01b9b79c2afaa266d8078caf04bd62b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063832"
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>在 Visual Studio 偵錯工具中檢視反組譯碼 (C#，c + +、 Visual Basic 中， F#)

[反組譯碼] 視窗會顯示對應到編譯器所建立之指令的組譯程式碼。 如果您偵錯 managed 程式碼時，這些組譯碼指令對應至 Just in Time (JIT) 編譯器，而不的 Microsoft intermediate language (MSIL) 建立的 Visual Studio 編譯器所建立的原生程式碼。

> [!NOTE]
> 若要充分善用**反組譯碼** 視窗中，了解，或了解的基本概念[組合語言程式](https://wikipedia.org/wiki/Assembly_language)。

這項功能才可使用已啟用位址層級偵錯。 它不適用於指令碼或 SQL 偵錯。

除了反組譯碼指令外，[反組譯碼] 視窗也可以顯示下列選擇性資訊：

- 每一指令所在的記憶體位址。 原生應用程式，它可以是實際的記憶體位址。 適用於 Visual Basic 或C#，它是從函式開頭的位移。

- 從組譯程式碼衍生的來源原始程式碼。

- 程式碼位元組，也就是實際的電腦或 MSIL 指令的位元組表示法。

- 記憶體位址的符號名稱。

- 原始程式碼的對應行號。

組合語言指令包含了*助憶鍵*，這是指令名稱的縮寫與*符號*的變數、 暫存器和常數。 每個機器語言指令被以一個組合語言助憶鍵可選擇性地跟著一或多個符號。

組譯程式碼依賴處理器暫存器，或 managed 程式碼，通用語言執行平台註冊。 您可以使用**反組譯碼**連同視窗**註冊**視窗，可讓您檢查暫存器內容。

若要檢視機器碼指令，以其原始的數值格式，而不是組件語言，請使用**記憶體**視窗中鍵入或選取**程式碼位元組**從快速鍵功能表中**反組譯碼**視窗。

## <a name="use-the-disassembly-window"></a>使用反組譯碼視窗

若要啟用**反組譯碼** 視窗底下**工具** > **選項**(或**工具** >  **選項**) >**偵錯**，選取**啟用位址層級偵錯**。

若要開啟 **反組譯碼**視窗中的偵錯期間，選取**Windows** > **反組譯碼**或按**Alt** + **8**。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

若要開啟或關閉選擇性資訊，請以滑鼠右鍵按一下**反組譯碼** 視窗中，並設定或清除想要的選項，在快顯功能表中。

在左邊界的黃色箭號標示目前的執行點。 原生程式碼，執行點會對應至 CPU 程式計數器。 這個位置顯示出下一個要執行的程式指令。

## <a name="see-also"></a>另請參閱

* [在記憶體中向上或向下翻頁](../debugger/how-to-page-up-or-down-in-memory.md)
* [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)
* [如何：使用暫存器視窗](../debugger/how-to-use-the-registers-window.md)