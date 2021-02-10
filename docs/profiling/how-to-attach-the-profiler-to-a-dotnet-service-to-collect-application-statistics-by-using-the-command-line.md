---
title: 將分析工具附加至 .NET 服務以收集應用程式統計資料
description: 使用 Visual Studio 分析工具命令列工具將分析工具附加至 .NET Framework 服務，並使用取樣方法取得效能統計資料。
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a0046c47-26c8-4bec-96a0-81da05e5104a
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 3808f004d9813e846a10c2b672b6406f9cc54cde
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958878"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-application-statistics-by-using-the-command-line"></a>如何：使用命令列將分析工具附加至 .NET 服務以收集應用程式統計資料
本文描述如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具命令列工具將分析工具附加至 .NET Framework 服務，並使用取樣方法收集效能統計資料。

> [!NOTE]
> Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 UWP App 也需要新的收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。
>
> 若要取得分析工具的路徑，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要使用程式碼剖析工具命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。
>
> 若要將階層互動資料加入至程式碼剖析回合中，則需要使用命令列程式碼剖析工具的特定程序。 請參閱 [收集階層互動資料](../profiling/adding-tier-interaction-data-from-the-command-line.md)。

 若要收集 .NET Framework 服務的效能資料，請使用 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 工具來初始化適當的環境變數。 您必須接著重新啟動裝載服務的電腦，並設定該電腦進行分析。 接著將分析工具附加至服務處理序。 分析工具附加至服務時，您可以暫停和繼續收集資料。

 若要結束分析工作階段，必須從服務中斷連結分析工具，而且必須明確地關閉分析工具。 在大部分情況下，建議您在工作階段結束時清除程式碼剖析環境變數。

## <a name="attach-the-profiler"></a>附加分析工具

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>將分析工具附加至 .NET Framework 服務

1. 安裝服務。

2. 開啟 [命令提示字元] 視窗。

3. 初始化程式碼剖析環境變數。 輸入：

    **VSPerfClrEnv /globalsampleon** [**/samplelineoff**]

   - **/globalsampleon** 會啟用取樣。

   - **/samplelineoff** 會停止將收集的資料指派給特定的原始程式碼行。 指定此選項時，資料只會指派給函式。

4. 重新啟動電腦。

5. 開啟 [命令提示字元] 視窗。

6. 啟動分析工具。 輸入：

    **>vsperfcmd**  [/start](../profiling/start.md) **： sample**  [/output](../profiling/output.md) **：** `OutputFile` [ `Options` ]

   - **/Start： sample** 選項會初始化 profiler。

   - /Start 需要 **/output：** `OutputFile` 選項。  `OutputFile` 指定程式碼剖析資料 (.vsp) 檔案的名稱和位置。

     您可以使用下列任一選項搭配 **/start:sample** 選項。

   > [!NOTE]
   > **/User** 和 **/crosssession** 選項通常是服務的必要選項。

   | 選項 | Description |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **：**[ `Domain` **\\** ]`UserName` | 指定擁有程式碼剖析處理序之帳戶的網域和使用者名稱。 只有在以登入的使用者之外的使用者身分執行處理序時，才需要這個選項。 處理序擁有者會列在 [Windows 工作管理員] 的 [處理程序] 索引標籤上的 [使用者名稱] 欄。 |
   | [/crosssession](../profiling/crosssession.md) | 在其他工作階段啟用處理序程式碼剖析。 如果服務在不同的工作階段中執行，則需要這個選項。 工作階段識別碼會列在 [Windows 工作管理員] 的 [處理程序] 索引標籤上的 [工作階段識別碼] 欄。 **/crosssession** 可縮寫成 **/CS**。 |
   | [/wincounter](../profiling/wincounter.md) **：**`WinCounterPath` | 指定程式碼剖析期間要收集的 Windows 效能計數器。 |
   | [/automark](../profiling/automark.md) **：**`Interval` | 只能搭配 **/wincounter** 使用。 指定 Windows 效能計數器收集事件間隔的毫秒數。 預設值為 500 毫秒。 |
   | [/events](../profiling/events-vsperfcmd.md) **：**`Config` | 指定程式碼剖析期間要收集的 Windows 事件追蹤 (ETW) 事件。 ETW 事件會收集至個別的 (.etl) 檔案。 |

7. 如有必要，請啟動該服務。

