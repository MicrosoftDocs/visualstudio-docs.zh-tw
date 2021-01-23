---
title: 同時使用多個分析工具 |Microsoft Docs
description: 瞭解效能分析工具如何設計為可在相同的會話中使用多個工具，以協助瞭解效能問題。
ms.date: 4/29/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, multiple tools
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 5a4c4658282f15b6b34562e51be94d9f2be195a8
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721173"
---
# <a name="using-multiple-profiler-tools-simultaneously"></a>同時使用多個分析工具

效能分析工具的概念是，您可以在相同的會話中使用多個工具，以協助瞭解效能問題。 效能分析工具中的大部分工具都支援並存執行，例如 [CPU 使用率](../profiling/cpu-usage.md)、 [.NET Async 工具](../profiling/analyze-async.md)和 [資料庫](../profiling/analyze-database.md) 工具。 若要同時在相同的診斷會話中執行工具，請按一下其旁邊的核取方塊，然後開始診斷會話。

![已選取診斷中樞所有工具](../profiling/media/diaghuballtoolsselected.png "已選取診斷中樞所有工具")

>[!NOTE]
>某些工具（例如 [.Net 物件配置](../profiling/dotnet-alloc-tool.md) 工具）無法與其他工具搭配使用，因為它們的負荷很高，或因其他技術限制而無法執行。

## <a name="time-filtering"></a>時間篩選 

在分析期間，會跨工具套用時間篩選作業，讓您可以使用一項工具中的資訊來縮小時間範圍，並在另一個工具中篩選資料。 這項功能有助於引導分析追蹤中的特定點，並協助您瞭解應用程式的狀態。

![診斷中樞時間篩選](../profiling/media/diaghubtimefiltering.png "診斷中樞時間篩選")

## <a name="see-also"></a>另請參閱

- [優化 profiler 設定](../profiling/optimize-profiler-settings.md)
- [使用或不使用偵錯工具來執行程式碼剖析工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [了解效能收集方法](../profiling/understanding-performance-collection-methods-perf-profiler.md)
