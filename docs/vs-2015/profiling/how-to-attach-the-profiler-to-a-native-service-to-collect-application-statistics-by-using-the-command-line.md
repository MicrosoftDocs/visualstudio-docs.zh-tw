---
title: HOW TO：使用命令列將分析工具附加至原生服務以收集應用程式統計資料 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f783817f-77a0-4eb8-985b-ec3b77eadc42
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 214a7fc8144d50dac52a5be1b45d9d5fc2b4a633
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60078599"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line"></a>HOW TO：Profiler 附加至原生服務以使用命令列收集應用程式統計資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題描述如何使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 分析工具命令列工具將分析工具附加至 原生服務，並使用取樣方法收集效能統計資料。  

> [!NOTE]
>  Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 Windows 市集應用程式也需要新的資料收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  

> [!NOTE]
>  程式碼剖析工具的命令列工具位於 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 安裝目錄的 \Team Tools\Performance Tools 子目錄中。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要使用程式碼剖析工具命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。 如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。  

 程式碼剖析工具附加至服務時，您可以暫停和繼續收集資料。  

 若要結束分析工作階段，必須從服務中斷連結分析工具，而且必須明確地關閉分析工具。  

## <a name="starting-the-application-with-the-profiler"></a>使用程式碼剖析工具啟動應用程式  
 若要將分析工具附加至原生服務，請使用 **VSPerfCmd.exe**[/start](../profiling/start.md) 和 [/attach](../profiling/attach.md) 選項來初始化分析工具，並將它附加至目標應用程式。 您可以在單一命令列上指定 **/start** 和 **/attach** 及其個別選項。 您也可以加入 [/globaloff](../profiling/globalon-and-globaloff.md) 選項以在目標應用程式啟動時暫停資料收集。 接著可使用 [/globalon](../profiling/globalon-and-globaloff.md) 開始收集資料。  

#### <a name="to-attach-the-profiler-to-a-native-service"></a>將程式碼剖析工具附加至原生服務  

1. 如有必要，請啟動服務。  

2. 開啟 [命令提示字元] 視窗。  

3. 啟動分析工具。 類型：  

    **VSPerfCmd /start:sample**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  

   - **/start:sample** 選項會初始化分析工具。  

   - **/output:**`OutputFile` 選項必須搭配 **/start** 使用。 `OutputFile` 指定程式碼剖析資料 (.vsp) 檔案的名稱和位置。  

     您可以使用下列任一選項搭配 **/start:sample** 選項。  

   > [!NOTE]
   >  **/User** 和 **/crosssession** 選項通常是服務的必要選項。  

   |                                 選項                                  |                                                                                                                                            描述                                                                                                                                             |
   |-------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` |        指定擁有程式碼剖析處理序之帳戶的網域和使用者名稱。 只有在以登入的使用者之外的使用者身分執行處理序時，才需要這個選項。 處理序擁有者會列在 [Windows 工作管理員] 的 [處理程序] 索引標籤上的 [使用者名稱] 欄。         |
   |              [/crosssession](../profiling/crosssession.md)              | 在其他工作階段啟用處理序程式碼剖析。 如果應用程式在不同的工作階段中執行，則需要這個選項。 工作階段識別碼會列在 [Windows 工作管理員] 的 [處理程序] 索引標籤上的 [工作階段識別碼] 欄。 **/crosssession** 可縮寫成 **/CS**。 |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                             指定程式碼剖析期間要收集的 Windows 效能計數器。                                                                                                              |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                           只能搭配 **/wincounter** 使用。 指定 Windows 效能計數器收集事件間隔的毫秒數。 預設值為 500 毫秒。                                                                            |
   |       [/events](../profiling/events-vsperfcmd.md) **:** `Config`        |                                                                              指定程式碼剖析期間要收集的 Windows 事件追蹤 (ETW) 事件。 ETW 事件會收集至個別的 (.etl) 檔案。                                                                              |

4. 將程式碼剖析工具附加至服務。 類型：  

    **VSPerfCmd /attach:** `PID` [`Sample Event`]  

    `PID` 指定目標應用程式的處理序 ID。 您可以在 [Windows 工作管理員] 中檢視所有執行中處理序的處理序 ID。  

    根據預設，每經過 10,000,000 個未暫止處理器時脈週期，會取樣一次效能資料。 在 1GH 處理器上，這大約是每 10 秒一次。 您可以指定下列任一選項來變更時脈週期間隔，或指定不同的取樣事件。  

   |取樣事件|描述|  
   |------------------|-----------------|  
   |[/timer](../profiling/timer.md) **:** `Interval`|將取樣間隔變更為 `Interval` 指定的未暫止時脈週期數。|  
   |[/pf](../profiling/pf.md)[**:**`Interval`]|將取樣事件變更為分頁錯誤。 如果指定 `Interval`，請設定樣本間的分頁錯誤數。 預設值為 10。|  
   |[/sys](../profiling/sys-vsperfcmd.md) [**:**`Interval`]|將取樣事件從處理器變更為作業系統核心的系統呼叫 (syscalls)。 如果指定 `Interval`，請設定樣本間的呼叫數。 預設值為 10。|  
   |[/counter](../profiling/counter.md) **:** `Config`|將取樣事件與間隔變更為 `Config` 中指定的處理器效能計數器與間隔。|  

## <a name="controlling-data-collection"></a>控制資料收集  
 當目標應用程式執行時，您可以使用 **VSPerfCmd.exe** 選項開始和停止將資料寫入至分析工具資料檔案。 控制資料收集可讓您收集特定程式執行 (例如啟動或關閉應用程式) 的資料。  

#### <a name="to-start-and-stop-data-collection"></a>開始和停止資料收集  

- 下列成對的 **VSPerfCmd** 選項會開始和停止資料收集。 請在個別的命令列上指定各個選項。 您可以多次開始和停止資料收集。  

    |選項|描述|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|開始 (**/globalon**) 或停止 (**/globaloff**) 所有處理序的資料收集。|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|開始 (**/processon**) 或停止 (**/processoff**) 處理序 ID (`PID`) 指定的處理序資料收集。|  
    |**/attach:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[:{`PID`&#124;`ProcName`}]|**/attach** 會開始為處理序 ID 或處理序名稱指定的處理序收集資料。 **/detach** 會停止指定的處理序或所有處理序 (如果未指定處理序) 的資料收集。|  

## <a name="ending-the-profiling-session"></a>結束程式碼剖析工作階段  
 若要結束分析工作階段，必須從服務中斷連結分析工具，然後明確地將它關閉。 您可以停止服務或呼叫 **VSPerfCmd /detach** 選項，將使用取樣方法分析的原生服務中斷連結。 接著呼叫 **VSPerfCmd** [/shutdown](../profiling/shutdown.md) 選項以關閉分析工具，並關閉分析資料檔案。  

#### <a name="to-end-a-profiling-session"></a>結束程式碼剖析工作階段  

1. 執行下列其中一項動作，以從目標應用程式中斷連結分析工具：  

    - 停止服務。  

         -或-  

    - 輸入 **VSPerfCmd /detach**  

2. 關閉分析工具。 類型：  

     **VSPerfCmd /shutdown**  

## <a name="see-also"></a>另請參閱  
 [分析服務](../profiling/command-line-profiling-of-services.md)   
 [取樣方法資料檢視](../profiling/profiler-sampling-method-data-views.md)
