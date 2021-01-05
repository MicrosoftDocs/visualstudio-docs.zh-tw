---
title: 配置攔截和 C 執行階段記憶體配置
description: 在 Visual Studio 的調試中瞭解配置攔截和 C 執行時間記憶體配置。 配置攔截函式必須明確地忽略 _CRT_BLOCK 區塊。
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
ms.openlocfilehash: f2c9225281952700b118f13b20a11f7619307b8e
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729167"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>配置攔截和 C 執行階段記憶體配置
配置攔截函式的一個非常重要的限制是它們必須明確地忽略 `_CRT_BLOCK` 區塊。 這些區塊是由 C 執行時間程式庫函式在內部進行的記憶體配置，如果它們對任何配置內部儲存體的 C 執行時間程式庫函式進行呼叫。 您可以 `_CRT_BLOCK` 在配置攔截函式的開頭包含下列程式碼，以忽略區塊：

```cpp
if ( nBlockUse == _CRT_BLOCK )
    return( TRUE );
```

如果您的配置攔截不會忽略 `_CRT_BLOCK` 區塊，則在攔截中呼叫的任何 C 執行時間程式庫函式可能會在無限迴圈中攔截程式。 例如，`printf` 會執行內部配置。 如果攔截程式碼呼叫 `printf`，那麼產生的配置會導致再次呼叫攔截，來再次呼叫 **printf**，直到堆疊溢位為止。 如果您要報告 `_CRT_BLOCK` 配置操作，避開這種限制的一種方法是使用 Windows API 函式，而不是執行階段函式來執行格式化和輸出。 因為 Windows Api 不會使用 C 執行時間程式庫堆積，所以不會在無限迴圈中攔截配置攔截。

如果檢查執行階段程式庫原始程式檔，您會看到預設的 **CrtDefaultAllocHook** 配置攔截函式 (只簡單傳回 **TRUE**) 位於本身不同的 DBGHOOK.C 檔案內。 如果您要針對在應用程式 **main** 函式前執行之執行階段起始程式碼的配置進行呼叫配置攔截，則您可以使用自己的攔截而不使用 [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) 來取代這個預設函式。

## <a name="see-also"></a>請參閱
- [調試攔截函式寫入](../debugger/debug-hook-function-writing.md)
