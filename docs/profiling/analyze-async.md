---
title: 分析 .NET 非同步程式碼的效能 |Microsoft Docs
description: 使用 .NET Async 工具來分析非同步程式碼的效能。 列出每個工作的時間。 若要查看程式碼，請使用 [移至原始程式檔]。
ms.custom: SEO-VS-2020
ms.date: 5/5/2020
ms.topic: conceptual
helpviewer_keywords:
- asynchronous, async, profiling
author: esteban-herrera
ms.author: esherrer
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 86575cd71c41ac8ac874e9b62f8273ee46e02c57
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205485"
---
# <a name="analyze-performance-of-net-asynchronous-code"></a>分析 .NET 非同步程式碼的效能

使用 .NET Async 工具來分析應用程式中非同步程式碼的效能。

> [!NOTE]
> .NET Async 工具需要 Visual Studio 2019 16.7 版或更新版本，以及使用 **Async** 和 **await** 的 .net 專案。

## <a name="setup"></a>安裝程式

1. 選取 **Alt + F2** 以開啟 Visual Studio 中的效能分析工具。

1. 選取 [ **.NET Async** ] 核取方塊。

   ![已選取 .NET Async 工具](../profiling/media/async-tool-selected.png "已選取 .NET Async 工具")

1. 按一下 [ **開始** ] 按鈕以執行工具。

1. 工具開始執行之後，請完成您想要在應用程式中進行分析的案例。 然後選取 [ **停止收集** ] 或關閉應用程式以查看您的資料。

1. 收集停止之後，您會看到程式碼剖析會話期間發生的活動資料表。

   ![.NET Async 工具已停止](../profiling/media/async-tool-opened.png ".NET Async 工具已停止")

非同步事件會依時間順序組織成活動。 每個都會顯示其開始時間、結束時間和持續時間。

對應至工作的每個資料 [列都會標示](/dotnet/api/system.threading.tasks) 于 [ **名稱** ] 資料行中。 針對無法解析的任何工作名稱，會顯示 [標籤] **中** 的工作。 後面接著工作發生的方法名稱。 如果非同步活動未在收集會話內完成，則 [**結束時間**] 資料行中會出現 **不完整** 的標籤。

若要進一步調查特定的工作或活動，請在資料列上按一下滑鼠右鍵。 然後選取 [ **移至原始** 程式檔]，以查看程式碼中活動發生的位置。

![.NET Async 已選取 [移至原始檔] 檔案的工具](../profiling/media/async-tool-gotosource.png ".NET Async 已選取 [移至原始檔] 檔案的工具")

## <a name="see-also"></a>請參閱

- [優化 Profiler 設定](../profiling/optimize-profiler-settings.md)