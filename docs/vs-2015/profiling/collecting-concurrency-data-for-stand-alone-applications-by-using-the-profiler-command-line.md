---
title: 使用分析工具命令列收集獨立應用程式的並行資料 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d722c90d8fdd77b9da56c08e224652ff8d7a3e9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287465"
---
# <a name="collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>使用程式碼剖析工具命令列收集獨立應用程式的並行資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 分析工具的並行方法可讓您收集資源爭用資料和執行緒活動資料，顯示 CPU 使用率、執行緒爭用、執行緒移轉、同步處理延遲、重疊 IO 區域 和其他系統事件。  
  
## <a name="common-tasks"></a>一般工作  
  
|工作|相關內容|  
|----------|---------------------|  
|**啟動 .NET Framework 應用程式並分析並行資料**|-   [如何：啟動 .NET Framework 應用程式以收集並行資料](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**啟動 C/C++ 應用程式並分析並行資料**|-   [如何：啟動原生應用程式以收集並行資料](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**將分析工具附加至執行中的 .NET Framework 應用程式**|-   [如何：將分析工具附加至 .NET Framework 應用程式以收集並行資料](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**將分析工具附加至執行中的 C/C++ 應用程式**|-   [如何：將分析工具附加至原生應用程式並收集並行資料](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>相關工作  
  
### <a name="profiling-stand-alone-applications"></a>對獨立應用程式進行程式碼剖析  
  
|工作|相關內容|  
|----------|---------------------|  
|**使用取樣方法進行分析**|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**使用檢測方法進行分析**|-   [使用檢測收集詳細計時資料](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**分析 .NET 記憶體配置和記憶體回收**|-   [收集 .NET Framework 記憶體資料](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**新增階層互動資料**|-   [收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
### <a name="profiling-concurrency-issues"></a>分析並行問題  
  
|工作|相關內容|  
|----------|---------------------|  
|**分析 ASP.NET 應用程式**|-   [收集並行資料](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**分析服務**|-   [收集並行資料](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-concurrency-data-views-and-reports"></a>分析並行資料檢視和報表  
 [資源爭用資料檢視](../profiling/resource-contention-data-views.md)  
  
 [並行視覺化檢視](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>參考資料  
 [命令列程式碼剖析工具參考](../profiling/command-line-profiling-tools-reference.md)



