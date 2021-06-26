---
title: 評估函數函 &apos; &apos; 式超時，需要以不安全的方式中止 |Microsoft Docs
description: 完整郵件內文：評估函式 ' function ' 超時，且需要以不安全的方式中止。
ms.date: 06/18/2021
ms.topic: error-reference
ms.custom: contperf-fy21q4
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 94c308e9ec960f744a98f0f930999df36afff475
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112925003"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>錯誤：評估函數 &#39;函式&#39; 超時，而且需要以不安全的方式中止

完整郵件內文：評估函式 ' function ' 超時，且需要以不安全的方式中止。 這可能已損毀目標進程。

為了讓您更輕鬆地檢查 .NET 物件的狀態，偵錯工具會自動強制調試的進程執行其他程式碼， (通常是屬性 getter 方法和 ToString 函數) 。 在大部分的情況下，這些函式會快速完成，並讓您更輕鬆地進行調試。 但是，偵錯工具不會在沙箱中執行應用程式。 如此一來，呼叫原生函式停止回應的屬性 getter 或 ToString 方法，可能會導致長時間的超時無法復原。 如果您遇到這個錯誤訊息，就會發生這種情況。

這個問題的其中一個常見原因是當偵錯工具評估屬性時，它只允許檢查執行緒執行。 因此，如果屬性正在等候其他執行緒在所調試的應用程式內執行，而且它正在等候 .NET 執行時間無法中斷的狀況，就會發生此問題。

## <a name="to-correct-this-error"></a>更正這個錯誤

請參閱下列各節，以瞭解此問題的幾個可能解決方案。

## <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>方案 #1：防止偵錯工具呼叫 getter 屬性或 ToString 方法

錯誤訊息會告訴您偵錯工具嘗試呼叫的函式名稱。 如果您可以修改此函式，則可以防止偵錯工具呼叫 property getter 或 ToString 方法。 請嘗試下列其中一項：

* 將方法變更為其他類型的程式碼（property getter 或 ToString 方法除外），問題就會消失。
  -或-
*  (ToString) 定義型別上的 [DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md) 屬性，而且您可以讓偵錯工具評估 ToString 以外的內容。
  -或-
* 針對屬性 getter 的 () 將 [DebuggerBrowsable (DebuggerBrowsableState。屬性上不) ](/dotnet/api/system.diagnostics.debuggerbrowsableattribute) 屬性。 如果您有需要針對 API 相容性的屬性保留屬性的方法，這會很有用，但其實它應該是方法。

## <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>解決方案 #2：讓目的程式代碼要求偵錯工具中止評估

錯誤訊息會告訴您偵錯工具嘗試呼叫的函式名稱。 如果屬性 getter 或 ToString 方法有時無法正常執行，尤其是在問題是程式碼需要另一個執行緒執行程式碼的情況下，則執行函式可以呼叫 [NotifyOfCrossThreadDependency](/dotnet/api/system.diagnostics.debugger.notifyofcrossthreaddependency) 來要求偵錯工具中止函數評估。 使用此解決方案時，仍然可以明確地評估這些函式，但預設行為是在發生 NotifyOfCrossThreadDependency 呼叫時停止執行。

## <a name="solution-3-disable-all-implicit-evaluation"></a>解決方案 #3：停用所有隱含評估

如果先前的解決方案無法修正問題，請移至 [**工具**  >  **選項**]，並取消核 **取 [**  >  **一般** 設定]  >  **啟用屬性評估及其他隱含函式呼叫** 的設定。 這將會停用大部分的隱含函式評估，並且應該解決問題。

## <a name="solution-4-check-compatibility-with-third-party-developer-tools"></a>解決方案 #4：檢查與協力廠商開發人員工具的相容性

如果您使用的是 Resharper，請參閱此 [問題](https://youtrack.jetbrains.com/issue/RSRP-476824) 以取得建議。

## <a name="solution-5-enable-managed-compatibility-mode"></a>解決方案 #5：啟用受管理的相容性模式

如果您切換至舊版的偵測引擎，您可以消除此錯誤。 移至 [**工具**  >  **選項**]，然後選取[一般] 設定 [  >  **一般**  >  **使用 managed 相容性模式]**。 如需詳細資訊，請參閱 [一般偵錯工具選項](../debugger/general-debugging-options-dialog-box.md)。
