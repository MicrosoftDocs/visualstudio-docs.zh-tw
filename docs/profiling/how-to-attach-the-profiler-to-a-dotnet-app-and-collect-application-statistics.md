---
title: 將分析工具附加至 .NET 獨立應用程式;取得應用程式統計資料
description: 瞭解如何使用 Visual Studio 分析工具命令列工具，將分析工具附加至執行中的 .NET Framework 獨立 (用戶端) 應用程式並取得統計資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: b62fcbc1-791f-474e-890a-a6c332e0c9ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 899a74894e34b43f87a7f45b4c4c90fff60088a1
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801140"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>如何：使用命令列將分析工具附加至 .NET Framework 獨立應用程式並收集應用程式統計資料
本文描述如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具命令列工具將分析工具附加到執行中的 .NET Framework 獨立 (用戶端) 應用程式，並使用取樣方法收集效能統計資料。

> [!NOTE]
> Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 UWP App 也需要新的收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。
>
> 若要取得分析工具的路徑，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要使用程式碼剖析工具命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。
>
> 若要將階層互動資料加入至程式碼剖析回合中，則需要使用命令列程式碼剖析工具的特定程序。 請參閱 [收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)。

 若要從 .NET Framework 應用程式收集效能資料，必須在目標應用程式啟動之前將適當的環境變數初始化。 分析工具附加至應用程式時，您可以暫停和繼續收集資料。

 若要結束分析工作階段，分析工具不得再附加至應用程式，而且必須明確地關閉分析工具。 在大部分情況下，建議您在分析工作階段結束時清除分析環境變數。

## <a name="attach-the-profiler"></a>附加分析工具

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>將分析工具附加至執行中的 .NET Framework 應用程式

1. 開啟命令提示字元視窗。

2. 初始化程式碼剖析環境變數。 輸入：

    **VSPerfClrEnv /sampleon** [**/samplelineoff**]

   - **/samplelineoff** 選項會停用原始程式碼行號資料的收集功能。

3. 啟動分析工具。 輸入：

    **>vsperfcmd/start：/output 範例：** `OutputFile` [`Options`]

   - [/start](../profiling/start.md)**:sample** 選項會初始化程式碼剖析工具。

   - /Start 需要 [/output](../profiling/output.md)**：** `OutputFile` 選項。  `OutputFile` 指定程式碼剖析資料 (.vsp) 檔案的名稱和位置。

     您可以使用下列任一選項搭配 **/start:sample** 選項。

   | 選項 | 描述 |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **：**[ `Domain` **\\** ]`UserName` | 針對擁有已分析處理序的帳戶，指定帳戶的選擇性網域和使用者名稱。 只有在受分析應用程式以不是登入的使用者啟動時，才需要此選項。 |
   | [/crosssession](../profiling/crosssession.md) | 在其他登入工作階段啟用處理序程式碼剖析。 **/crosssession** 可縮寫成 **/CS**。 如果應用程式在不同的工作階段中執行，則需要這個選項。 |
   | [/wincounter](../profiling/wincounter.md) **：**`WinCounterPath` | 指定程式碼剖析期間要收集的 Windows 效能計數器。 |
   | [/automark](../profiling/automark.md) **：**`Interval` | 只能搭配 **/wincounter** 使用。 指定 Windows 效能計數器收集事件間隔的毫秒數。 預設值為 500 毫秒。 |
   | [/events](../profiling/events-vsperfcmd.md) **：**`Config` | 指定程式碼剖析期間要收集的 Windows 事件追蹤 (ETW) 事件。 ETW 事件會收集在不同的 ( 中。*etl*) 檔。 |

4. 如有必要，請以一般方式啟動目標應用程式。

