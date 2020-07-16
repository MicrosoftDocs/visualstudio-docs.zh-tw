---
title: 錯誤：評估函式 &#39;函式&#39; 超時，而且需要以不安全的方式中止 |Microsoft Docs
ms.date: 11/15/2016
ms.topic: reference
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
ms.assetid: 0a9f70ed-21ad-4a10-8535-b9c5885ad8f4
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a27bf67770eef770fddef0301a804e6c45579539
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387118"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>錯誤：評估函式 &#39;函式&#39; 超時，而且需要以不安全的方式中止
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

完整郵件內文：評估函式 ' function ' 超時，而且需要以不安全的方式中止。 這可能會損毀目標進程。 

為了讓您更輕鬆地檢查 .NET 物件的狀態，偵錯工具會自動強制已調試的進程執行額外的程式碼（通常是屬性 getter 方法和 ToString 函數）。 在大部分的情況下，這些函式會快速完成，讓您更輕鬆地進行調試。 不過，偵錯工具不會在沙箱中執行應用程式。 如此一來，呼叫原生函式（停止回應）的屬性 getter 或 ToString 方法可能會導致長時間的超時，而無法復原。 如果您遇到這個錯誤訊息，就會發生這種情況。
 
這個問題的其中一個常見原因是，當偵錯工具評估屬性時，它只允許已檢查的執行緒執行。 因此，如果屬性正在等候其他執行緒在已調試的應用程式內執行，而且它正在等待 .NET 執行時間無法中斷的情況，就會發生這個問題。
 
## <a name="to-correct-this-error"></a>更正這個錯誤
 
此問題有三個可能的解決方案。
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>方案 #1：防止偵錯工具呼叫 getter 屬性或 ToString 方法
 
錯誤訊息會告訴您偵錯工具嘗試呼叫的函式名稱。 如果您可以修改這個函式，您可以防止偵錯工具呼叫屬性 getter 或 ToString 方法。 請嘗試下列其中一項：
 
* 將方法變更為其他類型的程式碼，但屬性 getter 或 ToString 方法除外，問題就會消失。
    -或-
* （適用于 ToString）在型別上定義 DebuggerDisplay 屬性，而且您可以讓偵錯工具評估 ToString 以外的專案。
    -或-
* （適用于屬性 getter）將 `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` 屬性放在屬性上。 如果您的方法需要針對 API 相容性而保留屬性，但它其實應該是方法，這會很有用。
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>方案 #2：讓目的程式代碼要求偵錯工具中止評估
 
錯誤訊息會告訴您偵錯工具嘗試呼叫的函式名稱。 如果屬性 getter 或 ToString 方法有時無法正確執行，特別是在問題是程式碼需要另一個執行緒來執行程式碼的情況下，則執行函式可以呼叫 `System.Diagnostics.Debugger.NotifyOfCrossThreadDependency` 來要求偵錯工具中止函數評估。 有了這個解決方案，仍然可以明確地評估這些函式，但預設行為是在發生 NotifyOfCrossThreadDependency 呼叫時停止執行。
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>解決方案 #3：停用所有隱含評估
 
如果先前的解決方案無法修正問題，請移至 [*工具*] [  /  *選項*]， *Debugging*然後取消核取 [  /  *一般*  /  *啟用屬性評估及其他隱含函式呼叫*] 設定。 這會停用大部分的隱含函式評估，並應解決此問題。
