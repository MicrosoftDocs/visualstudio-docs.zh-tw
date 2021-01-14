---
title: 分析記憶體使用量
description: 瞭解您可以用來找出記憶體流失和沒有效率的記憶體使用量的工具，例如記憶體使用量工具和 .NET 物件組態工具。
ms.custom: SEO-VS-2020, seodec18
ms.date: 10/12/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 675636b7abca10fb2f9f1898d753155235830f86
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205719"
---
# <a name="analyze-memory-usage"></a>分析記憶體使用量

若要找出記憶體流失和沒有效率的記憶體使用量，您可以使用工具（例如偵錯工具整合的記憶體使用量診斷工具或效能分析工具中的工具，例如 .NET 物件組態工具和事後剖析後的記憶體使用量工具）。

記憶體使用量工具可讓您擷取 Managed 和原生記憶體堆積的一個或多個 *「快照」* (Snapshot)。 您可以 ( .NET 和原生) 應用程式收集 .NET、ASP.NET、c + + 或混合模式的快照。 **記憶體使用量** 工具可以在開啟的 Visual Studio 專案上、已安裝的 Microsoft Store 應用程式上執行，或附加至執行中的應用程式或進程。 您可以執行 [ **記憶體使用量** ] 工具（不論是否有調試）。 如需詳細資訊，請參閱 [使用或不使用偵錯工具來執行程式碼剖析工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)。 在偵錯工具中，您可以開啟和關閉記憶體分析，並查看每個物件的記憶體使用量細目。 您可以在暫停執行時查看記憶體使用量結果，例如在中斷點上。

.NET 開發人員可以選擇 .NET 物件組態工具或 [ [記憶體使用量](../profiling/memory-usage.md) ] 工具。

- [.Net 物件組態工具](../profiling/dotnet-alloc-tool.md)可協助您識別 .net 程式碼中的配置模式和異常，並協助找出垃圾收集的常見問題。 此工具只會以事後剖析後工具的形式執行。 您可以在本機或遠端電腦上執行此工具。
- [記憶體使用量工具](../profiling/memory-usage-without-debugging2.md)很適合用來識別記憶體流失，通常在 .net 應用程式中並不常見。 如果您在檢查記憶體時需要使用偵錯工具功能，例如逐步執行程式碼，則建議使用 [偵錯工具整合的記憶體使用量](../profiling/memory-usage.md) 工具。

C + + 開發人員可以使用偵錯工具整合式或非偵錯工具記憶體使用量工具。

- [使用偵錯工具分析記憶體使用量](../profiling/memory-usage.md)
- [分析記憶體使用量 (不使用偵錯工具)](../profiling/memory-usage-without-debugging2.md)

您可以在 Windows 7 及更新版本使用不具偵錯工具的分析工具。 Windows 8 及更新版本必須執行附有偵錯工具的分析工具 ([診斷工具] 視窗)。

## <a name="blogs-and-videos"></a>部落格和影片

[在調試時分析 CPU 與記憶體](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ blog： Visual C++ 2015 中的記憶體分析](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>請參閱

- [Visual Studio 中的分析](../profiling/index.yml)
- [初步認識分析工具](../profiling/profiling-feature-tour.md)
