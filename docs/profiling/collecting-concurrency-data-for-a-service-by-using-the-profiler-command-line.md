---
title: 使用分析工具命令列來取得服務的並行資料
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4b7b60ad871f40e06e2a8fbf6782773ce6596f31
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779671"
---
# <a name="collect-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>使用分析工具命令列收集服務的並行資料
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具的並行方法可讓您收集資源爭用資料和執行緒活動資料，顯示 CPU 使用率、執行緒爭用、執行緒移轉、同步處理延遲、重疊 IO 區域 和其他系統事件。

> [!NOTE]
> Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 UWP App 也需要新的收集技術。 請參閱[Windows 8 和 Windows 伺服器 2012 應用程式中的性能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。

## <a name="common-tasks"></a>常見工作

|Task|相關內容|
|----------|---------------------|
|**附加至執行中的 .NET 服務**|-   [如何：將探測器附加到 .NET 服務以收集併發資料](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|
|**添加層交互資料**|-   [收集層交互資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**附加至執行中的 C/C++ 服務**|-   [如何：將探測器附加到本機服務以收集併發資料](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

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
|**分析獨立應用程式**|-   [收集併發資料](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|
|**分析 ASP.NET Web 應用程式**|-   [收集併發資料](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>分析並行資料檢視和報表
- [資源爭用資料檢視](../profiling/resource-contention-data-views.md)

- [並行視覺化檢視](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>參考
- [命令列分析工具參考](../profiling/command-line-profiling-tools-reference.md)
