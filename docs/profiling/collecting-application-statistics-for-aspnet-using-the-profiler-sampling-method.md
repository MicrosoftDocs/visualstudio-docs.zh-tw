---
title: 收集 ASP.NET Web 應用程式的統計資料
description: 請參閱使用 VSPerfASPNETCmd 和 >vsperfcmd 工具和取樣分析方法收集 ASP.NET Web 應用程式之效能統計資料的程式和選項。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling tools, sampling method
- sampling profling method
ms.assetid: f8383ab1-eb49-4d3f-8608-d8b4d51a81be
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: ef1f4ef1c50db1234425ab164f377dab5ff12ea6
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149530"
---
# <a name="collect-statistics-for-aspnet-web-apps"></a>收集 ASP.NET Web 應用程式的統計資料

本節說明使用 **VSPerfASPNETCmd** 和 **VSPerfCmd** 命令列工具和取樣分析方法收集 ASP.NET Web 應用程式之效能統計資料的程序和選項。

> [!NOTE]
> Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 UWP App 也需要新的收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。

> [!NOTE]
> 雖然 **VSPerfCmd** 工具可讓您完整存取分析工具的功能，包括暫停和繼續分析，以及收集處理器和 Windows 效能計數器的其他資料，但是您可以在不需要這項功能時使用 **VSPerfASPNETCmd** 命令列工具。 當您使用獨立的分析工具分析 ASP.NET 網站時，**VSPerfASPNETCmd** 命令列工具是慣用的方法。 相較於 [VSPerfCmd](../profiling/vsperfcmd.md) 命令列工具，無須設定任何環境變數，也不需要重新啟動電腦。 如需詳細資訊，請參閱 [使用 VSPerfASPNETCmd 快速](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)進行網站分析。

## <a name="common-tasks"></a>常見工作

|工作|相關內容|
|----------|---------------------|
|**將分析工具附加至 ASP.NET 應用程式**|-   [如何：將分析工具附加至 ASP.NET web 應用程式以收集應用程式統計資料](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>相關工作

### <a name="profile-aspnet-web-applications"></a>分析 ASP.NET Web 應用程式

|工作|相關內容|
|----------|---------------------|
|**使用檢測方法進行分析**|-   [使用檢測設備收集詳細計時資料](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**分析記憶體配置和記憶體回收**|-   [收集記憶體資料](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**分析資源爭用和執行緒活動**|-   [收集並行資料](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="sample-method"></a>取樣方法

|工作|相關內容|
|----------|---------------------|
|**分析獨立 (用戶端) 應用程式**|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|-   **設定檔服務**|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>分析取樣資料檢視和報表
- [取樣方法資料檢視](../profiling/profiler-sampling-method-data-views.md)
