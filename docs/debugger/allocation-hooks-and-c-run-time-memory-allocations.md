---
title: 配置攔截和 C 執行時間記憶體配置 |Microsoft Docs
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
ms.openlocfilehash: 79e55ec521de098a7ae0339c4460502dde3d482d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745790"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>配置攔截和 C 執行階段記憶體配置
對配置攔截函式而言，非常重要的限制是必須明確忽略 `_CRT_BLOCK` 組塊。 這些區塊是 C 執行時間程式庫函式內部所進行的記憶體配置，如果它們對 C 執行時間程式庫函式進行呼叫，而這些函式會配置內部記憶體。 您可以在配置攔截函式的開頭包含下列程式碼，以忽略 `_CRT_BLOCK` 組塊：

```cpp
if ( nBlockUse == _CRT_BLOCK )
    return( TRUE );
```

如果您的配置攔截不會忽略 `_CRT_BLOCK` 區塊，則在您的掛勾中呼叫的任何 C 執行時間程式庫函式，都可以在無止盡的迴圈中攔截程式。 例如，`printf` 會執行內部配置。 如果攔截程式碼呼叫 `printf`，那麼產生的配置會導致再次呼叫攔截，來再次呼叫 **printf**，直到堆疊溢位為止。 如果您要報告 `_CRT_BLOCK` 配置操作，避開這種限制的一種方法是使用 Windows API 函式，而不是執行階段函式來執行格式化和輸出。 由於 Windows Api 不會使用 C 執行時間程式庫堆積，因此它們不會在無止盡的迴圈中攔截您的配置攔截。

如果檢查執行階段程式庫原始程式檔，您會看到預設的 **CrtDefaultAllocHook** 配置攔截函式 (只簡單傳回 **TRUE**) 位於本身不同的 DBGHOOK.C 檔案內。 如果您要針對在應用程式 **main** 函式前執行之執行階段起始程式碼的配置進行呼叫配置攔截，則您可以使用自己的攔截而不使用 [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) 來取代這個預設函式。

## <a name="see-also"></a>請參閱
- [撰寫偵錯攔截函式](../debugger/debug-hook-function-writing.md)
