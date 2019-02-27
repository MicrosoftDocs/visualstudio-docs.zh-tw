---
title: 使用分析工具命令列收集獨立應用程式的並行資料 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c4794a0dd50423a7a1566b20e86aaa5501c94e5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56623134"
---
# <a name="collect-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>使用分析工具命令列收集獨立應用程式的並行資料
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具的並行方法可讓您收集資源爭用資料和執行緒活動資料，顯示 CPU 使用率、執行緒爭用、執行緒移轉、同步處理延遲、重疊 IO 區域 和其他系統事件。


## <a name="common-tasks"></a>一般工作

|工作|相關內容|
|----------|---------------------|
|**啟動 .NET Framework 應用程式並分析並行資料**|-   [如何：啟動 .NET Framework 應用程式以收集並行資料](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)|
|**啟動 C/C++ 應用程式並分析並行資料**|-   [如何：啟動原生應用程式以收集並行資料](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**將分析工具附加至執行中的 .NET Framework 應用程式**|-   [如何：將分析工具附加至 .NET Framework 應用程式以收集並行資料](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)|
|**將分析工具附加至執行中的 C/C++ 應用程式**|-   [如何：將分析工具附加至原生應用程式並收集並行資料](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)|

## <a name="related-tasks"></a>相關工作

### <a name="profile-stand-alone-applications"></a>分析獨立應用程式

|工作|相關內容|
|----------|---------------------|
|**使用取樣方法進行分析**|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**使用檢測方法進行分析**|-   [使用檢測設備收集詳細計時資料](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**分析 .NET 記憶體配置和記憶體回收**|-   [收集 .NET Framework 記憶體資料](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**新增階層互動資料**|-   [收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

### <a name="profile-concurrency-issues"></a>分析並行問題

|工作|相關內容|
|----------|---------------------|
|**分析 ASP.NET 應用程式**|-   [收集並行資料](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|
|**分析服務**|-   [收集並行資料](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>分析並行資料檢視和報表
- [資源爭用資料檢視](../profiling/resource-contention-data-views.md)

- [並行視覺化檢視](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>參考資料
- [命令列程式碼剖析工具參考](../profiling/command-line-profiling-tools-reference.md)