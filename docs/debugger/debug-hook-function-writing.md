---
title: 調試攔截函式寫入 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350715"
---
# <a name="debug-hook-function-writing"></a>撰寫偵錯攔截函式
本節將說明一些您可以撰寫的自訂偵錯攔截函式，這些函式可讓您將程式碼插入偵錯工具正常處理中的某些預先定義點。

## <a name="in-this-section"></a>本節內容
 [用戶端區塊攔截](../debugger/client-block-hook-functions.md) 函式提供撰寫函數的指引和原型，這些函式會驗證或報告儲存在 _CLIENT_BLOCK 區塊中的資料內容。

 [配置](../debugger/allocation-hook-functions.md) 攔截函式定義配置攔截函式、探索其不同的用法、指出限制，並提供原型。

 [配置攔截和 CRT 記憶體配置](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md) 描述 `_CRT_BLOCK` 當配置攔截函式對任何配置內部儲存體的 C 執行時間程式庫函式進行呼叫時，會明確忽略區塊的限制。 這個主題也列出如果配置攔截沒有忽略 `_CRT_BLOCK` 區塊的後果 (附範例)，以及如何變更預設配置攔截函式 **CrtDefaultAllocHook**。

 [報表](../debugger/report-hook-functions.md) 攔截函式討論 `_CrtSetReportHook` ，您可以用它來篩選報表，以專注于特定類型的配置。 這個主題也提供原型。

## <a name="related-sections"></a>相關章節

- [CRT 偵錯工具技術](../debugger/crt-debugging-techniques.md) ： C 執行時間程式庫之偵錯工具的連結，包括使用 CRT Debug 程式庫、用於報告的宏、和之間的差異 `malloc` 、撰寫 Debug 攔截函式 `_malloc_dbg` ，以及 CRT Debug 堆積。