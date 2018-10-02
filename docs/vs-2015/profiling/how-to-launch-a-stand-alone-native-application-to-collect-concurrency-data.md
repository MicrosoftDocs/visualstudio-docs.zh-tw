---
title: 如何：使用命令列搭配分析工具啟動獨立的原生應用程式以收集並行資料 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e5aed651-afed-4b70-9a7e-1a6032cc614f
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5060b22603f5cab408e6f15a9f33f104e76cd7bf
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "47588613"
---
# <a name="how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>如何：使用命令列搭配程式碼剖析工具啟動獨立的原生應用程式以收集並行資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 使用命令列啟動獨立原生應用程式使用 Profiler 收集並行資料](https://docs.microsoft.com/visualstudio/profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line)。  
  
本主題描述如何使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 程式碼剖析工具命令列工具啟動原生的獨立 (用戶端) 應用程式，並收集處理序和執行緒並行資料。  
  
 程式碼剖析工作階段分成下列幾個部分︰  
  
-   使用程式碼剖析工具啟動應用程式  
  
-   控制資料收集  
  
-   結束程式碼剖析工作階段  
  
> [!NOTE]
>  程式碼剖析工具的命令列工具位於 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 安裝目錄的 \Team Tools\Performance Tools 子目錄中。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要在命令提示字元使用程式碼剖析工具，必須將工具路徑加入至**命令提示字元**視窗的 PATH 環境變數，或將它加入至命令本身。 如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  
  
## <a name="starting-the-application-with-the-profiler"></a>使用程式碼剖析工具啟動應用程式  
 若要使用程式碼剖析工具啟動目標應用程式，請使用 [VSPerfCmd.exe](../profiling/vsperfcmd.md)**/start** 和 **/launch** 選項初始化程式碼剖析工具，並啟動應用程式。 您可以指定 **/start** 和 **/launch** 及其個別選項。 您也可以加入 **/globaloff** 選項以在目標應用程式啟動時暫停資料收集。 然後使用 **/globalon** 開始收集資料。  
  
#### <a name="to-start-an-application-with-the-profiler"></a>使用程式碼剖析工具啟動應用程式  
  
1.  在命令提示字元中，輸入下列命令：  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency  /output:** `OutputFile` [`Options`]  
  
     [/output](../profiling/output.md)**:**`OutputFile` 選項必須搭配 **/start** 使用。 `OutputFile` 指定程式碼剖析資料 (.vsp) 檔案的名稱和位置。  
  
     您可以使用下表中的任一選項搭配 **/start:concurrency** 選項。  
  
    |選項|描述|  
    |------------|-----------------|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|指定程式碼剖析期間要收集的 Windows 效能計數器。|  
    |[/automark](../profiling/automark.md) **:** `Interval`|只能搭配 **/wincounter** 使用。 指定 Windows 效能計數器收集事件間隔的毫秒數。 預設值為 500。|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|指定程式碼剖析期間要收集的 Windows 事件追蹤 (ETW) 事件。 ETW 事件會收集至個別的 (.etl) 檔案。|  
  
2.  輸入下列命令以啟動目標應用程式：  
  
     **VSPerfCmd**  [/launch](../profiling/launch.md) **:** `AppName` [`Options`]  
  
     您可以使用下表中的任一選項搭配 **/launch** 選項。  
  
    |選項|描述|  
    |------------|-----------------|  
    |[/args](../profiling/args.md) **:** `Arguments`|指定包含要傳遞至目標應用程式的命令列引數的字串。|  
    |[/console](../profiling/console.md)|在個別的視窗中啟動目標命令列應用程式。|  
    |[/targetclr](../profiling/targetclr.md) **:** `CLRVersion`|指定當應用程式載入多個版本的 Common Language Runtime (CLR) 時要分析的 CLR 版本。|  
  
## <a name="controlling-data-collection"></a>控制資料收集  
 當目標應用程式執行時，您可以使用 VSPerfCmd.exe 選項開始和停止將資料寫入至檔案，以控制資料收集。 透過控制資料收集，您可以收集特定程式執行 (例如啟動或關閉應用程式) 的資料。  
  
#### <a name="to-start-and-stop-data-collection"></a>開始和停止資料收集  
  
-   下表中成對的選項會開始和停止資料收集。 請在個別的命令列上指定各個選項。 您可以多次開始和停止資料收集。  
  
    |選項|描述|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|開始 (**/globalon**) 或停止 (**/globaloff**) 所有處理序的資料收集。|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|開始 (**/processon**) 或停止 (**/processoff**) 處理序 ID (`PID`) 指定的處理序資料收集。|  
    |[/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/attach** 會開始為處理序 ID (`PID`) 或處理序名稱 (*ProcName*) 指定的處理序收集資料。 **/detach** 會停止指定的處理序或所有處理序 (如果未指定處理序) 的資料收集。|  
  
-   您也可以使用 **VSPerfCmd.exe**[/mark](../profiling/mark.md) 選項將程式碼剖析標記插入資料檔案。 **/mark** 命令會新增識別碼、時間戳記和一個選擇性的使用者定義文字字串。 標記可用來篩選程式碼剖析工具報告和資料檢視中的資料。  
  
## <a name="ending-the-profiling-session"></a>結束程式碼剖析工作階段  
 若要結束程式碼剖析工作階段，程式碼剖析工具不得進行資料收集。 您可以關閉分析的應用程式或叫用 **VSPerfCmd /detach**選項，以停止收集並行資料。 接著叫用 **VSPerfCmd /shutdown** 選項以停止程式碼剖析工具，並關閉程式碼剖析資料檔案。  
  
#### <a name="to-end-a-profiling-session"></a>結束程式碼剖析工作階段  
  
1.  關閉目標應用程式或在命令提示字元中輸入下列命令，以將程式碼剖析工具從目標應用程式中斷連結︰  
  
     **VSPerfCmd /detach**  
  
2.  在命令提示字元中輸入下列命令，以關閉程式碼剖析工具︰  
  
     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)



