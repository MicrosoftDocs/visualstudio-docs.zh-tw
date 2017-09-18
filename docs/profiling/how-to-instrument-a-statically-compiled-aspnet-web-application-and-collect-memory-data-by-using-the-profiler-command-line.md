---
title: "如何：使用程式碼剖析工具命令列檢測靜態編譯的 ASP.NET Web 應用程式並收集記憶體資料 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea1dcb7c-1dc3-49ff-9418-8795b5b3d3bc
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用程式碼剖析工具命令列檢測靜態編譯的 ASP.NET Web 應用程式並收集記憶體資料
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本主題說明如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具命令列工具檢測預先編譯的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 元件或網站，以及收集 .NET 記憶體配置、物件存留期和詳細的執行時間資料。  
  
> [!NOTE]
>  程式碼剖析工具的命令列工具位於 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 安裝目錄的 \\Team Tools\\Performance Tools 子目錄中。  在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。  若要使用程式碼剖析工具的命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。  如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
 若要使用檢測方法收集 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 元件中的資料，您可以使用 [VSInstr.exe](../profiling/vsinstr.md) 工具產生元件的已檢測版本。  在裝載該元件的電腦上，以檢測過的元件版本取代未經檢測的元件。  使用 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 工具初始化全域程式碼剖析環境變數，然後重新啟動主機電腦。  接著啟動程式碼剖析工具。  
  
 當執行檢測元件時，時間資料會自動收集至資料檔案。  您可以在程式碼剖析工作階段期間暫停和繼續資料收集。  
  
 若要結束程式碼剖析工作階段，請關閉裝載元件的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序，然後明確地關閉程式碼剖析工具。  在許多情況下，我們建議在工作階段結尾清除程式碼剖析環境變數。  
  
## 啟動程式碼剖析  
  
#### 若要檢測 ASP.NET Web 元件並啟動程式碼剖析  
  
1.  使用 **VSInstr** 工具產生目標應用程式的檢測版本。  如有必要，請以檢測過的二進位檔來取代 ASP.NET 主機電腦上的應用程式二進位檔。  
  
2.  開啟命令提示字元視窗。  
  
3.  初始化 .NET 程式碼剖析環境變數。  在命令提示字元視窗中，輸入：  
  
     **VSPerfClrEnv \/globaltracegc**  
  
     \-或\-  
  
     **VSPerfClrEnv \/globaltracegclife**  
  
    -   **\/globaltracegc** 收集 .NET 記憶體配置和執行時間資料。  
  
    -   **\/globaltracegclife** 收集 .NET 記憶體配置、物件存留期和詳細的執行時間資料。  
  
4.  重新啟動電腦。  
  
5.  開啟命令提示字元視窗。  
  
6.  啟動程式碼剖析工具。  在命令提示字元視窗中，輸入：  
  
     **VSPerfCmd \/start:trace \/output:**`OutputFile` \[`Options`\]  
  
    -   [\/start](../profiling/start.md) **:trace** 選項會初始化程式碼剖析工具。  
  
    -   [\/output](../profiling/output.md) **:** `OutputFile` 選項必須搭配 **\/start** 使用。  `OutputFile` 指定程式碼剖析資料 \(.vsp\) 檔案的名稱和位置。  
  
     下列任何選項都可以搭配 **\/start:trace** 選項使用。  
  
    > [!NOTE]
    >  ASP.NET 應用程式通常需要 **\/user** 和 **\/crosssession** 選項。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|指定擁有 ASP.NET 背景工作處理序之帳戶的選擇性網域和使用者名稱。  如果處理序是以非登入使用者的身分執行，則這個選項是必要的。名稱會列在 \[Windows 工作管理員\] 的 \[處理程序\] 索引標籤上的 \[使用者名稱\] 欄中。|  
    |[\/crosssession](../profiling/crosssession.md)|對其他工作階段中的處理序啟用程式碼剖析。  如果應用程式在不同的工作階段中執行，就必須有這個選項。  工作階段 ID 列於 \[Windows 工作管理員\] 之 \[處理程序\] 索引標籤上的 \[工作階段識別碼\] 資料行。  **\/CS** 可以當做 **\/crosssession** 的縮寫來指定。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定程式碼剖析期間要收集的 Windows 效能計數器。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|僅能與 **\/wincounter** 搭配使用。  指定 Windows 效能計數器收集事件之間的毫秒數。  預設為 500 毫秒。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定程式碼剖析期間要收集的 Windows 事件追蹤 \(ETW\) 事件。  ETW 事件是在不同的 \(.etl\) 檔案中收集的。|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|若要在暫停資料收集的情況下啟動程式碼剖析工具，請將 **\/globaloff** 選項加入至 **\/start** 命令列。  使用 **\/globalon** 繼續程式碼剖析。|  
  
7.  開啟包含已檢測之元件的網站。  
  
## 控制資料收集  
 當目標應用程式正在執行時，您可以使用 **VSPerfCmd.exe** 選項啟動及停止將資料寫入檔案，以控制資料收集。  資料收集控制可讓您收集程式執行中特定組件的資料，例如應用程式的開始與結束。  
  
#### 若要啟動和停止資料收集  
  
-   下列選項配對會啟動和停止資料收集。  在不同的命令列上指定每個選項。  您可以多次開啟或關閉資料收集。  
  
    |選項|描述|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|啟動 \(**\/globalon**\) 或停止 \(**\/globaloff**\) 所有處理序的資料收集。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|針對處理序 ID \(`PID`\) 所指定的處理序，啟動 \(**\/processon**\) 或停止 \(**\/processoff**\) 資料收集。|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|針對執行緒 ID \(`TID`\) 所指定的執行緒，啟動 \(**\/threadon**\) 或停止 \(**\/threadoff**\) 資料收集。|  
  
## 結束程式碼剖析工作階段  
 若要結束程式碼剖析工作階段，請關閉 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式，然後使用網際網路資訊服務 \(IIS\) **IISReset** 命令關閉 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序。  呼叫 **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) 選項，關閉程式碼剖析工具並關閉程式碼剖析資料檔案。  **VSPerfClrEnv \/globaloff** 命令會清除程式碼剖析環境變數。  您必須重新啟動電腦，才能套用新的環境設定。  
  
#### 若要結束程式碼剖析工作階段  
  
1.  關閉 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式。  
  
2.  關閉 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序。  型別：  
  
     **IISReset \/stop**  
  
3.  關閉程式碼剖析工具。  型別：  
  
     **VSPerfCmd \/shutdown**  
  
4.  \(選擇性\)  清除程式碼剖析環境變數。  型別：  
  
     **VSPerfCmd \/globaloff**  
  
5.  重新啟動電腦。  若有必要，請重新啟動 IIS。  型別：  
  
     **IISReset \/start**  
  
## 請參閱  
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [.NET 記憶體資料檢視](../profiling/dotnet-memory-data-views.md)