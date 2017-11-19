---
title: "DebugBreak 和 __debugbreak |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DebugBreak
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
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1763c117ce9cdb815f12213830079136169b2c35
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="debugbreak-and-debugbreak"></a>DebugBreak 和 __debugbreak
您可以呼叫 DebugBreak Win32 函式或[__debugbreak](/cpp/intrinsics/debugbreak)內建在您的程式碼在任何時間點。 `DebugBreak` 和 `__debugbreak` 的作用與在該位置設定中斷點的作用相同。  
  
 由於 `DebugBreak` 屬於系統函式呼叫，因此必須安裝系統偵錯符號，才能確保中斷後會顯示正確的呼叫堆疊資訊。 否則，偵錯工具所顯示的呼叫堆疊資訊可能會偏移一個框架。 如果您使用 `__debugbreak`，就不需要符號。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建函式](/cpp/intrinsics/compiler-intrinsics)   
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯機器碼](../debugger/debugging-native-code.md)   
 [指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)