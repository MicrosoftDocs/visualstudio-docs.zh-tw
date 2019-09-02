---
title: 從命令列使用程式碼剖析方法收集效能資料 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fe9e8d3dbd1e7395287cd7241f1e6145dffca7e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68145390"
---
# <a name="using-profiling-methods-to-collect-performance-data-from-the-command-line"></a>從命令列使用程式碼剖析方法收集效能資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您選擇的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 程式碼剖析工具命令列工具與選項，取決於像是您要進行程式碼剖析的應用程式類型、您想要使用的程式碼剖析方法以及目標應用程式是否以原生或 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 程式碼撰寫等因素。  
  
 本主題根據您選擇的程式碼剖析方法來組織命令列程序性主題。  
  
## <a name="in-this-topic"></a>本主題內容  
 [使用取樣方法收集效能統計資料](#BKMK_Using_the_sampling_method_to_collect_performance_statistics)  
  
 [使用檢測方法收集詳細的計時資料](#BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data)  
  
 [使用 .NET 記憶體方法收集記憶體配置和物件存留期資料](#BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data)  
  
 [使用並行方法收集資源爭用和執行緒活動資料](#BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data)  
  
 [將階層互動資料加入至程式碼剖析執行](#BKMK_Adding_tier_interaction_data_to_a_profiling_run)  
  
## <a name="BKMK_Using_the_sampling_method_to_collect_performance_statistics"></a>使用取樣方法收集效能統計資料  
 程式碼剖析工具取樣方法會在程式碼剖析執行時以指定的間隔收集效能資料。 取樣資料可提供 CPU-bound 效能問題的深入資訊，並可能是開始探索應用程式效能的好方式。  
  
 您可以同時啟動分析工具和應用程式，或將分析工具附加至應用程式執行中的執行個體。  
  
|工作|目標應用程式類型|  
|----------|-----------------------------|  
|**啟動應用程式**|-   [獨立應用程式](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**附加至執行中的處理序**|-   [.NET Framework 獨立應用程式](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [原生獨立應用程式](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [ASP.NET Web 應用程式](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [.NET 服務](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [原生服務](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data"></a>使用檢測方法收集詳細的計時資料  
 程式碼剖析工具檢測方法可從包含軟體探查以記錄效能資訊的應用程式二進位檔複本收集效能資料。 在每個檢測函式開始和結束時，以及每次從檢測函式呼叫其他函式時，都會收集檢測資料。 檢測方法很適合用來探索和 I/O 問題相關效能問題，例如磁碟使用量。  
  
 您可以使用 [VInstr.exe](../profiling/vsinstr.md) 工具來建立檢測二進位檔。 在初始化分析工具之後，會在您執行目標應用程式時，自動從檢測的二進位檔收集資料。  
  
 **目標應用程式類型**  
  
- [.NET Framework 獨立元件](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
- [原生獨立元件](../profiling/how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
- [靜態編譯的 ASP.NET Web 應用程式](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
- [動態編譯的 ASP.NET Web 應用程式](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
- [.NET 服務](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
- [原生服務](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
## <a name="BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data"></a>使用 .NET 記憶體方法收集記憶體配置和物件存留期資料  
 程式碼剖析工具 .NET 記憶體方法可讓您收集 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 記憶體配置資料和 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 中有關物件存留期的資訊。  
  
 您可以使用分析工具，來啟動目標應用程式，您可以將分析工具附加至應用程式執行中的執行個體，而且您可以建立已檢測的應用程式版本，以收集詳細的計時資訊和 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 記憶體資料。  
  
|工作|目標應用程式類型|  
|----------|-----------------------------|  
|**啟動應用程式**|-   [獨立 .NET Framework 應用程式](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line.md)|  
|**附加至執行中的處理序**|-   [.NET Framework 獨立應用程式](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [ASP.NET Web 應用程式](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [.NET 服務](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|  
|**檢測模組**|-   [.NET Framework 獨立元件](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line.md)<br />-   [靜態編譯的 ASP.NET Web 應用程式](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [動態編譯的 ASP.NET Web 應用程式](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [.NET 服務](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## <a name="BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data"></a>使用並行方法收集資源爭用和執行緒活動資料  
 程式碼剖析工具並行方法可讓您從多執行緒應用程式，來收集資源爭用和執行緒與處理序活動資料。  
  
 您可以使用分析工具來啟動應用程式，或將分析工具附加至應用程式執行中的執行個體。  
  
|工作|目標應用程式類型|  
|----------|-----------------------------|  
|**啟動應用程式**|-   [獨立 .NET Framework 應用程式](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [獨立原生應用程式](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**附加至執行中的處理序**|-   [.NET Framework 獨立應用程式](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [原生獨立應用程式](/visualstudio/profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data?view=vs-2015)<br />-   [ASP.NET Web 應用程式](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [.NET 服務](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [原生服務](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="BKMK_Adding_tier_interaction_data_to_a_profiling_run"></a>將階層互動資料加入至程式碼剖析執行  
 若要將階層互動資料加入至程式碼剖析回合中，則需要使用命令列程式碼剖析工具的特定程序。 請參閱[收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)  
  
## <a name="see-also"></a>另請參閱  
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [對 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)
