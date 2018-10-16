---
title: 如何：從命令列使用程式碼剖析工具以檢測獨立的 .NET Framework 元件並收集記憶體資料 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d09cc46a-70f5-48f9-aa24-89913e67b359
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1650a228679a6ab4a84f71e09b3c548928d41587
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49214730"
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line"></a>如何：從命令列使用程式碼剖析工具以檢測獨立的 .NET Framework 元件並收集記憶體資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題描述如何使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 程式碼剖析工具命令列工具來檢測獨立應用程式的 .NET Framework 元件，例如 .exe 或 .dll 檔案，並使用程式碼剖析工具來收集記憶體資訊。  
  
> [!NOTE]
>  程式碼剖析工具的命令列工具位於 Visual Studio 安裝目錄的 \Team Tools\Performance Tools 子目錄中。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要使用程式碼剖析工具命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。 如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
 若要使用檢測方法從 .NET Framework 元件收集記憶體資料，可以使用 [VSInstr.exe](../profiling/vsinstr.md) 工具來產生已檢測版的元件，並使用 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 工具來初始化程式碼剖析環境變數。 然後使用 **VSPerfCmd.exe** 工具啟動程式碼剖析工具。  
  
 執行已檢測的元件時，記憶體資料會自動收集到資料檔案。 程式碼剖析工作階段期間，您可以暫停和繼續資料收集。  
  
 若要結束程式碼剖析工作階段，必須關閉目標應用程式，並明確地關閉程式碼剖析工具。 在大部分情況下，建議您在工作階段結束時清除程式碼剖析環境變數。  
  
## <a name="starting-the-application-with-the-profiler"></a>使用程式碼剖析工具啟動應用程式  
  
#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>將程式碼剖析工具附加至執行中的 .NET Framework 應用程式  
  
1.  開啟 [命令提示字元] 視窗。  
  
2.  使用 [VSInstr] 工具產生已檢測版的目標應用程式。  
  
3.  初始化 .NET Framework 程式碼剖析環境變數。 類型：  
  
     **VSPerfClrEnv** {**/tracegc** &#124; **/tracegclife**}  
  
    -   **/tracegc** 和 **/tracegclife** 選項會初始化環境變數，只收集記憶體配置資料，或同時收集記憶體配置和物件存留期資料。  
  
        |選項|描述|  
        |------------|-----------------|  
        |**/tracegc**|只收集記憶體配置資料。|  
        |**/tracegclife**|收集記憶體配置和物件存留期資料。|  
  
4.  啟動分析工具。 類型：  
  
     **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]  
  
    -   [/start](../profiling/start.md)**:trace** 選項會初始化程式碼剖析工具。  
  
    -   [/output](../profiling/output.md)**:**`OutputFile` 選項必須搭配 **/start** 使用。 `OutputFile` 指定程式碼剖析資料 (.vsp) 檔案的名稱和位置。  
  
     您可以使用下列任一選項搭配 **/start:trace** 選項。  
  
    |選項|描述|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|指定擁有程式碼剖析處理序之帳戶的網域和使用者名稱。 只有在以登入的使用者之外的使用者身分執行處理序時，才需要這個選項。 處理序擁有者會列在 [Windows 工作管理員] 的 [處理程序] 索引標籤上的 [使用者名稱] 欄。|  
    |[/crosssession](../profiling/crosssession.md)|在其他工作階段啟用處理序程式碼剖析。 如果應用程式在不同的工作階段中執行，則需要這個選項。 工作階段識別碼會列在 [Windows 工作管理員] 的 [處理程序] 索引標籤上的 [工作階段識別碼] 欄。 **/crosssession** 可縮寫成 **/CS**。|  
    |[/globaloff](../profiling/globalon-and-globaloff.md)|若要啟動暫停資料收集的程式碼剖析工具，請將 **/globaloff** 選項新增到 **/start** 命令列。 使用 **/globalon** 以繼續程式碼剖析。|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定程式碼剖析期間要收集的 Windows 效能計數器。|  
    |[/automark](../profiling/automark.md) **:** `Interval`|只能搭配 **/wincounter** 使用。 指定 Windows 效能計數器收集事件間隔的毫秒數。 預設值為 500 毫秒。|  
    |[/counter](../profiling/counter.md) **:** `Config`|從 Config 中指定的處理器效能計數器收集資訊。計數器資訊會新增至在每個程式碼剖析事件收集的資料。|  
    |[events](../profiling/events-vsperfcmd.md) **:** `Config`|指定程式碼剖析期間要收集的 Windows 事件追蹤 (ETW) 事件。 ETW 事件會收集至個別的 (.etl) 檔案。|  
  
5.  從命令提示字元視窗啟動目標應用程式。  
  
## <a name="controlling-data-collection"></a>控制資料收集  
 當目標應用程式執行時，您可以使用 **VSPerfCmd.exe** 選項開始和停止將資料寫入至檔案，以控制資料收集。 控制資料收集可讓您收集特定程式執行 (例如啟動或關閉應用程式) 的資料。  
  
#### <a name="to-start-and-stop-data-collection"></a>開始和停止資料收集  
  
-   下列成對的 **VSPerfCmd** 選項會開始和停止資料收集。 請在個別的命令列上指定各個選項。 您可以多次開始和停止資料收集。  
  
    |選項|描述|  
    |------------|-----------------|  
    |[/globalon](../profiling/globalon-and-globaloff.md) [/globaloff](../profiling/globalon-and-globaloff.md)|開始 (**/globalon**) 或停止 (**/globaloff**) 所有處理序的資料收集。|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|開始 (**/processon**) 或停止 (**/processoff**) 處理序 ID (`PID`) 指定的處理序資料收集。|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|開始 (**/threadon**) 或停止 (**/threadoff**) 執行緒識別碼 (`TID`) 指定的執行緒資料收集。|  
  
## <a name="ending-the-profiling-session"></a>結束程式碼剖析工作階段  
 若要結束程式碼剖析工作階段，請關閉正在執行已檢測元件的應用程式，然後呼叫 **VSPerfCmd** [/shutdown](../profiling/shutdown.md) 選項以關閉程式碼剖析工具，並關閉程式碼剖析資料檔案。 **VSPerfClrEnv /off** 命令會清除程式碼剖析環境變數。  
  
#### <a name="to-end-a-profiling-session"></a>結束程式碼剖析工作階段  
  
1.  關閉目標應用程式。  
  
2.  關閉分析工具。 類型：  
  
     **VSPerfCmd /shutdown**  
  
3.  (選擇性) 清除程式碼剖析環境變數。 類型：  
  
     **VSPerfCmd /off**  
  
## <a name="see-also"></a>另請參閱  
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [.NET 記憶體資料檢視](../profiling/dotnet-memory-data-views.md)