5. 將分析工具附加至目標應用程式。 輸入：

    **>vsperfcmd/attach：**{ `PID`&#124;`ProcessName` } [ `Sample Event` ] [**/targetclr：** `Version` ]

   - `PID` 指定目標應用程式的處理序 ID。 `ProcessName` 指定處理序的名稱。 請注意，如果您指定 `ProcessName` 且有多個名稱相同的處理序正在執行，則會發生無法預期的結果。 您可以在 [Windows 工作管理員] 中檢視所有執行中處理序的處理序 ID。

   - [/targetclr](../profiling/targetclr.md) **：** `Version` 指定在應用程式中載入多個版本的執行時間時要分析的 common language runtime (CLR) 的版本。 選擇性。

   - 根據預設，每經過 10,000,000 個未暫止處理器時脈週期，會取樣一次效能資料。 在 1GH 處理器上，這大約是每 10 秒一次。 您可以指定下列其中一個選項來變更頻率週期間隔，或指定不同的取樣事件。[/targetclr](../profiling/targetclr.md)**：** `Version` 指定在應用程式中載入多個版本的執行時間時要分析的 CLR 版本。 選擇性。

   |範例事件|描述|
   |-|-|
   |[/timer](../profiling/timer.md) **：**`Interval`|將取樣間隔變更為 `Interval` 指定的未暫止時脈週期數。|
   |[/pf](../profiling/pf.md) [**：** `Interval` ]|將取樣事件變更為分頁錯誤。 如果指定 `Interval`，請設定樣本間的分頁錯誤數。 預設值為 10。|
   |[/sys](../profiling/sys-vsperfcmd.md) [**：** `Interval` ]|將取樣事件從處理器變更為作業系統核心的系統呼叫 (syscalls)。 如果指定 `Interval`，請設定樣本間的呼叫數。 預設值為 10。|
   |[/counter](../profiling/counter.md) **：**`Config`|將取樣事件與間隔變更為 `Config` 中指定的處理器效能計數器與間隔。|

## <a name="control-data-collection"></a>控制資料收集
 當目標應用程式執行時，您可以使用 *VSPerfCmd.exe* 選項開始和停止將資料寫入至程式碼剖析資料檔案，以控制資料收集。 控制資料收集可讓您收集特定程式執行 (例如啟動或關閉應用程式) 的資料。

#### <a name="to-start-and-stop-data-collection"></a>開始和停止資料收集

- 下列成對的選項會開始和停止資料收集。 請在個別的命令列上指定各個選項。 您可以多次開始和停止資料收集。

    |選項|描述|
    |------------|-----------------|
    |[/globalon/globaloff](../profiling/globalon-and-globaloff.md)|開始 (**/globalon**) 或停止 (**/globaloff**) 所有處理序的資料收集。|
    |[/processon](../profiling/processon-and-processoff.md) **：** `PID` [/processoff](../profiling/processon-and-processoff.md) **：**`PID`|開始 (**/processon**) 或停止 (**/processoff**) 對 `PID` 指定的處理序收集資料。|
    |[/attach](../profiling/attach.md) **：**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**：**{ `PID`&#124;`ProcName` }]|**/attach** 會開始收集 `PID` 或處理序名稱 (ProcName) 指定的處理序資料。 如果未指定特定進程， **/detach** 會停止指定進程或所有進程的資料收集。|

## <a name="end-the-profiling-session"></a>結束程式碼剖析工作階段
 若要結束程式碼剖析工作階段，必須從所有分析的處理序中斷連結程式碼剖析工具，而且必須明確地關閉程式碼剖析工具。 您可以關閉應用程式或呼叫 **VSPerfCmd /detach** 選項，以從使用取樣方法剖析的應用程式中斷連結程式碼剖析工具。 接著呼叫 **VSPerfCmd /shutdown** 選項以停止程式碼剖析工具，並關閉程式碼剖析資料檔案。 **VSPerfClrEnv /off** 命令會清除程式碼剖析環境變數。

#### <a name="to-end-a-profiling-session"></a>結束程式碼剖析工作階段

1. 執行下列其中一個步驟，以從目標應用程式中斷連結程式碼剖析工具：

    - 輸入 **>vsperfcmd/detach**

         -或-

    - 關閉目標應用程式。

2. 關閉程式碼剖析工具。 輸入：

     **>vsperfcmd**  [/shutdown](../profiling/shutdown.md)

3. (選擇性) 清除程式碼剖析環境變數。 輸入：

     **VSPerfClrEnv /off**

## <a name="see-also"></a>另請參閱
- [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [取樣方法資料檢視](../profiling/profiler-sampling-method-data-views.md)
