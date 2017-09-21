---
title: "如何：使用命令列將程式碼剖析工具附加至 .NET 服務以收集記憶體資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aeac39af-ad99-479f-aa36-4104356ca512
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用命令列將程式碼剖析工具附加至 .NET 服務以收集記憶體資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題說明如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具命令列工具將分析工具附加至 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 服務，以及收集記憶體資料。  您可以收集記憶體配置數目和大小的相關資料，也可以收集記憶體物件存留期的相關資料。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中的增強安全性功能，需要在 Visual Studio 分析工具收集這些平台資料的方式上進行重大變更。  Windows 市集應用程式也需要新的收集技術。  請參閱 [剖析 Windows 8 和 Windows Server 2012 應用程式](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
> [!NOTE]
>  程式碼剖析工具的命令列工具位於 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 安裝目錄的 \\Team Tools\\Performance Tools 子目錄中。  在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。  若要使用程式碼剖析工具的命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。  如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
 若要收集 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 服務的記憶體資料，可以使用 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 工具，在裝載服務的電腦上初始化適當的環境變數。  電腦必須重新啟動，才能設定它進行程式碼剖析。  
  
 接著，使用 [VSPerfCmd](../profiling/vsperfcmd.md) 工具將程式碼剖析工具附加至服務處理序。  當程式碼剖析工具附加至服務時，您可以暫停和繼續資料收集。  
  
 若要結束程式碼剖析工作階段，程式碼剖析工具必須從服務中斷連結，而且程式碼剖析工具必須明確關閉。  在許多情況下，我們建議在工作階段結尾清除程式碼剖析環境變數。  
  
## 附加程式碼剖析工具  
  
#### 若要將程式碼剖析工具附加至 .NET Framework 服務  
  
1.  如有必要，請安裝服務。  
  
2.  開啟命令提示字元視窗。  
  
3.  初始化程式碼剖析環境變數。  型別：  
  
     **VSPerfClrEnv** {**\/globalsamplegc \/globalsamplegclife**}\[**\/samplelineoff**\]  
  
    -   選項 **\/globalsamplegclife** 和 **\/globalsamplegclife** 會指定要收集之記憶體資料的類型。  只指定下列其中一個選項。  
  
     **\/globalsamplegc**  
     啟用記憶體配置資料的收集功能。  
  
     **\/globalsamplegclife**  
     啟用記憶體配置資料和物件存留期資料的收集功能。  
  
    -   **\/samplelineoff** 選項會停用原始程式碼行號資料的收集功能。  
  
4.  重新啟動電腦以進行新的環境設定。  
  
5.  如有必要，請啟動服務。  
  
6.  開啟命令提示字元視窗。  如有需要，請將程式碼剖析工具路徑加入至 PATH 環境變數。  
  
7.  啟動程式碼剖析工具。  型別：  
  
     **VSPerfCmd**  [\/start](../profiling/start.md) **:sample**  [\/output](../profiling/output.md) **:** `OutputFile` \[`Options`\]  
  
    -   **\/start:sample** 選項會初始化此分析工具。  
  
    -   **\/output:** `OutputFile` 選項必須搭配 **\/start** 使用。  `OutputFile` 指定程式碼剖析資料 \(.vsp\) 檔案的名稱和位置。  
  
     您可以使用下列一個或多個選項搭配 **\/start:sample** 選項。  
  
    > [!NOTE]
    >  服務通常需要 **\/user** 和 **\/crosssession** 選項。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|指定擁有處理序之帳戶的網域和使用者名稱。  如果處理序是以非登入使用者的身分執行，就必須有這個選項。  處理序擁有人列於 \[Windows 工作管理員\] 的 \[處理程序\] 索引標籤上的 \[使用者名稱\] 資料行。|  
    |[\/crosssession](../profiling/crosssession.md)|對其他登入工作階段中的處理序啟用程式碼剖析。  如果 ASP.NET 應用程式在不同的工作階段中執行，就必須有這個選項。  工作階段 ID 列於 \[Windows 工作管理員\] 之 \[處理程序\] 索引標籤上的 \[工作階段識別碼\] 資料行。  **\/CS** 可以當做 **\/crosssession** 的縮寫來指定。|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|指定用來執行服務之登入帳戶的選擇性網域和使用者名稱。  登入帳戶會在 \[Windows 服務控制管理員\] 中服務的 \[登入身分\] 資料行中列出。|  
    |[\/crosssession&#124;cs](../profiling/crosssession.md)|對其他登入工作階段中的處理序啟用程式碼剖析。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定程式碼剖析期間要收集的 Windows 效能計數器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|僅能與 **\/wincounter** 搭配使用。  指定 Windows 效能計數器收集事件之間的毫秒數。  預設為 500 毫秒。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定程式碼剖析期間要收集的 Windows 事件追蹤 \(ETW\) 事件。  ETW 事件是在不同的 \(.etl\) 檔案中收集的。|  
  
8.  將程式碼剖析工具附加到服務。  型別：  
  
     **VSPerfCmd**  [\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   指定服務的處理序 ID 或處理序名稱。  您可以在 \[Windows 工作管理員\] 中檢視所有執行中處理序的處理序 ID 和名稱。  
  
    -   如果有多個 Common Language Runtime \(CLR\) 版本載入到某一種應用程式中，則 **targetclr:**`Version` 會指定要進行程式碼剖析的 Runtime 版本。  選擇項。  
  
## 控制資料收集  
 當服務正在執行時，您可以使用 **VSPerfCmd.exe** 選項停止及啟動將資料寫入程式碼剖析工具資料檔案。  控制資料收集可讓您收集特定程式執行部分的資料，例如啟動或關閉應用程式。  
  
#### 若要啟動和停止資料收集  
  
-   下列 **VSPerfCmd** 選項配對會啟動和停止資料收集。  在不同的命令列上指定每個選項。  您可以多次開啟或關閉資料收集。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|啟動 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有處理序的資料收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID`  [\/processoff](../profiling/processon-and-processoff.md) **:** `PID`|啟動 \(**\/processon**\) 或停止 \(**\/processoff**\) 對處理序 ID \(`PID`\) 所指定的處理序進行資料收集。|  
    |**\/attach:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[:{`PID`&#124;`ProcName`}\]|**\/attach** 會開始針對處理序 ID 或處理序名稱指定的處理序來收集資料。  **\/detach** 會停止對指定的處理序收集資料，如果沒有指定特定的處理序，則停止所有處理序的資料收集。|  
  
## 結束程式碼剖析工作階段  
 若要結束程式碼剖析工作階段，程式碼剖析工具不能正在收集資料。  您可以停止服務或呼叫 **VSPerfCmd \/detach** 選項，藉此停止從使用取樣方法進行程式碼剖析的應用程式中收集資料。  然後呼叫 **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) 選項，關閉程式碼剖析工具並關閉程式碼剖析資料檔案。  **VSPerfClrEnv \/globaloff** 命令會清除程式碼剖析環境變數，但是系統組態在電腦重新啟動後才會重設。  
  
#### 若要結束程式碼剖析工作階段  
  
1.  請執行下列其中一個動作，從目標應用程式中斷連結程式碼剖析工具：  
  
    -   停止服務。  
  
         \-或\-  
  
    -   輸入 **VSPerfCmd \/detach**  
  
2.  關閉程式碼剖析工具。  型別：  
  
     **VSPerfCmd \/shutdown**  
  
3.  \(選擇項\) 清除程式碼剖析環境變數。  型別：  
  
     **VSPerfClrEnv \/globaloff**  
  
4.  重新啟動電腦。  
  
## 請參閱  
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)   
 [.NET 記憶體資料檢視](../profiling/dotnet-memory-data-views.md)