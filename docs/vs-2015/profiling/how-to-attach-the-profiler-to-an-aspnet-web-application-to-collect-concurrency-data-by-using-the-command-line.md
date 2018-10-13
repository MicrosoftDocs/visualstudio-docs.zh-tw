---
title: 如何：使用命令列將程式碼剖析工具附加至 ASP.NET Web 應用程式以收集並行資料 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0e215fdd-55f8-43ef-9534-06542eefe223
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a3428e2de8475109a7b6277ac5e61fc6a87d1768
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49194242"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line"></a>如何：使用命令列將程式碼剖析工具附加至 ASP.NET Web 應用程式以收集並行資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題描述如何使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 程式碼剖析工具命令列工具將程式碼剖析工具附加至 ASP.NET 應用程式，並收集處理序和執行緒並行資料。  
  
 程式碼剖析工具的命令列工具位於 Visual Studio 安裝目錄的 \Team Tools\Performance Tools 子目錄中。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要在命令提示字元使用程式碼剖析工具，必須將工具路徑加入至**命令提示字元**視窗的 PATH 環境變數，或將它加入至命令本身。 如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
 若要收集並行資料，您可以將程式碼剖析工具附加至裝載您的網站的 ASP.NET 背景工作處理序。 程式碼剖析工具附加至應用程式時，您可以暫停和繼續收集資料。 若要結束程式碼剖析工作階段，程式碼剖析工具不得再附加至應用程式，而且必須明確地關閉程式碼剖析工具。 在大部分情況下，您應在工作階段結束時清除程式碼剖析環境變數。  
  
## <a name="attaching-the-profiler"></a>附加程式碼剖析工具  
  
#### <a name="to-attach-the-profiler-to-a-aspnet-application"></a>將程式碼剖析工具附加至 ASP.NET 應用程式  
  
1.  輸入下列命令以啟動程式碼剖析工具︰  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency /output:** `OutputFile` [`Options`]  
  
    -   [/start](../profiling/start.md)選項會初始化程式碼分析工具以收集資源爭用資料。  
  
    -   [/output](../profiling/output.md)**:**`OutputFile` 選項必須搭配 **/start** 使用。 `OutputFile` 指定程式碼剖析資料 (.vsp) 檔案的名稱和位置。  
  
     您可以使用下表中的任一選項搭配 **/start** 選項。  
  
    |選項|描述|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain\`]`UserName`|指定要授與程式碼剖析工具存取權之帳戶的選擇性網域和使用者名稱。|  
    |[/crosssession](../profiling/crosssession.md)|在其他登入工作階段啟用處理序程式碼剖析。|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定程式碼剖析期間要收集的 Windows 效能計數器。|  
    |[/automark](../profiling/automark.md) **:** `Interval`|只能搭配 **/wincounter** 使用。 指定 Windows 效能計數器收集事件間隔的毫秒數。 預設值為 500。|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定程式碼剖析期間要收集的 Windows 事件追蹤 (ETW) 事件。 ETW 事件會收集至個別的 (.etl) 檔案。|  
  
2.  以一般方式啟動 ASP.NET 應用程式。  
  
3.  輸入下列命令，將程式碼剖析工具附加至 ASP.NET 背景工作處理序︰**VSPerfCmd /attach:**`PID` [**/targetclr:**`Version`]  
  
    -   `PID`指定 ASP.NET 背景工作處理序的識別碼或名稱。 您可以在 [Windows 工作管理員] 中檢視所有執行中處理序的處理序 ID。  
  
    -   [/targetclr](../profiling/targetclr.md) **:** `Version` 指定當應用程式載入多個版本的執行階段時要分析的 Common Language Runtime (CLR) 版本。 這是選擇性參數。  
  
## <a name="controlling-data-collection"></a>控制資料收集  
 當應用程式執行時，您可以使用 VSPerfCmd.exe 選項開始和停止將資料寫入至檔案，以控制資料收集。 透過控制資料收集，您可以收集特定程式執行 (例如啟動或關閉應用程式) 的資料。  
  
#### <a name="to-start-and-stop-data-collection"></a>開始和停止資料收集  
  
-   下表中成對的 VSPerfCmd 選項會開始和停止資料收集。 請在個別的命令列上指定各個選項。 您可以多次開始和停止資料收集。  
  
    |選項|描述|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|開始 (**/globalon**) 或停止 (**/globaloff**) 所有處理序的資料收集。|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID`  [processoff](../profiling/processon-and-processoff.md) **:** `PID`|開始 (**/processon**) 或停止 (**/processoff**) 處理序 ID (`PID`) 指定的處理序資料收集。|  
    |[/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/attach** 會開始為處理序 ID (`PID`) 或處理序名稱 (*ProcName*) 指定的處理序收集資料。 **/detach** 會停止指定的處理序或所有處理序 (如果未指定處理序) 的資料收集。|  
  
## <a name="ending-the-profiling-session"></a>結束程式碼剖析工作階段  
 若要結束程式碼剖析工作階段，程式碼剖析工具不得進行資料收集。 您可以重新啟動 ASP.NET 背景工作處理序或叫用 **VSPerfCmd /detach** 選項，以停止從使用並行方法剖析的應用程式中收集資料。 接著叫用 **VSPerfCmd /shutdown** 選項以停止程式碼剖析工具，並關閉程式碼剖析資料檔案。 **VSPerfClrEnv /globaloff** 命令會清除程式碼剖析環境變數，但在重新啟動電腦之前不會重設系統組態。  
  
#### <a name="to-end-a-profiling-session"></a>結束程式碼剖析工作階段  
  
1.  關閉目標應用程式或在命令提示字元中輸入下列命令，以將程式碼剖析工具從目標應用程式中斷連結︰  
  
     **VSPerfCmd /detach**  
  
2.  在命令提示字元中輸入下列命令，以關閉程式碼剖析工具︰  
  
     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)  
  
## <a name="see-also"></a>另請參閱  
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [使用 VSPerfASPNETCmd 快速進行網站程式碼剖析](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)



