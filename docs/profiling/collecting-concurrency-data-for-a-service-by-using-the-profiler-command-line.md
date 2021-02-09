---
title: Profiler 命令列-取得服務的並行資料
description: 使用 Visual Studio 分析工具的並行方法收集資源爭用資料和執行緒活動資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8ae2d3678ec05ce583c9c0b7daf202f3272f4b77
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868448"
---
# <a name="collect-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>使用分析工具命令列收集服務的並行資料
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具的並行方法可讓您收集資源爭用資料和執行緒活動資料，顯示 CPU 使用率、執行緒爭用、執行緒移轉、同步處理延遲、重疊 IO 區域 和其他系統事件。

> [!NOTE]
> Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 UWP App 也需要新的收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。

## <a name="common-tasks"></a>常見工作

|Task|相關內容|
|----------|---------------------|
|**附加至執行中的 .NET 服務**|-   [如何：將分析工具附加至 .NET 服務以收集並行資料](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|
|**新增階層互動資料**|-   [收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**附加至執行中的 C/C++ 服務**|-   [如何：將分析工具附加至原生服務以收集並行資料](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="related-tasks"></a>相關工作

### <a name="profile-windows-services"></a>分析 Windows 服務

|Task|相關內容|
|----------|---------------------|
|**使用取樣方法進行分析**|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|
|**使用檢測方法進行分析**|-   [使用檢測設備收集詳細計時資料](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**分析 .NET 記憶體配置和記憶體回收**|-   [收集 .NET 記憶體資料](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="profile-concurrency-data"></a>分析並行資料

|Task|相關內容|
|----------|---------------------|
|**分析獨立應用程式**|-   [收集並行資料](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|
|**分析 ASP.NET Web 應用程式**|-   [收集並行資料](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>分析並行資料檢視和報表
- [資源爭用資料檢視](../profiling/resource-contention-data-views.md)

- [並行視覺化檢視](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>參考
- [命令列分析工具參考](../profiling/command-line-profiling-tools-reference.md)
