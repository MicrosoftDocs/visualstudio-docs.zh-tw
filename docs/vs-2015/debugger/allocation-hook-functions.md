---
title: 配置攔截函式 |Microsoft Docs
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
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c42d1984d8138186241fddaf3d8dbaee7f02338d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499976"
---
# <a name="allocation-hook-functions"></a>配置攔截函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[配置攔截函式](https://docs.microsoft.com/visualstudio/debugger/allocation-hook-functions)。  
  
配置攔截函式，使用安裝[_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d)，稱為每次配置、 重新配置或釋放記憶體。 這種類型的攔截 (Hook) 可以用於許多不同的用途。 例如，可以使用它來測試應用程式處理記憶體不足的方式、檢查配置模式或記錄供稍後分析的配置資訊。  
  
> [!NOTE]
>  請留意有關使用 C 執行階段程式庫函式中的配置攔截函式中所述的限制[配置攔截和 C 執行階段記憶體配置](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)。  
  
 配置攔截函式應該有像下列的原型：  
  
```  
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 將指標傳遞給[_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d)別的 **_CRT_ALLOC_HOOK**、 CRTDBG 中所定義。H:  
  
```  
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 當執行階段程式庫呼叫攔截， *nAllocType*引數會指出哪些配置在即將執行的作業 (**_HOOK_ALLOC**， **_HOOK_REALLOC**，或 **_HOOK_FREE**)。 在釋放或重新配置的情況裡，`pvData` 包含即將要釋放的使用者區塊主題指標。 然而，在配置時，這個指標是 Null，因為還沒發生配置。 其餘的引數包含問題裡配置的大小、區塊類型、相關的要求順序編號，如果有的話，也包含指向執行配置時的檔名和行號的指標。 攔截函式會執行任何分析或其他工作作者所要求之後，它必須傳回**真**，表示配置操作可以繼續進行，或**FALSE**，這表示，作業應該會失敗。 這種類型的簡單攔截可能會檢查截至目前為止，配置的記憶體數量，並傳回**FALSE**數量超過小型限制。 然後應用程式會經歷只有在可用記憶體非常低時才會發生的配置錯誤。 更複雜的攔截可能會追蹤配置模式、分析記憶體使用或在特定情況發生時報告。  
  
## <a name="see-also"></a>另請參閱  
 [配置攔截和 C 執行階段記憶體配置](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [撰寫偵錯攔截函式](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 範例](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)



