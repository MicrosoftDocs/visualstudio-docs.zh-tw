---
title: 分析工具 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.diagnosticshub.overview
ms.assetid: 0fb6cd5d-e16a-4526-84a5-19e63c625bc5
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 93ef837da86056acc720abff9ad33cbf457a108f
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54780840"
---
# <a name="profiling-tools"></a>程式碼剖析工具
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

程式碼剖析和診斷工具可協助您診斷記憶體和 CPU 使用量，以及其他應用程式層級的問題。 利用這些工具，您可以隨著您在偵錯工具中執行應用程式時間而累積資料 (例如變數值、函式呼叫和事件)。 您可以在執行程式碼時檢視應用程式在不同時間點的狀態。  
  
 查看底部的摘要，了解哪些工具可供您的專案類型使用 (例如，桌面、UWP、ASP.NET)。  
  
 您可以藉由使用 [偵錯] / [視窗] / [顯示診斷工具]  在偵錯工作階段期間使用工具，或者藉由使用 [偵錯] / [效能分析工具...]  進行專注效能分析，來存取程式碼剖析工具。  如需不同方法的詳細資訊，請參閱 [Running Profiling Tools With or Without the Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md) 。  
  
 ![DebugDiagnosticsToolsMenu](../profiling/media/debugdiagnosticstoolsmenu.png "DebugDiagnosticsToolsMenu")  
  
 請參閱[程式碼剖析工具的新功能](../profiling/what-s-new-in-profiling-tools.md)以了解這一版的新功能。  
  
 下列各節會說明 Visual Studio 中所提供的不同效能工具。  
  
