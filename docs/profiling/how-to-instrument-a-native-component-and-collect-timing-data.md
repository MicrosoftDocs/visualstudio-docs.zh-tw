---
title: 分析工具命令列檢測原生元件，取得計時資料
description: 瞭解如何使用 Visual Studio 分析工具命令列工具來收集原生元件（如 c + + .exe 或 .dll 檔案）的詳細計時資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 36883074-9be8-4e90-a66f-7e87f21fcd30
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 7d63ec7bded9cc19e31ee0d6f8ce7346990bf7aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929130"
---
# <a name="how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line"></a>如何：從命令列使用分析工具檢測原生獨立元件並收集計時資料
本主題描述如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具命令列工具來檢測原生元件 (例如 C++ .*exe* 或 .*dll* 檔案)，並收集詳細的計時資料。

> [!NOTE]
> 若要取得分析工具的路徑，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要使用程式碼剖析工具命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。

若要使用檢測方法從元件收集詳細的計時資料，您可使用 [VSInstr.exe](../profiling/vsinstr.md) 工具產生已檢測的元件版本。 然後啟動分析工具。 執行已檢測的元件時，計時資料會自動收集到資料檔案。 程式碼剖析工作階段期間，您可以暫停和繼續資料收集。

 若要結束分析工作階段，必須關閉目標應用程式，並明確地關閉分析工具。

## <a name="start-the-profiling-session"></a>啟動分析工作階段

#### <a name="to-start-profiling-by-using-the-instrumentation-method"></a>使用檢測方法開始分析

1. 開啟命令提示字元視窗。

2. 使用 [VSInstr] 工具產生已檢測版的目標應用程式。

3. 啟動分析工具。 輸入：

    **>vsperfcmd/start： trace/output：** `OutputFile` [`Options`]

   - [/start](../profiling/start.md)**:trace** 選項會初始化程式碼剖析工具。

   - /Start 需要 [/output](../profiling/output.md)**：** `OutputFile` 選項。  `OutputFile` 指定程式碼剖析資料 (.vsp) 檔案的名稱和位置。

     您可以使用下列一或多個選項搭配 **/start:trace** 選項。

   | 選項 | Description |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **：**[ `Domain` **\\** ]`UserName` | 指定擁有程式碼剖析處理序之帳戶的網域和使用者名稱。 只有在以登入的使用者之外的使用者身分執行處理序時，才需要這個選項。 進程擁有者會列在 Windows 工作管理員的 [**進程**] 索引標籤上的 [**使用者名稱**] 欄中。 |
   | [/crosssession](../profiling/crosssession.md) | 在其他工作階段啟用處理序程式碼剖析。 如果應用程式在不同的工作階段中執行，則需要這個選項。 會話識別碼會列在 Windows 工作管理員的 [處理常式] 索引標籤上的 [ **會話** 識別碼] 欄中。 **/crosssession** 可縮寫成 **/CS**。 |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | 啟動分析工具，但暫停資料收集。 使用 [/globalon](../profiling/globalon-and-globaloff.md) 以繼續程式碼剖析。 |
   | [/counter](../profiling/counter.md) **：**`Config` | 從 `Config` 中指定的處理器效能計數器收集資訊。 計數器資訊會新增至在每個程式碼剖析事件收集的資料。 |
   | [/wincounter](../profiling/wincounter.md) **：**`WinCounterPath` | 指定程式碼剖析期間要收集的 Windows 效能計數器。 |
   | [/automark](../profiling/automark.md) **：**`Interval` | 只能搭配 **/wincounter** 使用。 指定 Windows 效能計數器收集事件間隔的毫秒數。 預設值為 500 毫秒。 |
   | [/events](../profiling/events-vsperfcmd.md) **：**`Config` | 指定程式碼剖析期間要收集的 Windows 事件追蹤 (ETW) 事件。 ETW 事件會收集在不同的 ( 中。*etl*) 檔。 |

4. 以一般方式啟動目標應用程式。

## <a name="control-data-collection"></a>控制資料收集
 當目標應用程式執行時，您可以使用 *VSPerfCmd.exe* 選項開始和停止將資料寫入至檔案，以控制資料收集。 控制資料收集可讓您收集特定程式執行 (例如啟動或關閉應用程式) 的資料。

#### <a name="to-start-and-stop-data-collection"></a>開始和停止資料收集

- 下列成對的選項會開始和停止資料收集。 請在個別的命令列上指定各個選項。 您可以多次開始和停止資料收集。

    |選項|Description|
    |------------|-----------------|
    |[/globalon/globaloff](../profiling/globalon-and-globaloff.md)|開始 (**/globalon**) 或停止 (**/globaloff**) 所有處理序的資料收集。|
    |[/processon](../profiling/processon-and-processoff.md) **：** `PID` [/processoff](../profiling/processon-and-processoff.md) **：**`PID`|開始 (**/processon**) 或停止 (**/processoff**) 處理序 ID (`PID`) 指定的處理序資料收集。|
    |[/threadon](../profiling/threadon-and-threadoff.md) **：** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **：**`TID`|開始 (**/threadon**) 或停止 (**/threadoff**) 執行緒識別碼 (`TID`) 指定的執行緒資料收集。|

## <a name="end-the-profiling-session"></a>結束程式碼剖析工作階段
 若要結束程式碼剖析工作階段，請關閉正在執行已檢測元件的應用程式，然後呼叫 **VSPerfCmd** [/shutdown](../profiling/shutdown.md) 選項以關閉程式碼剖析工具，並關閉程式碼剖析資料檔案。

#### <a name="to-end-a-profiling-session"></a>結束程式碼剖析工作階段

1. 關閉目標應用程式。

2. 關閉程式碼剖析工具。 輸入：

     **VSPerfCmd /shutdown**

## <a name="see-also"></a>另請參閱
- [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [檢測方法資料檢視](../profiling/instrumentation-method-data-views.md)
