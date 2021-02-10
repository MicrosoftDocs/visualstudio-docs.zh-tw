---
title: 服務的命令列分析 | Microsoft Docs
description: 瞭解如何從命令列流量分析工具來收集 Windows 服務的效能資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling toos,services
- profiling services
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dd77161184c5cb8be89ed522bbf06b6d80ca4bee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969499"
---
# <a name="command-line-profiling-of-services"></a>服務的命令列分析
本節說明從命令列使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具收集 Windows 服務之效能資料的程序和選項。

> [!NOTE]
> Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 UWP App 也需要新的收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。

## <a name="common-tasks"></a>常見工作

| Task | 相關內容 |
| - | - |
| **收集應用程式統計資料：** 使用取樣方法收集效能統計資料。 取樣資料可用來分析 CPU 使用率的問題，以及了解應用程式的一般效能特性。 | -   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) |
| **收集詳細計時資料：** 使用檢測方法收集詳細的計時資訊。 檢測資料可用來分析 IO 問題，並且適用於更細緻的應用程式案例分析。 | -   [使用檢測設備收集詳細計時資料](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md) |
| **收集 .NET 記憶體資料︰** 使用取樣或檢測收集 .NET 記憶體配置資料，顯示配置物件的大小和數目。 您也可以收集物件存留期資料，顯示每個記憶體回收層代中回收的物件大小和數目。 | -   [收集 .NET 記憶體資料](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md) |
| **收集並行資料：** 使用並行方法收集資源爭用資料和執行緒活動資料，以顯示 CPU 使用率、執行緒爭用、執行緒遷移、同步處理延遲、重迭 IO 區域和其他系統事件。 | -   [收集並行資料](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md) |
| **加入階層互動資料︰** 您可以新增服務對 Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] 資料庫之同步 ADO.NET 呼叫的相關效能資料。 | -   [收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>相關工作

|Task|相關內容|
|----------|---------------------|
|**分析獨立 (用戶端) 應用程式**|-   [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**分析 ASP.NET 應用程式**|-   [分析 ASP.NET web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
