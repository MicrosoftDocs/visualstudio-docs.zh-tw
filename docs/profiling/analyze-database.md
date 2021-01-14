---
title: 分析 .NET Core 專案的資料庫使用量 |Microsoft Docs
description: 使用資料庫工具記錄應用程式的資料庫查詢，然後加以分析，以找出改善效能的方法。
ms.custom: SEO-VS-2020
ms.date: 5/5/2020
ms.topic: conceptual
helpviewer_keywords:
- database, profiling
author: esteban-herrera
ms.author: esherrer
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: a8518e3f43bec3a9d5f696a07613dee84829dbc2
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205459"
---
# <a name="analyze-database-performance-using-the-database-tool"></a>使用資料庫工具分析資料庫效能

使用資料庫工具記錄您的應用程式在診斷會話期間所進行的資料庫查詢。 然後，您可以分析個別查詢的相關資訊，以找出可改善應用程式效能的位置。

> [!NOTE]
> 資料庫工具需要 Visual Studio 2019 16.3 版或更新版本，以及在 Windows 上使用 [ADO.NET]( https://docs.microsoft.com/dotnet/framework/data/adonet/ado-net-overview) 或 [Entity Framework Core](/ef/core/)的 .net Core 專案。

## <a name="setup"></a>安裝程式

1. 選取 **Alt + F2** 以開啟 Visual Studio 中的效能分析工具。

1. 選取 [ **資料庫** ] 核取方塊。

   ![已選取資料庫工具](./media/db-launch.png "已選取資料庫工具")

   > [!NOTE]
   > 如果工具無法供選取，請清除所有其他工具的核取方塊，因為有些工具需要單獨執行。 若要深入瞭解如何一起執行工具，請參閱 [從命令列使用程式碼剖析工具](../profiling/using-the-profiling-tools-from-the-command-line.md)。
   >
   > 如果仍然無法使用此工具，請確認您的專案符合上述需求。 請確定您的專案處於發行模式，以抓取最精確的資料。

1. 選取 [ **開始** ] 按鈕以執行工具。

1. 工具開始執行之後，請完成您想要在應用程式中進行分析的案例。 然後選取 [ **停止收集** ] 或關閉應用程式以查看您的資料。

1. 收集停止之後，您會看到在分析會話期間執行的查詢資料表。

   ![資料庫工具已停止](./media/db-after.png "資料庫工具已停止")

查詢會依時間順序排列，但您可以依任何資料行來排序。 您可以用滑鼠右鍵按一下資料行標題，以顯示更多資料行。 選取 [ **持續時間** ] 資料行會將查詢從最長持續時間排序到最短。

當您找到想要調查的查詢之後，請以滑鼠右鍵按一下查詢。 然後選取 [ **移至原始** 程式檔]，以查看哪些程式碼負責該查詢。

![移至選取的來源檔案](./media/db-gotosource.png "移至選取的來源檔案")

如果您選取圖形上的時間範圍，查詢資料表只會顯示該時間範圍內發生的查詢。 當您也執行 [ [CPU 使用量] 工具](./cpu-usage.md?view=vs-2019&preserve-view=true)時，此行為特別有用。

## <a name="see-also"></a>請參閱

- [優化 Profiler 設定](../profiling/optimize-profiler-settings.md)