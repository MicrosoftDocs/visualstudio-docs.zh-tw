---
title: 探測器命令列：儀器動態ASP.NET應用，獲取記憶體資料
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 3378a45ebace942bb8696f2f67962365b5f57796
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778878"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>如何：使用分析工具命令列檢測動態編譯的 ASP.NET Web 應用程式並收集記憶體資料
本主題描述如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具命令列工具，利用檢測分析方法來收集動態編譯之 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式的詳細 .NET 記憶體配置和物件存留期資料。

> [!NOTE]
> 若要取得分析工具的路徑，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要使用程式碼剖析工具命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。

 要從[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Web 應用程式收集效能資料，請修改目標應用程式的*Web.config*檔，使[VSInstr.exe](../profiling/vsinstr.md)工具能夠檢測動態編譯的應用程式檔。 您接著使用 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 工具來設定裝載 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式的伺服器，並設定適當的環境變數來啟用 .NET 記憶體分析，然後重新啟動電腦。

 若要收集資料，請啟動分析工具，然後執行目標應用程式。 分析工具附加到應用程式時，您可以暫停和繼續資料收集。當您已收集適當的資料時，請關閉應用程式，並關閉 Internet Information Services (IIS) 背景工作處理序，然後關閉分析工具。

 完成分析工作後，將*Web.config 檔和*Web 服務器還原到其原始狀態。

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>設定 ASP.NET Web 應用程式和網頁伺服器

#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>設定 ASP.NET Web 應用程式和網頁伺服器

1. 修改目標應用程式的*Web.config*檔。 請參閱[如何：修改 Web.config 檔以檢測和設定檔動態編譯ASP.NET Web 應用程式](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md)。

2. 在裝載 Web 應用程式的電腦上開啟命令提示字元視窗。

3. 初始化程式碼剖析環境變數。 輸入：

     **VSPerfClrEnv /globaltracegc**

     -或-

     **VSPerfClrEnv /globaltracegclife**

    - **/globaltracegc** 啟用記憶體配置資料的收集。

    - **/globaltracegclife** 啟用記憶體配置資料和物件存留期資料的收集。

4. 重新啟動電腦。

## <a name="run-the-profiling-session"></a>執行分析工作階段

#### <a name="to-profile-the-aspnet-web-application"></a>分析 ASP.NET Web 應用程式

1. 啟動分析工具。 輸入：

    **VSPerfCmd** [/開始](../profiling/start.md) **：跟蹤** [/輸出](../profiling/output.md) **：** `OutputFile` |`Options`

   - **/start：跟蹤**選項初始化探測器。

   - **/輸出：**`OutputFile`選項在 **/start**時是必需的。 `OutputFile`指定分析資料 （的名稱和位置 （。*vsp*） 檔。

     您可以使用下列任一選項搭配 **/start:trace** 選項。

   > [!NOTE]
   > **/user** 和 **/crosssession** 選項通常是 ASP.NET 應用程式的必要選項。

   | 選項 | 描述 |
   | - | - |
   | [/使用者](../profiling/user-vsperfcmd.md) **：**[ ]`Domain` **\\**`UserName` | 指定擁有 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序之帳戶的選用網域和使用者名稱。 如果以登入的使用者之外的使用者身分執行處理序，就需要這個選項。 該名稱列在 Windows 工作管理員的"**進程"** 選項卡上的 **"使用者名**"列中。 |
   | [/交叉會話](../profiling/crosssession.md) | 在其他工作階段啟用處理序程式碼剖析。 如果應用程式在不同的工作階段中執行，則需要這個選項。 會話 ID 列在 Windows 工作管理員的 **"進程"** 選項卡上的 **"會話 ID"** 列中。 **/crosssession** 可縮寫成 **/CS**。 |
   | [/全域關閉](../profiling/globalon-and-globaloff.md) | 啟動分析工具，但暫停資料收集。 使用 [/globalon](../profiling/globalon-and-globaloff.md) 以繼續程式碼剖析。 |
   | [/計數器](../profiling/counter.md) **：**`Config` | 從 `Config` 中指定的處理器效能計數器收集資訊。 計數器資訊會新增至在每個分析事件收集的資料。 |
   | [/贏計數器](../profiling/wincounter.md) **：**`WinCounterPath` | 指定程式碼剖析期間要收集的 Windows 效能計數器。 |
   | [/自動標記](../profiling/automark.md) **：**`Interval` | 只能搭配 **/wincounter** 使用。 指定 Windows 效能計數器收集事件間隔的毫秒數。 預設值為 500 毫秒。 |
   | [/事件](../profiling/events-vsperfcmd.md) **：**`Config` | 指定程式碼剖析期間要收集的 Windows 事件追蹤 (ETW) 事件。 ETW 事件在單獨的 （中收集）*etl*） 檔。 |

2. 以一般方式啟動 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式。

## <a name="control-data-collection"></a>控制資料收集
 當目標應用程式在執行時，您可以使用 *VSPerfCmd.exe* 選項，藉由開始和停止將資料寫入至分析工具資料檔中的方式，控制資料收集。 控制資料收集可讓您收集特定程式執行 (例如啟動或關閉應用程式) 的資料。

#### <a name="to-start-and-stop-data-collection"></a>開始和停止資料收集

- 下列成對的選項會開始和停止資料收集。 請在個別的命令列上指定各個選項。 您可以多次開始和停止資料收集。

    |選項|描述|
    |------------|-----------------|
    |[/全域/全域關閉](../profiling/globalon-and-globaloff.md)|開始 (**/globalon**) 或停止 (**/globaloff**) 所有處理序的資料收集。|
    |[/進程](../profiling/processon-and-processoff.md)**：** `PID` [/進程關閉](../profiling/processon-and-processoff.md) **：**`PID`|開始 (**/processon**) 或停止 (**/processoff**) 處理序 ID (`PID`) 指定的處理序資料收集。|
    |[/執行緒](../profiling/threadon-and-threadoff.md)**：** `TID` [/執行緒關閉](../profiling/threadon-and-threadoff.md) **：**`TID`|開始 (**/threadon**) 或停止 (**/threadoff**) 執行緒識別碼 (`TID`) 所指定執行緒的資料收集。|

- 您也可以使用 **VSPerfCmd.exe**[/mark](../profiling/mark.md) 選項將程式碼剖析標記插入資料檔案。 **/mark** 命令會新增識別碼、時間戳記和一個選擇性的使用者定義文字字串。 標記可用來篩選程式碼剖析工具報告和資料檢視中的資料。

## <a name="end-the-profiling-session"></a>結束程式碼剖析工作階段
 若要結束分析工作階段，請關閉目標 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式，並停止 Internet Information Services (IIS) 以停止已分析的處理序，然後關閉分析工具。 然後重新啟動 IIS。

#### <a name="to-end-a-profiling-session"></a>結束程式碼剖析工作階段

1. 關閉 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式。

2. 重設 Internet Information Services (IIS) 來關閉 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序。 輸入：

    **IISReset /stop**

3. 關閉程式碼剖析工具。 輸入：

    **VSPerfCmd** [/關機](../profiling/shutdown.md)

4. 重新啟動 IIS。 輸入：

    **IISReset /start**

## <a name="restore-the-application-and-computer-configuration"></a>還原應用程式和電腦組態
 完成所有分析後，請替換*Web.config*檔，清除分析環境變數，然後重新開機電腦以將伺服器和[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]應用程式還原到其原始狀態。

#### <a name="to-restore-the-application-and-computer-configuration"></a>還原應用程式和電腦組態

1. 將*Web.config*檔替換為原始檔案的副本。

2. (選擇性)。 清除分析環境變數。 輸入：

     **VSPerfCmd /globaloff**

3. 重新啟動電腦。

## <a name="see-also"></a>另請參閱
- [設定檔ASP.NET Web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [.NET 記憶體資料檢視](../profiling/dotnet-memory-data-views.md)
