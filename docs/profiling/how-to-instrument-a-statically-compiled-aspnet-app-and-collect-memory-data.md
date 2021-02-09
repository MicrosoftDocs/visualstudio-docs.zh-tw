---
title: Profiler 命令列檢測靜態 ASP.NET 應用程式，取得記憶體資料
description: 瞭解如何使用 Visual Studio 分析工具命令列工具收集預先編譯 ASP.NET web 元件或網站的記憶體和計時資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ea1dcb7c-1dc3-49ff-9418-8795b5b3d3bc
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d067e929fe36036457bef59b6ff477180b51c6dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928948"
---
# <a name="how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>如何：使用分析工具命令列檢測靜態編譯的 ASP.NET Web 應用程式並收集記憶體資料
本文描述如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具命令列工具來檢測先行編譯的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 元件或網站，並收集 .NET 記憶體配置、物件存留期和詳細的計時資料。

> [!NOTE]
> 若要取得分析工具的路徑，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要使用程式碼剖析工具命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。

 若要使用檢測方法從 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 元件收集資料，您可使用 [VSInstr.exe](../profiling/vsinstr.md) 工具產生已檢測的元件版本。 在主控元件的電腦上，使用已檢測版本取代元件的未檢測版本。 然後使用 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 工具初始化全域分析環境變數，並重新啟動主機電腦。 然後啟動分析工具。

 執行已檢測的元件時，計時資料會自動收集到資料檔案。 程式碼剖析工作階段期間，您可以暫停和繼續資料收集。

 若要結束分析工作階段，您要關閉主控元件的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序，並明確地關閉分析工具。 在大部分情況下，建議您在工作階段結束時清除程式碼剖析環境變數。

## <a name="start-to-profile"></a>開始分析

#### <a name="to-instrument-an-aspnet-web-component-and-start-profiling"></a>檢測 ASP.NET Web 元件並開始分析

1. 使用 [VSInstr] 工具產生已檢測版的目標應用程式。 如有必要，使用已檢測的二進位檔取代 ASP.NET 主機電腦上的應用程式二進位檔。

2. 開啟 [命令提示字元] 視窗

3. 初始化 .NET 程式碼剖析環境變數。 在 [命令提示字元] 視窗中鍵入：

    **VSPerfClrEnv /globaltracegc**

    -或-

    **VSPerfClrEnv /globaltracegclife**

   - **/globaltracegc** 會收集 .NET 記憶體配置和計時資料。

   - **/globaltracegclife** 會收集 .NET 記憶體配置、物件存留期和詳細的計時資料。

4. 重新啟動電腦。

5. 開啟 [命令提示字元] 視窗。

6. 啟動分析工具。 在 [命令提示字元] 視窗中鍵入：

    **>vsperfcmd/start： trace/output：** `OutputFile` [`Options`]

   - [/start](../profiling/start.md)**:trace** 選項會初始化程式碼剖析工具。

   - /Start 需要 [/output](../profiling/output.md)**：** `OutputFile` 選項。  `OutputFile` 指定程式碼剖析資料 (.vsp) 檔案的名稱和位置。

     您可以使用下列任一選項搭配 **/start:trace** 選項。

   > [!NOTE]
   > **/user** 和 **/crosssession** 選項通常是 ASP.NET 應用程式的必要選項。

   | 選項 | Description |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **：**[ `Domain` **\\** ]`UserName` | 指定擁有 ASP.NET 背景工作處理序之帳戶的選用網域和使用者名稱。 如果不是使用登入使用者的使用者身分執行處理序，就需要此選項。名稱會列在 [Windows 工作管理員] 之 [處理程序] 索引標籤上的 [使用者名稱] 資料行中。 |
   | [/crosssession](../profiling/crosssession.md) | 在其他工作階段啟用處理序程式碼剖析。 如果應用程式在不同的工作階段中執行，則需要這個選項。 會話識別碼會列在 Windows 工作管理員的 [ **處理** 程式] 索引標籤上的 [會話識別碼] 欄中。 **/crosssession** 可縮寫成 **/CS**。 |
   | [/wincounter](../profiling/wincounter.md) **：**`WinCounterPath` | 指定程式碼剖析期間要收集的 Windows 效能計數器。 |
   | [/automark](../profiling/automark.md) **：**`Interval` | 只能搭配 **/wincounter** 使用。 指定 Windows 效能計數器收集事件間隔的毫秒數。 預設值為 500 毫秒。 |
   | [/events](../profiling/events-vsperfcmd.md) **：**`Config` | 指定程式碼剖析期間要收集的 Windows 事件追蹤 (ETW) 事件。 ETW 事件會收集至個別的 (.etl) 檔案。 |
   | [/globaloff](../profiling/globalon-and-globaloff.md) | 若要啟動暫停資料收集的程式碼剖析工具，請將 **/globaloff** 選項新增到 **/start** 命令列。 使用 **/globalon** 以繼續程式碼剖析。 |

7. 開啟包含已檢測元件的網站。

## <a name="control-data-collection"></a>控制資料收集
 當目標應用程式執行時，您可以使用 *VSPerfCmd.exe* 選項開始和停止將資料寫入至檔案，以控制資料收集。 控制資料收集可讓您收集特定程式執行 (例如啟動或關閉應用程式) 的資料。

#### <a name="to-start-and-stop-data-collection"></a>開始和停止資料收集

- 下列成對的選項會開始和停止資料收集。 請在個別的命令列上指定各個選項。 您可以多次開始和停止資料收集。

    |選項|Description|
    |------------|-----------------|
    |[/globalon/globaloff](../profiling/globalon-and-globaloff.md)|開始 (**/globalon**) 或停止 (**/globaloff**) 所有處理序的資料收集。|
    |[/processon](../profiling/processon-and-processoff.md) **：** `PID` [/processoff](../profiling/processon-and-processoff.md) **：**`PID`|開始 (**/processon**) 或停止 (**/processoff**) 處理序 ID (`PID`) 指定的處理序資料收集。|
    |[/threadon](../profiling/threadon-and-threadoff.md) **：** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **：**`TID`|開始 (**/threadon**) 或停止 (**/threadoff**) 執行緒識別碼 (`TID`) 所指定執行緒的資料收集。|

## <a name="end-the-profiling-session"></a>結束程式碼剖析工作階段
 若要結束分析工作階段，請關閉 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式，然後使用 Internet Information Services (IIS) **IISReset** 命令關閉 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序。 呼叫 **VSPerfCmd** [/shutdown](../profiling/shutdown.md) 選項關閉分析工具，並結束分析資料檔案。 **VSPerfClrEnv /globaloff** 命令會清除分析環境變數。 您必須重新啟動電腦才能套用新的環境設定。

#### <a name="to-end-a-profiling-session"></a>結束程式碼剖析工作階段

1. 關閉 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式。

2. 關閉 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序。 輸入：

    **IISReset /stop**

3. 關閉程式碼剖析工具。 輸入：

    **VSPerfCmd /shutdown**

4. (選擇性) 清除分析環境變數。 輸入：

    **VSPerfCmd /globaloff**

5. 重新啟動電腦。 如有必要，請重新啟動 IIS。 輸入：

    **IISReset /start**

## <a name="see-also"></a>另請參閱
- [分析 ASP.NET web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [.NET 記憶體資料檢視](../profiling/dotnet-memory-data-views.md)
