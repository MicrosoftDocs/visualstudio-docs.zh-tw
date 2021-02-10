---
title: Profiler 命令列檢測獨立的 .NET 元件，取得記憶體資料
description: 瞭解如何使用 Visual Studio 分析工具命令列工具來收集獨立應用程式 .NET Framework 元件的記憶體資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d09cc46a-70f5-48f9-aa24-89913e67b359
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 40d9476b1a96e212709528aa4b8f572cd665fcbc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942733"
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line"></a>如何：使用命令列以分析工具檢測獨立的 .NET Framework 元件並收集記憶體資料
本文描述如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具命令列工具來檢測獨立應用程式的 .NET Framework 元件 (例如 .exe 或 .dll 檔案)，並使用分析工具來收集記憶體資訊。

> [!NOTE]
> 若要取得分析工具的路徑，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要使用程式碼剖析工具命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。

 若要使用檢測方法從 .NET Framework 元件收集記憶體資料，可以使用 [VSInstr.exe](../profiling/vsinstr.md) 工具來產生已檢測版的元件，並使用 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 工具來初始化程式碼剖析環境變數。 然後使用 *VSPerfCmd.exe* 工具啟動程式碼剖析工具。

 執行已檢測的元件時，記憶體資料會自動收集到資料檔案。 程式碼剖析工作階段期間，您可以暫停和繼續資料收集。

 若要結束程式碼剖析工作階段，必須關閉目標應用程式，並明確地關閉程式碼剖析工具。 在大部分情況下，建議您在工作階段結束時清除程式碼剖析環境變數。

## <a name="start-the-application-with-the-profiler"></a>使用分析工具啟動應用程式

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>將分析工具附加至執行中的 .NET Framework 應用程式

1. 開啟命令提示字元視窗。

2. 使用 [VSInstr] 工具產生已檢測版的目標應用程式。

3. 初始化 .NET Framework 程式碼剖析環境變數。 輸入：

    **VSPerfClrEnv** {**/tracegc** &#124; **/tracegclife**}

   - **/tracegc** 和 **/tracegclife** 選項會初始化環境變數，只收集記憶體配置資料，或同時收集記憶體配置和物件存留期資料。

       |選項|Description|
       |------------|-----------------|
       |**/tracegc**|只收集記憶體配置資料。|
       |**/tracegclife**|收集記憶體配置和物件存留期資料。|

4. 啟動分析工具。 輸入：

    **>vsperfcmd/start： trace/output：** `OutputFile` [`Options`]

   - [/start](../profiling/start.md)**:trace** 選項會初始化程式碼剖析工具。

   - /Start 需要 [/output](../profiling/output.md)**：** `OutputFile` 選項。  `OutputFile` 指定分析資料 ( 的名稱和位置。*.vsp*) 檔。

     您可以使用下列任一選項搭配 **/start:trace** 選項。

   | 選項 | Description |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **：**[ `Domain` **\\** ]`UserName` | 指定擁有程式碼剖析處理序之帳戶的網域和使用者名稱。 只有在以登入的使用者之外的使用者身分執行處理序時，才需要這個選項。 進程擁有者會列在 Windows 工作管理員的 [ **進程** ] 索引標籤上的 [使用者名稱] 欄中。 |
   | [/crosssession](../profiling/crosssession.md) | 在其他工作階段啟用處理序程式碼剖析。 如果應用程式在不同的工作階段中執行，則需要這個選項。 會話識別碼會列在 Windows 工作管理員的 [**處理** 程式] 索引標籤上的 [**會話** 識別碼] 欄中。 **/crosssession** 可縮寫成 **/CS**。 |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | 若要啟動暫停資料收集的程式碼剖析工具，請將 **/globaloff** 選項新增到 **/start** 命令列。 使用 **/globalon** 以繼續程式碼剖析。 |
   | [/wincounter](../profiling/wincounter.md) **：**`WinCounterPath` | 指定程式碼剖析期間要收集的 Windows 效能計數器。 |
   | [/automark](../profiling/automark.md) **：**`Interval` | 只能搭配 **/wincounter** 使用。 指定 Windows 效能計數器收集事件間隔的毫秒數。 預設值為 500 毫秒。 |
   | [/counter](../profiling/counter.md) **：**`Config` | 從 Config 中指定的處理器效能計數器收集資訊。計數器資訊會新增至每個程式碼剖析事件所收集的資料。 |
   | [事件](../profiling/events-vsperfcmd.md) **：**`Config` | 指定程式碼剖析期間要收集的 Windows 事件追蹤 (ETW) 事件。 ETW 事件會收集在不同的 ( 中。*etl*) 檔。 |

5. 從命令提示字元視窗啟動目標應用程式。

## <a name="control-data-collection"></a>控制資料收集
 當目標應用程式執行時，您可以使用 *VSPerfCmd.exe* 選項開始和停止將資料寫入至檔案，以控制資料收集。 控制資料收集可讓您收集特定程式執行 (例如啟動或關閉應用程式) 的資料。

#### <a name="to-start-and-stop-data-collection"></a>開始和停止資料收集

- 下列 **>vsperfcmd** 選項配對會開始和停止資料收集。 請在個別的命令列上指定各個選項。 您可以多次開始和停止資料收集。

    |選項|Description|
    |------------|-----------------|
    |[/globalon](../profiling/globalon-and-globaloff.md) [/globaloff](../profiling/globalon-and-globaloff.md)|開始 (**/globalon**) 或停止 (**/globaloff**) 所有處理序的資料收集。|
    |[/processon](../profiling/processon-and-processoff.md) **：** `PID` [/processoff](../profiling/processon-and-processoff.md) **：**`PID`|開始 (**/processon**) 或停止 (**/processoff**) 處理序 ID (`PID`) 指定的處理序資料收集。|
    |[/threadon](../profiling/threadon-and-threadoff.md) **：** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **：**`TID`|開始 (**/threadon**) 或停止 (**/threadoff**) 執行緒識別碼 (`TID`) 指定的執行緒資料收集。|

## <a name="end-the-profiling-session"></a>結束程式碼剖析工作階段
 若要結束程式碼剖析工作階段，請關閉正在執行已檢測元件的應用程式，然後呼叫 **VSPerfCmd** [/shutdown](../profiling/shutdown.md) 選項以關閉程式碼剖析工具，並關閉程式碼剖析資料檔案。 **VSPerfClrEnv /off** 命令會清除程式碼剖析環境變數。

#### <a name="to-end-a-profiling-session"></a>結束程式碼剖析工作階段

1. 關閉目標應用程式。

2. 關閉程式碼剖析工具。 輸入：

     **VSPerfCmd /shutdown**

3. (選擇性) 清除程式碼剖析環境變數。 輸入：

     **VSPerfCmd /off**

## <a name="see-also"></a>另請參閱
- [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [.NET 記憶體資料檢視](../profiling/dotnet-memory-data-views.md)
