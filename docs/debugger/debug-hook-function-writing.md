---
title: 撰寫偵錯攔截函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], CRT debug support
- debug hook functions
- hooks, debug
- hooks
- debugging [CRT], debug hook functions
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82145d39adc519bfd1324cc36805cea7b97b1664
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628919"
---
# <a name="debug-hook-function-writing"></a>撰寫偵錯攔截函式
本節將說明一些您可以撰寫的自訂偵錯攔截函式，這些函式可讓您將程式碼插入偵錯工具正常處理中的某些預先定義點。

## <a name="in-this-section"></a>本節內容
 [用戶端區塊攔截函式](../debugger/client-block-hook-functions.md)提供指引和原型中撰寫驗證或報告的資料儲存於 _CLIENT_BLOCK 區塊內容的函式。

 [配置攔截函式](../debugger/allocation-hook-functions.md)定義配置攔截函式、 探索其不同用法、 指出限制，和提供原型。

 [配置攔截和 CRT 記憶體配置](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)描述限制在配置攔截函式，明確忽略`_CRT_BLOCK`封鎖如果它們呼叫任何配置內部記憶體的 C 執行階段程式庫函式。 這個主題也列出如果配置攔截沒有忽略 `_CRT_BLOCK` 區塊的後果 (附範例)，以及如何變更預設配置攔截函式 **CrtDefaultAllocHook**。

 [報告攔截函式](../debugger/report-hook-functions.md)討論`_CrtSetReportHook`，可用來篩選報告以專注於特定類型的配置。 這個主題也提供原型。

## <a name="related-sections"></a>相關章節

- [CRT 偵錯技術](../debugger/crt-debugging-techniques.md)-若要偵錯技術的 C 執行階段程式庫，包括使用 CRT 偵錯程式庫、 報告巨集、 連結之間的差異`malloc`和`_malloc_dbg`，撰寫偵錯攔截函式和 CRT偵錯堆積。