---
title: 配置攔截函式 |Microsoft Docs
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
ms.openlocfilehash: 6c8a051641811da3658ffe556982c67649704069
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433352"
---
# <a name="allocation-hook-functions"></a>配置攔截函式
配置攔截函式，使用安裝[_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook)，每次記憶體配置、 重新配置，或釋出呼叫。 您可以使用這種類型的攔截程序針對許多不同的用途。 使用它來測試應用程式如何處理記憶體不足的情況下，例如檢查配置模式，或記錄配置資訊以供稍後分析。  
  
> [!NOTE]
>  請留意有關使用 C 執行階段程式庫函式中的配置攔截函式中所述的限制[配置攔截和 C 執行階段記憶體配置](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)。  
  
 配置攔截函式應該有一個原型，如下列範例所示：  
  
```cpp
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 將指標傳遞給[_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook)別的 **_CRT_ALLOC_HOOK**、 CRTDBG 中所定義。H:  
  
```cpp
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 當執行階段程式庫呼叫攔截， *nAllocType*引數會指出哪些配置作業即將成為 (**_HOOK_ALLOC**， **_HOOK_REALLOC**，或 **_HOOK_FREE**)。 在免費或重新配置，`pvData`具有使用者文件即將要釋放的區塊的指標。 不過針對配置中，此指標為 null，因為配置尚未發生。 其餘的引數包含配置的大小，其區塊型別，循序要求相關聯的編號，且檔案名稱的指標。 如果有的話，則引也會包含執行配置時的行號。 攔截函式會執行任何分析或其他工作作者所要求之後，它必須傳回**真**，表示配置操作可以繼續進行，或**FALSE**，這表示，作業應該會失敗。 這種類型的簡單攔截可能會檢查截至目前為止，配置的記憶體數量，並傳回**FALSE**數量超過小型限制。 然後應用程式會經歷只有在可用記憶體非常低時才會發生的配置錯誤。 更複雜的攔截可能會追蹤配置模式、分析記憶體使用或在特定情況發生時報告。  
  
## <a name="see-also"></a>另請參閱  
 [配置攔截和 C 執行階段記憶體配置](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [撰寫偵錯攔截函式](../debugger/debug-hook-function-writing.md)   
