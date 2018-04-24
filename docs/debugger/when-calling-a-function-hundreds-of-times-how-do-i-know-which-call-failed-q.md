---
title: 呼叫函式好幾百次時，如何判斷是哪一個呼叫失敗？ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac6edf60616a3cbf67d05282ebd15798749b263f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>呼叫函式好幾百次時，如何判斷是哪一個呼叫失敗？
## <a name="problem-description"></a>問題說明  
 我的程式在呼叫某個函式 (`CnvtV`) 時失敗。 失敗之前，程式大概會呼叫此函式幾百次。 如果我在 `CnvtV` 上設定一個中斷點，程式會在每次呼叫此函式時停止，但是我不要這樣。 我不知道什麼條件會造成呼叫失敗，因此我無法設定條件中斷點。 我該怎麼做？  
  
## <a name="solution"></a>方案  
 您可以在函式上設定中斷點**叫用次數**欄位設為高，它會永遠不會達到的值。 在此情況下，因為您相信函式`CnvtV`會遭呼叫幾百次，您可能設定**叫用次數**設為 1000年或更多。 接著執行程式並且等候它失敗。 當程式失敗時，開啟 [中斷點] 視窗並且查看中斷點的清單。 您在 `CnvtV` 上設定的中斷點會出現，其後跟著叫用次數和未完成的重複運算次數：  
  
```  
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)  
```  
  
 現在您已經知道函式會在第 101 次呼叫時失敗。 如果您以叫用次數 101 重設中斷點並且再次執行程式，程式會在上次造成失敗的 `CnvtV` 呼叫處停止。  
  
## <a name="see-also"></a>另請參閱  
 [機器碼偵錯 Faq](../debugger/debugging-native-code-faqs.md)   
 [設定中斷點](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [偵錯機器碼](../debugger/debugging-native-code.md)