---
title: 配置攔截和 C 執行階段記憶體配置 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3dbb9f2640d3da71566b8c8839b413943927af2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47492478"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>配置攔截和 C 執行階段記憶體配置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[配置攔截和 C 執行階段記憶體配置](https://docs.microsoft.com/visualstudio/debugger/allocation-hooks-and-c-run-time-memory-allocations)。  
  
如果呼叫任何配置內部記憶體的 C 執行階段程式庫函式，配置攔截函式上非常重要的限制是必須明確地忽略 `_CRT_BLOCK` 區塊 (由 C 執行階段程式庫函式所做的內部記憶體配置)。 在配置攔截函式的開頭包含有像下列的程式碼可以忽略 `_CRT_BLOCK` 區塊：  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 如果配置攔截沒有忽略 `_CRT_BLOCK` 區塊，那麼攔截裡的任何 C 執行階段程式庫函式可以捕捉無窮迴圈裡的程式。 例如，`printf` 會執行內部配置。 如果攔截程式碼呼叫`printf`，則產生的配置會再次呼叫攔截稱之為**printf** ，依此類推，直到堆疊溢位。 如果您要報告 `_CRT_BLOCK` 配置操作，避開這種限制的一種方法是使用 Windows API 函式，而不是執行階段函式來執行格式化和輸出。 因為 Windows API 不會使用 C 執行階段程式庫堆積，它們不會在無窮迴圈裡捕捉配置攔截。  
  
 如果您檢查執行階段程式庫原始程式檔時，您會看到，預設配置攔截函式**CrtDefaultAllocHook** (只簡單傳回 **，則為 TRUE**)，位於個別的檔案，DBGHOOK。C。 如果您想要呼叫甚至會在您的應用程式前執行的執行階段啟始程式碼所做的配置中的配置攔截**主要**函式，您可以使用您自己，而不是取代這個預設函式使用[_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d)。  
  
## <a name="see-also"></a>另請參閱  
 [撰寫偵錯攔截函式](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 範例](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)



