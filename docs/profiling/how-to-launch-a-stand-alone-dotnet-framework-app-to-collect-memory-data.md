---
title: Profiler 命令列-開啟用戶端 .NET Framework 應用程式，取得記憶體資料
description: 瞭解如何使用 Visual Studio 分析工具命令列工具來啟動 .NET Framework 的獨立應用程式，並收集記憶體活動資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3bc53041-91b7-4ad0-8413-f8bf2c4b3f5e
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: acfa657552cb070fe8b98ff4dc761ab6913a6c93
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860811"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line"></a>如何：使用命令列以分析工具啟動獨立的 .NET Framework 應用程式來收集記憶體資料
本主題描述如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具命令列工具啟動 .NET Framework 獨立 (用戶端) 應用程式，並收集記憶體資料。

 程式碼剖析工作階段有三個部分︰

- 使用程式碼剖析工具啟動應用程式。

- 收集程式碼剖析資料。

- 結束程式碼剖析工作階段。

> [!NOTE]
> 若要取得分析工具的路徑，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要使用程式碼剖析工具命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。

## <a name="start-the-application-with-the-profiler"></a>使用分析工具啟動應用程式
 若要使用程式碼剖析工具啟動目標應用程式，請使用 **VSPerfCmd.exe/start** 和 **/launch** 選項初始化程式碼剖析工具，並啟動應用程式。 您可以在單一命令列上指定 **/start** 和 **/launch** 及其個別選項。

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

3. 啟動目標應用程式。 輸入：

    **>vsperfcmd**  [/launch](../profiling/launch.md) **：** `appName` **/gc：**{**配置**&#124;**存留期**} [ `Options` ]

   - 需要 [/gc](../profiling/gc-vsperfcmd.md)**：** `Keyword` 選項才能收集 .NET Framework 的記憶體資料。 關鍵字參數指定要收集記憶體配置資料，或收集記憶體配置和物件存留期資料。

     |關鍵字|描述|
     |-------------|-----------------|
     |**分配**|僅收集記憶體配置資料。|
     |**一生**|收集記憶體配置和物件存留期資料。|

     您可以使用下列任一選項搭配 **/launch** 選項。

   |選項|Description|
   |------------|-----------------|
   |[/args](../profiling/args.md) **：**`Arguments`|指定包含要傳遞至目標應用程式的命令列引數的字串。|
   |[/console](../profiling/console.md)|在個別的視窗中啟動目標命令列應用程式。|
   |[/events](../profiling/events-vsperfcmd.md) **：**`Config`|指定程式碼剖析期間要收集的 Windows 事件追蹤 (ETW) 事件。 ETW 事件會收集至個別的 (.etl) 檔案。|
   |[/targetclr](../profiling/targetclr.md) **：**`Version`|指定當應用程式載入多個版本的執行階段時要分析的 Common Language Runtime (CLR) 版本。|

## <a name="control-data-collection"></a>控制資料收集
 當目標應用程式執行時，您可以使用 *VSPerfCmd.exe* 選項開始和停止將資料寫入至檔案，以控制資料收集。 控制資料收集可讓您收集特定程式執行 (例如啟動或關閉應用程式) 的資料。

#### <a name="to-start-and-stop-data-collection"></a>開始和停止資料收集

- 下列成對的選項會開始和停止資料收集。 請在個別的命令列上指定各個選項。 您可以多次開始和停止資料收集。

    |選項|Description|
    |------------|-----------------|
    |[/globalon/globaloff](../profiling/globalon-and-globaloff.md)|開始 (**/globalon**) 或停止 (**/globaloff**) 所有處理序的資料收集。|
    |[/processon](../profiling/processon-and-processoff.md) **：** `PID` [processoff](../profiling/processon-and-processoff.md) **：**`PID`|開始 (**/processon**) 或停止 (**/processoff**) 處理序 ID (`PID`) 指定的處理序資料收集。|
    |[/attach](../profiling/attach.md) **：** `PID` [/detach](../profiling/detach.md)|**/attach** 會開始為 `PID`(處理序 ID) 指定的處理序收集資料。 **/detach** 停止所有處理序的資料收集。|

- 您也可以使用 **VSPerfCmd.exe**[/mark](../profiling/mark.md) 選項將程式碼剖析標記插入資料檔案。 **/mark** 命令會新增識別碼、時間戳記和一個選擇性的使用者定義文字字串。 標記可用來篩選資料。

## <a name="end-the-profiling-session"></a>結束程式碼剖析工作階段
 若要結束程式碼剖析工作階段，必須從所有分析的處理序中斷連結程式碼剖析工具，而且必須明確地關閉程式碼剖析工具。 您可以關閉應用程式或呼叫 **VSPerfCmd /detach** 選項，以從使用取樣方法剖析的應用程式中斷連結程式碼剖析工具。 接著呼叫 **VSPerfCmd /shutdown** 選項以停止程式碼剖析工具，並關閉程式碼剖析資料檔案。 **VSPerfClrEnv /off** 命令會清除程式碼剖析環境變數。

#### <a name="to-end-a-profiling-session"></a>結束程式碼剖析工作階段

1. 執行下列其中一個步驟，以從目標應用程式中斷連結程式碼剖析工具：

    - 關閉目標應用程式。

         -或-

    - 輸入 **>vsperfcmd/detach**

2. 關閉程式碼剖析工具。 輸入：

     **>vsperfcmd**  [/shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>另請參閱
- [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [.NET 記憶體資料檢視](../profiling/dotnet-memory-data-views.md)
