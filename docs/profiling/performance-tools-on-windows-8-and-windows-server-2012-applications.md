---
title: "Windows 8 和 Windows Server 2012 應用程式的效能工具 | Microsoft Docs"
ms.custom: 
ms.date: 06/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a704215d-d252-4087-921b-ac81ebe2a9c9
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b82860f4bdbf206441591703137f15decb294269
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Windows 8 和 Windows Server 2012 應用程式的效能工具
自 Windows 8 和 Windows Server 2012 開始的增強式安全性功能需要的重大變更，是 Visual Studio 效能工具在這些平台收集資料的方式。 UWP App 也需要新的收集技術。 本主題描述自 Windows 8 和 Windows Server 2012 平台開始的效能工具變更。
  
> [!NOTE]
>  其他支援的 Windows 版本 (Windows 7、Windows Server 2008 R2) 的效能工具並未變更。
  
##  <a name="BKMK_In_this_topic"></a>本主題內容  
 [從 Visual Studio IDE 收集 UWP App 資料](#BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE)  
  
 [從 Visual Studio IDE 收集 Windows 8 桌面或 Windows Server 2012 上所執行應用程式的資料](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE)  
  
-   [使用來自 Visual Studio IDE 的取樣，收集 Windows 8 桌面或 Windows Server 2012 上所執行應用程式的資料](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE)  
  
 [從命令列進行程式碼剖析](#BKMK_Profiling_from_the_command_line)  
  
 [收集階層互動 (TIP) 資料](#BKMK_Collecting_tier_interaction__TIP__data)  
  
##  <a name="BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE"></a> 從 Visual Studio IDE 收集 UWP App 資料  
 當您分析以 JavaScript 和 HTML 5 撰寫的 UWP App 時，要收集 JavaScript 程式碼的檢測資料。 當您分析以 Visual C++、Visual C# 或 Visual Basic 撰寫的 UWP App 或元件時，要收集機器碼和 Managed 程式碼的取樣資料。 您可以在本機或遠端電腦上剖析應用程式的程式碼。  
  
 分析 UWP App 時，不支援下列分析功能和選項：  
  
-   使用取樣方法剖析 JavaScript 應用程式。  
  
-   使用檢測方法剖析 Managed 程式碼和機器碼。  
  
-   並行分析  
  
-   .NET 記憶體分析  
  
-   階層互動分析 (TIP)  
  
-   取樣選項，例如設定取樣事件和逾時間隔，或收集其他效能計數器資料。  
  
-   檢測選項，例如收集效能和視窗計數器資料，或指定其他命令列選項。  
  
 如需對 UWP App 進行分析的詳細資訊，請參閱下列主題：  
  
 [在本機電腦上執行 UWP App](../debugger/run-windows-store-apps-on-the-local-machine.md)  
  
 [在遠端電腦上執行 UWP App](../debugger/run-windows-store-apps-on-a-remote-machine.md)  
  
 [分析工具](profiling-tools.md)  
  
-   [JavaScript 記憶體](../profiling/javascript-memory.md)
  
-   [在本機電腦上分析 UWP App 中的 Visual C++、Visual C# 和 Visual Basic 程式碼](http://msdn.microsoft.com/en-us/2d0c939e-0bac-48c5-b727-46f6c6113060)  
  
-   [在遠端裝置上分析 UWP App 中的 Visual C++、Visual C# 和 Visual Basic 程式碼](http://msdn.microsoft.com/en-us/b932a2be-11b0-40fd-b996-75c6b6a79d22)  
  
-   [分析 UWP App 中 Visual C++、Visual C# 和 Visual Basic 程式碼的效能資料](http://msdn.microsoft.com/en-us/5de4a413-d924-425f-afc4-e1ecfb0fca18)  
  
 [本主題內容](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE"></a>從 Visual Studio IDE 收集 Windows 8 桌面或 Windows Server 2012 上所執行應用程式的資料  
 Windows 8 尚未變更使用檢測方法進行程式碼剖析。  
  
 階層互動分析 (TIP) 不支援使用取樣方法。  
  
###  <a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE"></a>使用來自 Visual Studio IDE 的取樣，收集 Windows 8 桌面或 Windows Server 2012 上所執行應用程式的資料  
 使用取樣方法剖析 Windows 8 桌面應用程式或 Windows Server 2012 應用程式時，不支援這些程式碼剖析功能和選項：
  
-   階層互動分析 (TIP)。 使用檢測支援收集 TIP 資料。
  
-   取樣選項，例如設定取樣事件和逾時間隔，或收集其他效能計數器資料。  
  
##  <a name="BKMK_Profiling_from_the_command_line"></a> 從命令列進行程式碼剖析  
 您使用兩種命令列工具在 Windows 8 和 Windows Server 2012 的裝置上收集程式碼剖析資料，包括沒有安裝 Visual Studio 的裝置：  
  
|工具名稱|描述|  
|---------------|-----------------|  
|[VSPerf](../profiling/vsperf.md)|從 UWP App 收集分析資料，以及從 Windows 8 傳統型應用程式和 Windows Server 2012 應用程式收集樣本分析資料。|  
|[VSPerfCmd](../profiling/vsperfcmd.md)|從 Windows 8 桌面程式或 Windows Server 2012 中執行的應用程式，收集檢測、並行和階層互動分析資料。 從舊版 Windows 中收集所有類型的程式碼剖析資料。|  
  
 兩種工具都以 Visual Studio 安裝，以在本機電腦上使用。  
  
 若要在沒有安裝 Visual Studio 的裝置上剖析應用程式，請執行下列任一作業：  
  
-   從 [MSDN 網站](http://go.microsoft.com/fwlink/?LinkID=219549)下載工具當做 Visual studio 遠端工具的一部分。  
  
-   從您的 Visual Studio 電腦複製並執行獨立的分析工具安裝程式。 安裝程式位在 *%VSInstallDir%* **\Team Tools\Performance Tools\Setups** 資料夾。 選擇遠端電腦的作業系統 (x86/x64) 安裝程式。  
  
> [!NOTE]
>  若要收集 TIP 程式碼剖析資料，您必須從遠端電腦的 Visual Studio 電腦安裝獨立分析工具。  
  
 從命令列剖析 Windows 8 和 Windows Server 2012 應用程式時，不支援這些程式碼剖析功能和選項：  
  
-   使用取樣模式和 [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md)，從 Windows 8 和 Windows Server 2012 Web 應用程式收集資料。  
  
-   使用 VsPerfCmd.exe 收集取樣資料。  
  
-   取樣選項，例如設定取樣事件和逾時間隔，或收集其他效能計數器資料。  
  
##  <a name="BKMK_Collecting_tier_interaction__TIP__data"></a> 收集階層互動 (TIP) 資料  
 階層互動分析提供透過 ADO.NET 服務與資料庫通訊之多介層應用程式函式執行時間的其他資訊。 只針對同步函式呼叫收集資料。  
  
 **Visual Studio 版本**  
  
 使用 [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]、 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]或 [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)]可以收集階層互動分析資料。 不過，只能在 [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] 和 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]檢視階層互動分析資料。  
  
 **Windows 8 和 Windows Server 2012**  
  
1.  若要從 Windows 8 桌面程式或 Windows Server 2012 中執行的應用程式收集階層互動資料，您必須使用檢測方法。  
  
2.  您無法收集 UWP App 的階層互動資料。  
  
3.  其他支援的 Windows 版本上的所有程式碼剖析方法都可以包含階層互動資料。  
  
 **[效能精靈] 和 [效能總管]**  
  
 您必須將階層互動資料收集選項加入從 [效能總管] 執行的程式碼剖析。 您也必須將專案、可執行檔或網站加入 [效能總管] 的 [目標] 節點。 請參閱[收集階層互動資料](../profiling/collecting-tier-interaction-data.md)。  
  
 **在遠端電腦上收集 TIP 資料**  
  
 若要在遠端電腦上收集階層互動資料，您必須從 Visual Studio 電腦的 *%VSInstallDir%***\Team Tools\Performance Tools\Setups** 資料夾中，將 **vs_profiler_***\<平台>***_***\<語言>***.exe** 檔案複製並安裝到遠端電腦。 您無法使用[遠端偵錯](../debugger/remote-debugging.md)下載套件中的程式碼剖析工具。  
  
 您可以使用 [VSPerfCmd](../profiling/vsperfcmd.md) 或 [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) 收集程式碼剖析資料。  
  
 **TIP 報告**  
  
 階層互動資料只能在 [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] 或 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] IDE 中檢視。 不提供透過 [VSPerfReport](../profiling/vsperfreport.md) 的檔案型階層互動報告。  
  
## <a name="see-also"></a>請參閱  
 [效能總管](../profiling/performance-explorer.md)   
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)   
 [從命令列進行程式碼剖析](../profiling/using-the-profiling-tools-from-the-command-line.md)