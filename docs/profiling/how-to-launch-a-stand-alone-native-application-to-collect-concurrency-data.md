---
title: Profiler 命令列-開啟原生用戶端應用程式，取得並行資料
description: 瞭解如何使用 Visual Studio 分析工具命令列工具來啟動原生獨立用戶端應用程式，並收集進程和執行緒並行資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e5aed651-afed-4b70-9a7e-1a6032cc614f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: ce8c16c3c895c0538f91bdb27af08e003b1450cf
ms.sourcegitcommit: 8e15b434bf5db3e0f719320ca82682df1a3da110
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98883448"
---
# <a name="how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>如何：使用命令列以分析工具啟動獨立的原生應用程式來收集並行資料
本主題描述如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具命令列工具啟動原生的獨立 (用戶端) 應用程式，並收集處理序和執行緒並行資料。

 程式碼剖析工作階段分成下列幾個部分︰

- 使用程式碼剖析工具啟動應用程式

- 控制資料收集

- 結束程式碼剖析工作階段

> [!NOTE]
> 若要取得分析工具的路徑，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要使用程式碼剖析工具命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。

## <a name="start-the-application-with-the-profiler"></a>使用分析工具啟動應用程式
 若要使用程式碼剖析工具啟動目標應用程式，請使用 [VSPerfCmd.exe](../profiling/vsperfcmd.md)**/start** 和 **/launch** 選項初始化程式碼剖析工具，並啟動應用程式。 您可以指定 **/start** 和 **/launch** 及其個別選項。 您也可以加入 **/globaloff** 選項以在目標應用程式啟動時暫停資料收集。 然後使用 **/globalon** 開始收集資料。

#### <a name="to-start-an-application-with-the-profiler"></a>使用分析工具啟動應用程式

1. 在命令提示字元中，輸入下列命令：

     [>vsperfcmd](../profiling/vsperfcmd.md) **/start： concurrency/output：** `OutputFile` [ `Options` ]

     /Start 需要 [/output](../profiling/output.md)**：** `OutputFile` 選項。  `OutputFile` 指定程式碼剖析資料 (.vsp) 檔案的名稱和位置。

     您可以使用下表中的任一選項搭配 **/start:concurrency** 選項。

    |選項|描述|
    |------------|-----------------|
    |[/wincounter](../profiling/wincounter.md) **：**`WinCounterPath`|指定程式碼剖析期間要收集的 Windows 效能計數器。|
    |[/automark](../profiling/automark.md) **：**`Interval`|只能搭配 **/wincounter** 使用。 指定 Windows 效能計數器收集事件間隔的毫秒數。 預設值為 500。|
    |[/events](../profiling/events-vsperfcmd.md) **：**`Config`|指定程式碼剖析期間要收集的 Windows 事件追蹤 (ETW) 事件。 ETW 事件會收集至個別的 (.etl) 檔案。|

2. 輸入下列命令以啟動目標應用程式：

     **>vsperfcmd**  [/launch](../profiling/launch.md) **：** `AppName` [ `Options` ]

     您可以使用下表中的任一選項搭配 **/launch** 選項。

    |選項|描述|
    |------------|-----------------|
    |[/args](../profiling/args.md) **：**`Arguments`|指定包含要傳遞至目標應用程式的命令列引數的字串。|
    |[/console](../profiling/console.md)|在個別的視窗中啟動目標命令列應用程式。|
    |[/targetclr](../profiling/targetclr.md) **：**`CLRVersion`|指定當應用程式載入多個版本的 Common Language Runtime (CLR) 時要分析的 CLR 版本。|

## <a name="control-data-collection"></a>控制資料收集
 當目標應用程式正在執行時，您可以使用 *VSPerfCmd.exe* 選項啟動和停止將資料寫入檔案，以控制資料收集。 透過控制資料收集，您可以收集特定程式執行 (例如啟動或關閉應用程式) 的資料。

#### <a name="to-start-and-stop-data-collection"></a>開始和停止資料收集

- 下表中成對的選項會開始和停止資料收集。 請在個別的命令列上指定各個選項。 您可以多次開始和停止資料收集。

    |選項|描述|
    |------------|-----------------|
    |[/globalon/globaloff](../profiling/globalon-and-globaloff.md)|開始 (**/globalon**) 或停止 (**/globaloff**) 所有處理序的資料收集。|
    |[/processon](../profiling/processon-and-processoff.md) **：** `PID` [/processoff](../profiling/processon-and-processoff.md) **：**`PID`|開始 (**/processon**) 或停止 (**/processoff**) 處理序 ID (`PID`) 指定的處理序資料收集。|
    |[/attach](../profiling/attach.md) **：**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**：**{ `PID`&#124;`ProcName` }]|**/attach** 會開始為處理序 ID (`PID`) 或處理序名稱 (*ProcName*) 指定的處理序收集資料。 **/detach** 會停止指定的處理序或所有處理序 (如果未指定處理序) 的資料收集。|

- 您也可以使用 **VSPerfCmd.exe**[/mark](../profiling/mark.md) 選項將程式碼剖析標記插入資料檔案。 **/mark** 命令會新增識別碼、時間戳記和一個選擇性的使用者定義文字字串。 標記可用來篩選程式碼剖析工具報告和資料檢視中的資料。

## <a name="end-the-profiling-session"></a>結束程式碼剖析工作階段
 若要結束程式碼剖析工作階段，程式碼剖析工具不得進行資料收集。 您可以關閉分析的應用程式或叫用 **VSPerfCmd /detach** 選項，以停止收集並行資料。 接著叫用 **VSPerfCmd /shutdown** 選項以停止程式碼剖析工具，並關閉程式碼剖析資料檔案。

#### <a name="to-end-a-profiling-session"></a>結束程式碼剖析工作階段

1. 關閉目標應用程式或在命令提示字元中輸入下列命令，以將程式碼剖析工具從目標應用程式中斷連結︰

     **VSPerfCmd /detach**

2. 在命令提示字元中輸入下列命令，以關閉程式碼剖析工具︰

     **>vsperfcmd**  [/shutdown](../profiling/shutdown.md)