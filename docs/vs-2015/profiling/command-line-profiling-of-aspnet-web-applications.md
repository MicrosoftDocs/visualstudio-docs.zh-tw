---
title: ASP.NET Web 應用程式的命令列分析 | Microsoft Docs
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
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf3727447d17d941f477dfb71373a8c90e518dd0
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "53861691"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>ASP.NET Web 應用程式的命令列分析
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本節說明從命令列使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 分析工具收集 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web 應用程式之效能資料的程序和選項。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 Windows 市集應用程式也需要新的資料收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
## <a name="common-tasks"></a>一般工作  
  
|工作|相關內容|  
|----------|---------------------|  
|**輕鬆收集基本的 ASP.NET 分析資料：** 使用 **VSPerfASPNETCmd** 工具可收集取樣、檢測、.NET 記憶體、爭用或階層互動資料，不需要進行設定，也不需要像使用 **VSPerfCmd** 時必須重新啟動 Internet Information Services (IIS)。 **VSPerfASPNETCmd** 不允許您收集其他資料，或控制資料收集。 **注意：** 建議您使用 **VSPerfASPNETCmd** 這項獨立分析工具分析 ASP.NET 網站。|-   [使用 VSPerfASPNETCmd 快速進行網站分析](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)|  
|**收集應用程式統計資料：** 使用取樣方法收集效能統計資料。 取樣資料可用來分析 CPU 使用量的問題，以及了解應用程式的一般效能特性。|-   [使用取樣收集應用程式統計資料](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**收集詳細計時資料：** 使用檢測方法收集詳細的計時資訊。 檢測資料可用來分析 IO 問題，並且適用於更細緻的應用程式案例分析。|-   [使用檢測收集詳細計時資料](/visualstudio/profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method?view=vs-2015)|  
|**收集 .NET 記憶體資料：** 使用取樣或檢測收集 .NET 記憶體配置資料，以顯示配置物件的大小和數目。 您也可以收集物件存留期資料，顯示每個記憶體回收層代中回收的物件大小和數目。|-   [收集記憶體資料](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**收集並行資料：** 使用並行方法收集資源爭用資料。 **注意：** Web 應用程式不支援收集執行緒活動和視覺化資料。|-   [收集並行資料](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**新增階層互動資料：** 您可以新增下列相關效能資料：[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web 應用程式對 Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫發出的同步 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 呼叫。|-   [收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>相關工作  
  
|工作|相關內容|  
|----------|---------------------|  
|**分析獨立 (用戶端) 應用程式**|-   [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**分析服務**|-   [分析服務](../profiling/command-line-profiling-of-services.md)|



