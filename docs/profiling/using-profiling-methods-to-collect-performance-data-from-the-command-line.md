---
title: 使用命令列分析方法來取得效能資料
description: 瞭解 Visual Studio 分析工具命令列工具和選項的選擇，取決於您要分析之應用程式的類型等因素。
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1796fad03d04ffb79ca1c8aeccc241ee3698f9f1
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98723240"
---
# <a name="use-profiling-methods-to-collect-performance-data-from-the-command-line"></a>從命令列使用分析方法收集效能資料
您選擇的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具命令列工具與選項，取決於像是您要進行程式碼剖析的應用程式類型、您想要使用的程式碼剖析方法以及目標應用程式是否以原生或 .NET Framework 程式碼撰寫等因素。

 本主題根據您選擇的程式碼剖析方法來組織命令列程序性主題。

## <a name="use-the-sampling-method-to-collect-performance-statistics"></a>使用取樣方法收集效能統計資料
 程式碼剖析工具取樣方法會在程式碼剖析執行時以指定的間隔收集效能資料。 取樣資料可提供 CPU-bound 效能問題的深入資訊，並可能是開始探索應用程式效能的好方式。

 您可以同時啟動分析工具和應用程式，或將分析工具附加至應用程式執行中的執行個體。

|Task|目標應用程式類型|
|----------|-----------------------------|
|**啟動應用程式**|-   [獨立應用程式](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**附加至執行中的處理序**|-   [.NET Framework 獨立應用程式](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)<br />-   [原生獨立應用程式](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)<br />-   [ASP.NET web 應用程式](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [.NET 服務](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [原生服務](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="use-the-instrumentation-method-to-collect-detailed-timing-data"></a>使用檢測方法收集詳細的計時資料
 程式碼剖析工具檢測方法可從包含軟體探查以記錄效能資訊的應用程式二進位檔複本收集效能資料。 在每個檢測函式開始和結束時，以及每次從檢測函式呼叫其他函式時，都會收集檢測資料。 檢測方法很適合用來探索和 I/O 問題相關效能問題，例如磁碟使用量。

 您可以使用 [VInstr.exe](../profiling/vsinstr.md) 工具來建立檢測二進位檔。 在初始化分析工具之後，會在您執行目標應用程式時，自動從檢測的二進位檔收集資料。

 **目標應用程式類型**

- [.NET Framework 獨立元件](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-timing-data.md)

- [原生獨立元件](../profiling/how-to-instrument-a-native-component-and-collect-timing-data.md)

- [靜態編譯的 ASP.NET web 應用程式](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)

- [動態編譯的 ASP.NET web 應用程式](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)

- [.NET 服務](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

- [原生服務](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

## <a name="use-net-memory-methods-to-collect-memory-allocation-and-object-lifetime-data"></a>使用 .NET 記憶體方法收集記憶體配置和物件存留期資料
 分析工具 .NET 記憶體方法可讓您收集 .NET Framework 記憶體配置資料和 .NET Framework 中有關物件存留期的資訊。

 您可以使用分析工具來啟動目標應用程式；您可以將分析工具附加至應用程式執行中的執行個體；您也可以建立已檢測的應用程式版本，以收集詳細的計時資訊和 .NET Framework 記憶體資料。

|Task|目標應用程式類型|
|----------|-----------------------------|
|**啟動應用程式**|-   [獨立 .NET Framework 應用程式](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-memory-data.md)|
|**附加至執行中的處理序**|-   [.NET Framework 獨立應用程式](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-app-to-collect-memory-data.md)<br />-   [ASP.NET web 應用程式](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [.NET 服務](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|
|**檢測模組**|-   [.NET Framework 獨立元件](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-memory-data.md)<br />-   [靜態編譯的 ASP.NET web 應用程式](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)<br />-   [動態編譯的 ASP.NET web 應用程式](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)<br />-   [.NET 服務](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|

## <a name="use-the-concurrency-method-to-collect-resource-contention-and-thread-activity-data"></a>使用並行方法收集資源爭用和執行緒活動資料
 程式碼剖析工具並行方法可讓您從多執行緒應用程式，來收集資源爭用和執行緒與處理序活動資料。

 您可以使用分析工具來啟動應用程式，或將分析工具附加至應用程式執行中的執行個體。

|Task|目標應用程式類型|
|----------|-----------------------------|
|**啟動應用程式**|-   [獨立 .NET Framework 應用程式](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)<br />-   [獨立原生應用程式](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**附加至執行中的處理序**|-   [.NET Framework 獨立應用程式](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)<br />-   [原生獨立應用程式](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)<br />-   [ASP.NET web 應用程式](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [.NET 服務](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [原生服務](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="add-tier-interaction-data-to-a-profiling-run"></a>將階層互動資料新增至程式碼剖析執行
 若要將階層互動資料加入至程式碼剖析回合中，則需要使用命令列程式碼剖析工具的特定程序。 請參閱[收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)

## <a name="see-also"></a>另請參閱
- [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [分析 ASP.NET web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [分析服務](../profiling/command-line-profiling-of-services.md)
