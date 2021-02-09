---
title: Profiler 命令列-取得獨立應用程式並行資料
description: 使用 Visual Studio 中的 profiler 命令列收集獨立應用程式的並行資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 24cd41210628bc507b3666e57f9cdc2abf609a6f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868432"
---
# <a name="collect-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>使用分析工具命令列收集獨立應用程式的並行資料
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具的並行方法可讓您收集資源爭用資料和執行緒活動資料，顯示 CPU 使用率、執行緒爭用、執行緒移轉、同步處理延遲、重疊 IO 區域 和其他系統事件。

## <a name="common-tasks"></a>常見工作

|Task|相關內容|
|----------|---------------------|
|**啟動 .NET Framework 應用程式並分析並行資料**|-   [如何：啟動 .NET Framework 的應用程式以收集並行資料](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)|
|**啟動 C/C++ 應用程式並分析並行資料**|-   [如何：啟動原生應用程式以收集並行資料](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**將分析工具附加至執行中的 .NET Framework 應用程式**|-   [如何：將分析工具附加至 .NET Framework 應用程式以收集並行資料](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)|
|**將分析工具附加至執行中的 C/C++ 應用程式**|-   [如何：將分析工具附加至原生應用程式並收集並行資料](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)|

## <a name="related-tasks"></a>相關工作

### <a name="profile-stand-alone-applications"></a>分析獨立應用程式

|Task|相關內容|
|----------|---------------------|
|**使用取樣方法進行分析**|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**使用檢測方法進行分析**|-   [使用檢測設備收集詳細計時資料](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**分析 .NET 記憶體配置和記憶體回收**|-   [收集 .NET Framework 記憶體資料](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**新增階層互動資料**|-   [收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

### <a name="profile-concurrency-issues"></a>分析並行問題

|Task|相關內容|
|----------|---------------------|
|**分析 ASP.NET 應用程式**|-   [收集並行資料](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|
|**分析服務**|-   [收集並行資料](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>分析並行資料檢視和報表
- [資源爭用資料檢視](../profiling/resource-contention-data-views.md)

- [並行視覺化檢視](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>參考
- [命令列分析工具參考](../profiling/command-line-profiling-tools-reference.md)