8. 將程式碼剖析工具附加至服務。 輸入：

    **>vsperfcmd**[/attach](../profiling/attach.md) **：** { `PID`&#124;`ProcName` } [ `Sample Event` ] [[/targetclr](../profiling/targetclr.md)**：** `Version` ]  

   - 指定服務的處理序識別碼 (`PID`) 或處理序名稱 (ProcName)。 您可以在 [Windows 工作管理員] 中檢視所有執行中處理序的處理序識別碼和名稱。

     根據預設，每經過 10,000,000 個未暫止處理器時脈週期，會取樣一次效能資料。 這在 1GH 處理器上大約是每秒 100 次取樣。 您可以指定下列任一選項來變更時脈週期間隔，或指定不同的取樣事件。

   |取樣事件|Description|
   |------------------|-----------------|
   |[/timer](../profiling/timer.md) **：**`Interval`|將取樣間隔變更為 `Interval` 指定的未暫止時脈週期數。|
   |[/pf](../profiling/pf.md)[**：** `Interval` ]|將取樣事件變更為分頁錯誤。 如果指定 `Interval`，請設定樣本間的分頁錯誤數。 預設值為 10。|
   |[/sys](../profiling/sys-vsperfcmd.md)[ `:``Interval` ]|將取樣事件從處理器變更為作業系統核心的系統呼叫 (syscalls)。 如果指定 `Interval`，請設定樣本間的呼叫數。 預設值為 10。|
   |[/counter](../profiling/counter.md) **：**`Config`|將取樣事件與間隔變更為 `Config` 中指定的處理器效能計數器與間隔。|

   - **targetclr：** `Version` 指定當應用程式載入多個版本的執行時間時，要進行分析的 common language runtime 版本 (CLR) 。 選擇性。

## <a name="control-data-collection"></a>控制資料收集
 當服務執行時，您可以使用 *VSPerfCmd.exe* 選項開始和停止將資料寫入至分析工具資料檔案。 控制資料收集可讓您收集特定程式執行 (例如啟動或關閉應用程式) 的資料。

#### <a name="to-start-and-stop-data-collection"></a>開始和停止資料收集

- 下列 **>vsperfcmd** 選項配對會開始和停止資料收集。 請在個別的命令列上指定各個選項。 您可以多次開始和停止資料收集。

    |選項|Description|
    |------------|-----------------|
    |[/globalon/globaloff](../profiling/globalon-and-globaloff.md)|開始 (**/globalon**) 或停止 (**/globaloff**) 所有處理序的資料收集。|
    |[/processon](../profiling/processon-and-processoff.md) **：** `PID` [/processoff](../profiling/processon-and-processoff.md) **：**`PID`|開始 (**/processon**) 或停止 (**/processoff**) 處理序 ID (`PID`) 指定的處理序資料收集。|
    |**/attach：**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[： { `PID`&#124;`ProcName` }]|**/attach** 會開始為處理序 ID 或處理序名稱指定的處理序收集資料。 如果未指定特定進程， **/detach** 會停止指定進程或所有進程的資料收集。|

## <a name="end-the-profiling-session"></a>結束程式碼剖析工作階段
 若要結束程式碼剖析工作階段，必須從所有分析的處理序中斷連結程式碼剖析工具，而且必須明確地關閉程式碼剖析工具。 您可以關閉應用程式或呼叫 **VSPerfCmd /detach** 選項，以從使用取樣方法分析的應用程式中斷連結。 接著呼叫 **VSPerfCmd /shutdown** 選項以停止程式碼剖析工具，並關閉程式碼剖析資料檔案。

 **VSPerfClrEnv /globaloff** 命令會清除程式碼剖析環境變數，但在重新啟動電腦之前不會重設系統組態。

#### <a name="to-end-a-profiling-session"></a>結束程式碼剖析工作階段

1. 執行下列其中一項動作，以從目標應用程式中斷連結分析工具：

    - 停止服務。

         -或-

    - 輸入 **>vsperfcmd/detach**

2. 關閉程式碼剖析工具。 輸入：

     **VSPerfCmd /shutdown**

3. (選擇性) 清除程式碼剖析環境變數。 輸入：

     **VSPerfClrEnv /globaloff**

4. 重新啟動電腦。

## <a name="see-also"></a>另請參閱
- [分析服務](../profiling/command-line-profiling-of-services.md)
- [取樣方法資料檢視](../profiling/profiler-sampling-method-data-views.md)
