---
title: 配置攔截函式 |Microsoft Docs
description: 瞭解如何使用 _CrtSetAllocHook 安裝的配置攔截函式（當您需要執行 C 執行時間 (CRT) Visual Studio 中的調試）時。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3c032ca57e5a046a9f2dd2295226263ffe20f99e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858003"
---
# <a name="allocation-hook-functions"></a>配置攔截函式
配置攔截函式（使用 [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook)安裝）會在每次配置、重新配置或釋放記憶體時呼叫。 您可以將這種類型的攔截用於許多不同的用途。 您可以使用它來測試應用程式如何處理記憶體不足的情況，例如檢查配置模式或記錄配置資訊以供稍後分析。

> [!NOTE]
> 請留意在配置攔截函式中使用 C 執行階段程式庫功能的相關限制，如[配置攔截和 C 執行階段記憶體配置](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)所述。

 配置攔截函式應該具有類似下列範例的原型：

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

 當執行時間程式庫呼叫您的勾點時， *nAllocType* 引數會指出即將進行的配置作業 (**_HOOK_ALLOC**、 **_HOOK_REALLOC** 或 **_HOOK_FREE**) 。 在「免費」或「重新配置」中， `pvData` 具有要釋放之區塊的使用者發行項指標。 但是針對配置，這個指標是 null，因為配置尚未發生。 其餘的引數包含有問題配置的大小、其區塊類型、與其相關聯的順序要求編號，以及檔案名的指標。 如果有的話，引數也會包含進行配置的行號。 攔截函式在執行任何作者所要求的分析或其他工作之後，必須傳回 **TRUE** (表示配置操作可以繼續) 或 **FALSE** (表示操作應該會失敗)。 這種類型的簡單攔截可能會檢查截至目前為止所配置的記憶體數量，並在總數量超過小型限制時傳回 **FALSE**。 然後應用程式會經歷只有在可用記憶體非常低時才會發生的配置錯誤。 更複雜的攔截可能會追蹤配置模式、分析記憶體使用或在特定情況發生時報告。

## <a name="see-also"></a>另請參閱

- [配置攔截和 C Run-Time 記憶體配置](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)
- [調試攔截函式寫入](../debugger/debug-hook-function-writing.md)