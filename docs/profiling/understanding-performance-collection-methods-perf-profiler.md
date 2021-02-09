---
title: 瞭解 profiler 效能收集方法
description: 瞭解 Visual Studio 效能分析工具中的工具所使用的資料收集方法。
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords: ''
helpviewer_keywords:
- Performance Profiler, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2017'
ms.workload:
- multiple
ms.openlocfilehash: f9128700f6ad54f3d92108d92e25e13b9ee4266c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921863"
---
# <a name="understand-profiler-performance-collection-methods"></a>瞭解 profiler 效能收集方法

本檔概述 Visual Studio 效能分析工具中的工具所使用的資料收集方法。 

## <a name="sampling"></a>取樣

分析的取樣方法會收集應用程式在分析執行期間所執行之工作的相關統計資料。 資料收集的完成方式是以定期間隔或取樣頻率（例如每毫秒）收集應用程式的資訊，然後分析此資料，以建立在應用程式中花費時間的模型。 取樣方法很輕量，且對所分析之應用程式的執行不會有很大的影響。 使用取樣方法的效能分析工具中的工具組括 [CPU 使用量](../profiling/cpu-usage.md) 工具。

## <a name="instrumentation"></a>測試設備

檢測分析會收集應用程式在分析執行期間所執行之工作的詳細資訊。 資料收集是由工具所完成，這些工具會將程式碼插入至可捕獲計時資訊的二進位檔案，或在應用程式執行時使用回呼勾點來收集和發出確切的計時和呼叫計數資訊。 相較于以取樣為基礎的方法，檢測方法會有很高的負擔。 使用檢測的效能分析工具中的工具組含 [.Net 物件配置](../profiling/dotnet-alloc-tool.md) 工具。