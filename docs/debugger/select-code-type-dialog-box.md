---
title: '[選取程式碼類型] 對話方塊 |Microsoft Docs'
ms.date: 06/12/2020
ms.topic: reference
f1_keywords:
- vs.debug.selectengines
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- debugging [Visual Studio], engine selection
- debugger, engine selection
- debugging engine selection dialog box
ms.assetid: 932269fe-94e3-43cb-8931-078f31afd177
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6831837853f2e8dd5502e57d0976899c5d31a1a
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285422"
---
# <a name="select-code-type-dialog-box"></a>選取程式碼類型對話方塊

若要開啟這個對話方塊，請開啟 [附加至處理序]**** 對話方塊，然後按一下 [選取]**** 按鈕。

**自動判斷要進行偵錯工具的程式碼類型**系統會根據執行的程式碼類型來選取適當的偵錯工具。

**Debug 這些程式碼類型：** 從提供的清單中，選擇您要進行偵錯工具的程式碼類型。 當[疑難排解無法附加的問題](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md#BKMK_Troubleshoot_attach_errors)時，這會很有説明。 此選項會將偵測限制為僅限您想要進行偵錯工具的程式碼類型。

   ::: moniker range=">=vs-2019"
   - Blazor WebAssembly-用戶端 Blazor WebAssembly
   - GPU-軟體模擬器-在 GPU 軟體模擬器上執行的 c + + 程式碼
   - JavaScript （Chrome）-在 Chrome 中執行的 JavaScript
   - JavaScript （Microsoft Edge-Chromium）-在以 Chromium 為基礎的 Microsoft Edge for Windows 10 中執行的 JavaScript
   - JavaScript CDP （V3）偵錯工具-Chrome DevTools 通訊協定第3版，用於在 CDP 用戶端中進行偵錯工具
   - 受控（CoreCLR）-.NET Core
   - Managed （原生編譯）-c + +/CLR 程式碼
   - 受控（3.5、v3.0、v2.0）-適用于 .NET Framework 2.0 和更高版本的 .NET Framework 程式碼（最多3.5）
   - 受控（4.6、4.5、v4.0）-適用于 .NET Framework 4.0 和更新版本的 .NET Framework 程式碼
   - Native-C/c + +
   - Node.js 的偵錯工具-由 Node.js 執行時間裝載的程式碼
   - Python-Python 
   - 腳本-指定 JavaScript 的一般腳本偵錯工具。 如果適用于您的案例，例如 JavaScript （Chrome），請使用更嚴格的選項。
   - T-sql-Transact-sql
   - Unity-Unity
   - Managed 相容性模式-指定受控碼的舊版偵錯工具，以供一般用於使用 c + +/CLR 程式碼進行混合模式的偵錯工具（針對混合模式啟用 [編輯後繼續]）或支援以舊版偵錯工具為目標的延伸模組。 在大部分的混合模式偵錯工具案例中，選取**原生**和適當的**managed**程式碼類型，而不是 managed 相容性模式。
   ::: moniker-end

   在大部分的情況下，不支援在相同的偵錯工具中附加多個偵錯工具。 您可以使用 Visual Studio 的第二個實例來執行這項操作。

## <a name="see-also"></a>另請參閱
- [偵錯工具安全性](../debugger/debugger-security.md)
- [附加到正在執行的處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)