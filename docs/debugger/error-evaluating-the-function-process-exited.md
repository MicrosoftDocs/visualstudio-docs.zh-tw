---
title: 錯誤-在評估函式 &#39;函式&#39; 時，目標進程結束，程式碼 &#39;程式碼&#39; |Microsoft Docs
ms.date: 4/06/2018
ms.topic: error-reference
f1_keywords:
- vs.debug.error.process_exit_during_func_eval
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1721196becf1f746d81fa7e3d4ff5f0371e3f57
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460774"
---
# <a name="error-the-target-process-exited-with-code-39code39-while-evaluating-the-function-39function39"></a>錯誤：在評估函式 &#39;函式時，目標進程結束，程式碼 &#39;程式碼&#39;&#39;

完整郵件內文：評估函式 ' function ' 時，目標進程以程式碼 ' code ' 結束。

為了讓您更輕鬆地檢查 .NET 物件的狀態，偵錯工具會自動強制已調試的進程執行額外的程式碼（通常是屬性 getter 方法和函式 `ToString` ）。 在大部分的情況下，這些函式會順利完成，或擲回偵錯工具可能攔截到的例外狀況。 不過，在某些情況下無法攔截例外狀況，因為它們跨越核心界限、需要使用者訊息提取或無法復原。 因此，執行程式碼以明確終止進程（例如，呼叫）或擲回無法攔截之未處理的例外狀況（例如）的屬性 getter 或 ToString 方法， `ExitProcess()` `StackOverflowException` 會終止已調試的進程並結束 debug 會話。 如果您遇到這個錯誤訊息，就會發生這種情況。

這個問題的其中一個常見原因是，當偵錯工具評估呼叫本身的屬性時，這可能會造成堆疊溢位例外狀況。 無法復原堆疊溢位例外狀況，且目標進程將會終止。

## <a name="to-correct-this-error"></a>更正這個錯誤

此問題有兩個可能的解決方案。

### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>方案 #1：防止偵錯工具呼叫 getter 屬性或 ToString 方法 

錯誤訊息會告訴您，偵錯工具嘗試呼叫的函式名稱。 使用函式的名稱，您可以嘗試從 [即時**運算] 視窗**重新評估該函式，以進行評估。 從 [即時運算] 視窗進行評估時，可能會進行偵錯工具，因為與 [自動**變數/區域變數/監看****式] 視窗**的隱含評估不同，偵錯工具會中斷未處理的例外

如果您可以修改這個函式，您可以防止偵錯工具呼叫屬性 getter 或 `ToString` 方法。 請嘗試下列其中一項：

* 將方法變更為其他類型的程式碼，但屬性 getter 或 ToString 方法除外，問題就會消失。
    -或-
* （適用于 `ToString` ）在 `DebuggerDisplay` 型別上定義屬性，而且您可以讓偵錯工具評估以外的某個專案 `ToString` 。
    -或-
* （適用于屬性 getter）將 `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` 屬性放在屬性上。 如果您的方法需要針對 API 相容性而保留屬性，但它應該是方法，這會很有用。

如果您無法修改此方法，您可以在其他指令中斷目標進程，然後重試評估。

### <a name="solution-2-disable-all-implicit-evaluation"></a>解決方案 #2：停用所有隱含評估

如果先前的解決方案無法修正問題，請移至 [**工具**] [  >  **選項**]， **Debugging**然後取消核取 [  >  **一般**  >  **啟用屬性評估及其他隱含函式呼叫**] 設定。 這會停用大部分的隱含函式評估，並應解決此問題。
