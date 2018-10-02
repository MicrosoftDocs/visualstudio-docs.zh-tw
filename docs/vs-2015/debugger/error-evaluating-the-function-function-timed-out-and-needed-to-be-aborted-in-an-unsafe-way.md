---
title: 錯誤： 評估函式&#39;函式&#39;逾時，需要以不安全的方式中止 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
ms.assetid: 0a9f70ed-21ad-4a10-8535-b9c5885ad8f4
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b78d4b8f433c925521a978ab5c3a5076f329c407
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491703"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>錯誤： 評估函式&#39;函式&#39;已逾時及所需的不安全的方法中止
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[錯誤： 評估函式&#39;函式&#39;已逾時及所需的不安全的方式會中止](https://docs.microsoft.com/visualstudio/debugger/error-evaluating-the-function-function-timed-out-and-needed-to-be-aborted-in-an-unsafe-way)。  
  
完整訊息文字： 評估函式 'function' 已逾時及所需的不安全的方法中止。 這可能已損毀目標處理序。 

若要讓您更輕鬆地檢查.NET 物件的狀態，偵錯工具會自動強制執行額外的程式碼 （通常是屬性 getter 方法和 ToString 函式） 偵錯的處理序。 在大部分的所有情況下，這些函式會快速完成，並進行偵錯更容易。 不過，偵錯工具不會在沙箱中執行應用程式。 如此一來，屬性 getter 或停止回應的原生函式所呼叫的 ToString 方法可能會導致長的逾時，可能無法復原。 如果您遇到此錯誤訊息發生這種情況。
 
此問題的一個常見原因是，當偵錯工具會評估屬性，它只允許檢查要執行的執行緒。 因此如果在偵錯的應用程式內執行其他執行緒正在等候屬性，並等待.NET 執行階段無法中斷的方式，將會發生此問題。
 
## <a name="to-correct-this-error"></a>更正這個錯誤
 
有三個可能的解決方案，此問題。
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>解決方案 1： 可防止偵錯工具呼叫 ToString 方法的 getter 屬性
 
錯誤訊息會告訴您偵錯工具嘗試呼叫函式的名稱。 如果您可以修改這個函式，您可以防止偵錯工具呼叫屬性 getter 或 ToString 方法。 請嘗試下列其中一項：
 
* 將方法變更為其他類型的程式碼除了屬性 getter 或 ToString 方法和問題就會消失。
    -或-
* （如 ToString)定義 DebuggerDisplay 屬性型別上，您可以讓偵錯工具評估 ToString 以外的項目。
    -或-
* （適用於屬性 getter)Put`[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]`屬性上的屬性。 這非常有用，如果您有必須保持 API 相容性的原因，屬性的方法，但它其實應該是一種方法。
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>解決方案 2： 已要求中止評估偵錯工具的目標程式碼
 
錯誤訊息會告訴您偵錯工具嘗試呼叫函式的名稱。 如果屬性 getter 或 ToString 方法有時會無法正確執行，特別是在的情況下問題的程式碼需要另一個執行緒來執行程式碼，然後實作函式可以呼叫`System.Diagnostics.Debugger.NotifyOfCrossThreadDependency`要求中止函式偵錯工具評估之旅。 使用此解決方案，仍可明確評估這些函式，但預設行為是 NotifyOfCrossThreadDependency 呼叫發生時停止執行。
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>解決方案 3： 停用所有隱含的評估
 
如果先前的解決方案不修正此問題，請移至*工具* / *選項*，然後取消選取設定*偵錯* /  *一般* / *啟用屬性評估及其他隱含函式呼叫*。 這將會停用大部分的隱含函式評估，並應可解決問題。



  




