---
title: 將分析工具附加至原生應用程式 & 收集並行資料
description: 使用 Visual Studio 分析工具命令列工具，將分析工具附加至執行中的原生 (C/c + +) 獨立應用程式，並取得執行緒爭用資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 12d3e0f3-4b74-4e66-8fbf-8ac99bd4f91c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: fd06783f50708e13c97f7bfe00a22be26739fd9c
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801643"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line"></a>如何：使用命令列將分析工具附加至原生獨立應用程式並收集並行資料
本文描述如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具命令列工具將分析工具附加至執行中的原生 (C/C++) 獨立應用程式，並收集執行緒爭用資料。

> [!NOTE]
> 若要取得分析工具的路徑，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要使用程式碼剖析工具命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。

 程式碼剖析工具附加至應用程式時，您可以暫停和繼續收集資料。 若要結束程式碼剖析工作階段，程式碼剖析工具不得再附加至應用程式，而且必須明確地關閉程式碼剖析工具。

## <a name="attach-the-profiler-to-a-running-native-application"></a>將分析工具附加至執行中的原生應用程式

#### <a name="to-attach-the-profiler-to-a-running-native-application"></a>將分析工具附加至執行中的原生應用程式

1. 在命令提示字元中，輸入下列命令：

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency**

     您可以使用下表中的任一選項搭配 **/start:concurrency** 選項。

    |選項|描述|
    |------------|-----------------|
    |[/user](../profiling/user-vsperfcmd.md) **：**[ `Domain\` ]`Username`|指定要授與程式碼剖析工具存取權之帳戶的選擇性網域和使用者名稱。|
    |[/crosssession](../profiling/crosssession.md)|在其他登入工作階段啟用處理序程式碼剖析。|
    |[/wincounter](../profiling/wincounter.md) **：**`WinCounterPath`|指定程式碼剖析期間要收集的 Windows 效能計數器。|
    |[/automark](../profiling/automark.md) **：**`Interval`|只能搭配 **/wincounter** 使用。 指定 Windows 效能計數器收集事件間隔的毫秒數。 預設值為 500。|
    |[/events](../profiling/events-vsperfcmd.md) **：**`Config`|指定程式碼剖析期間要收集的 Windows 事件追蹤 (ETW) 事件。 ETW 事件會收集至個別的 (.etl) 檔案。|

2. 輸入下列命令，將程式碼剖析工具附加至目標應用程式︰

     **>vsperfcmd**  [/attach](../profiling/attach.md) **：**{ `PID`&#124;`ProcName` }

     `PID` 指定目標應用程式的處理序 ID。 您可以在 [Windows 工作管理員] 中檢視所有執行中處理序的處理序 ID。

## <a name="control-data-collection"></a>控制資料收集
 當目標應用程式執行時，您可以使用 *VSPerfCmd.exe* 選項開始和停止將資料寫入至檔案，以控制資料收集。 透過控制資料收集，您可以收集特定程式執行 (例如啟動或關閉應用程式) 的資料。

#### <a name="to-start-and-stop-data-collection"></a>開始和停止資料收集

- 下表中成對的選項會開始和停止資料收集。 請在個別的命令列上指定各個選項。 您可以多次開始和停止資料收集。

    |選項|描述|
    |------------|-----------------|
    |[/globalon/globaloff](../profiling/globalon-and-globaloff.md)|開始 (**/globalon**) 或停止 (**/globaloff**) 所有處理序的資料收集。|
    |[/processon](../profiling/processon-and-processoff.md) **：** `PID` [/processoff](../profiling/processon-and-processoff.md) **：**`PID`|開始 (**/processon**) 或停止 (**/processoff**) 處理序 ID (`PID`) 指定的處理序資料收集。|
    |[/attach](../profiling/attach.md) **：**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**：**{ `PID`&#124;`ProcName` }]|**/attach** 會開始為處理序 ID (`PID`) 或處理序名稱 (*ProcName*) 指定的處理序收集資料。 **/detach** 會停止指定的處理序或所有處理序 (如果未指定處理序) 的資料收集。|

## <a name="end-the-profiling-session"></a>結束程式碼剖析工作階段
 若要結束程式碼剖析工作階段，程式碼剖析工具不得進行資料收集。 您可以關閉應用程式或叫用 **VSPerfCmd /detach** 選項，以停止從使用取樣方法剖析的應用程式中收集資料。 接著叫用 **VSPerfCmd /shutdown** 選項以停止程式碼剖析工具，並關閉程式碼剖析資料檔案。

#### <a name="to-end-a-profiling-session"></a>結束程式碼剖析工作階段

1. 關閉目標應用程式或輸入下列命令，以將程式碼剖析工具從目標應用程式中斷連結︰

     **VSPerfCmd /detach**

2. 輸入下列命令以關閉程式碼剖析工具︰

     **>vsperfcmd**  [/shutdown](../profiling/shutdown.md)
