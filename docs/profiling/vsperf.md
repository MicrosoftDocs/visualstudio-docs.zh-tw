---
title: "VSPerf | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# VSPerf
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用 **VsPerf** 命令列工具:  
  
1.  當 Visual Studio 未安裝在裝置時，從命令列設定 Windows 市集應用程式。  
  
2.  使用取樣程式碼剖析方法，分析 Windows 8 桌上型電腦應用程式和 Windows Server 2012 應用程式。  
  
 如需您的程式碼剖析選項的詳細資訊，請參閱 [剖析 Windows 8 和 Windows Server 2012 應用程式](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
##  <a name="BKMK_In_this_topic"></a> 本主題內容  
 本主題描述可用於 `vsperf.exe` 命令列工具的選項。  此主題包括下列章節：  
  
 [限 Windows 市集應用程式](#BKMK_windows_store_apps_only)  
  
 [只有Windows 8 桌上型電腦應用程式和 Windows Server 2012 應用程式](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [所有應用程式](#BKMK_All_applications)  
  
##  <a name="BKMK_windows_store_apps_only"></a> 限 Windows 市集應用程式  
 這些選項只適用於 Windows 市集應用程式。  
  
|||  
|-|-|  
|**\/app:{AppName}**|啟動程式碼剖析工具並等待指定的應用程式從 \[開始\] 功能表啟動。<br /><br /> 執行 `vsperf /listapps` 檢視安裝之應用程式的應用程式名稱和 PackageFullName。|  
|**\/package:{PackageFullName}**|啟動程式碼剖析工具並等待指定的應用程式從 \[開始\] 功能表啟動。<br /><br /> 執行 `vsperf /listapps` 檢視安裝之應用程式的應用程式名稱和 PackageFullName。|  
|**\/js**|分析 JavaScript 應用程式時需要這一項。<br /><br /> 從 JavaScript 應用程式收集效能資料。<br /><br /> 只能搭配 \/package 或 \/attach 一起使用。|  
|**\/noclr**|選擇項。  不收集CLR 資料。<br /><br /> 只能搭配 \/package 或 \/attach 一起使用。<br /><br /> 最佳化，不解析任何 Managed 符號。|  
|**\/listapps**|列出已安裝的應用程式名稱和 PackageFullNames。|  
  
##  <a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a> 只有Windows 8 桌上型電腦應用程式和 Windows Server 2012 應用程式  
 這些選項在 Windows 市集應用程式無法運作。  
  
|||  
|-|-|  
|**\/launch:{Executable}**|啟動並啟動程式碼剖析指定的可執行檔。|  
|**\/args:{ExecutableArguments}**|傳遞指定命令列引數至 **\/launch** 目標。|  
|**\/console**|在新的命令視窗中執行 **\/launch** 目標。|  
  
##  <a name="BKMK_All_applications"></a> 所有應用程式  
 這些選項會套用至所有 Windows 8 或 Windows Server 2012 應用程式。  
  
|||  
|-|-|  
|**\/attach:{PID&#124;ProcessName}\[,PID&#124;ProcessName\]...**|從指定的處理序收集資料。<br /><br /> 使用工作管理員檢視處理序 ID \(PID\) 和執行應用程式的名稱。|  
|**\/file:{ReportName}**|選擇項。  指定輸出檔 \(覆寫現有檔案\)。<br /><br /> 只能搭配 \/package 或 \/attach 一起使用。|  
|**\/pause**|暫停資料收集。|  
|**\/resume**|繼續資料收集。|  
|**\/stop**|停止資料收集，並終止目標處理序。|  
|**\/detach**|停止資料收集，但讓目標處理序繼續執行。|  
|**\/status**|顯示程式碼剖析工具狀態。|  
  
## 請參閱  
 [剖析 Windows 8 和 Windows Server 2012 應用程式](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [從命令列進行程式碼剖析](../profiling/using-the-profiling-tools-from-the-command-line.md)