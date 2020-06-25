---
title: 分析 .NET Core 專案的資料庫使用量 |Microsoft Docs
ms.date: 5/5/2020
ms.topic: conceptual
helpviewer_keywords:
- database, profiling
author: esteban-herrera
ms.author: esherrer
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: b369fe6998cd7ef134af765d6d849f41bc93527c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290193"
---
# <a name="analyze-database-performance-using-the-database-tool"></a>使用資料庫工具分析資料庫效能

使用資料庫工具，記錄您的應用程式在診斷會話期間所進行的資料庫查詢。 接著，您可以分析個別查詢的相關資訊，以找出可改善應用程式效能的位置。

> [!NOTE]
> 資料庫工具需要 Visual Studio 2019 16.3 版或更新版本，以及在 Windows 上使用[ADO.NET]( https://docs.microsoft.com/dotnet/framework/data/adonet/ado-net-overview)或[Entity Framework Core](https://docs.microsoft.com/ef/core/)的 .net Core 專案。

## <a name="setup"></a>安裝程式

1. 選取 [ **Alt + F2** ] 以在 Visual Studio 中開啟效能分析工具。

1. 選取 [**資料庫**] 核取方塊。

   ![已選取資料庫工具](./media/db-launch.png "已選取資料庫工具")

   > [!NOTE]
   > 如果無法選取此工具，請清除每個其他工具的核取方塊，因為某些工具必須單獨執行。 若要深入瞭解如何一起執行工具，請參閱[從命令列使用程式碼剖析工具](../profiling/using-the-profiling-tools-from-the-command-line.md)。
   >
   > 如果此工具仍然無法使用，請檢查您的專案是否符合上述需求。 請確定您的專案處於發行模式，以捕捉最精確的資料。

1. 選取 [**開始**] 按鈕以執行工具。

1. 工具開始執行之後，請完成您想要在應用程式中分析的案例。 然後選取 [**停止收集**] 或關閉您的應用程式，以查看您的資料。

1. 收集停止之後，您會看到在分析會話期間執行之查詢的資料表。

   ![資料庫工具已停止](./media/db-after.png "資料庫工具已停止")

查詢會依序排列，但您可以依任何資料行進行排序。 您可以用滑鼠右鍵按一下資料行標題，以顯示更多資料行。 選取 [**持續時間**] 資料行會將查詢從最長持續到最短的順序排序。

找到您想要調查的查詢之後，請以滑鼠右鍵按一下查詢。 然後選取 [**移至原始**程式檔]，以查看該查詢有哪些代碼負責。

![移至選取的來源檔案](./media/db-gotosource.png "移至選取的來源檔案")

如果您選取圖形上的時間範圍，則查詢資料表只會顯示在該時間範圍內發生的查詢。 當您同時執行 [ [CPU 使用量] 工具](https://docs.microsoft.com/visualstudio/profiling/cpu-usage?view=vs-2019)時，此行為特別有用。

## <a name="see-also"></a>另請參閱

- [優化 Profiler 設定](../profiling/optimize-profiler-settings.md)
