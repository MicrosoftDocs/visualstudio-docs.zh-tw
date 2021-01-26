---
title: 將分析工具附加至 .NET 以收集記憶體資料
description: 瞭解如何使用 Visual Studio 分析工具命令列工具，將分析工具附加至執行中的 .NET Framework 獨立 (用戶端) 應用程式，並取得記憶體資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 1a80e4201f04565aaa163d58bca8e13ae715b09f
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801102"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line"></a>如何：使用命令列將分析工具附加至 .NET Framework 獨立應用程式以收集記憶體資料

本文描述如何使用 Visual Studio 分析工具命令列工具，將分析工具附加至執行中的 .NET Framework 獨立 (用戶端) 應用程式，並收集記憶體資料。

> [!NOTE]
> 若要取得分析工具的路徑，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要使用程式碼剖析工具命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。

若要附加至 .NET Framework 應用程式並收集記憶體資料，您必須在目標應用程式啟動前，先使用 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 工具初始化適當的環境變數。 分析工具附加至應用程式時，您可以使用 *VSPerfCmd.exe* 工具暫停和繼續收集資料。

若要結束程式碼剖析工作階段，必須從所有分析的處理序中斷連結程式碼剖析工具，而且必須明確地關閉程式碼剖析工具。 在大部分情況下，建議您在工作階段結束時清除程式碼剖析環境變數。

## <a name="attach-the-profiler"></a>附加分析工具

### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>將分析工具附加至執行中的 .NET Framework 應用程式

1. 開啟命令提示字元視窗。

2. 初始化程式碼剖析環境變數。 輸入：

     **VSPerfClrEnv** {**/samplegc** &#124; **/samplegclife**} [**/samplelineoff**]

    - **/samplegc** 和 **/samplegclife** 選項指定只收集記憶體配置資料，或收集記憶體配置和物件存留期資料。 必須且只能指定一個選項。

        |選項|說明|
        |------------|------------------|
        |**/samplegc**|只收集記憶體配置資料。|
        |**/samplegclife**|收集記憶體配置和物件存留期資料。|

    - **/samplelineoff** 選項會停用原始程式碼行號資料的收集功能。

3. 啟動分析工具。 輸入：

     **>vsperfcmd/start：/output 範例：** `OutputFile` [`Options`]

   - [/start](../profiling/start.md)**:sample** 選項會初始化程式碼剖析工具。

   - /Start 需要 [/output](../profiling/output.md)**：** `OutputFile` 選項。  `OutputFile` 指定程式碼剖析資料 (.vsp) 檔案的名稱和位置。

     您可以使用下列任一選項搭配 **/start:sample** 選項。

     | 選項 | 描述 |
     | - | - |
     | [/user](../profiling/user-vsperfcmd.md) **：**[ `Domain` **\\** ]`UserName` | 指定擁有程式碼剖析處理序之帳戶的網域和使用者名稱。 只有在以登入的使用者之外的使用者身分執行處理序時，才需要這個選項。 處理序擁有者會列在 [Windows 工作管理員] 的 [處理程序] 索引標籤上的 [使用者名稱] 欄。 |
     | [/crosssession &#124; /cs](../profiling/crosssession.md) | 在其他工作階段啟用處理序程式碼剖析。 如果應用程式在不同的工作階段中執行，則需要這個選項。 工作階段識別碼會列在 [Windows 工作管理員] 的 [處理程序] 索引標籤上的 [工作階段識別碼] 欄。 **/crosssession** 可縮寫成 **/CS**。 |
     | [/wincounter](../profiling/wincounter.md) **：**`WinCounterPath` | 指定程式碼剖析期間要收集的 Windows 效能計數器。 |
     | [/automark](../profiling/automark.md) **：**`Interval` | 只能搭配 **/wincounter** 使用。 指定 Windows 效能計數器收集事件間隔的毫秒數。 預設值為 500 毫秒。 |

4. 如有必要，請以一般方式啟動目標應用程式。

5. 將分析工具附加至目標應用程式。 輸入：

     **>vsperfcmd**[/attach](../profiling/attach.md) **：**{ `PID`&#124;`ProcName` } [[/targetclr](../profiling/targetclr.md)**：** `Version` ]  

    - `PID` 指定目標應用程式的處理序 ID。 `ProcessName` 指定處理序的名稱。 請注意，如果您指定 `ProcessName` 且有多個名稱相同的處理序正在執行，則會發生無法預期的結果。 您可以在 [Windows 工作管理員] 中檢視所有執行中處理序的處理序 ID。

    - **/targetclr：** `Version` 指定當應用程式載入多個版本的執行時間時，要進行分析的 common language runtime 版本 (CLR) 。 選擇性。

## <a name="control-data-collection"></a>控制資料收集

當目標應用程式執行時，您可以使用 *VSPerfCmd.exe* 選項開始和停止將資料寫入至檔案，以控制資料收集。 控制資料收集可讓您收集特定程式執行 (例如啟動或關閉應用程式) 的資料。

### <a name="to-start-and-stop-data-collection"></a>開始和停止資料收集

- 下列成對的選項會開始和停止資料收集。 請在個別的命令列上指定各個選項。 您可以多次開始和停止資料收集。

    |選項|描述|
    |------------|-----------------|
    |[/globalon/globaloff](../profiling/globalon-and-globaloff.md)|開始 (**/globalon**) 或停止 (**/globaloff**) 所有處理序的資料收集。|
    |[/processon](../profiling/processon-and-processoff.md) **：** `PID` [/processoff](../profiling/processon-and-processoff.md) **：**`PID`|開始 (**/processon**) 或停止 (**/processoff**) 對 `PID` 指定的處理序收集資料。|
    |[/attach](../profiling/attach.md) **：**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**：**{ `PID`&#124;`ProcName` }]|**/attach** 會開始收集 `PID` 或處理序名稱 (ProcName) 指定的處理序資料。 如果未指定特定進程， **/detach** 會停止指定進程或所有進程的資料收集。|

## <a name="end-the-profiling-session"></a>結束程式碼剖析工作階段

若要結束程式碼剖析工作階段，必須從所有分析的處理序中斷連結程式碼剖析工具，而且必須明確地關閉程式碼剖析工具。 您可以關閉應用程式或呼叫 **VSPerfCmd /detach** 選項，以從使用取樣方法剖析的應用程式中斷連結程式碼剖析工具。 接著呼叫 **VSPerfCmd /shutdown** 選項以停止程式碼剖析工具，並關閉程式碼剖析資料檔案。 **VSPerfClrEnv /off** 命令會清除程式碼剖析環境變數。

### <a name="to-end-a-profiling-session"></a>結束程式碼剖析工作階段

1. 執行下列其中一個步驟，以從目標應用程式中斷連結程式碼剖析工具：

    - 輸入 **>vsperfcmd/detach**

         -或-

    - 關閉目標應用程式。

2. 關閉程式碼剖析工具。 輸入：

     **>vsperfcmd**  [/shutdown](../profiling/shutdown.md)

3. (選擇性) 清除程式碼剖析環境變數。 輸入：

     **VSPerfCmd /off**

## <a name="see-also"></a>另請參閱

[分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md) 
[.Net 記憶體資料檢視](../profiling/dotnet-memory-data-views.md)
