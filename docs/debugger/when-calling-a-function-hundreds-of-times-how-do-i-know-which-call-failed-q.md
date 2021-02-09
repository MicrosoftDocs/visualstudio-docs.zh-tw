---
title: 多次呼叫函式時尋找呼叫失敗
description: 請參閱在函式上設定中斷點的技巧，讓中斷只會發生在函式失敗的呼叫上。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.functions
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- conditional breakpoints
- errors [debugger], function calls
- breakpoints, troubleshooting
- errors [debugger], finding which function call failed
- failures
- location breakpoint call failures
- errors [Visual Studio], function calls
- hit counts
- function calls, failure
- functions [debugger]
- Skip Count
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8937b58277450198d7c0927d93118c492faedfbc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883879"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>呼叫函式好幾百次時，如何判斷是哪一個呼叫失敗？
## <a name="problem-description"></a>問題說明
 我的程式在呼叫某個函式 (`CnvtV`) 時失敗。 失敗之前，程式大概會呼叫此函式幾百次。 如果我在 `CnvtV` 上設定一個中斷點，程式會在每次呼叫此函式時停止，但是我不要這樣。 我不知道什麼條件會造成呼叫失敗，因此我無法設定條件中斷點。 我該怎麼處理？

## <a name="solution"></a>解決方案
 您可以在函式上設定一個 [叫用次數] 欄位值永遠無法遇到的中斷點。 在這種情況下，因為您相信函式 `CnvtV` 會遭呼叫幾百次，請將 [叫用次數] 設為 1000 或更高。 接著執行程式並且等候它失敗。 當程式失敗時，開啟 [中斷點] 視窗並且查看中斷點的清單。 您在 `CnvtV` 上設定的中斷點會出現，其後跟著叫用次數和未完成的重複運算次數：

```cpp
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)
```

 現在您已經知道函式會在第 101 次呼叫時失敗。 如果您以叫用次數 101 重設中斷點並且再次執行程式，程式會在上次造成失敗的 `CnvtV` 呼叫處停止。

## <a name="see-also"></a>另請參閱
- [原生程式碼的偵錯工具常見問題](../debugger/debugging-native-code-faqs.md)
- [設定中斷點](/previous-versions/ktf38f66(v=vs.100))
- [偵錯機器碼](../debugger/debugging-native-code.md)