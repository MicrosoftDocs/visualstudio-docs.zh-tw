---
title: DebugBreak 和 __debugbreak |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DebugBreak
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb05c054ffc5dd273b532f72afe0ca046adbe606
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55041720"
---
# <a name="debugbreak-and-debugbreak"></a>DebugBreak 和 __debugbreak
您可以在程式碼中的任何一點呼叫 DebugBreak Win32 函式或 [__debugbreak](/cpp/intrinsics/debugbreak) 內建。 `DebugBreak` 和 `__debugbreak` 的作用與在該位置設定中斷點的作用相同。  
  
 由於 `DebugBreak` 屬於系統函式呼叫，因此必須安裝系統偵錯符號，才能確保中斷後會顯示正確的呼叫堆疊資訊。 否則，偵錯工具所顯示的呼叫堆疊資訊可能會偏移一個框架。 如果您使用 `__debugbreak`，就不需要符號。  
  
## <a name="see-also"></a>請參閱  
 [編譯器內建](/cpp/intrinsics/compiler-intrinsics)   
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯機器碼](../debugger/debugging-native-code.md)   
 [指定符號 (.pdb) 和來源檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)