---
title: .NET 記憶體資料檢視 | Microsoft Docs
description: 請參閱包含 .NET 記憶體程式碼剖析資料的程式碼剖析工具資料檔案之視圖和報表的參考資訊連結。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method views
- profiling tools,.NET memory profiling views
ms.assetid: 79184d8e-769b-4ace-be2b-521147772081
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8a4a6143127a2e55bf5c13cf6606bfe00de5cd9e
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801270"
---
# <a name="net-memory-data-views"></a>.NET 記憶體資料檢視
本節包含程式碼剖析工具資料檔案的檢視與報告，而此檔案含有 .NET 記憶體程式碼剖析資料。

## <a name="in-this-section"></a>本節內容
- [摘要檢視](../profiling/summary-view-dotnet-memory-data.md)

 列出配置最多記憶體的函式和型別。

- [配置檢視](../profiling/dotnet-memory-allocations-view.md)

 列出在程式碼剖析執行中配置的型別，以及產生型別之配置的呼叫樹狀圖 (執行路徑)。

- [物件存留期檢視](../profiling/object-lifetime-view.md)

 列出在程式碼剖析執行中配置的型別、執行個體數目、大小 (位元組) 和型別的記憶體回收層代。

- [呼叫樹狀檢視 - 取樣](../profiling/call-tree-view-dotnet-memory-sampling-data.md)

 顯示階層式樹狀圖，表示程式碼剖析執行中函式的執行路徑和記憶體配置資料。

- [模組視圖-取樣](../profiling/modules-view-dotnet-memory-sampling-data.md)

 依模組組織 .NET 記憶體配置資料，並列出配置記憶體時正在執行的函式、原始程式碼行及指令。

- [呼叫端/被呼叫端視圖-.NET 記憶體取樣資料](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)

 列出所選函式的記憶體配置資料、呼叫所選函式的函式，以及所選函式呼叫的函式。

- [函式檢視 - 取樣](../profiling/functions-view-dotnet-memory-sampling-data.md)

 列出程式碼剖析執行中函式的記憶體配置資料。

- [程式行檢視 - 取樣](../profiling/lines-view-dotnet-memory-sampling-data.md)

 列出程式碼剖析執行中函式的原始程式碼行的記憶體配置資料。

- [指令指標 (IP) 檢視 - 取樣](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)

 列出程式碼剖析執行中函式指令的記憶體配置資料。

- [呼叫樹狀檢視 - 檢測設備](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)

 顯示階層式樹狀圖，表示程式碼剖析執行中檢測的函式的執行路徑、記憶體配置資料及詳細的計時資料。

- [模組檢視 - 檢測設備](../profiling/modules-view-dotnet-memory-instrumentation-data.md)

 依模組組織程式碼剖析資料，並列出模組的函式、記憶體配置資料及詳細的計時資訊。

- [呼叫端/被呼叫端視圖-.NET 記憶體檢測資料](../profiling/caller-callee-view-net-memory-instrumentation-data.md)

 列出所選檢測函式的記憶體配置資料和詳細計時資訊、呼叫所選函式的函式，以及所選函式呼叫的函式。

- [函式檢視 - 檢測](../profiling/functions-view-dotnet-memory-instrumentation-data.md)

 列出程式碼剖析執行中檢測的函式的記憶體配置資料。

## <a name="reference"></a>參考
- [函式詳細資料檢視](../profiling/function-details-view.md)

 顯示選取的函式及所呼叫函式 (由該所選函式呼叫的函式) 之間關聯性的圖形化圖表。

- [處理序檢視](../profiling/process-view.md)

 列出處理序和執行緒開始和結束時間。

- [標記檢視](../profiling/marks-view.md)

 列出已插入程式碼剖析資料檔中的 ETW 和取樣事件。

## <a name="related-sections"></a>相關章節
- [取樣方法資料檢視](../profiling/profiler-sampling-method-data-views.md)

 使用取樣方法所產生的程式碼剖析工具資料檔案之檢視和報告的參考資訊。

- [檢測方法資料檢視](../profiling/instrumentation-method-data-views.md)

 使用檢測方法所產生的程式碼剖析工具資料檔案之檢視和報告的參考資訊。
