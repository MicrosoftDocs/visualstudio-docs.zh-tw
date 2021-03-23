---
title: Profiler 命令列-開啟用戶端 .NET 應用程式，取得並行資料
description: 瞭解如何使用 Visual Studio 分析工具命令列工具來啟動 .NET 獨立應用程式，並收集進程和執行緒並行資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 17a48848-bd3e-44ef-9971-e39836ff1df2
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 81311e9dea2c5367b44cdf2cc8e2327a8aff5617
ms.sourcegitcommit: 20f546a0b13b56e7b0da21abab291d42a5ba5928
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2021
ms.locfileid: "104884105"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>如何：使用命令列以分析工具啟動獨立的 .NET Framework 應用程式並收集並行資料
本主題描述如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具命令列工具啟動 .NET Framework stand-alone 獨立 (用戶端) 應用程式，並收集處理序和執行緒並行資料

> [!NOTE]
> 若要取得分析工具的路徑，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要使用程式碼剖析工具命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。

 程式碼剖析工具附加至應用程式時，您可以暫停和繼續收集資料。 若要結束分析工作階段，分析工具不得再附加至應用程式，而且必須明確地關閉分析工具。

## <a name="start-the-application-with-the-profiler"></a>使用分析工具啟動應用程式
 若要流量分析工具啟動 .NET Framework 目標應用程式，您可以使用 *VSPerfClrEnv.exe* 來設定 .NET Framework 分析變數。 然後，使用 VSPerfCmd **/start** 和 **/launch** 選項來初始化分析工具，並啟動應用程式。 您可以在單一命令列上指定 **/start** 和 **/launch** 及其個別選項。 您也可以將 **/globaloff** 選項加入命令列，以在目標應用程式啟動時暫停資料收集。 然後在單獨的命令列上使用 **/globalon**，以開使收集資料。

#### <a name="to-start-an-application-with-the-profiler"></a>使用分析工具啟動應用程式

1. 開啟 [命令提示字元] 視窗。

2. 啟動分析工具。 輸入：

    [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency**[**,**{**ResourceOnly**&#124;**ThreadOnly**}] **/output:**`OutputFile` [`Options`]

   - [/start](../profiling/start.md) 選項將分析工具初始化。

     | 命令 | 描述 |
     |-------------------------------------| - |
     | **/start:concurrency** | 啟用收集資源爭用和執行緒執行資料。 |
     | **/start:concurrency,resourceonly** | 啟用只收集資源爭用資料。 |
     | **/start:concurrency,threadonly** | 啟用只收集執行緒執行資料。 |

   - /Start 需要 [/output](../profiling/output.md)**：** `OutputFile` 選項。  `OutputFile` 指定程式碼剖析資料 (.vsp) 檔案的名稱和位置。

     您可以使用下列任一選項搭配 **/start:concurrency** 選項。

   | 選項 | 描述 |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **：**[ `domain\` ]`username` | 指定要授與程式碼剖析工具存取權之帳戶的選擇性網域和使用者名稱。 |
   | [/crosssession](../profiling/crosssession.md) | 在其他登入工作階段啟用處理序程式碼剖析。 |
   | [/wincounter](../profiling/wincounter.md) **：**`WinCounterPath` | 指定程式碼剖析期間要收集的 Windows 效能計數器。 |
   | [/automark](../profiling/automark.md) **：**`Interval` | 只能搭配 **/wincounter** 使用。 指定 Windows 效能計數器收集事件間隔的毫秒數。 預設值為 500 毫秒。 |
   | [/events](../profiling/events-vsperfcmd.md) **：**`Config` | 指定程式碼剖析期間要收集的 Windows 事件追蹤 (ETW) 事件。 ETW 事件會收集在不同的 ( 中。*etl*) 檔。 |

3. 啟動目標應用程式。 輸入：

    **>vsperfcmd**  [/launch](../profiling/launch.md) **：** `AppName` [ `Options` ] [ `Sample Event` ]

    您可以使用下列任一選項搭配 **/launch** 選項。

   |選項|描述|
   |------------|-----------------|
   |[/args](../profiling/args.md) **：**`Arguments`|指定包含要傳遞至目標應用程式的命令列引數的字串。|
   |[/console](../profiling/console.md)|在個別的視窗中啟動目標命令列應用程式。|
   |[/targetclr](../profiling/targetclr.md) **：**`Version`|指定當應用程式載入多個版本的執行階段時要分析的 Common Language Runtime (CLR) 版本。|

## <a name="control-data-collection"></a>控制資料收集
 當目標應用程式執行時，您可以使用 *VSPerfCmd.exe* 選項開始和停止將資料寫入至檔案，以控制資料收集。 控制資料收集可讓您收集特定程式執行 (例如啟動或關閉應用程式) 的資料。

#### <a name="to-start-and-stop-data-collection"></a>開始和停止資料收集

1. 下列 *VSPerfCmd.exe* 選項配對會開始和停止資料收集。 請在個別的命令列上指定各個選項。 您可以多次開始和停止資料收集。

    |選項|描述|
    |------------|-----------------|
    |[/globalon/globaloff](../profiling/globalon-and-globaloff.md)|開始 (**/globalon**) 或停止 (**/globaloff**) 所有處理序的資料收集。|
    |[/processon](../profiling/processon-and-processoff.md) **：** `PID` [/processoff](../profiling/processon-and-processoff.md) **：**`PID`|開始 (**/processon**) 或停止 (**/processoff**) 處理序 ID (`PID`) 指定的處理序資料收集。|
    |[/attach](../profiling/attach.md) **：**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**：**{ `PID`&#124;`ProcName` }]|**/attach** 會開始為處理序 ID (`PID`) 或處理序名稱 (ProcName) 指定的處理序收集資料。 如果未指定特定進程， **/detach** 會停止指定進程或所有進程的資料收集。|

## <a name="end-the-profiling-session"></a>結束程式碼剖析工作階段
 若要結束程式碼剖析工作階段，程式碼剖析工具不得進行資料收集。 您可以關閉分析的應用程式或叫用 **VSPerfCmd /detach** 選項，以停止收集並行資料。 接著叫用 **VSPerfCmd /shutdown** 選項以停止程式碼剖析工具，並關閉程式碼剖析資料檔案。 **VSPerfClrEnv /off** 命令會清除程式碼剖析環境變數。

#### <a name="to-end-a-profiling-session"></a>結束程式碼剖析工作階段

1. 執行下列其中一項動作，以從目標應用程式中斷連結程式碼剖析工具。

    - 關閉目標應用程式。

         -或-

    - 輸入 **>vsperfcmd/detach**

2. 關閉分析工具

     **>vsperfcmd**  [/shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>另請參閱
- [收集並行資料](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)
