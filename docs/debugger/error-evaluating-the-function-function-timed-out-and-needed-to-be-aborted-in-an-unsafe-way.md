---
title: 評估函數函 &apos; &apos; 式超時，需要以不安全的方式中止 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1f6cae3ffb692161deb0b162a6432efe90f12bf3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871646"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>錯誤：評估函數 &#39;函式&#39; 超時，而且需要以不安全的方式中止

完整郵件內文：評估函式 ' function ' 超時，且需要以不安全的方式中止。 這可能已損毀目標進程。

為了讓您更輕鬆地檢查 .NET 物件的狀態，偵錯工具會自動強制調試的進程執行其他程式碼， (通常是屬性 getter 方法和 ToString 函數) 。 在大部分的情況下，這些函式會快速完成，並讓您更輕鬆地進行調試。 但是，偵錯工具不會在沙箱中執行應用程式。 如此一來，呼叫原生函式停止回應的屬性 getter 或 ToString 方法，可能會導致長時間的超時無法復原。 如果您遇到這個錯誤訊息，就會發生這種情況。

這個問題的其中一個常見原因是當偵錯工具評估屬性時，它只允許檢查執行緒執行。 因此，如果屬性正在等候其他執行緒在所調試的應用程式內執行，而且它正在等候 .NET 執行時間無法中斷的狀況，就會發生此問題。

## <a name="to-correct-this-error"></a>更正這個錯誤

有幾個可能的解決方案可解決此問題。

### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>方案 #1：防止偵錯工具呼叫 getter 屬性或 ToString 方法

錯誤訊息會告訴您偵錯工具嘗試呼叫的函式名稱。 如果您可以修改此函式，則可以防止偵錯工具呼叫 property getter 或 ToString 方法。 請嘗試下列其中一項：

* 將方法變更為其他類型的程式碼（property getter 或 ToString 方法除外），問題就會消失。
    -或-
*  (ToString) 定義型別上的 DebuggerDisplay 屬性，而且您可以讓偵錯工具評估 ToString 以外的內容。
    -或-
* 屬性 getter 的 () 將屬性放 `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` 在屬性上。 如果您有需要針對 API 相容性的屬性保留屬性的方法，這會很有用，但其實它應該是方法。

### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>解決方案 #2：讓目的程式代碼要求偵錯工具中止評估

錯誤訊息會告訴您偵錯工具嘗試呼叫的函式名稱。 如果屬性 getter 或 ToString 方法有時無法正常執行，特別是在問題是程式碼需要另一個執行緒執行程式碼的情況下，則執行函式可以呼叫， `System.Diagnostics.Debugger.NotifyOfCrossThreadDependency` 要求偵錯工具中止函數評估。 使用此解決方案時，仍然可以明確地評估這些函式，但預設行為是在發生 NotifyOfCrossThreadDependency 呼叫時停止執行。

### <a name="solution-3-disable-all-implicit-evaluation"></a>解決方案 #3：停用所有隱含評估

如果先前的解決方案無法修正問題，請移至 [**工具**  >  **選項**]，並取消核 **取 [**  >  **一般** 設定]  >  **啟用屬性評估及其他隱含函式呼叫** 的設定。 這將會停用大部分的隱含函式評估，並且應該解決問題。

### <a name="solution-4-enable-managed-compatibility-mode"></a>解決方案 #4：啟用受管理的相容性模式

如果您切換至舊版的偵測引擎，您可以消除此錯誤。 移至 [**工具**  >  **選項**]，然後選取[一般] 設定 [  >  **一般**  >  **使用 managed 相容性模式]**。 如需詳細資訊，請參閱 [一般偵錯工具選項](../debugger/general-debugging-options-dialog-box.md)。
