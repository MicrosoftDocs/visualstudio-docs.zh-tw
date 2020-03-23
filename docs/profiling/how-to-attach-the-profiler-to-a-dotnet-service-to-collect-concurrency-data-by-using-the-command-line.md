---
title: 將分析工具附加至 .NET 服務以收集並行資料
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ffbdfe37-8325-44be-bd36-2c8aab2dec7b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: a95e907379db19d88fd7204e8410038ddb881d3b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779112"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-concurrency-data-by-using-the-command-line"></a>如何：使用命令列將分析工具附加至 .NET 服務以收集並行資料
本文描述如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具命令列工具將分析工具附加至 .NET Framework 服務，並使用取樣方法收集處理序和執行緒並行資料。

> [!NOTE]
> Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 UWP App 也需要新的收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。

> [!NOTE]
> 若要取得分析工具的路徑，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要使用程式碼剖析工具命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。

 若要收集並行資料，您要將程式碼剖析工具附加至服務處理序。 程式碼剖析工具附加至服務時，您可以暫停和繼續收集資料。 若要結束分析工作階段，分析工具不得再附加至服務，而且必須明確地關閉分析工具。 在大部分情況下，建議您在工作階段結束時清除程式碼剖析環境變數。

## <a name="attach-the-profiler"></a>附加分析工具

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>將分析工具附加至 .NET Framework 服務

1. 安裝服務。

2. 開啟命令視窗。

3. 初始化程式碼剖析環境變數。 輸入：

     [VSPerfClrEnv](../profiling/vsperfclrenv.md) **/globalsampleon** [**/samplelineoff**]

    - **/globalsampleon** 會啟用取樣。

    - **/samplelineoff** 會停止將收集的資料指派給特定的原始程式碼行。 指定此選項時，資料只會指派給函式。

4. 重新啟動電腦。

5. 啟動分析工具。 輸入：

     [VSPerfCmd](../profiling/vsperfcmd.md) **/開始：併發/輸出：** `OutputFile` |`Options`

     [/輸出](../profiling/output.md)**：**`OutputFile`選項在 **/start**時是必需的。 `OutputFile` 指定程式碼剖析資料 (.vsp) 檔案的名稱和位置。

     您可以使用下列任一選項搭配 **/start** 選項。

    > [!NOTE]
    > **/User** 和 **/crosssession** 選項通常是服務的必要選項。

    |選項|描述|
    |------------|-----------------|
    |[/使用者](../profiling/user-vsperfcmd.md) **：**[ ]`Domain` **\\**`UserName`|指定擁有程式碼剖析處理序之帳戶的網域和使用者名稱。 只有在以登入的使用者之外的使用者身分執行處理序時，才需要這個選項。 進程擁有者列在 Windows 工作管理員的"**進程"** 選項卡上的 **"使用者名**"列中。|
    |[/交叉會話](../profiling/crosssession.md)|在其他工作階段啟用處理序程式碼剖析。 如果服務在不同的工作階段中執行，則需要這個選項。 會話 ID 列在 Windows 工作管理員的 **"進程"** 選項卡上的 **"會話 ID"** 列中。 **/crosssession** 可縮寫成 **/CS**。|
    |[/贏計數器](../profiling/wincounter.md) **：**`WinCounterPath`|指定程式碼剖析期間要收集的 Windows 效能計數器。|
    |[/自動標記](../profiling/automark.md) **：**`Interval`|只能搭配 **/wincounter** 使用。 指定 Windows 效能計數器收集事件間隔的毫秒數。 預設值為 500 毫秒。|
    |[/事件](../profiling/events-vsperfcmd.md) **：**`Config`|指定程式碼剖析期間要收集的 Windows 事件追蹤 (ETW) 事件。 ETW 事件在單獨的 （中收集）*etl*） 檔。|

6. 如有必要，請啟動該服務。

7. 將程式碼剖析工具附加至服務。 輸入：

     **VSPerfCmd /附加：** `PID` [[/目標clr](../profiling/targetclr.md)**：**`Version`]

    - `PID` 指定服務的處理序 ID 或處理序名稱。 您可以在 [Windows 工作管理員] 中檢視所有執行中處理序的處理序 ID。

    - **目標clr：**`Version`指定在應用程式中載入多個版本的運行時時要設定檔的通用語言運行時 （CLR） 的版本。 選擇性。

## <a name="control-data-collection"></a>控制資料收集
 在服務運行時，您可以通過使用*VSPerfCmd.exe*選項啟動和停止將資料寫入檔來控制資料收集。 控制資料收集可讓您收集特定程式執行 (例如啟動或關閉應用程式) 的資料。

#### <a name="to-start-and-stop-data-collection"></a>開始和停止資料收集

- 以下**VSPerfCmd**選項對開始並停止資料收集。 請在個別的命令列上指定各個選項。 您可以多次開始和停止資料收集。

    |選項|描述|
    |------------|-----------------|
    |[/全域/全域關閉](../profiling/globalon-and-globaloff.md)|開始 (**/globalon**) 或停止 (**/globaloff**) 所有處理序的資料收集。|
    |[/進程](../profiling/processon-and-processoff.md)**：** `PID` [/進程關閉](../profiling/processon-and-processoff.md) **：**`PID`|開始 (**/processon**) 或停止 (**/processoff**) 處理序 ID (`PID`) 指定的處理序資料收集。|
    |**/附加：** `PID` [ `ProcName`&#124;] [/分離](../profiling/detach.md)[： ]`PID`&#124;`ProcName`*|**/attach** 會開始為處理序 ID 或處理序名稱指定的處理序收集資料。 **/detach**將停止對指定進程或未指定特定進程的所有進程的資料收集。|

- 您也可以使用 **VSPerfCmd.exe**[/mark](../profiling/mark.md) 選項將程式碼剖析標記插入資料檔案。 **/mark** 命令會新增識別碼、時間戳記和一個選擇性的使用者定義文字字串。 標記可用來篩選程式碼剖析工具報告和資料檢視中的資料。 下列成對的 VSPerfCmd 選項會開始和停止資料收集。 請在個別的命令列上指定各個選項。 您可以多次開始和停止資料收集。

## <a name="end-the-profiling-session"></a>結束程式碼剖析工作階段
 若要結束程式碼剖析工作階段，程式碼剖析工具不得進行資料收集。 您可以停止服務或叫用 **VSPerfCmd /detach** 選項，以停止從使用並行方法剖析的應用程式中收集資料。 接著叫用 **VSPerfCmd /shutdown** 選項以停止程式碼剖析工具，並關閉程式碼剖析資料檔案。 **VSPerfClrEnv /globaloff** 命令會清除程式碼剖析環境變數，但在重新啟動電腦之前不會重設系統組態。

#### <a name="to-end-a-profiling-session"></a>結束程式碼剖析工作階段

1. 執行下列其中一項動作，以從目標應用程式中斷連結程式碼剖析工具。

    - 停止服務。

         -或-

    - 輸入 **VSPerfCmd /detach**。

2. 關閉程式碼剖析工具。 輸入：

     **VSPerfCmd**  [Shutdown](../profiling/shutdown.md)
