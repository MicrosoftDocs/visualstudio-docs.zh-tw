---
title: "如何：使用程式碼剖析工具命令列以檢測 .NET 服務並收集詳細計時資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9f73593a-69a7-41b7-a21c-81d3ab0eb8fe
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用程式碼剖析工具命令列以檢測 .NET 服務並收集詳細計時資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題說明如何使用 [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] 程式碼剖析工具命令列工具檢測 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 服務，以及收集詳細的執行時間資料。  
  
> [!NOTE]
>  如果服務無法在電腦啟動後重新啟動，例如只在作業系統啟動時一起啟動的服務，您便無法使用檢測方法對服務進行程式碼剖析。  
>   
>  程式碼剖析工具的命令列工具位於 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 安裝目錄的 \\Team Tools\\Performance Tools 子目錄中。  在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。  若要使用程式碼剖析工具的命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。  如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
>   
>  有命令列程式碼剖析工具的特定程序才可將階層互動資料加入至程式碼剖析。  請參閱 [收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)。  
  
 若要使用檢測方法收集 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 服務的詳細執行時間資料，您可以使用 [VSInstr.exe](../profiling/vsinstr.md) 工具產生元件的已檢測版本。  然後，使用已檢測的版本取代未檢測的服務，藉此確認服務已設定為手動啟動。  使用 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 工具初始化全域程式碼剖析環境變數，然後重新啟動主機電腦。接著啟動分析工具。  接著啟動程式碼剖析工具。  
  
 當服務啟動時，執行時間資料會自動收集至資料檔案。  您可以在程式碼剖析工作階段期間暫停和繼續資料收集。  
  
 若要結束程式碼剖析工作階段，請關閉服務，然後明確地關閉程式碼剖析工具。  在許多情況下，我們建議在工作階段結尾清除程式碼剖析環境變數。  
  
## 以程式碼剖析工具啟動應用程式  
  
#### 若要開始對 .NET Framework 服務進行程式碼剖析  
  
1.  開啟命令提示字元視窗。  
  
2.  使用 **VSInstr** 工具產生服務二進位檔案的檢測版本。  
  
3.  以檢測後的版本取代原始的二進位檔案。  在 \[Windows 服務控制管理員\] 中，確定服務的 \[啟動類型\] 設定為 \[手動\]。  
  
4.  初始化 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 程式碼剖析環境變數。  型別：  
  
     **VSPerfClrEnv \/globaltraceon**  
  
5.  重新啟動電腦。  
  
6.  開啟命令提示字元視窗。  
  
7.  啟動程式碼剖析工具。  型別：  
  
     **VSPerfCmd \/start:trace \/output:** `OutputFile` \[`Options`\]  
  
    -   [\/start](../profiling/start.md) **:trace** 選項會初始化程式碼剖析工具。  
  
    -   [\/output](../profiling/output.md) **:** `OutputFile` 選項必須搭配 **\/start** 使用。  `OutputFile` 指定程式碼剖析資料 \(.vsp\) 檔案的名稱和位置。  
  
     您可以使用下列任何一個選項搭配 **\/start:trace** 選項使用。  
  
    > [!NOTE]
    >  程式碼剖析服務通常需要 **\/user** 和 **\/crosssession** 選項。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|指定擁有已進行程式碼剖析處理序之帳戶的網域和使用者名稱。  只有在處理序是以非登入使用者的身分執行時，才需要這個選項。  處理序擁有人列於 \[Windows 工作管理員\] 的 \[處理程序\] 索引標籤上的 \[使用者名稱\] 資料行。|  
    |[\/crosssession](../profiling/crosssession.md)|對其他工作階段中的處理序啟用程式碼剖析。  如果應用程式在不同的工作階段中執行，就必須有這個選項。  工作階段 ID 列於 \[Windows 工作管理員\] 之 \[處理程序\] 索引標籤上的 \[工作階段識別碼\] 資料行。  **\/CS** 可以當做 **\/crosssession** 的縮寫來指定。|  
    |[\/waitstart](../profiling/waitstart.md)\[**:**`Interval`\]|指定在程式碼剖析工具傳回錯誤之前，等候它初始化的秒數。  如果未指定 `Interval`，程式碼剖析工具會一直等待。  根據預設，**\/start** 會立即傳回。|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|若要在暫停資料收集的情況下啟動程式碼剖析工具，請將 **\/globaloff** 選項加入至 **\/start** 命令列。  使用 **\/globalon** 繼續程式碼剖析。|  
    |[\/counter](../profiling/counter.md) **:** `Config`|從 Config 中指定的處理器效能計數器收集資訊。  計數器資訊會加入至每個程式碼剖析事件收集的資料中。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定程式碼剖析期間要收集的 Windows 效能計數器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|僅能與 **\/wincounter** 搭配使用。  指定 Windows 效能計數器收集事件之間的毫秒數。  預設為 500 毫秒。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定程式碼剖析期間要收集的 Windows 事件追蹤 \(ETW\) 事件。  ETW 事件是在不同的 \(.etl\) 檔案中收集的。|  
  
8.  從 \[Windows 服務控制管理員\] 啟動服務。  
  
## 控制資料收集  
 當服務執行時，您可以使用 **VSPerfCmd.exe** 選項，啟動及停止將資料寫入程式碼剖析工具資料檔案。  控制資料收集可讓您收集特定程式執行部分的資料，例如服務的開始或結束。  
  
#### 若要啟動和停止資料收集  
  
-   下列 **VSPerfCmd** 選項配對會啟動和停止資料收集。  在不同的命令列上指定每個選項。  您可以多次開啟或關閉資料收集。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|啟動 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有處理序的資料收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|啟動 \(**\/processon**\) 或停止 \(**\/processoff**\) 對處理序 ID \(`PID`\) 所指定的處理序進行資料收集。|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|啟動 \(**\/threadon**\) 或停止 \(**\/threadoff**\) 對執行緒 ID \(`TID`\) 所指定的執行緒進行資料收集。|  
  
## 結束程式碼剖析工作階段  
 若要結束程式碼剖析工作階段，請關閉執行檢測元件的應用程式，然後呼叫 **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) 選項以關閉程式碼剖析工具，並關閉程式碼剖析資料檔案。  **VSPerfClrEnv \/globaloff** 命令會清除程式碼剖析環境變數。  
  
 您必須重新啟動電腦，才能套用新的環境設定。  
  
#### 若要結束程式碼剖析工作階段  
  
1.  從 \[服務控制管理員\] 停止服務。  
  
2.  關閉程式碼剖析工具。  型別：  
  
     **VSPerfCmd \/shutdown**  
  
3.  當您完成所有程式碼剖析時，請清除程式碼剖析環境變數。  型別：  
  
     **VSPerfClrEnv \/globaloff**  
  
4.  將檢測模組替換成原始模組。  如有必要，請重新設定服務的啟動類型。  
  
5.  重新啟動電腦。  
  
## 請參閱  
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)   
 [檢測方法資料檢視](../profiling/instrumentation-method-data-views.md)