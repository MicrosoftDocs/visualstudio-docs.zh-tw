---
title: 將分析工具附加至 .NET 以收集並行資料
description: 瞭解如何使用 Visual Studio 分析工具命令列工具，將分析工具附加至執行中的 .NET Framework 應用程式，以取得進程和執行緒並行資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: fdd41576-797e-4312-8520-fee7bb767e4a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 4d584d9d6cecc4d5df0f3c32172d4aeec9c02c97
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801134"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line"></a>如何：使用命令列將分析工具附加至 .NET Framework 獨立應用程式以收集並行資料
本文描述如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具命令列工具將分析工具附加至執行中的 .NET Framework 獨立 (用戶端) 應用程式，並收集處理序和執行緒並行資料。

> [!NOTE]
> 若要取得分析工具的路徑，請參閱 [逐步解說：使用 Profiler api](../profiling/walkthrough-using-profiler-apis.md)。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要使用分析工具命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。 如需詳細資訊，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。

 程式碼剖析工具附加至應用程式時，您可以暫停和繼續收集資料。 若要結束分析工作階段，分析工具不得再附加至應用程式，而且必須明確地關閉分析工具。

## <a name="attach-the-profiler"></a>附加分析工具

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>將分析工具附加至執行中的 .NET Framework 應用程式

1. 開啟 [命令提示字元] 視窗。

2. 啟動分析工具。 輸入：

     [>vsperfcmd](../profiling/vsperfcmd.md) **/start： concurrency/output：** `OutputFile` [ `Options` ]

     /Start 需要 [/output](../profiling/output.md)**：** `OutputFile` 選項。  `OutputFile` 指定程式碼剖析資料 (.vsp) 檔案的名稱和位置。

     您可以使用下列任一選項搭配 **/start:concurrency** 選項。

    |選項|描述|
    |------------|-----------------|
    |[/wincounter](../profiling/wincounter.md) **：**`WinCounterPath`|指定程式碼剖析期間要收集的 Windows 效能計數器。|
    |[/automark](../profiling/automark.md) **：**`Interval`|只能搭配 **/wincounter** 使用。 指定 Windows 效能計數器收集事件間隔的毫秒數。 預設值為 500 毫秒。|
    |[/events](../profiling/events-vsperfcmd.md) **：**`Config`|指定程式碼剖析期間要收集的 Windows 事件追蹤 (ETW) 事件。 ETW 事件會收集至個別的 (.etl) 檔案。|

3. 以一般方式啟動目標應用程式。

4. 將分析工具附加至目標應用程式。 輸入：

     **VSPerfCmd /attach:** `PID` [**/lineoff**] [**/targetclr:**`Version`]

    - `PID` 指定目標應用程式的處理序 ID。 您可以在 [Windows 工作管理員] 中檢視所有執行中處理序的處理序 ID。

    - [/lineoff](../profiling/lineoff.md) 會停用行號資料收集。

    - [/targetclr](../profiling/targetclr.md) **：** `Version` 指定在應用程式中載入多個版本的執行時間時要分析的 common language runtime (CLR) 的版本。 選擇性。

## <a name="control-data-collection"></a>控制資料收集
 當目標應用程式執行時，您可以使用 *VSPerfCmd.exe* 選項開始和停止將資料寫入至檔案，以控制資料收集。 控制資料收集可讓您收集特定程式執行 (例如啟動或關閉應用程式) 的資料。

#### <a name="to-start-and-stop-data-collection"></a>開始和停止資料收集

- 下列 *VSPerfCmd.exe* 選項配對會開始和停止資料收集。 請在個別的命令列上指定各個選項。 您可以多次開始和停止資料收集。

    |選項|描述|
    |------------|-----------------|
    |[/globalon/globaloff](../profiling/globalon-and-globaloff.md)|開始 (**/globalon**) 或停止 (**/globaloff**) 所有處理序的資料收集。|
    |[/processon](../profiling/processon-and-processoff.md) **：** `PID` [/processoff](../profiling/processon-and-processoff.md) **：**`PID`|開始 (**/processon**) 或停止 (**/processoff**) 處理序 ID (`PID`) 指定的處理序資料收集。|
    |[/attach](../profiling/attach.md) **：**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**：**{ `PID`&#124;`ProcName` }]|**/attach** 會開始為處理序 ID (`PID`) 或處理序名稱 (ProcName) 指定的處理序收集資料。 如果未指定特定進程， **/detach** 會停止指定進程或所有進程的資料收集。|

## <a name="end-the-profiling-session"></a>結束程式碼剖析工作階段
 若要結束程式碼剖析工作階段，程式碼剖析工具不得進行資料收集。 您可以關閉應用程式或叫用 **VSPerfCmd /detach** 選項，以停止從使用並行方法分析的應用程式中收集資料。 接著叫用 **VSPerfCmd /shutdown** 選項以停止程式碼剖析工具，並關閉程式碼剖析資料檔案。 **VSPerfClrEnv /off** 命令會清除程式碼剖析環境變數。

#### <a name="to-end-a-profiling-session"></a>結束程式碼剖析工作階段

1. 執行下列其中一項動作，以從目標應用程式中斷連結程式碼剖析工具。

    - 輸入 **>vsperfcmd/detach**

         -或-

    - 關閉目標應用程式。

2. 關閉程式碼剖析工具。 輸入：

     >vsperfcmd[/shutdown](../profiling/shutdown.md)
