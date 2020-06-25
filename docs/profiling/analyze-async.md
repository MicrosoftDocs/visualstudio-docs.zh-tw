---
title: 分析 .NET 非同步程式碼的效能 |Microsoft Docs
ms.date: 5/5/2020
ms.topic: conceptual
helpviewer_keywords:
- asynchronous, async, profiling
author: esteban-herrera
ms.author: esherrer
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 49091ba472637d480c04c39f0170c2aee00595d2
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290194"
---
# <a name="analyze-performance-of-net-asynchronous-code"></a>分析 .NET 非同步程式碼的效能

使用 .NET Async 工具來分析應用程式中非同步程式碼的效能。

> [!NOTE]
> .NET Async 工具需要 Visual Studio 2019 16.7 版或更新版本，以及使用**Async**和**await**的 .net 專案。

## <a name="setup"></a>安裝程式

1. 選取 [ **Alt + F2** ] 以在 Visual Studio 中開啟效能分析工具。

1. 選取 [ **.Net 非同步**] 核取方塊。

   ![已選取 .NET Async 工具](../profiling/media/async-tool-selected.png "已選取 .NET Async 工具")

1. 按一下 [**啟動**] 按鈕以執行工具。

1. 工具開始執行之後，請完成您想要在應用程式中分析的案例。 然後選取 [**停止收集**] 或關閉您的應用程式，以查看您的資料。

1. 收集停止後，您會看到在分析會話期間發生的活動資料表。

   ![.NET Async 工具已停止](../profiling/media/async-tool-opened.png ".NET Async 工具已停止")

非同步事件會依序排列到活動中。 每個都會顯示其開始時間、結束時間和持續時間。

對應至工作的每個資料[列都會標記](https://docs.microsoft.com/dotnet/api/system.threading.tasks)在 [**名稱**] 資料行中。 針對無法解析的任何工作名稱，會出現 [標籤]**中**的工作。 後面接著工作發生的方法名稱。 如果非同步活動未在集合會話中完成，[**結束時間**] 資料行中就會出現 [**不完整**] 標籤。

若要進一步調查特定的工作或活動，請以滑鼠右鍵按一下該資料列。 然後選取 [**移至原始**程式檔]，以查看您的程式碼中活動的發生位置。

![已選取 [移至原始檔] 檔案的 .NET 非同步工具](../profiling/media/async-tool-gotosource.png "已選取 [移至原始檔] 檔案的 .NET 非同步工具")

## <a name="see-also"></a>另請參閱

- [優化 Profiler 設定](../profiling/optimize-profiler-settings.md)
