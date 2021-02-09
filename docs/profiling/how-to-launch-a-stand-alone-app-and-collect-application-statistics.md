---
title: Profiler 命令列-啟動獨立應用程式，取得應用程式統計資料
description: 瞭解如何使用 Visual Studio 分析工具命令列工具來啟動獨立應用程式，並使用取樣方法收集效能資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 52dcee2b-f178-4a76-bddc-e36c50bfcb78
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 49955afdb97ade1612c270dbb1094ca0ef04a947
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928970"
---
# <a name="how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line"></a>如何：使用命令列以分析工具啟動獨立應用程式並收集應用程式統計資料
本主題描述如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具命令列工具啟動獨立的 (用戶端) 應用程式，並使用取樣方法收集效能統計資料。

> [!NOTE]
> Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 UWP App 也需要新的收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。
>
> 若要將階層互動資料新增至分析回合中，則需要使用命令列分析工具的特定程序。 請參閱[收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)

 若要使用程式碼剖析工具命令列工具，必須將路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。 您可以從 Visual Studio 命令視窗，在已安裝 Visual Studio 的電腦上執行程式碼剖析工具。

1. 如果您是從已安裝 Visual Studio 的電腦上執行程式碼剖析工具，Visual Studio 命令視窗會設定正確的路徑。 在 [工具] 功能表上，選擇 [VS 命令提示字元]。

> [!NOTE]
> 若要取得分析工具的路徑，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要使用程式碼剖析工具命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。

## <a name="start-the-application-with-the-profiler"></a>使用分析工具啟動應用程式
 若要使用程式碼剖析工具啟動目標應用程式，您可以使用 VSPerfCmd **/start** 和 **/launch** 選項初始化程式碼剖析工具，並啟動應用程式。 您可以在單一命令列上指定 **/start** 和 **/launch** 及其個別選項。

 您也可以加入 **/globaloff** 選項以在目標應用程式啟動時暫停資料收集。 然後使用 **/globalon** 開始收集資料。

#### <a name="to-start-an-application-by-using-the-profiler"></a>使用分析工具啟動應用程式

1. 開啟命令提示字元視窗。

2. 啟動分析工具。 輸入：

    **>vsperfcmd/start：/output 範例：** `OutputFile` [`Options`]

   - [/start](../profiling/start.md)**:sample** 選項會初始化程式碼剖析工具。

   - /Start 需要 [/output](../profiling/output.md)**：** `OutputFile` 選項。  `OutputFile` 指定程式碼剖析資料 (.vsp) 檔案的名稱和位置。

     您可以使用下列任一選項搭配 **/start:sample** 選項。

   | 選項 | Description |
   | - | - |
   | [/wincounter](../profiling/wincounter.md) **：**`WinCounterPath` | 指定程式碼剖析期間要收集的 Windows 效能計數器。 |
   | [/automark](../profiling/automark.md) **：**`Interval` | 只能搭配 **/wincounter** 使用。 指定 Windows 效能計數器收集事件間隔的毫秒數。 預設值為 500 毫秒。 |
   | [/events](../profiling/events-vsperfcmd.md) **：**`Config` | 指定程式碼剖析期間要收集的 Windows 事件追蹤 (ETW) 事件。 ETW 事件會收集在不同的 ( 中。*etl*) 檔。 |

3. 啟動目標應用程式。 Type：**>vsperfcmd/launch：** `appName` [ `Options` ] [ `Sample Event` ]

    您可以使用下列一或多個選項搭配 **/launch** 選項。

   |選項|Description|
   |------------|-----------------|
   |[/args](../profiling/args.md) **：**`Arguments`|指定包含要傳遞至目標應用程式的命令列引數的字串。|
   |[/console](../profiling/console.md)|在個別的視窗中啟動目標命令列應用程式。|

    根據預設，每經過 10,000,000 個未暫止處理器時脈週期，會取樣一次效能資料。 在 1GHz 處理器上，這大約是每 10 秒一次。 您可以指定下列任一選項來變更時脈週期間隔，或指定不同的取樣事件。

   |範例事件|Description|
   |------------------|-----------------|
   |[/timer](../profiling/timer.md) **：**`Interval`|將取樣間隔變更為 `Interval` 指定的未暫止時脈週期數。|
   |[/pf](../profiling/pf.md)[**：** `Interval` ]|將取樣事件變更為分頁錯誤。 如果指定 `Interval`，請設定樣本間的分頁錯誤數。 預設值為 10。|
   |[/sys](../profiling/sys-vsperfcmd.md)[**：** `Interval` ]|將取樣事件從處理器變更為作業系統核心的系統呼叫 (syscalls)。 如果指定 `Interval`，請設定樣本間的呼叫數。 預設值為 10。|
   |[/counter](../profiling/counter.md) **：**`Config`|將取樣事件與間隔變更為 `Config` 中指定的處理器效能計數器與間隔。|

## <a name="control-data-collection"></a>控制資料收集
 當目標應用程式執行時，您可以使用 *VSPerfCmd.exe* 選項開始和停止將資料寫入至程式碼剖析資料檔案，以控制資料收集。 控制資料收集可讓您收集特定程式執行 (例如啟動或關閉應用程式) 的資料。

#### <a name="to-start-and-stop-data-collection"></a>開始和停止資料收集

- 下列成對的選項會開始和停止資料收集。 請在個別的命令列上指定各個選項。 您可以多次開始和停止資料收集。

    |選項|Description|
    |------------|-----------------|
    |[/globalon/globaloff](../profiling/globalon-and-globaloff.md)|開始 (**/globalon**) 或停止 (**/globaloff**) 所有處理序的資料收集。|
    |[/processon](../profiling/processon-and-processoff.md) **：** `PID` [/processoff](../profiling/processon-and-processoff.md) **：**  `PID`|開始 (**/processon**) 或停止 (**/processoff**) 處理序 ID (`PID`) 指定的處理序資料收集。|
    |[/attach](../profiling/attach.md) **：**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**：**{ `PID`&#124;`ProcName` }]|**/attach** 會開始為 `PID` 或處理序名稱 (ProcName) 指定的處理序收集資料。 如果未指定特定進程， **/detach** 會停止指定進程或所有進程的資料收集。|

## <a name="end-the-profiling-session"></a>結束程式碼剖析工作階段
 若要結束程式碼剖析工作階段，程式碼剖析工具不得附加至任何分析的處理序，而且必須明確地關閉程式碼剖析工具。 您可以關閉應用程式或呼叫 **VSPerfCmd /detach** 選項，以從使用取樣方法剖析的應用程式中斷連結程式碼剖析工具。 接著呼叫 **VSPerfCmd /shutdown** 選項以停止程式碼剖析工具，並關閉程式碼剖析資料檔案。 **VSPerfClrEnv /off** 命令會清除程式碼剖析環境變數。

#### <a name="to-end-a-profiling-session"></a>結束程式碼剖析工作階段

1. 執行下列其中一個步驟，以從目標應用程式中斷連結程式碼剖析工具：

    - 關閉目標應用程式。

         -或-

    - 輸入 **>vsperfcmd/detach**

2. 關閉程式碼剖析工具。 輸入：

     **>vsperfcmd**  [/shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>另請參閱
- [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [取樣方法資料檢視](../profiling/profiler-sampling-method-data-views.md)