## <a name="memory-usage"></a>記憶體使用量  
 ![DiagMemorySmall](../profiling/media/diagmemorysmall.png "DiagMemorySmall")  
  
 當您進行偵錯時，您可以使用「記憶體使用量」工具，來找出記憶體流失和記憶體使用沒有效率等問題。 此工具可讓您擷取 Managed 和原生記憶體堆積的快照。 您可以使用此工具，搭配桌面應用程式、Windows 通用應用程式，和 ASP.NET 應用程式。 **記憶體使用量** 工具可以在您執行偵錯時從 [診斷工具]  視窗執行 ([偵錯] / [視窗] / [顯示診斷工具]) 或在偵錯工具之外執行 ([偵錯] / [效能分析工具...])。如需詳細資訊，請參閱[記憶體使用量](../profiling/memory-usage.md)和[記憶體使用量 (不偵錯)](http://msdn.microsoft.com/library/8883bc5f-df86-4f84-aa2b-a21150f499b0)。  
  
## <a name="cpu-usage"></a>CPU 使用量  
 ![DiagCPUSmall](../profiling/media/diagcpusmall.png "DiagCPUSmall")  
  
 [CPU 使用量]  工具顯示 CPU 花時間執行 C++、C#/VB 和 JavaScript 程式碼的地方。  您可以使用這項工具搭配桌面和 Windows 通用應用程式，也可以搭配 Azure App Service 應用程式。 **CPU 使用量** 工具可以在您執行偵錯時從 [診斷工具]  視窗執行 ([偵錯] / [視窗] / [顯示診斷工具]) 或在偵錯工具之外執行 ([偵錯] / [效能分析工具...])。如需不同方法的詳細資訊，請參閱 [CPU 使用量](../profiling/cpu-usage.md) 。  
  
## <a name="performance-explorer"></a>效能總管  
 ![PerfTools](../profiling/media/perftools.png "PerfTools")  
  
 **效能總管** ([偵錯] / [程式碼剖析工具] / [效能總管]) 可讓您使用許多不同的工具，包括 **CPU 取樣**、**檢測**、 **.NET 記憶體配置**和**資源爭用**。 您可以使用效能總管工具搭配桌面應用程式和 ASP.NET 應用程式，但不能搭配 Windows 通用應用程式。 如需詳細資訊，請參閱 [效能總管](../profiling/performance-explorer.md)。  
  
## <a name="gpu-usage"></a>GPU 使用量  
 ![DiagGPUUsage](../profiling/media/diaggpuusage.png "DiagGPUUsage")  
  
 請使用[「GPU 使用量」](../debugger/gpu-usage.md)工具來深入了解 Direct3D 應用程式的高階硬體使用率。 您可以使用此工具，搭配桌面應用程式和 Windows 通用應用程式，但不能搭配 ASP.NET 應用程式。 **GPU 使用量** 工具可以在您執行偵錯時從 [診斷工具]  視窗執行 ([偵錯] / [顯示診斷工具]) 或在偵錯工具之外執行 ([偵錯] / [效能分析工具...])。  
  
## <a name="application-timeline"></a>應用程式時間軸  
 ![DiagAppTimeline](../profiling/media/diagapptimeline.png "DiagAppTimeline")  
  
 [Application Timeline](../profiling/application-timeline.md) 工具可透過提供資源耗用量的詳細檢視，來協助改善 XAML 應用程式的效能。 您可以使用 **應用程式時間軸** ，搭配桌面應用程式和 Windows 通用應用程式，但不能搭配 ASP.NET 應用程式。 **應用程式時間軸** 工具可以從 [診斷工具]  視窗執行 ([偵錯] / [效能分析工具...])。  
  
## <a name="perftips"></a>效能提示  
 ![DiagPerfTips](../profiling/media/diagperftips.png "DiagPerfTips")  
  
 當偵錯工具於中斷點或逐步執行的作業停止執行時，該中斷與上一個中斷點之間經過的時間會在 [編輯器] 視窗中顯示為提示。 這些 [PerfTips](../profiling/perftips.md) 有助於您監視及分析應用程式的效能，同時進行偵錯。 您可以在桌面應用程式、Windows 通用應用程式和 ASP.NET 應用程式中看到 **效能提示** 。  
  
## <a name="javascript-memory"></a>JavaScript 記憶體  
 ![DiagJSMemory](../profiling/media/diagjsmemory.png "DiagJSMemory")  
  
 [JavaScript Memory](../profiling/javascript-memory.md) 工具可讓您測量、評估及鎖定程式碼中的效能相關問題，方法是收集應用程式中每個函式的進入和離開計時資訊。 您可以使用此工具搭配 Windows 通用 HTML 應用程式。 **JavaScript 函式計時** 工具可以從 [診斷工具]  視窗執行 ([偵錯] / [效能分析工具...])。  
  
## <a name="html-ui-responsiveness"></a>HTML UI 回應性  
 ![DiagHTMLResp](../profiling/media/diaghtmlresp.png "DiagHTMLResp")  
  
 [HTML UI 回應性](../profiling/html-ui-responsiveness.md)工具可協助您找出應用程式中的效能問題，包括缺乏回應性、載入時間緩慢，以及視覺效果更新不如預期頻繁。 您可以使用這項工具搭配 Windows 通用 HTML 應用程式。 **HTML UI 回應性** 工具可以從 [診斷工具]  視窗執行 ([偵錯] / [效能分析工具...])。  
  
## <a name="intellitrace"></a>IntelliTrace  
 ![DiagIntelliTrace](../profiling/media/diagintellitrace.png "DiagIntelliTrace")  
  
 [IntelliTrace](../debugger/intellitrace.md) 可讓您記錄特定事件、在偵錯工具事件和函式呼叫期間檢查 [區域變數] 視窗中的資料，以及針對難以重現的錯誤進行偵錯。  IntelliTrace 主要是偵錯工具，但它也提供可用於效能調查的資訊。 您只能在 Visual Studio 企業版使用此工具，並且用於桌面應用程式、Windows 通用應用程式和 ASP.NET C# 應用程式。 您可以在偵錯時，在 [診斷工具]  視窗找到 IntelliTrace ([偵錯] / [視窗] / [顯示診斷工具])。  
  
## <a name="profiling-in-production"></a>在生產環境中進行程式碼剖析  
 在生產環境中進行程式碼剖析的建議的方法是從 [命令列使用 vsperf.exe](../profiling/using-the-profiling-tools-from-the-command-line.md) 收集 CPU 的設定檔來進行程式碼剖析。 如需 Azure App Service 中的遠端程式碼剖析支援，您可以透過 [伺服器總管或 Kudu 入口網站](https://azure.microsoft.com/blog/remote-profiling-support-in-azure-app-service/)進行程式碼剖析。  
  
## <a name="which-tool-should-i-use"></a>應該使用哪一種工具？  
 以下資料表列出 Visual Studio 提供的各種工具和您可以用它們處理的不同專案類型︰  
  
|效能工具|Windows 桌面|Windows 通用/市集|ASP.NET|  
|----------------------|---------------------|------------------------------|-------------|  
|[記憶體使用量](../profiling/memory-usage.md)|是|是|否|  
|[CPU 使用量](../profiling/cpu-usage.md)|是|是|僅限 Azure App Service|  
|[GPU 使用量](../debugger/gpu-usage.md)|是|是|no|  
|[應用程式時間軸](../profiling/application-timeline.md)|是|是|否|  
|[效能提示](../profiling/perftips.md)|是|對 XAML 為是，對 HTML 為否|否|  
|[效能總管](../profiling/performance-explorer.md)|是|否|是|  
|[IntelliTrace](../debugger/intellitrace.md)|僅限 .NET Enterprise|僅限 .NET Enterprise|僅限 .NET Enterprise|  
|[HTML UI responsiveness](../profiling/html-ui-responsiveness.md)|否|對 HTML 為是，對 XAML 為否|否|  
|[JavaScript 記憶體](../profiling/javascript-memory.md)|否|對 HTML 為是，對 XAML 為否|否|  
  
## <a name="see-also"></a>請參閱  
 [Visual Studio IDE](../ide/visual-studio-ide.md)
