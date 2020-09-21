---
title: 使用檢測收集計時資料以進行 ASP.NET
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling tools,instrumentation method
- instrumentation profiling method
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: a73d81eaaef45a9ae97e733a8ae94805106a9ef8
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809631"
---
# <a name="collect-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>從命令列使用分析工具檢測方法以收集 ASP.NET Web 應用程式的詳細計時資料
本節描述使用 **VSPerfCmd** 命令列工具及檢測方法收集 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式詳細效能資料的程序和選項。

> [!NOTE]
> **VSPerfCmd** 工具可讓您完整存取分析工具功能，包含暫停和繼續分析，以及收集處理器和 Windows 效能計數器的其他資料。 您也可以在不需要這項功能時使用 **VSPerfASPNETCmd** 命令列工具。 與 [VSPerfCmd](../profiling/vsperfcmd.md) 命令列工具相較之下，無須設定任何環境變數，也不需要重新啟動電腦。 如需詳細資訊，請參閱 [使用 VSPerfASPNETCmd 快速](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)進行網站分析。

## <a name="common-tasks"></a>常見工作

|Task|相關內容|
|----------|---------------------|
|**分析靜態編譯的二進位檔**|-   [如何：檢測靜態編譯的 ASP.NET 應用程式並收集詳細計時資料](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)|
|**分析動態編譯的二進位檔**|-   [如何：檢測動態編譯的 ASP.NET 應用程式並收集詳細計時資料](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)|

## <a name="related-tasks"></a>相關工作

### <a name="profile-aspnet-web-applications"></a>分析 ASP.NET Web 應用程式

|Task|相關內容|
|----------|---------------------|
|**使用取樣方法進行分析**|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**分析記憶體配置和記憶體回收**|-   [收集記憶體資料](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**分析資源爭用和執行緒活動**|-   [收集並行資料](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-by-using-the-instrumentation-method"></a>使用檢測方法進行分析

|Task|相關內容|
|----------|---------------------|
|**分析獨立 (用戶端) 應用程式**|-   [使用檢測設備收集詳細計時資料](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**分析服務**|-   [使用檢測設備收集詳細計時資料](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|

### <a name="analyze-instrumentation-data-views-and-reports"></a>分析檢測資料檢視和報表
- [檢測方法資料檢視](../profiling/instrumentation-method-data-views.md)
