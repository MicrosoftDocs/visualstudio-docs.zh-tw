---
title: 配置攔截函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c46b498ea36459dff0eb538ac3e0371fd9c5707
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="allocation-hook-functions"></a>配置攔截函式
配置攔截函式，使用安裝[_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook)，稱為每次配置、 重新配置或釋放記憶體。 這種類型的攔截 (Hook) 可以用於許多不同的用途。 例如，可以使用它來測試應用程式處理記憶體不足的方式、檢查配置模式或記錄供稍後分析的配置資訊。  
  
> [!NOTE]
>  請留意在配置攔截函式，在描述中使用 C 執行階段程式庫函式的相關限制[配置攔截和 C 執行階段記憶體配置](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)。  
  
 配置攔截函式應該有像下列的原型：  
  
```  
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 您傳遞給指標[_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook)的型別 **_CRT_ALLOC_HOOK**、 CRTDBG 中所定義。H:  
  
```  
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 當執行階段程式庫呼叫您攔截*nAllocType*引數指出哪些配置是即將執行的作業 (**_HOOK_ALLOC**， **_HOOK_REALLOC**，或 **_HOOK_FREE**)。 在釋放或重新配置的情況裡，`pvData` 包含即將要釋放的使用者區塊主題指標。 然而，在配置時，這個指標是 Null，因為還沒發生配置。 其餘的引數包含問題裡配置的大小、區塊類型、相關的要求順序編號，如果有的話，也包含指向執行配置時的檔名和行號的指標。 攔截函式會執行任何分析或其他工作作者之後，它必須傳回**TRUE**，表示配置操作可以繼續，或**FALSE**，這表示，操作應該會失敗。 此類型的簡單攔截可能會檢查目前為止，配置的記憶體數量，傳回**FALSE**數量超過小型限制。 然後應用程式會經歷只有在可用記憶體非常低時才會發生的配置錯誤。 更複雜的攔截可能會追蹤配置模式、分析記憶體使用或在特定情況發生時報告。  
  
## <a name="see-also"></a>另請參閱  
 [配置攔截和 C 執行階段記憶體配置](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [撰寫偵錯攔截函式](../debugger/debug-hook-function-writing.md)   
