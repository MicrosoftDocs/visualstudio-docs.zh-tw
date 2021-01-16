---
title: 獨立應用程式的命令列分析 | Microsoft Docs
description: 瞭解如何從命令列流量分析工具，收集用戶端 (獨立) 應用程式的效能資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profillng tools,stand-alone applications
- profling stand-alone applications
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 876c2a72f0929cffa3613026fa56a17d82786854
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533637"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>獨立應用程式的命令列分析
本節說明從命令列使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具收集獨立 (用戶端) 應用程式之效能資料的程序和選項。

## <a name="common-tasks"></a>常見工作

| 工作 | 相關內容 |
| - | - |
| **收集應用程式統計資料：** 使用取樣方法收集效能統計資料。 取樣資料可用來分析 CPU 使用率的問題，以及了解應用程式的一般效能特性。 | -   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-stand-alone-applications.md) |
| **收集詳細計時資料：** 使用檢測方法收集詳細的計時資訊。 檢測資料可用來分析 I/O 問題，並且適用於更細緻的應用程式案例分析。 | -   [使用檢測設備收集詳細計時資料](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md) |
| **收集 .NET 記憶體資料︰** 使用取樣或檢測收集 .NET 記憶體配置資料，顯示配置物件的大小和數目。 您也可以收集物件存留期資料，顯示每個記憶體回收層代中回收的物件大小和數目。 | -   [收集 .NET Framework 記憶體資料](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md) |
| **收集並行資料：** 使用並行方法收集資源爭用資料和執行緒活動資料，顯示 CPU 使用率、執行緒爭用、執行緒移轉、同步處理延遲、重疊 I/O 區域 和其他系統事件。 | -   [收集並行資料](../profiling/collecting-concurrency-data-for-stand-alone-applications.md) |
| **加入階層互動資料︰** 您可以新增應用程式對 Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] 資料庫之同步 ADO.NET 呼叫的相關效能資料。 若要將階層互動資料加入至程式碼剖析回合中，則需要使用命令列程式碼剖析工具的特定程序。 | -   [收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>相關工作

|Task|相關內容|
|----------|---------------------|
|**分析 ASP.NET 應用程式**|-   [分析 ASP.NET web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
|**分析服務**|-   [設定檔服務](../profiling/command-line-profiling-of-services.md)|
