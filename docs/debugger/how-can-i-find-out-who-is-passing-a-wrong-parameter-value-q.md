---
title: 找出誰傳遞錯誤的參數值 |Microsoft 檔
description: 您可以找出呼叫函式的程式碼，並傳遞不正確的參數值。 瞭解如何使用條件式中斷點來執行此動作。
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.parameters
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], parameters
- parameters [debugger]
- passing parameters, troubleshooting wrong values
- functions [debugger], detecting wrong parameter values
- parameter values, troubleshooting
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cb4b3c41b46817d15a13626983ccf55ffa9acc5f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155176"
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>如何發現誰傳錯參數值？
## <a name="problem-description"></a>問題說明
 我的函式中傳入了一個錯誤的參數。 這個函式會從許多地方呼叫。 我該如何確定錯誤值是誰傳出的？

## <a name="solution"></a>解決方法

#### <a name="to-resolve-this-problem"></a>若要解決這個問題

1. 在函式的開頭設定位置中斷點。

2. 以滑鼠右鍵按一下中斷點並選取 [條件]。

3. 在 [中斷點條件] 對話方塊中，按一下 [條件] 核取方塊。 請參閱 [Advanced 中斷點](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)。

4. 在文字方塊中輸入運算式，例如 `Var==3`；其中 `Var` 是含有錯誤值的參數名稱，而 `3` 則是傳入的錯誤值。

5. 選取 [為 True] 選項按鈕，然後按一下 [確定] 按鈕。

6. 現在再次執行程式。 當 `Var` 參數的值是 `3` 時，中斷點會造成程式暫止在函式的開頭。

7. 然後您可以使用 [呼叫堆疊] 視窗來找出呼叫函式並且巡覽原始程式碼。 如需詳細資訊，請參閱 [如何：使用呼叫堆疊視窗](../debugger/how-to-use-the-call-stack-window.md)。

## <a name="see-also"></a>另請參閱
- [原生程式碼的偵錯工具常見問題](../debugger/debugging-native-code-faqs.md)
- [[中斷點]](/previous-versions/ktf38f66(v=vs.100))
- [偵錯機器碼](../debugger/debugging-native-code.md)
