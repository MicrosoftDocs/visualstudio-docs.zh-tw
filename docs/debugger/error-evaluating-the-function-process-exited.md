---
title: 錯誤： 目標處理序已結束，代碼&#39;程式碼&#39;時評估該函式&#39;函式&#39;|Microsoft 文件
ms.custom: ''
ms.date: 4/06/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.process_exit_during_func_eval
ms.technology: vs-ide-debug
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d5e9221ccf162180a89cc88b1ceebcf55be39eef
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="error-the-target-process-exited-with-code-39code39-while-evaluating-the-function-39function39"></a>錯誤： 目標處理序已結束，代碼&#39;程式碼&#39;時評估該函式&#39;函式&#39;

完整訊息文字： 嘗試評估函式 'function' 目標處理序已結束，代碼 'code'。

若要讓您更輕鬆地檢查.NET 物件的狀態，偵錯工具會自動強制執行額外的程式碼偵錯的處理序 (通常是屬性 getter 方法和`ToString`函式)。 在大部分情況下，這些函式會順利完成，或擲回例外狀況可以攔截的偵錯工具。 不過，有某些情況下，在其中例外狀況無法攔截，因為它們跨核心界限、 需要使用者訊息幫浦，或是無法復原。 做為結果的屬性 getter 或執行程式碼的 ToString 方法來明確終止處理序 (例如，呼叫`ExitProcess()`) 或擲回未處理的例外狀況無法攔截，(比方說， `StackOverflowException`) 將會終止偵錯處理序與結束偵錯工作階段。 如果您遇到這個錯誤訊息時，發生這種情況。
 
這個問題的一個常見原因是，當偵錯工具會評估呼叫其本身的屬性，這可能會導致堆疊溢位例外狀況。 無法復原堆疊溢位例外狀況，而且目標處理序會終止。
 
## <a name="to-correct-this-error"></a>更正這個錯誤
 
有兩個可能的解決方案，此問題。
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>解決方案 1： 防止偵錯工具呼叫 ToString 方法的 getter 屬性 

錯誤訊息會告訴您偵錯工具嘗試呼叫的函式的名稱。 函式的名稱，您可以嘗試重新評估該函式從**即時運算**視窗來偵錯評估。 偵錯時，可能從評估**即時運算**視窗，因為與不同的是隱含的評估與**自動變數/區域變數/監看式**windows 中，偵錯工具會在未處理例外狀況上中斷。

如果您可以修改此函式，您可以防止偵錯工具呼叫屬性 getter 或`ToString`方法。 請嘗試下列其中一項：
 
* 將方法變更為其他類型的屬性 getter 以外的程式碼或 ToString 方法和問題就會消失。
    -或-
* (如`ToString`) 定義`DebuggerDisplay`屬性的類型和您可以偵錯工具以外的項目評估`ToString`。
    -或-
* （適用於屬性 getter)Put`[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]`屬性上的屬性。 這可以是適用於您有必須一直保持應用程式開發介面相容性考量，屬性的方法，但它實際上應該是一種方法。

如果您無法修改這個方法，您可以在替代指令處中斷目標處理序，然後再次嘗試評估。
 
### <a name="solution-2-disable-all-implicit-evaluation"></a>解決方案 2： 停用所有隱含的評估
 
如果先前的解決方案未能解決此問題，請移至**工具** > **選項**，然後取消選取設定**偵錯** >  **一般** > **啟用屬性評估及其他隱含函式呼叫**。 這將會停用大部分隱含函式評估並解決問題。



  
