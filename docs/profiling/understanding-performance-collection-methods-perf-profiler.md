---
title: 了解效能收集方法 | Microsoft Docs
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords: ''
helpviewer_keywords:
- Performance Profiler, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2017'
ms.workload:
- multiple
ms.openlocfilehash: 03a49763a682f6b98b02fe40ba957efa8f5483c8
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290183"
---
# <a name="understand-performance-collection-methods"></a>了解效能收集方法

本檔概述 Visual Studio 的效能分析工具中的工具所使用的資料收集方法。 

## <a name="sampling"></a>取樣

分析的取樣方法會收集應用程式在分析執行期間所執行之工作的相關統計資料。 資料收集的完成方式是定期收集應用程式的資訊或取樣頻率（例如每毫秒），然後分析此資料，以建立在應用程式中花費時間的模型。 取樣方法很輕量，而且對正在分析的應用程式執行沒有太大的影響。 效能分析工具中利用取樣方法的工具組括 [ [CPU 使用量](../profiling/cpu-usage.md)] 工具。

## <a name="instrumentation"></a>測試設備

檢測分析會收集應用程式在分析執行期間所執行之工作的詳細資訊。 資料收集是藉由將程式碼插入二進位檔案中的工具來完成，此檔案會在應用程式執行時，使用回呼勾點來收集和發出精確的計時和呼叫計數資訊。 相較于以取樣為基礎的方法，檢測方法會有高額外負荷。 效能分析工具中使用檢測的工具組含[.Net 物件配置](../profiling/dotnet-alloc-tool.md)工具。