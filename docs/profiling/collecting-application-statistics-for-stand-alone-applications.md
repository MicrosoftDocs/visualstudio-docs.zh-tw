---
title: Profiler 命令列：收集獨立的應用程式統計資料
description: 使用 Visual Studio 中的 profiler 命令列收集獨立應用程式的應用程式統計資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- sampling profiling method
- profilng tools,sampling method
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6567b0116227bf259eb3591bc6880a6841252869
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148297"
---
# <a name="collect-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>使用分析工具命令列收集獨立應用程式的應用程式統計資料
本節說明從命令列使用取樣方法收集用戶端 (獨立) 應用程式之效能統計資料的程序和選項。

> [!NOTE]
> Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 UWP App 也需要新的收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。

## <a name="common-tasks"></a>常見工作

|工作|相關內容|
|----------|---------------------|
|**使用分析啟動應用程式**|-   [如何：啟動獨立應用程式並收集應用程式統計資料](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**將分析工具附加至執行中的 .NET Framework 應用程式**|-   [如何：將分析工具附加至 .NET Framework 應用程式並收集應用程式統計資料](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)|
|**將分析工具附加至執行中的 C/C++ 應用程式**|-   [如何：將分析工具附加至原生應用程式並收集應用程式統計資料](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)|
|**新增階層互動資料**|-   [收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

## <a name="related-tasks"></a>相關工作

### <a name="profile-stand-alone-applications"></a>分析獨立應用程式

|工作|相關內容|
|----------|---------------------|
|**檢測應用程式**|-   [使用檢測設備收集詳細計時資料](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**收集 .NET 記憶體配置和記憶體回收資料**|-   [收集 .NET Framework 記憶體資料](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**收集資源爭用和執行緒執行資料**|-   [收集並行資料](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|

### <a name="profile-by-using-the-sampling-method"></a>使用取樣方法進行分析

|工作|相關內容|
|----------|---------------------|
|**分析 ASP.NET web 應用程式**|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**分析服務**|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)。 說明如何使用取樣方法收集 Windows 服務的效能統計資料。|

### <a name="analyze-sampling-data-views-and-reports"></a>分析取樣資料檢視和報表
- [取樣方法資料檢視](../profiling/profiler-sampling-method-data-views.md)
