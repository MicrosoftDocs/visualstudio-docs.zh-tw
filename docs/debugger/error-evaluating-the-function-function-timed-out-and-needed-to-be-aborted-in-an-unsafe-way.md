---
title: 錯誤： 評估該函式&#39;函式&#39;逾時，需要中止不安全的方式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
ms.technology: vs-ide-debug
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9843dd870521312f45353c894908130fba0074c7
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>錯誤： 評估該函式&#39;函式&#39;逾時，需要中止不安全的方式

完整訊息文字： 評估該函式 'function' 已逾時，需要中止不安全的方式。 這可能已損毀目標處理序。 

若要讓您更輕鬆地檢查.NET 物件的狀態，偵錯工具會自動強制執行額外的程式碼 （通常是屬性 getter 方法和 ToString 函式） 偵錯的處理序。 在大部分的所有情況下，這些函式會快速完成，然後進行偵錯更容易。 不過，偵錯工具不會在沙箱中執行應用程式。 如此一來，可能無法復原的長逾時可能導致屬性 getter 或停止回應的原生函式所呼叫的 ToString 方法。 如果您遇到這個錯誤訊息時，發生這種情況。
 
這個問題的一個常見原因是，當偵錯工具會評估屬性，它只能讓正在檢查要執行的執行緒。 因此如果屬性正在等候其他執行緒中執行偵錯的應用程式，而且正在等候.NET 執行階段無法中斷的方式，將會發生這個問題。
 
## <a name="to-correct-this-error"></a>更正這個錯誤
 
有三個可能的解決方案，此問題。
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>解決方案 1： 防止偵錯工具呼叫 ToString 方法的 getter 屬性
 
錯誤訊息會告訴您偵錯工具嘗試呼叫的函式的名稱。 如果您可以修改此函式，您可以防止偵錯工具呼叫屬性 getter 或 ToString 方法。 請嘗試下列其中一項：
 
* 將方法變更為其他類型的屬性 getter 以外的程式碼或 ToString 方法和問題就會消失。
    -或-
* （適用於 ToString)類型上定義 DebuggerDisplay 屬性，且您可以偵錯工具評估 ToString 以外的項目。
    -或-
* （適用於屬性 getter)Put`[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]`屬性上的屬性。 這很有用，如果您擁有需要保持應用程式開發介面相容性考量，屬性的方法，但它實際上應該是一種方法。
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>解決方案 2： 已要求中止評估偵錯工具的目標程式碼
 
錯誤訊息會告訴您偵錯工具嘗試呼叫的函式的名稱。 如果屬性 getter 或 ToString 方法有時會無法正確執行，特別是在問題時，程式碼需要另一個執行緒來執行程式碼，然後實作函式可以呼叫`System.Diagnostics.Debugger.NotifyOfCrossThreadDependency`向偵錯工具 abort 函式評估。 使用此解決方案中，仍可明確地評估這些函式，但預設行為是 NotifyOfCrossThreadDependency 呼叫時停止執行。
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>解決方案 #3： 停用所有隱含的評估
 
如果先前的解決方案未能解決此問題，請移至*工具* > *選項*，然後取消選取設定*偵錯* >  *一般* > *啟用屬性評估及其他隱含函式呼叫*。 這將會停用大部分隱含函式評估並解決問題。



  
