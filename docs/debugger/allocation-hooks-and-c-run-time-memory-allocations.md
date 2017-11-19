---
title: "配置攔截和 C 執行階段記憶體配置 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62a8be3b1a1c98a330efeb26d9a84e74f2334423
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>配置攔截和 C 執行階段記憶體配置
如果呼叫任何配置內部記憶體的 C 執行階段程式庫函式，配置攔截函式上非常重要的限制是必須明確地忽略 `_CRT_BLOCK` 區塊 (由 C 執行階段程式庫函式所做的內部記憶體配置)。 在配置攔截函式的開頭包含有像下列的程式碼可以忽略 `_CRT_BLOCK` 區塊：  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 如果配置攔截沒有忽略 `_CRT_BLOCK` 區塊，那麼攔截裡的任何 C 執行階段程式庫函式可以捕捉無窮迴圈裡的程式。 例如，`printf` 會執行內部配置。 如果您攔截的程式碼呼叫`printf`，則產生的配置會導致將呼叫一次，呼叫攔截**printf** ，依此類推，直到堆疊溢位。 如果您要報告 `_CRT_BLOCK` 配置操作，避開這種限制的一種方法是使用 Windows API 函式，而不是執行階段函式來執行格式化和輸出。 因為 Windows API 不會使用 C 執行階段程式庫堆積，它們不會在無窮迴圈裡捕捉配置攔截。  
  
 如果您檢查執行階段程式庫原始程式檔，您會看到預設配置攔截函式， **CrtDefaultAllocHook** (只簡單傳回**TRUE**)，位於自己的個別檔案DBGHOOK。C。 如果您想要呼叫即使對於會在您的應用程式之前執行的執行階段啟始程式碼所做的配置配置攔截**主要**函式，您可以使用您自己，而不是取代此預設函式使用[_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯攔截函式寫入](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 範例](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)