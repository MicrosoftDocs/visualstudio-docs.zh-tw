---
title: 從命令列使用程式碼剖析工具 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 74b00a65dac65bc9b0f5f6b7a4084c1a0999f0e2
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
---
# <a name="use-the-profiling-tools-from-the-command-line"></a>從命令列使用分析工具
您可以使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具的命令列工具，在命令提示字元分析應用程式，並使用批次檔和指令碼將程式碼剖析自動化。 您也可以在命令提示字元產生報告檔。 您可以使用輕量型獨立分析工具，在未安裝 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的的電腦上收集資料。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 UWP App 也需要新的收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
## <a name="common-tasks"></a>一般工作  
  
|工作|相關內容|  
|----------|---------------------|  
|**設定符號位置︰** 若要顯示函式和參數的名稱，分析工具必須要有已進行程式碼剖分析二進位檔的符號 (.pdb) 檔存取權。 這些檔案應該包含 Microsoft 作業系統的符號檔，以及您想要在分析中檢視的應用程式。 您可以使用公用 Microsoft 符號伺服器，確定您有適用於 Microsoft 二進位檔的正確.pdb 檔。|-   [如何：從命令列指定符號檔位置](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)|  
|**分析應用程式：** 您用來分析目標應用程式的命令列工具與選項，取決於應用程式的類型、程式碼剖析工具以及目標為 Managed 或原生應用程式。|-   [從命令列使用分析方法](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [分析 ASP.NET Web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [分析服務](../profiling/command-line-profiling-of-services.md)|  
|**建立 .xml 和 .csv 報表：** 在命令提示自原進行程式碼剖析，會建立可在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的介面中檢視的資料檔案。 您也可以使用 VSPerfReport 命令列工具，產生 .xml 或逗號分隔值 (.csv) 的資料檔案。|-   [從命令列建立分析工具報告](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md)|  
|**在沒有 Visual Studio 的電腦上分析程式碼︰** 您可以使用程式碼剖析工具的獨立分析工具，在未安裝 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的電腦上收集應用程式的資料。|-   [如何：安裝獨立分析工具](../profiling/how-to-install-the-stand-alone-profiler.md)|  
  
## <a name="reference"></a>參考資料  
 [命令列分析工具參考](../profiling/command-line-profiling-tools-reference.md)  
  
## <a name="see-also"></a>另請參閱  
 [效能總管](../profiling/performance-explorer.md)