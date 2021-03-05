---
description: 完整郵件內文：評估函式 ' function ' 時，目標進程以程式碼 ' code ' 結束。
title: '&apos; &apos; 評估函數函式時， &apos; 目標進程以程式碼結束 &apos;Microsoft 檔'
ms.date: 4/06/2018
ms.topic: error-reference
f1_keywords:
- vs.debug.error.process_exit_during_func_eval
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ba1e2e258a12c6548317b272365db67503dc3d16
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146999"
---
# <a name="error-the-target-process-exited-with-code-39code39-while-evaluating-the-function-39function39"></a>錯誤：評估函數 &#39;函數時，目標進程以程式碼 &#39;程式碼&#39; 結束&#39;

完整郵件內文：評估函式 ' function ' 時，目標進程以程式碼 ' code ' 結束。

為了讓您更輕鬆地檢查 .NET 物件的狀態，偵錯工具會自動強制調試的進程執行額外的程式碼， (通常是屬性 getter 方法和 `ToString` 函數) 。 在大部分的情況下，這些函式會順利完成，或擲回偵錯工具可能捕捉的例外狀況。 不過，在某些情況下無法攔截例外狀況，因為它們跨核心界限、需要使用者訊息提取或無法復原。 如此一來，執行明確終止進程之程式碼的屬性 getter 或 ToString 方法 (例如，會呼叫) 或擲回無法攔截的 `ExitProcess()` 未處理例外狀況 (例如， `StackOverflowException`) 將終止已調試的進程，並結束偵錯工具。 如果您遇到這個錯誤訊息，就會發生這種情況。

這個問題的其中一個常見原因是當偵錯工具評估呼叫本身的屬性時，這可能會導致堆疊溢位例外狀況。 無法復原堆疊溢位例外狀況，而且目標進程將會結束。

## <a name="to-correct-this-error"></a>更正這個錯誤

有兩個可能的解決方案可解決此問題。

### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>方案 #1：防止偵錯工具呼叫 getter 屬性或 ToString 方法 

錯誤訊息會告訴您偵錯工具嘗試呼叫的函式名稱。 使用函式的名稱，您可以嘗試從 [即時 **運算] 視窗** 重新評估該函數，以進行評估。 從 [即時運算] 視窗進行評估時可以進行偵錯工具，因為與 [自動 **變數/區域變數]/[監看** 式 **] 視窗的** 隱含評估不同，偵錯工具會在未處理的例外

如果您可以修改此函式，則可以防止偵錯工具呼叫屬性 getter 或 `ToString` 方法。 請嘗試下列其中一項：

* 將方法變更為其他類型的程式碼（property getter 或 ToString 方法除外），問題就會消失。
    -或-
*  (`ToString`) 定義類型的 `DebuggerDisplay` 屬性，而且您可以讓偵錯工具評估以外的某個值 `ToString` 。
    -或-
* 屬性 getter 的 () 將屬性放 `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` 在屬性上。 如果您的方法需要針對 API 相容性的原因維持屬性，但它其實應該是方法，這會很有用。

如果您無法修改這個方法，您可以在替代的指令中斷目標進程，然後重試一次評估。

### <a name="solution-2-disable-all-implicit-evaluation"></a>解決方案 #2：停用所有隱含評估

如果先前的解決方案無法修正問題，請移至 [**工具**  >  **選項**]，並取消核 **取 [**  >  **一般** 設定]  >  **啟用屬性評估及其他隱含函式呼叫** 的設定。 這將會停用大部分的隱含函式評估，並且應該解決問題。
