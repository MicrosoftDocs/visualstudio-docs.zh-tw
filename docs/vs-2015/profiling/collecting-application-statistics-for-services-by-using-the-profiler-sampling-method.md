---
title: 使用分析工具取樣方法收集服務的應用程式統計資料 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37e08c4b9af5c4d870be1ddf7bac0cba677f5cf3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947728"
---
# <a name="collecting-application-statistics-for-services-by-using-the-profiler-sampling-method"></a>使用程式碼剖析工具取樣方法收集服務的應用程式統計資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本節說明從命令列使用取樣方法收集 Windows 服務之效能統計資料的程序和選項。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 Windows 市集應用程式也需要新的資料收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
## <a name="common-tasks"></a>一般工作  
  
|工作|相關內容|  
|----------|---------------------|  
|**將分析工具附加至 .NET 服務**|-   [如何：將分析工具附加至 .NET 服務以收集應用程式統計資料](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|  
|**新增階層互動資料**|-   [收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**將分析工具附加至 C/C++ 服務**|-   [如何：將分析工具附加至原生服務以收集應用程式統計資料](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>相關工作  
  
### <a name="profiling-windows-services"></a>分析 Windows 服務  
  
|工作|相關內容|  
|----------|---------------------|  
|**使用檢測方法進行分析**|-   [使用檢測收集詳細計時資料](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**分析 .NET 記憶體配置和記憶體回收**|-   [收集 .NET 記憶體資料](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
|**分析資源爭用和執行緒活動**|-   [收集並行資料](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### <a name="profiling-by-using-the-sampling-method"></a>使用取樣方法進行分析  
  
|工作|相關內容|  
|----------|---------------------|  
|**分析獨立 (用戶端) 應用程式**|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**分析 ASP.NET Web 應用程式**|-   [使用取樣收集應用程式統計資料](/visualstudio/profiling/collecting-concurrency-data-for-an-aspnet-web-application?view=vs-2015)|  
  
### <a name="analyzing-sampling-data-views-and-reports"></a>分析取樣資料檢視和報表  
 [取樣方法資料檢視](../profiling/profiler-sampling-method-data-views.md)



