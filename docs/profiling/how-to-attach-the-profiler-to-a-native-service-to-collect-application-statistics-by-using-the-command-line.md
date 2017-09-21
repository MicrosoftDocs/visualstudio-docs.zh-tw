---
title: "如何：使用命令列將程式碼剖析工具附加至原生服務以收集應用程式統計資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f783817f-77a0-4eb8-985b-ec3b77eadc42
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用命令列將程式碼剖析工具附加至原生服務以收集應用程式統計資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題說明如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具命令列工具將分析工具附加至原生服務，以及使用取樣方法收集效能統計資料。  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 中的增強安全性功能，需要在 Visual Studio 分析工具收集這些平台資料的方式上進行重大變更。  Windows 市集應用程式也需要新的收集技術。  請參閱 [剖析 Windows 8 和 Windows Server 2012 應用程式](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
> [!NOTE]
>  程式碼剖析工具的命令列工具位於 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 安裝目錄的 \\Team Tools\\Performance Tools 子目錄中。  在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。  若要使用程式碼剖析工具的命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。  如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
 當程式碼剖析工具附加至服務時，您可以暫停和繼續資料收集。  
  
 若要結束程式碼剖析工作階段，程式碼剖析工具必須從服務中斷連結，而且程式碼剖析工具必須明確關閉。  
  
## 以程式碼剖析工具啟動應用程式  
 若要將程式碼剖析工具附加至原生服務，請使用 **VSPerfCmd.exe** [\/start](../profiling/start.md) 和 [\/attach](../profiling/attach.md) 選項初始化程式碼剖析工具並附加至目標應用程式。  在單一命令列上，可指定 **\/start** 和 **\/attach** 以及其個別選項。  您也可以加入 [\/globaloff](../profiling/globalon-and-globaloff.md) 選項，在目標應用程式啟動時暫停資料收集。  接著使用 [\/globalon](../profiling/globalon-and-globaloff.md) 開始收集資料。  
  
#### 若要將程式碼剖析工具附加至原生服務  
  
1.  如有必要，請啟動服務。  
  
2.  開啟命令提示字元視窗。  
  
3.  啟動程式碼剖析工具。  型別：  
  
     **VSPerfCmd \/start:sample**  [\/output](../profiling/output.md) **:** `OutputFile` \[`Options`\]  
  
    -   **\/start:sample** 選項會初始化此分析工具。  
  
    -   **\/output:** `OutputFile` 選項必須搭配 **\/start** 使用。  `OutputFile` 指定程式碼剖析資料 \(.vsp\) 檔案的名稱和位置。  
  
     下列任何選項都可以搭配 **\/start:sample** 選項使用。  
  
    > [!NOTE]
    >  服務通常需要 **\/user** 和 **\/crosssession** 選項。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|指定擁有已進行程式碼剖析處理序之帳戶的網域和使用者名稱。  只有在處理序是以非登入使用者的身分執行時，才需要這個選項。  處理序擁有人列於 \[Windows 工作管理員\] 的 \[處理程序\] 索引標籤上的 \[使用者名稱\] 資料行。|  
    |[\/crosssession](../profiling/crosssession.md)|對其他工作階段中的處理序啟用程式碼剖析。  如果應用程式在不同的工作階段中執行，就必須有這個選項。  工作階段 ID 列於 \[Windows 工作管理員\] 之 \[處理程序\] 索引標籤上的 \[工作階段識別碼\] 資料行。  **\/CS** 可以當做 **\/crosssession** 的縮寫來指定。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定程式碼剖析期間要收集的 Windows 效能計數器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|僅能與 **\/wincounter** 搭配使用。  指定 Windows 效能計數器收集事件之間的毫秒數。  預設為 500 毫秒。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定程式碼剖析期間要收集的 Windows 事件追蹤 \(ETW\) 事件。  ETW 事件是在不同的 \(.etl\) 檔案中收集的。|  
  
4.  將程式碼剖析工具附加到服務。  型別：  
  
     **VSPerfCmd \/attach:** `PID` \[`Sample Event`\]  
  
     `PID` 指定目標應用程式的處理序 ID。  您可以在 \[Windows 工作管理員\] 中檢視所有執行中處理序的處理序 ID。  
  
     根據預設，效能資料為每 10,000,000 個未暫止處理器時脈循環取樣一次。  在 1GHz 的處理器上，大約每 10 秒鐘一次。  您可以指定下列其中一項，變更時脈循環間隔或指定不同的取樣事件。  
  
    |取樣事件|描述|  
    |----------|--------|  
    |[\/timer](../profiling/timer.md) **:** `Interval`|將取樣間隔變更為 `Interval` 所指定的未暫止時脈循環數目。|  
    |[\/pf](../profiling/pf.md)\[**:**`Interval`\]|將取樣事件變更為分頁錯誤。  如果已指定 `Interval`，則會設定樣本之間的分頁錯誤數目。  預設值為 10。|  
    |[\/sys](../profiling/sys-vsperfcmd.md) \[**:**`Interval`\]|將取樣事件變更為從處理序對作業系統核心的系統呼叫 \(syscall\)。  如果已指定 `Interval`，則會設定樣本之間的呼叫數目。  預設值為 10。|  
    |[\/counter](../profiling/counter.md) **:** `Config`|將取樣事件和間隔變更為 `Config` 中指定的處理器效能計數器和間隔。|  
  
## 控制資料收集  
 當目標應用程式正在執行時，您可以使用 **VSPerfCmd.exe** 選項，啟動及停止將資料寫入程式碼剖析工具資料檔案。  資料收集控制可讓您收集程式執行中特定組件的資料，例如應用程式的開始與結束。  
  
#### 若要啟動和停止資料收集  
  
-   下列 **VSPerfCmd** 選項配對會啟動和停止資料收集。  在不同的命令列上指定每個選項。  您可以多次開啟或關閉資料收集。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|啟動 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有處理序的資料收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|啟動 \(**\/processon**\) 或停止 \(**\/processoff**\) 對處理序 ID \(`PID`\) 所指定的處理序進行資料收集。|  
    |**\/attach:** {`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[:{`PID`&#124;`ProcName`}\]|**\/attach** 會開始針對處理序 ID 或處理序名稱指定的處理序來收集資料。  **\/detach** 會停止對指定的處理序收集資料，如果沒有指定處理序，則停止所有處理序的資料收集。|  
  
## 結束程式碼剖析工作階段  
 若要結束程式碼剖析工作階段，程式碼剖析工具必須從服務中斷連結，然後明確地關閉。  您可以藉由停止服務或呼叫 **VSPerfCmd \/detach** 選項，將使用取樣方法進行程式碼剖析的原生服務中斷連結。  然後呼叫 **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) 選項，關閉程式碼剖析工具並關閉程式碼剖析資料檔案。  
  
#### 若要結束程式碼剖析工作階段  
  
1.  請執行下列其中一個動作，從目標應用程式中斷連結程式碼剖析工具：  
  
    -   停止服務。  
  
         \-或\-  
  
    -   輸入 **VSPerfCmd \/detach**  
  
2.  關閉程式碼剖析工具。  型別：  
  
     **VSPerfCmd \/shutdown**  
  
## 請參閱  
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)   
 [取樣方法資料檢視](../profiling/profiler-sampling-method-data-views.md)