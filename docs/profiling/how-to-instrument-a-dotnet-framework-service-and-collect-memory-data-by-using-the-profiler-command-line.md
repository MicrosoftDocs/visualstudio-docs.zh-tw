---
title: "如何：使用程式碼剖析工具命令列以檢測 .NET Framework 服務並收集記憶體資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2fa072fc-05fe-4420-99c0-51d2ea3ac4ce
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用程式碼剖析工具命令列以檢測 .NET Framework 服務並收集記憶體資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題說明如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具命令列工具來檢測 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 服務，以及收集記憶體使用量資料。  您可以收集記憶體配置資料，或是同時收集記憶體配置和物件存留期資料。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中的增強安全性功能，需要在 Visual Studio 分析工具收集這些平台資料的方式上進行重大變更。  Windows 市集應用程式也需要新的收集技術。  請參閱 [剖析 Windows 8 和 Windows Server 2012 應用程式](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
> [!NOTE]
>  不過，如果在作業系統啟動時一併啟動的這類服務無法在電腦啟動後重新啟動，則無法使用檢測方法對服務進行程式碼剖析。  
>   
>  程式碼剖析工具的命令列工具位於 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 安裝目錄的 \\Team Tools\\Performance Tools 子目錄中。  在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。  若要使用程式碼剖析工具的命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。  如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
## 啟動程式碼剖析工作階段  
 若要從 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 服務收集效能資料，您可以使用 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 工具初始化適當的環境變數，並且使用 [VSInstr.exe](../profiling/vsinstr.md) 工具建立服務二進位檔的檢測複本。  
  
 裝載服務的電腦必須重新啟動，才能設定它進行程式碼剖析。  此外還必須從 \[服務控制管理員\] 手動啟動服務。  接著啟動程式碼剖析工具，再啟動 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 服務。  
  
 當已檢測的元件執行時，記憶體資料會自動收集至資料檔案。  您可以在程式碼剖析工作階段期間暫停和繼續資料收集。  
  
 若要結束程式碼剖析工作階段，請關閉服務，然後明確地關閉程式碼剖析工具。  在許多情況下，我們建議在工作階段結尾清除程式碼剖析環境變數。  
  
#### 若要開始對 .NET Framework 服務進行程式碼剖析  
  
1.  開啟命令提示字元視窗。  
  
2.  使用 **VSInstr** 工具產生服務二進位檔案的檢測版本。  
  
3.  使用 \[服務控制管理員\] 將原始二進位檔案取代為檢測版的檔案。  請確定服務的 \[啟動類型\] 設為 \[手動\]。  
  
4.  初始化程式碼剖析環境變數。  類型：  
  
     **VSPerfClrEnv** {**\/globaltracegc** &#124; **\/globaltracegclife**}  
  
    -   **\/globaltracegc** 和 **\/globaltracegclife** 會啟用記憶體配置和物件存留期資料的收集功能。  
  
        |選項|描述|  
        |--------|--------|  
        |**\/globaltracegc**|僅收集記憶體配置資料。|  
        |**\/globaltracegclife**|收集記憶體配置和物件留存期資料。|  
  
5.  重新啟動電腦。  
  
6.  開啟命令提示字元視窗。  
  
7.  啟動程式碼剖析工具。  類型：  
  
     **VSPerfCmd**  [\/start](../profiling/start.md) **:trace**  [\/output](../profiling/output.md) **:** `OutputFile` \[`Options`\]  
  
    -   **\/start: contention** 選項會初始化此分析工具。  
  
    -   **\/output:** `OutputFile` 選項必須搭配 **\/start** 使用。  `OutputFile` 指定程式碼剖析資料 \(.vsp\) 檔案的名稱和位置。  
  
     下列任何選項都可以搭配 **\/start:sample** 選項使用。  
  
    > [!NOTE]
    >  服務通常需要 **\/user** 和 **\/crosssession** 選項。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|指定擁有 ASP.NET 背景工作處理序之帳戶的網域和使用者名稱。  如果處理序是以非登入使用者的身分執行，就必須有這個選項。  處理序擁有人列於 \[Windows 工作管理員\] 的 \[處理程序\] 索引標籤上的 \[使用者名稱\] 資料行。|  
    |[\/crosssession](../profiling/crosssession.md)|對其他登入工作階段中的處理序啟用程式碼剖析。  如果 ASP.NET 應用程式在不同的工作階段中執行，就必須有這個選項。  工作階段 ID 列於 \[Windows 工作管理員\] 之 \[處理程序\] 索引標籤上的 \[工作階段識別碼\] 資料行。  **\/CS** 可以當做 **\/crosssession** 的縮寫來指定。|  
    |[\/waitstart](../profiling/waitstart.md)\[**:**`Interval`\]|指定在程式碼剖析工具傳回錯誤之前，等候它初始化的秒數。  如果未指定 `Interval`，程式碼剖析工具會一直等待。  根據預設，**\/start** 會立即傳回。|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|若要在暫停資料收集的情況下啟動程式碼剖析工具，請將 **\/globaloff** 選項加入至 **\/start** 命令列。  使用 **\/globalon** 繼續程式碼剖析。|  
    |[\/counter](../profiling/counter.md) **:** `Config`|從 Config 中指定的處理器效能計數器收集資訊。  計數器資訊會加入至每個程式碼剖析事件收集的資料中。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定程式碼剖析期間要收集的 Windows 效能計數器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|僅能與 **\/wincounter** 搭配使用。  指定 Windows 效能計數器收集事件之間的毫秒數。  預設為 500 毫秒。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定程式碼剖析期間要收集的 Windows 事件追蹤 \(ETW\) 事件。  ETW 事件是在不同的 \(.etl\) 檔案中收集的。|  
  
8.  如有必要，請啟動服務。  
  
9. 將程式碼剖析工具附加到服務。  類型：  
  
     **VSPerfCmd \/attach:** `PID` &#124;`ProcessName`  
  
    -   指定服務的處理序 ID 或處理序名稱。  您可以在 \[Windows 工作管理員\] 中檢視所有執行中處理序的處理序 ID 和名稱。  
  
## 控制資料收集  
 當服務正在執行時，您可以透過 **VSPerfCmd.exe** 選項啟動及停止將資料寫入檔案，以控制資料收集。  資料收集控制可讓您收集程式執行中特定組件的資料，例如應用程式的開始與結束。  
  
#### 若要啟動和停止資料收集  
  
-   下列 **VSPerfCmd** 選項配對會啟動和停止資料收集。  在不同的命令列上指定每個選項。  您可以多次開啟或關閉資料收集。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|啟動 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有處理序的資料收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID`  [\/processoff](../profiling/processon-and-processoff.md) **:** `PID`|啟動 \(**\/processon**\) 或停止 \(**\/processoff**\) 對處理序 ID \(`PID`\) 所指定的處理序進行資料收集。|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID`  [\/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|啟動 \(**\/threadon**\) 或停止 \(**\/threadoff**\) 對執行緒 ID \(`TID`\) 所指定的執行緒進行資料收集。|  
  
## 結束程式碼剖析工作階段  
 若要結束程式碼剖析工作階段，請關閉執行檢測元件的應用程式，然後啟動 **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) 選項以關閉程式碼剖析工具，並關閉程式碼剖析資料檔案。  **VSPerfClrEnv \/globaloff** 命令會清除程式碼剖析環境變數。  
  
#### 若要結束程式碼剖析工作階段  
  
1.  從 \[服務控制管理員\] 停止服務。  
  
2.  關閉程式碼剖析工具。  類型：  
  
     **VSPerfCmd \/shutdown**  
  
3.  當您完成所有程式碼剖析時，請清除程式碼剖析環境變數。  類型：  
  
     **VSPerfClrEnv \/globaloff**  
  
     將檢測模組替換成原始模組。  如有必要，請重新設定服務的啟動類型。  
  
4.  重新啟動電腦。  
  
## 請參閱  
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)   
 [.NET 記憶體資料檢視](../profiling/dotnet-memory-data-views.md)