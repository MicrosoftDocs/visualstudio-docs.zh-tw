---
title: 配置攔截和 C 執行階段記憶體配置 |Microsoft Docs
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
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f7f81abd82857b3d9ed2161a6923a79b614bf5a
ms.sourcegitcommit: 0342f99120fbd603b8f06f7e9166c39f2896827a
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742397"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>配置攔截和 C 執行階段記憶體配置
配置攔截函式非常重要的限制是，必須明確地忽略`_CRT_BLOCK`區塊。 這些區塊是由 C 執行階段程式庫函式內部做，如果它們呼叫任何配置內部記憶體的 C 執行階段程式庫函式的記憶體配置。 您可以忽略`_CRT_BLOCK`所配置的開頭將下列程式碼區塊攔截函式：

```cpp
if ( nBlockUse == _CRT_BLOCK )
    return( TRUE );
```

如果配置攔截沒有忽略`_CRT_BLOCK`區塊，那麼攔截任何 C 執行階段程式庫函式可以捕捉無窮迴圈裡的程式。 例如，`printf` 會執行內部配置。 如果攔截程式碼呼叫 `printf`，那麼產生的配置會導致再次呼叫攔截，來再次呼叫 **printf**，直到堆疊溢位為止。 如果您要報告 `_CRT_BLOCK` 配置操作，避開這種限制的一種方法是使用 Windows API 函式，而不是執行階段函式來執行格式化和輸出。 Windows Api 不使用 C 執行階段程式庫堆積，因為它們不會捕捉配置攔截永無止盡的迴圈中。

如果檢查執行階段程式庫原始程式檔，您會看到預設的 **CrtDefaultAllocHook** 配置攔截函式 (只簡單傳回 **TRUE**) 位於本身不同的 DBGHOOK.C 檔案內。 如果您要針對在應用程式 **main** 函式前執行之執行階段起始程式碼的配置進行呼叫配置攔截，則您可以使用自己的攔截而不使用 [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) 來取代這個預設函式。

## <a name="see-also"></a>請參閱
[撰寫偵錯攔截函式](../debugger/debug-hook-function-writing.md)
