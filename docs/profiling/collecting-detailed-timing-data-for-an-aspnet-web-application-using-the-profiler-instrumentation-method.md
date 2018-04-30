---
title: 從命令列使用分析工具檢測方法以收集 ASP.NET Web 應用程式的詳細計時資料 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools,instrumentation method
- instrumentation profiling method
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 3665046320b644ebd9689e14c18cc68b79c95347
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>從命令列使用程式碼剖析工具檢測方法以收集 ASP.NET Web 應用程式的詳細計時資料
本節描述使用 **VSPerfCmd** 命令列工具及檢測方法收集 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式詳細效能資料的程序和選項。  
  
> [!NOTE]
>  **VSPerfCmd** 工具可讓您完整存取分析工具功能，包含暫停和繼續分析，以及收集處理器和 Windows 效能計數器的其他資料。 您也可以在不需要這項功能時使用 **VSPerfASPNETCmd** 命令列工具。 與 [VSPerfCmd](../profiling/vsperfcmd.md) 命令列工具相較之下，無須設定任何環境變數，也不需要重新啟動電腦。 如需詳細資訊，請參閱[使用 VSPerfASPNETCmd 快速進行網站分析](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)。  
  
## <a name="common-tasks"></a>一般工作  
  
|工作|相關內容|  
|----------|---------------------|  
|**分析靜態編譯的二進位檔**|-   [如何：檢測靜態編譯的 ASP.NET 應用程式並收集詳細計時資料](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)|  
|**分析動態編譯的二進位檔**|-   [如何：檢測動態編譯的 ASP.NET 應用程式並收集詳細計時資料](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler.md)|  
  
## <a name="related-tasks"></a>相關工作  
  
### <a name="profiling-aspnet-web-applications"></a>為 ASP.NET Web 應用程式進行程式碼剖析  
  
|工作|相關內容|  
|----------|---------------------|  
|**使用取樣方法進行分析**|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**分析記憶體配置和記憶體回收**|-   [收集記憶體資料](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**分析資源爭用和執行緒活動**|-   [收集並行資料](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="profiling-by-using-the-instrumentation-method"></a>使用檢測方法進行分析  
  
|工作|相關內容|  
|----------|---------------------|  
|**分析獨立 (用戶端) 應用程式**|-   [使用檢測收集詳細計時資料](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**分析服務**|-   [使用檢測收集詳細計時資料](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
  
### <a name="analyzing-instrumentation-data-views-and-reports"></a>分析檢測資料檢視和報表  
 [檢測方法資料檢視](../profiling/instrumentation-method-data-views.md)