---
title: 分析記憶體使用量
ms.custom: seodec18
ms.date: 03/30/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21522ba32990a850a388bfcf69ab239232a2c23d
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638417"
---
# <a name="analyze-memory-usage"></a>分析記憶體使用量

要查找記憶體洩漏和記憶體使用效率低下,可以使用諸如調試器集成記憶體使用方式診斷工具或性能探查器中的工具,如 .NET 物件分配工具和事後記憶體使用工具。

記憶體使用量工具可讓您擷取 Managed 和原生記憶體堆積的一個或多個 *「快照」* (Snapshot)。 您可以收集 .NET、ASP.NET、原生或混合模式 (.NET 和原生) 應用程式的快照。 **記憶體使用方式**工具可以在打開的 Visual Studio 專案上、已安裝的 Microsoft 應用商店應用上運行,也可以附加到正在運行的應用或進程。 您可以執行**記憶體使用**工具,無論是否進行除錯。 有關詳細資訊,請參閱[執行具有或不帶除錯器的分析工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)。 在除錯器中,您可以打開和關閉記憶體分析,並查看每個物件的記憶體使用情況細目。 您可以在暫停執行時查看記憶體使用結果,例如在斷點。

**.NET 物件配置**工具可説明您識別 .NET 代碼中的分配模式和異常。 此工具僅作為事後工具運行。 您可以在本地或遠端電腦上執行此工具。

有關描述如何使用記憶體分析工具的詳細說明,請參閱[分析記憶體使用方式](../profiling/memory-usage.md)教學和[.NET 物件配置工具](../profiling/dotnet-alloc-tool.md)。

您可以在 Windows 7 及更新版本使用不具偵錯工具的分析工具。 Windows 8 及更新版本必須執行附有偵錯工具的分析工具 ([診斷工具]**** 視窗)。

## <a name="blogs-and-videos"></a>部落格和影片

[除錯時分析 CPU 和記憶體](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[視覺C++博客:視覺C++ 2015 中的記憶體分析](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的分析](../profiling/index.yml)
- [初步認識分析工具](../profiling/profiling-feature-tour.md)
- [分析記憶體使用量 (不使用偵錯工具)](../profiling/memory-usage-without-debugging2.md)
