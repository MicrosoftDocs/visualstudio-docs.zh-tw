---
title: "從命令列使用分析工具取樣方法收集 ASP.NET Web 應用程式的應用程式統計資料 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools, sampling method
- sampling profling method
ms.assetid: f8383ab1-eb49-4d3f-8608-d8b4d51a81be
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 7c87490f8e4ad01df8761ebb2afee0b2d3744fe2
ms.openlocfilehash: fa272e590d1cec839e51110d63ee6224466d12e4
ms.contentlocale: zh-tw
ms.lasthandoff: 09/06/2017

---
# <a name="collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line"></a>從命令列使用程式碼剖析工具取樣方法收集 ASP.NET Web 應用程式的應用程式統計資料
本節說明使用 **VSPerfASPNETCmd** 和 **VSPerfCmd** 命令列工具和取樣分析方法收集 ASP.NET Web 應用程式之效能統計資料的程序和選項。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 Windows 市集應用程式也需要新的資料收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
> [!NOTE]
>  雖然 **VSPerfCmd** 工具可讓您完整存取分析工具的功能，包括暫停和繼續分析，以及收集處理器和 Windows 效能計數器的其他資料，但是您可以在不需要這項功能時使用 **VSPerfASPNETCmd** 命令列工具。 當您使用獨立的分析工具分析 ASP.NET 網站時，**VSPerfASPNETCmd** 命令列工具是慣用的方法。 相較於 [VSPerfCmd](../profiling/vsperfcmd.md) 命令列工具，無須設定任何環境變數，也不需要重新啟動電腦。 如需詳細資訊，請參閱[使用 VSPerfASPNETCmd 快速進行網站分析](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)。  
  
## <a name="common-tasks"></a>一般工作  
  
|工作|相關內容|  
|----------|---------------------|  
|**將分析工具附加至 ASP.NET 應用程式**|-   [如何：將分析工具附加至 ASP.NET Web 應用程式以收集應用程式統計資料](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>相關工作  
  
### <a name="profiling-aspnet-web-applications"></a>為 ASP.NET Web 應用程式進行程式碼剖析  
  
|工作|相關內容|  
|----------|---------------------|  
|**使用檢測方法進行分析**|-   [使用檢測收集詳細計時資料](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**分析記憶體配置和記憶體回收**|-   [收集記憶體資料](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**分析資源爭用和執行緒活動**|-   [收集並行資料](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="sampling-method"></a>取樣方法  
  
|工作|相關內容|  
|----------|---------------------|  
|**分析獨立 (用戶端) 應用程式**|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|-   **分析服務**|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
  
### <a name="analyzing-sampling-data-views-and-reports"></a>分析取樣資料檢視和報表  
 [取樣方法資料檢視](../profiling/profiler-sampling-method-data-views.md)
