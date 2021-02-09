---
title: 將分析工具附加至原生服務以取得並行資料
description: 從命令列使用 Visual Studio 分析工具，從原生 (C/c + +) 服務收集進程和執行緒並行資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 283a1ee1-b43e-4daf-95ae-1311925a42a8
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 301e507e7debb04aab25b30e0a4e8f234f57a46b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881629"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line-vsperfcmd"></a>如何：使用命令列將分析工具附加至原生服務以收集並行資料 (>vsperfcmd) 
本文描述如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具命令列工具將分析工具附加至原生 (C/C++) 服務，並使用取樣方法收集處理序和執行緒並行資料。

> [!NOTE]
> Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 UWP App 也需要新的收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。

> [!NOTE]
> 若要取得分析工具的路徑，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要使用程式碼剖析工具命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。

 程式碼剖析工具附加至服務時，您可以暫停和繼續收集資料。 若要結束分析工作階段，分析工具不得再附加至服務，而且必須明確地關閉分析工具。

## <a name="attach-the-profiler"></a>附加分析工具
 若要將程式碼剖析工具附加至原生服務，您可以使用 **VSPerfCmd/start** 和 **/attach** 選項初始化程式碼剖析工具，並將它附加至目標應用程式。 您可以在單一命令列上指定 **/start** 和 **/attach** 及其個別選項。 您也可以加入 **/globaloff** 選項以在目標應用程式啟動時暫停資料收集。 然後使用 **/globalon** 開始收集資料。

#### <a name="to-attach-the-profiler-to-a-native-service"></a>將分析工具附加至原生服務

1. 如果服務未執行，請啟動服務。

2. 在命令提示字元中輸入下列命令，以啟動程式碼剖析工具︰

    [>vsperfcmd](../profiling/vsperfcmd.md) **/start： concurrency/output：** `OutputFile` [ `Options` ]

   - /Start 需要 [/output](../profiling/output.md)**：** `OutputFile` 選項。  `OutputFile` 指定程式碼剖析資料 (.vsp) 檔案的名稱和位置。

     您可以使用下表中的任一選項搭配 **/start** 選項。

   > [!NOTE]
   > 大多數服務都需要 **/user** 和 **/crosssession** 選項。

   | 選項 | Description |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **：**[ `Domain\` ]`UserName` | 指定要授與程式碼剖析工具存取權之帳戶的選擇性網域和使用者名稱。 |
   | [/crosssession](../profiling/crosssession.md) | 在其他登入工作階段啟用處理序程式碼剖析。 |
   | [/wincounter](../profiling/wincounter.md) **：**`WinCounterPath` | 指定程式碼剖析期間要收集的 Windows 效能計數器。 |
   | [/automark](../profiling/automark.md) **：**`Interval` | 只能搭配 **/wincounter** 使用。 指定 Windows 效能計數器收集事件間隔的毫秒數。 預設值為 500。 |
   | [/events](../profiling/events-vsperfcmd.md) **：**`Config` | 指定程式碼剖析期間要收集的 Windows 事件追蹤 (ETW) 事件。 ETW 事件會收集至個別的 (.etl) 檔案。 |

3. 在命令提示字元中輸入下列命令，以將程式碼剖析工具附加至服務︰

    **VSPerfCmd /attach:** `PID`

    `PID` 指定目標應用程式的處理序 ID 或處理序名稱。 您可以在 [Windows 工作管理員] 中檢視所有執行中處理序的處理序 ID。

## <a name="control-data-collection"></a>控制資料收集
 當目標應用程式正在執行時，您可以使用 *VSPerfCmd.exe* 選項啟動和停止將資料寫入檔案，以控制資料收集。 透過控制資料收集，您可以收集特定程式執行 (例如啟動或關閉應用程式) 的資料。

#### <a name="to-start-and-stop-data-collection"></a>開始和停止資料收集

- 下表中成對的選項會開始和停止資料收集。 請在個別的命令列上指定各個選項。 您可以多次開始和停止資料收集。

    |選項|Description|
    |------------|-----------------|
    |[/globalon/globaloff](../profiling/globalon-and-globaloff.md)|開始 (**/globalon**) 或停止 (**/globaloff**) 所有處理序的資料收集。|
    |[/processon](../profiling/processon-and-processoff.md) **：** `PID` [/processoff](../profiling/processon-and-processoff.md) **：**`PID`|開始 (**/processon**) 或停止 (**/processoff**) 處理序 ID (`PID`) 指定的處理序資料收集。|
    |[/attach](../profiling/attach.md) **：**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**：**{ `PID`&#124;`ProcName` }]|**/attach** 會開始為處理序 ID (`PID`) 或處理序名稱 (*ProcName*) 指定的處理序收集資料。 **/detach** 會停止指定的處理序或所有處理序 (如果未指定處理序) 的資料收集。|

## <a name="end-the-profiling-session"></a>結束程式碼剖析工作階段
 若要結束程式碼剖析工作階段，程式碼剖析工具不得進行資料收集。 您可以停止服務或叫用 **VSPerfCmd /detach** 選項，以停止從使用並行方法剖析的原生服務中收集資料。 接著叫用 **VSPerfCmd /shutdown** 選項以停止程式碼剖析工具，並關閉程式碼剖析資料檔案。

#### <a name="to-end-a-profiling-session"></a>結束程式碼剖析工作階段

1. 停止服務或在命令提示字元中輸入下列命令，以將程式碼剖析工具從目標應用程式中斷連結︰

     輸入 **>vsperfcmd/detach**

2. 在命令提示字元中輸入下列命令，以關閉程式碼剖析工具︰

     **>vsperfcmd**  [/shutdown](../profiling/shutdown.md)
