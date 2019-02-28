---
title: 配置攔截函式 |Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd2900544fe2c33cfaaf9d1a0da5d4ff1ac41ab4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616787"
---
# <a name="allocation-hook-functions"></a>配置攔截函式
配置攔截函式，使用安裝[_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook)，每次記憶體配置、 重新配置，或釋出呼叫。 您可以使用這種類型的攔截程序針對許多不同的用途。 使用它來測試應用程式如何處理記憶體不足的情況下，例如檢查配置模式，或記錄配置資訊以供稍後分析。

> [!NOTE]
>  請留意在配置攔截函式中使用 C 執行階段程式庫功能的相關限制，如[配置攔截和 C 執行階段記憶體配置](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)所述。

 配置攔截函式應該有一個原型，如下列範例所示：

```cpp
int YourAllocHook(int nAllocType, void *pvData,
        size_t nSize, int nBlockUse, long lRequest,
        const unsigned char * szFileName, int nLine )
```

 您傳入至 [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) 的指標是在 CRTDBG.H 中定義的 **_CRT_ALLOC_HOOK** 類型：

```cpp
typedef int (__cdecl * _CRT_ALLOC_HOOK)
    (int, void *, size_t, int, long, const unsigned char *, int);
```

 當執行階段程式庫呼叫攔截， *nAllocType*引數會指出哪些配置作業即將成為 (**_HOOK_ALLOC**， **_HOOK_REALLOC**，或 **_HOOK_FREE**)。 在免費或重新配置，`pvData`具有使用者文件即將要釋放的區塊的指標。 不過針對配置中，此指標為 null，因為配置尚未發生。 其餘的引數包含配置的大小，其區塊型別，循序要求相關聯的編號，且檔案名稱的指標。 如果有的話，則引數也會包含執行配置時的行號。 攔截函式在執行任何作者所要求的分析或其他工作之後，必須傳回 **TRUE** (表示配置操作可以繼續) 或 **FALSE** (表示操作應該會失敗)。 這種類型的簡單攔截可能會檢查截至目前為止所配置的記憶體數量，並在總數量超過小型限制時傳回 **FALSE**。 然後應用程式會經歷只有在可用記憶體非常低時才會發生的配置錯誤。 更複雜的攔截可能會追蹤配置模式、分析記憶體使用或在特定情況發生時報告。

## <a name="see-also"></a>請參閱

- [配置攔截和 C 執行階段記憶體配置](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)
- [撰寫偵錯攔截函式](../debugger/debug-hook-function-writing.md)