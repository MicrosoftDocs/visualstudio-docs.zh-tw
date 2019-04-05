---
title: DebugBreak 和 __debugbreak |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- DebugBreak
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c7d26d78cf5e1995c25560e70e46ee4f6fde3a25
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945325"
---
# <a name="debugbreak-and-debugbreak"></a>DebugBreak 和 __debugbreak
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以在程式碼中的任何一點呼叫 DebugBreak Win32 函式或 [__debugbreak](http://msdn.microsoft.com/library/1d1e1c0c-891a-4613-ae4b-d790094ba830) 內建。 `DebugBreak` 和 `__debugbreak` 的作用與在該位置設定中斷點的作用相同。  
  
 由於 `DebugBreak` 屬於系統函式呼叫，因此必須安裝系統偵錯符號，才能確保中斷後會顯示正確的呼叫堆疊資訊。 否則，偵錯工具所顯示的呼叫堆疊資訊可能會偏移一個框架。 如果您使用 `__debugbreak`，就不需要符號。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建](http://msdn.microsoft.com/library/48bb9929-7d78-4fd8-a092-ae3c9f971858)   
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯機器碼](../debugger/debugging-native-code.md)   
 [指定符號 (.pdb) 和來源檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
