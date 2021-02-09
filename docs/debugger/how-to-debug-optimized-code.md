---
title: 偵錯工具優化程式碼 |Microsoft Docs
description: 可能的話，在您的程式進行調試之前，請勿建立 Win32 發行目標，因為優化可能會讓偵錯工具變得複雜。 請參閱本文中的詳細資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- breakpoints, in optimized code
- debugging [C++], optimized code
- optimization, debug builds
- debug builds, optimizing
- optimized code, debugging
ms.assetid: fc8eeeb8-6629-4c9b-99f7-2016aee81dff
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 19b09831aea0f7e38c7d095c1e549496569405c9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899304"
---
# <a name="how-to-debug-optimized-code"></a>如何：偵錯最佳化程式碼

> [!NOTE]
> 您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。 若要變更設定，請從 [工具] 功能表中選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

> [!NOTE]
> [/Zo (增強最佳化的偵錯)](/cpp/build/reference/zo-enhance-optimized-debugging) 編譯器選項 (在 Visual Studio Update 3 引入) 會針對最佳化程式碼 (不使用 **/Od** 編譯器選項建置的專案) 產生更豐富的偵錯資訊。 請參閱 [/O 選項 (最佳化程式碼)](/cpp/build/reference/o-options-optimize-code))。 這包括改善對於本機變數和內嵌函式的偵錯支援。
>
> 使用 **/Zo** 編譯器選項時，會停用 [編輯後繼續](../debugger/edit-and-continue-visual-csharp.md)。

 當編譯器最佳化程式碼時，它會重新調整位置並重新組織指令。 這會產生較有效率的已編譯程式碼。 因為這種重新安排，偵錯工具不一定能辨識對應到一組指令的原始程式碼。

 最佳化會影響：

- 區域變數，這些區域變數可能會由最佳化程式移除，或是移至偵錯工具不認識的位置。

- 函式內部的位置，這些位置在最佳化程式合併程式碼區塊時會變更。

- 呼叫堆疊上框架的函式名稱，這個名稱在最佳化程式合併兩個函式時可能會出錯。

  不過，假設所有框架都有符號，則您在呼叫堆疊上看見的框架幾乎一定是正確的。 如果您有堆疊損毀、以組件語言撰寫的函式，或是呼叫堆疊上的作業系統框架沒有相符的符號時，呼叫堆疊上的框架就會出錯。

  全域變數和靜態變數一定會正確顯示， 結構配置也會。 如果您有結構的指標，而且指標的值是正確的，則結構的每個成員變數都會顯示正確的值。

  由於這些限制，您應該盡可能地使用程式的非最佳化版本來進行偵錯。 根據預設，c + + 程式的 Debug 設定中會關閉優化，並在發行設定中開啟。

  然而，有時錯誤可能只出現在程式的最佳化版本中。 在這種情況下，您必須偵錯最佳化程式碼。

## <a name="to-turn-on-optimization-in-a-debug-build-configuration"></a>若要啟動偵錯組建組態的最佳化

1. 當您建立新專案時，選取 `Win32 Debug` 目標。 在您完成程式的偵錯，並準備好建置 `Win32 Release` 目標以前，請使用 `Win32 Debug` 目標。 編譯器不會最佳化 `Win32 Debug` 目標。

2. 在 [方案總管] 中選取專案。

3. 在 [檢視] 功能表上按一下 [屬性頁]。

4. 請確認在 [屬性頁] 對話方塊的 [組態] 下拉式清單中，選取 `Debug`。

5. 在左邊的資料夾檢視中，選取 **C/C++** 資料夾。

6. 在 **C++** 資料夾下方，選取 `Optimization`。

7. 在右邊的屬性清單裡，尋找 `Optimization`。 它旁的設定可能會顯示為 `Disabled (` [/od](/cpp/build/reference/od-disable-debug) `)` 。 選擇其中一個其他選項 (`Minimum Size``(` [/O1](/cpp/build/reference/o1-o2-minimize-size-maximize-speed) `)` 、 `Maximum Speed``(` [/O2](/cpp/build/reference/o1-o2-minimize-size-maximize-speed) `)` 、 `Full Optimization``(` [/ox](/cpp/build/reference/ox-full-optimization) `)` 或 `Custom`) 。

8. 如果您選擇 `Custom` 的 `Optimization` 選項，現在就可以為其他顯示在屬性清單裡的任一屬性設定其選項。

9. 選取 [專案屬性] 頁面的 [設定屬性]、[C/c + +]、[命令列] 節點，然後將 `(` [/Zo](/cpp/build/reference/zo-enhance-optimized-debugging)加入 `)` [**其他選項**] 文字方塊中。

    > [!WARNING]
    > `/Zo` 需要 Visual Studio 2013 Update 3 或更新版本。
    >
    >  新增 `/Zo` 將會停用 [編輯後繼續](../debugger/edit-and-continue-visual-csharp.md)。

   偵錯最佳化程式碼時，使用 [反組譯碼] 視窗來查看哪些指令已經確實建立和執行。 設定中斷點時，您必須了解中斷點可能會隨著指令移動。 例如，請參考下列程式碼：

```cpp
for (x=0; x<10; x++)
```

 假設您在這行設定中斷點。 您可以預期會叫用 10 次中斷點，但是如果程式碼已完成最佳化，便只會叫用中斷點一次。 原因是第一個指令會將 `x` 值設為 0。 編譯器會辨識這個動作只需做一次，並且將它移出迴圈外。 中斷點會隨著移動。 迴圈內部則仍保留比較和累加 `x` 的指令。 當您檢視 [反組譯碼] 視窗時，為取得更佳控制，[步驟單位](/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100))會自動設為指令，這在逐步執行最佳化程式碼時非常有用。

## <a name="see-also"></a>另請參閱

- [偵錯工具安全性](../debugger/debugger-security.md)
- [偵錯機器碼](../debugger/debugging-native-code.md)