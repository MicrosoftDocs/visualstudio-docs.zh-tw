---
title: 同時使用多個 profiler 工具 |Microsoft Docs
ms.date: 4/29/2020
ms.topic: conceptual
helpviewer_keywords:
- Profiler, multiple tools
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 7844d81af02211d1c9f4e444c6367152e73392e9
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290182"
---
# <a name="using-multiple-profiler-tools-simultaneously"></a>同時使用多個 profiler 工具

「效能分析工具」的設計概念是可以在相同的會話中使用多個工具，以協助瞭解效能問題。 效能分析工具中大部分的工具支援並存執行，例如[CPU 使用量](../profiling/cpu-usage.md)、 [.net 非同步工具](../profiling/analyze-async.md)和[資料庫](../profiling/analyze-database.md)工具。 若要同時在相同的診斷會話中執行工具，請按一下其旁邊的核取方塊，然後啟動診斷會話。

![診斷中樞已選取所有工具](../profiling/media/diaghuballtoolsselected.png "診斷中樞已選取所有工具")

>[!NOTE]
>某些工具（例如[.Net 物件配置](../profiling/dotnet-alloc-tool.md)工具）無法與其他工具一起執行，因為它們的負荷較高，或因為其他技術限制。

## <a name="time-filtering"></a>時間篩選 

在分析期間，時間篩選作業會跨工具套用，因此您可以使用一種工具中的資訊來縮小時間範圍，並在另一個工具中篩選資料。 這項功能有助於引導分析追蹤中的特定點，並協助您瞭解應用程式的狀態。

![診斷中樞時間篩選](../profiling/media/diaghubtimefiltering.png "診斷中樞時間篩選")

## <a name="see-also"></a>另請參閱

- [優化 profiler 設定](../profiling/optimize-profiler-settings.md)
- [使用或不使用偵錯工具來執行分析工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [了解效能收集方法](../profiling/understanding-performance-collection-methods-perf-profiler.md)
