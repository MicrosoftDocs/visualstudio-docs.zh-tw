---
title: Profiler 命令列-取得 ASP.NET web 應用程式記憶體資料
description: 瞭解如何使用 >vsperfcmd 命令列工具來收集 ASP.NET web 應用程式的記憶體配置和物件存留期日期。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- .NET memory profiling method
- profiling tools,.NET memory method
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: edcac130a37b90f164cc2b90c11fe43adeea8414
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949398"
---
# <a name="collect-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>使用分析工具命令列收集 ASP.NET Web 應用程式的記憶體資料
本節說明使用 **>vsperfcmd** 命令列工具收集 ASP.NET web 應用程式之記憶體配置和物件存留期資料的程式和選項。

> [!NOTE]
> **VSPerfCmd** 工具可讓您完整存取分析工具功能，包含暫停和繼續分析，以及收集處理器和 Windows 效能計數器的其他資料。 您也可以在不需要這項功能時使用 **VSPerfASPNETCmd** 命令列工具。 相較於 [VSPerfCmd](../profiling/vsperfcmd.md) 命令列工具，無須設定任何環境變數，也不需要重新啟動電腦。 如需詳細資訊，請參閱 [使用 VSPerfASPNETCmd 快速](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)進行網站分析。

## <a name="common-tasks"></a>常見工作

|Task|相關內容|
|----------|---------------------|
|**將分析工具附加至執行中的 ASP.NET 應用程式**|-   [如何：將分析工具附加至 ASP.NET web 應用程式以收集記憶體資料](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|
|**檢測靜態編譯的二進位檔**|-   [如何：檢測靜態編譯的 ASP.NET 應用程式並收集記憶體資料](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)|
|**檢測動態編譯的二進位檔**|-   [如何：檢測動態編譯的 ASP.NET 應用程式並收集記憶體資料](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)|

## <a name="related-tasks"></a>相關工作

### <a name="profile-aspnet-web-applications"></a>分析 ASP.NET Web 應用程式

|Task|相關內容|
|----------|---------------------|
|**使用取樣方法進行分析**|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**使用檢測方法進行分析**|-   [使用檢測設備收集詳細計時資料](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**分析資源爭用和執行緒活動**|-   [收集並行資料](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-net-framework-memory-data"></a>分析 .NET Framework 記憶體資料

|Task|相關內容|
|----------|---------------------|
|**分析獨立 (用戶端) 應用程式**|-   [收集 .NET Framework 記憶體資料](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**分析服務**|-   [收集 .NET 記憶體資料](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="analyze-net-memory-data-views-and-reports"></a>分析 .NET 記憶體資料檢視和報表
- [.NET 記憶體資料檢視](../profiling/dotnet-memory-data-views.md)

## <a name="reference"></a>參考
- [命令列分析工具參考](../profiling/command-line-profiling-tools-reference.md)
