---
title: "如何：使用程式碼剖析工具命令列檢測動態編譯的 ASP.NET Web 應用程式並收集記憶體資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用程式碼剖析工具命令列檢測動態編譯的 ASP.NET Web 應用程式並收集記憶體資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題說明如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具命令列工具，透過檢測程式碼剖析方法來為動態編譯的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式收集詳細的 .NET 記憶體配置和物件存留期資料。  
  
> [!NOTE]
>  程式碼剖析工具的命令列工具位於 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 安裝目錄的 \\Team Tools\\Performance Tools 子目錄中。  在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。  若要使用程式碼剖析工具的命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。  如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
 若要收集 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式的效能資料，您可以修改目標應用程式的 web.config 檔案啟用 [VSInstr.exe](../profiling/vsinstr.md) 工具，以檢測動態編譯的應用程式檔案。  然後使用 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 工具設定裝載 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式的伺服器，並且設定適當的環境變數以啟用 .NET 記憶體程式碼剖析，再重新啟動電腦。  
  
 若要收集資料，請啟動程式碼剖析工具，然後執行目標應用程式。  程式碼剖析工具會附加至應用程式時，您可以暫停和繼續資料收集。當您收集到適當的資料時，依序關閉應用程式、Internet Information Services \(IIS\) 背景工作處理序，再關閉程式碼剖析工具。  
  
 完成程式碼剖析工作時，將 web.config 檔案和 Web 伺服器還原為原始狀態。  
  
## 設定 ASP.NET Web 應用程式和 Web 伺服器  
  
#### 若要設定 ASP.NET Web 應用程式和 Web 伺服器  
  
1.  修改目標應用程式的 web.config 檔案。  請參閱 [如何：修改 Web.Config 檔案以檢測並分析動態編譯的 ASP.NET Web 應用程式](../Topic/How%20to:%20Modify%20Web.Config%20Files%20to%20Instrument%20and%20Profile%20Dynamically%20Compiled%20ASP.NET%20Web%20Applications.md)。  
  
2.  在裝載 Web 應用程式的電腦上開啟命令提示字元視窗。  
  
3.  初始化程式碼剖析環境變數。  型別：  
  
     **VSPerfClrEnv \/globaltracegc**  
  
     \-或\-  
  
     **VSPerfClrEnv \/globaltracegclife**  
  
    -   **\/globaltracegc** 可啟用記憶體配置資料的收集功能。  
  
    -   **\/globaltracegclife** 可啟用記憶體配置資料和物件存留期資料的收集功能。  
  
4.  重新啟動電腦。  
  
## 執行程式碼剖析工作階段  
  
#### 若要對 ASP.NET Web 應用程式進行程式碼剖析  
  
1.  啟動程式碼剖析工具。  型別：  
  
     **VSPerfCmd** [\/start](../profiling/start.md)**:trace** [\/output](../profiling/output.md)**:**`OutputFile` \[`Options`\]  
  
    -   **\/start:trace** 選項會初始化程式碼剖析工具。  
  
    -   **\/output:** `OutputFile` 選項必須搭配 **\/start** 使用。  `OutputFile` 指定程式碼剖析資料 \(.vsp\) 檔案的名稱和位置。  
  
     下列任何選項都可以搭配 **\/start:trace** 選項使用。  
  
    > [!NOTE]
    >  ASP.NET 應用程式通常需要 **\/user** 和 **\/crosssession** 選項。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|指定擁有 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序之帳戶的選擇性網域和使用者名稱。  如果處理序是以非登入使用者的身分執行，就必須有這個選項。  該名稱會列於 \[Windows 工作管理員\] 的 \[處理程序\] 索引標籤上的 \[使用者名稱\] 資料行。|  
    |[\/crosssession](../profiling/crosssession.md)|對其他工作階段中的處理序啟用程式碼剖析。  如果應用程式在不同的工作階段中執行，就必須有這個選項。  工作階段 ID 列於 \[Windows 工作管理員\] 之 \[處理程序\] 索引標籤上的 \[工作階段識別碼\] 資料行。  **\/CS** 可以當做 **\/crosssession** 的縮寫來指定。|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|在暫停資料收集的情況下，啟動程式碼剖析工具。  使用 [\/globalon](../profiling/globalon-and-globaloff.md) 繼續程式碼剖析。|  
    |[\/counter](../profiling/counter.md) **:** `Config`|從 `Config` 中指定的處理器效能計數器收集資訊。  計數器資訊會加入至每個程式碼剖析事件收集的資料中。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定程式碼剖析期間要收集的 Windows 效能計數器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|僅能與 **\/wincounter** 搭配使用。  指定 Windows 效能計數器收集事件之間的毫秒數。  預設為 500 毫秒。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定程式碼剖析期間要收集的 Windows 事件追蹤 \(ETW\) 事件。  ETW 事件是在不同的 \(.etl\) 檔案中收集的。|  
  
2.  以一般方式啟動 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式。  
  
## 控制資料收集  
 當目標應用程式正在執行時，您可以使用 **VSPerfCmd.exe** 選項，啟動及停止將資料寫入程式碼剖析工具資料檔案，以控制資料收集。  資料收集控制可讓您收集程式執行中特定組件的資料，例如應用程式的開始與結束。  
  
#### 若要啟動和停止資料收集  
  
-   下列選項配對會啟動和停止資料收集。  在不同的命令列上指定每個選項。  您可以多次開啟或關閉資料收集。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|啟動 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有處理序的資料收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|啟動 \(**\/processon**\) 或停止 \(**\/processoff**\) 對處理序 ID \(`PID`\) 所指定的處理序進行資料收集。|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|啟動 \(**\/threadon**\) 或停止 \(**\/threadoff**\) 對執行緒 ID \(`TID`\) 所指定的執行緒進行資料收集。|  
  
-   您也可以使用 **VSPerfCmd.exe** [\/mark](../profiling/mark.md) 選項，將程式碼剖析標記插入資料檔案。  **\/mark** 命令會加入識別項、時間戳記和選擇性使用者定義的文字字串。  標記可用來篩選程式碼剖析工具報告和資料檢視中的資料。  
  
## 結束程式碼剖析工作階段  
 若要結束程式碼剖析工作階段，請關閉目標 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式，停止 Internet Information Services \(IIS\) 以停止進行程式碼剖析的處理序，然後關閉程式碼剖析工具。  接著重新啟動 IIS。  
  
#### 若要結束程式碼剖析工作階段  
  
1.  關閉 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式。  
  
2.  重設網際網路資訊服務 \(IIS\) 以關閉 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序。  型別：  
  
     **IISReset \/stop**  
  
3.  關閉程式碼剖析工具。  型別：  
  
     **VSPerfCmd** [\/shutdown](../profiling/shutdown.md)  
  
4.  重新啟動 IIS。  型別：  
  
     **IISReset \/start**  
  
## 還原應用程式和電腦組態  
 完成所有程式碼剖析時，請取代 web.config 檔案、清除程式碼剖析環境變數，然後重新啟動電腦，將伺服器和 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式還原為原始狀態。  
  
#### 若要還原應用程式和電腦組態  
  
1.  以原始檔案複本取代 web.config 檔案。  
  
2.  \(選擇性\)  清除程式碼剖析環境變數。  型別：  
  
     **VSPerfCmd \/globaloff**  
  
3.  重新啟動電腦。  
  
## 請參閱  
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [.NET 記憶體資料檢視](../profiling/dotnet-memory-data-views.md)