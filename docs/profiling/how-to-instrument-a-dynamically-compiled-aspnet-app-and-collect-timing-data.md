---
title: HOW TO：使用命令列以分析工具檢測動態編譯的 ASP.NET Web 應用程式並收集詳細計時資料 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 581c72ba7a43e3a7b31fa45e10067e33e15f4e35
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63386521"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>HOW TO：使用命令列以分析工具檢測動態編譯的 ASP.NET Web 應用程式並收集詳細計時資料

本文描述如何使用 Visual Studio 分析工具命令列工具，利用檢測分析方法來收集動態編譯之 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 應用程式的詳細計時資料。

> [!NOTE]
> 若要取得分析工具的路徑，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要使用程式碼剖析工具命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。

若要從 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式收集效能資料，您需要修改目標應用程式的 *web.config* 檔案來啟用 [VSInstr.exe](../profiling/vsinstr.md) 工具，以檢測動態編譯的應用程式檔案。 接著，您需要使用 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 工具在 網頁伺服器上設定適當的環境變數以啟用分析，然後重新啟動電腦。

請啟動分析工具，然後執行目標應用程式。 程式碼剖析工具附加至應用程式時，您可以暫停和繼續收集資料。 完成分析時，請關閉應用程式、關閉 Internet Information Services (IIS) 背景工作處理序，然後關閉分析工具。 完成分析工作後，請將 *web.config* 檔案和網頁伺服器還原至其原始狀態。

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>設定 ASP.NET Web 應用程式和網頁伺服器

1. 修改目標應用程式的 *web.config* 檔案。 請參閱[如何：修改 Web.Config 檔案以檢測並分析動態編譯的 ASP.NET Web 應用程式](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md)。

2. 開啟 [命令提示字元] 視窗。

3. 初始化程式碼剖析環境變數。 類型：

     **VSPerfClrEnv /globaltraceon**

    - **/globaltraceon** 可讓您使用檢測方法來啟用分析。

4. 重新啟動電腦。

## <a name="run-the-profiling-session"></a>執行分析工作階段

1. 開啟 [命令提示字元] 視窗。

2. 啟動分析工具。 類型：

     **VSPerfCmd**  [/start](../profiling/start.md) **:trace**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - **/start:trace** 選項會將分析工具初始化。

   - **/output:**`OutputFile` 選項必須搭配 **/start** 使用。 `OutputFile` 指定分析資料 (.*vsp*) 檔案的名稱和位置。

     您可以使用下列任一選項搭配 **/start:trace** 選項。

     > [!NOTE]
     > **/user** 和 **/crosssession** 選項通常是 ASP.NET 應用程式的必要選項。

     | 選項 | 說明 |
     | - | - |
     | [/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | 指定擁有 ASP.NET 背景工作處理序之帳戶的網域和使用者名稱。 如果以登入的使用者之外的使用者身分執行處理程序，就需要這個選項。 處理序擁有者會列在 [Windows 工作管理員] [處理序] 索引標籤上的 [使用者名稱] 資料行。 |
     | [/crosssession](../profiling/crosssession.md) | 在其他登入工作階段啟用處理序程式碼剖析。 如果 ASP.NET 應用程式是在不同的工作階段中執行，就需要這個選項。 工作階段識別碼會列在 [Windows 工作管理員] 之 [處理程序] 索引標籤上的 [工作階段識別碼] 資料行中。 **/crosssession** 可縮寫成 **/CS**。 |
     | [/globaloff](../profiling/globalon-and-globaloff.md) | 啟動分析工具，但暫停資料收集。 使用 [/globalon](../profiling/globalon-and-globaloff.md) 以繼續程式碼剖析。 |
     | [/counter](../profiling/counter.md) **:** `Config` | 從 `Config` 中指定的處理器效能計數器收集資訊。 計數器資訊會新增至在每個程式碼剖析事件收集的資料。 |
     | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | 指定程式碼剖析期間要收集的 Windows 效能計數器。 |
     | [/automark](../profiling/automark.md) **:** `Interval` | 只能搭配 **/wincounter** 使用。 指定 Windows 效能計數器收集事件間隔的毫秒數。 預設值為 500 毫秒。 |
     | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | 指定程式碼剖析期間要收集的 Windows 事件追蹤 (ETW) 事件。 ETW 事件會收集至個別的 (.*etl*) 檔案。 |

3. 以一般方式啟動 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式。

## <a name="control-data-collection"></a>控制資料收集

當目標應用程式在執行時，您可以使用 *VSPerfCmd.exe* 選項，藉由開始和停止將資料寫入至分析工具資料檔中的方式，控制資料收集。 控制資料收集可讓您收集特定程式執行 (例如啟動或關閉應用程式) 的資料。

- 下列成對的選項會開始和停止資料收集。 請在個別的命令列上指定各個選項。 您可以多次開始和停止資料收集。

    |選項|說明|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|開始 (**/globalon**) 或停止 (**/globaloff**) 所有處理序的資料收集。|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|開始 (**/processon**) 或停止 (**/processoff**) 處理序 ID (`PID`) 指定的處理序資料收集。|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|開始 (**/threadon**) 或停止 (**/threadoff**) 執行緒識別碼 (`TID`) 所指定執行緒的資料收集。|

- 您也可以使用 **VSPerfCmd.exe**[/mark](../profiling/mark.md) 選項將程式碼剖析標記插入資料檔案。 **/mark** 命令會新增識別碼、時間戳記和一個選擇性的使用者定義文字字串。 標記可用來篩選程式碼剖析工具報告和資料檢視中的資料。

## <a name="end-the-profiling-session"></a>結束程式碼剖析工作階段

若要結束分析工作階段，請關閉目標 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式、重設 IIS 以停止已分析的處理序，然後關閉分析工具。

1. 關閉 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式。

2. 重設 Internet Information Services (IIS) 來關閉 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序。 類型：

     **IISReset /stop**

3. 關閉分析工具。 類型：

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

4. 重新啟動 IIS。 類型：

     **IISReset /start**

## <a name="restore-the-application-and-computer-configuration"></a>還原應用程式和電腦組態

當您已完成所有分析時，請取代 *web.config* 檔案、清除分析環境變數，然後重新啟動電腦，將應用程式和伺服器還原至進行分析之前的狀態。

1. 以原始檔案複本取代 *web.config* 檔案。

2. 清除分析環境變數。 類型：

     **VSPerfCmd /globaloff**

3. 重新啟動電腦。

## <a name="see-also"></a>另請參閱

[分析 ASP.NET Web 應用程式程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)
[檢測方法資料檢視](../profiling/instrumentation-method-data-views.md)