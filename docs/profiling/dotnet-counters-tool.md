---
title: 視覺化 dotnet 計數器 |Microsoft Docs
description: 瞭解如何使用 Visual Studio 效能分析工具中的 [.NET 計數器] 工具。
ms.date: 12/7/2020
ms.topic: conceptual
helpviewer_keywords:
- dotnet, counters, profiling
author: sagar-shetty
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 7a09cc073b2886ab0d374bccaf8b85f3bb729dd7
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97905017"
---
# <a name="visualize-dotnet-counters-from-the-visual-studio-profiler"></a>從 Visual Studio profiler 將 dotnet 計數器視覺化


.NET 計數器工具可讓您在 Visual Studio 分析工具內，一段時間內將 [dotnet 計數器](/dotnet/core/diagnostics/dotnet-counters) 視覺化。


> [!NOTE]
> .NET 計數器工具需要 Visual Studio 2019 16.7 版或更新版本，並以 .NET Core 3.0 + 為目標。

## <a name="setup"></a>安裝程式

1. 開啟) 中的效能分析工具 (**Alt + F2** 或 **Debug-> 效能分析工具** Visual Studio。

2. 選取 [ **.Net 計數器** ] 核取方塊。

   :::image type="content" source="../profiling/media/dotnet-counters-tool-selected.png" alt-text="選取的計數器工具。":::

3. 按一下 [ **開始** ] 按鈕以執行工具。

如需如何優化工具效能的詳細資訊，請參閱 [優化 Profiler 設定](../profiling/optimize-profiler-settings.md)。


## <a name="understand-your-data"></a>瞭解您的資料

工具一開始會收集資料，您可以看到 [dotnet 計數器](/dotnet/core/diagnostics/dotnet-counters)的即時值。

:::image type="content" source="../profiling/media/dotnet-counters-tool-collecting.png" alt-text=".NET 計數器工具收集。":::

您也可以選取計數器名稱旁邊的核取方塊，來查看計數器的圖表。 您可以一次顯示多個計數器的圖形。


當您完成應用程式的練習並收集資料之後，您可以停止收集更詳細的報表。 若要這樣做，請按下 [ **停止收集** ] 按鈕。


報表載入後，您應該會看到類似下面所示的完成報表。

:::image type="content" source="../profiling/media/dotnet-counters-tool-report.png" alt-text=".NET 計數器工具報表。":::

報表會顯示下列值：

- 最小值-所選時間範圍內該計數器的最小值。
- 最大值-所選時間範圍內該計數器的最大值。
- 平均-在選取的時間範圍內，該計數器的平均值。

您可以用滑鼠右鍵按一下資料行標題，然後選取標題，以篩選或加入資料表中的資料行。

:::image type="content" source="../profiling/media/dotnet-counters-tool-columns.png" alt-text=".NET 計數器工具資料行。":::

您也可以選取 [計數器] 旁的核取方塊，以查看詳細報表中的圖表。 依預設，資料表中的資料代表所收集追蹤的整個持續時間值。 若要將資料篩選至特定時間範圍，請按一下並拖曳圖形。

:::image type="content" source="../profiling/media/dotnet-counters-tool-time-filtering.png" alt-text=".NET 計數器工具時間篩選。":::

資料表會針對在圖形中選取的時間，更新為相關的值。 使用 [ **清除選取** 範圍] 按鈕，將選取的時間範圍重設為整個追蹤。


## <a name="see-also"></a>另請參閱

- [優化 Profiler 設定](../profiling/optimize-profiler-settings.md)
- [dotnet 計數器](/dotnet/core/diagnostics/dotnet-counters)
