---
title: 正在寫入的調試攔截函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 038c976380ff1e1f0a1a7c4c150fc462f6b1d1db
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350715"
---
# <a name="debug-hook-function-writing"></a>撰寫偵錯攔截函式
本節將說明一些您可以撰寫的自訂偵錯攔截函式，這些函式可讓您將程式碼插入偵錯工具正常處理中的某些預先定義點。

## <a name="in-this-section"></a>本節內容
 [用戶端區塊攔截](../debugger/client-block-hook-functions.md)函式提供指導方針和原型，用於撰寫可驗證或報告 _CLIENT_BLOCK 區塊中所儲存之資料內容的函式。

 [配置](../debugger/allocation-hook-functions.md)攔截函式定義配置攔截函式、探索其不同的使用、指出限制，並提供原型。

 [配置攔截和 CRT 記憶體配置](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)描述在對 `_CRT_BLOCK` 配置內部儲存體的 C 執行時間程式庫函式進行任何呼叫時，明確忽略區塊之配置攔截功能的限制。 這個主題也列出如果配置攔截沒有忽略 `_CRT_BLOCK` 區塊的後果 (附範例)，以及如何變更預設配置攔截函式 **CrtDefaultAllocHook**。

 [報告](../debugger/report-hook-functions.md)攔截函式討論 `_CrtSetReportHook` ，您可以使用它來篩選報表，以專注于特定類型的配置。 這個主題也提供原型。

## <a name="related-sections"></a>相關章節

- [CRT 偵錯工具技術](../debugger/crt-debugging-techniques.md)-C 執行時間程式庫的偵錯工具技術連結，包括使用 CRT Debug 程式庫、用於報告的宏、和之間的差異、撰寫偵錯工具攔截函式 `malloc` `_malloc_dbg` ，以及 CRT 偵錯工具堆積。