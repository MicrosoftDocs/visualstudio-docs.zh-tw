---
title: 配置攔截和 C 執行階段記憶體配置 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9faacefd4fc0817f5dd5cae31392017458ede49e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58944156"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>配置攔截和 C 執行階段記憶體配置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果呼叫任何配置內部記憶體的 C 執行階段程式庫函式，配置攔截函式上非常重要的限制是必須明確地忽略 `_CRT_BLOCK` 區塊 (由 C 執行階段程式庫函式所做的內部記憶體配置)。 在配置攔截函式的開頭包含有像下列的程式碼可以忽略 `_CRT_BLOCK` 區塊：  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 如果配置攔截沒有忽略 `_CRT_BLOCK` 區塊，那麼攔截裡的任何 C 執行階段程式庫函式可以捕捉無窮迴圈裡的程式。 例如，`printf` 會執行內部配置。 如果攔截程式碼呼叫`printf`，則產生的配置會再次呼叫攔截稱之為**printf** ，依此類推，直到堆疊溢位。 如果您要報告 `_CRT_BLOCK` 配置操作，避開這種限制的一種方法是使用 Windows API 函式，而不是執行階段函式來執行格式化和輸出。 因為 Windows API 不會使用 C 執行階段程式庫堆積，它們不會在無窮迴圈裡捕捉配置攔截。  
  
 如果檢查執行階段程式庫原始程式檔，您會看到預設的 **CrtDefaultAllocHook** 配置攔截函式 (只簡單傳回 **TRUE**) 位於本身不同的 DBGHOOK.C 檔案內。 如果您要針對在應用程式 **main** 函式前執行之執行階段起始程式碼的配置進行呼叫配置攔截，則您可以使用自己的攔截而不使用 [_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d) 來取代這個預設函式。  
  
## <a name="see-also"></a>另請參閱  
 [撰寫偵錯攔截函式](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 範例](http://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
