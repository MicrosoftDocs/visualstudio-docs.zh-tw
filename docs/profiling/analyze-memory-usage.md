---
title: 分析記憶體使用量
ms.custom: seodec18
ms.date: 01/02/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ddb082bf2451759be239d5c16404e82bcd84733
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578156"
---
# <a name="analyze-memory-usage"></a>分析記憶體使用量

若要找出記憶體流失和記憶體使用量不佳的情況，您可以使用工具，例如 [偵錯工具整合的記憶體使用量] 診斷工具，或 [效能分析工具] 中的工具，例如 [.NET 物件配置] 工具和 [事後剖析後的記憶體使用量] 工具。 記憶體使用量工具可讓您擷取 Managed 和原生記憶體堆積的一個或多個 *「快照」* (Snapshot)。 您可以收集 .NET、ASP.NET、原生或混合模式 (.NET 和原生) 應用程式的快照。 

[**記憶體使用量**] 工具可以在開啟的 Visual Studio 專案、已安裝的 Microsoft Store 應用程式上執行，或附加至執行中的應用程式或進程。 您可以在本機或遠端電腦上，或在模擬器 (Simulator 或 Emulator) 中執行工具。 如需詳細資訊，請參閱[使用或不使用偵錯工具來執行分析工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)。

您可以執行**記憶體使用量**工具，並搭配或不使用調試。 在偵錯工具中，您可以開啟和關閉記憶體分析，並查看每個物件的記憶體使用量細目。 您可以在執行暫停時查看記憶體使用量結果，例如在中斷點上。

**.Net 物件配置**工具只會以事後剖析後工具的形式執行。

如需描述如何使用記憶體分析工具的詳細指示，請參閱[分析記憶體使用量](../profiling/memory-usage.md)教學課程和[.net 物件組態工具](../profiling/dotnet-alloc-tool.md)。

您可以在 Windows 7 及更新版本使用不具偵錯工具的分析工具。 Windows 8 及更新版本必須執行附有偵錯工具的分析工具 ([診斷工具] 視窗)。

## <a name="blogs-and-videos"></a>部落格和影片

[偵錯時分析 CPU 與記憶體](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ 部落格：Visual C++ 2015 中的記憶體分析](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的分析](../profiling/index.yml)
- [初步認識分析工具](../profiling/profiling-feature-tour.md)
- [不使用偵錯工具分析記憶體使用量](../profiling/memory-usage-without-debugging2.md)
