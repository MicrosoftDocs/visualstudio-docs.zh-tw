---
title: 將 profiler 附加至 ASP.NET 以收集記憶體資料
description: 使用 Visual Studio 分析工具將分析工具附加至 ASP.NET Web 應用程式，並取得 .NET Framework 記憶體配置數目和大小的相關資料。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d608f85a-41ae-4ca7-85e6-b96624dbc83c
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: eb90141f10787b820fcb31ee0337f6cd8402f084
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877079"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line"></a>如何：使用命令列將分析工具附加至 ASP.NET Web 應用程式以收集記憶體資料
本文描述如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具命令列工具將分析工具附加至 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式，並收集 .NET Framework 記憶體配置數量和大小的相關資料。 您也可以收集 .NET Framework 記憶體物件存留期的相關資料。

> [!NOTE]
> 若要取得分析工具的路徑，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。 在 64 位元電腦上，64 位元和 32 位元版本的工具都可以使用。 若要使用程式碼剖析工具命令列工具，必須將工具路徑加入至命令提示字元視窗的 PATH 環境變數，或將它加入至命令本身。

 若要收集 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式的效能資料，您必須使用 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 工具在裝載 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式的電腦上初始化適當的環境變數。 然後，您必須重新啟動電腦，設定 Web 伺服器進行分析。

 接著使用 [VSPerfCmd.exe](../profiling/vsperfcmd.md) 工具將分析工具附加至裝載您網站的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序。 分析工具附加至應用程式時，您可以暫停和繼續收集資料。

 若要結束分析工作階段，分析工具不得再附加至應用程式，而且必須明確地關閉分析工具。 在大部分情況下，建議您在工作階段結束時清除程式碼剖析環境變數。

## <a name="attach-the-profiler"></a>附加分析工具

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>將分析工具附加至 ASP.NET Web 應用程式

1. 開啟命令提示字元視窗。

2. 初始化程式碼剖析環境變數。 輸入：

    **VSPerfClrEnv** {**/globalsamplegc** &#124; **/globalsamplegclife**} [**/samplelineoff**]

   - 選項 **/globalsamplegc** 和 **/globalsamplegclife** 會指定要收集之記憶體資料的類型。

        只指定下列其中一個選項。

       |選項|Description|
       |------------|-----------------|
       |**/globalsamplegc**|啟用記憶體配置資料的收集功能。|
       |**/globalsamplegclife**|啟用記憶體配置資料和物件存留期資料的收集功能。|

   - **/samplelineoff** 選項會停止將收集的資料指派給特定的原始程式碼。 如果指定此選項，則在函式層級指派資料。

3. 重新啟動電腦，以設定進行新的環境組態。

4. 開啟命令提示字元視窗。 如有必要，設定分析工具路徑環境變數。

5. 啟動分析工具。 輸入：

    **>vsperfcmd**  [/start](../profiling/start.md) **： sample**  [/output](../profiling/output.md) **：** `OutputFile` [ `Options` ]

   - **/Start： sample** 選項會初始化 profiler。

   - /Start 需要 **/output：** `OutputFile` 選項。  `OutputFile` 指定程式碼剖析資料 (.vsp) 檔案的名稱和位置。

     您可以使用下列任一選項搭配 **/start:sample** 選項。

   > [!NOTE]
   > **/user** 和 **/crosssession** 選項通常是 ASP.NET 應用程式的必要選項。

   | 選項 | Description |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **：**[ `Domain` **\\** ]`UserName` | 指定擁有 ASP.NET 背景工作處理序之帳戶的網域和使用者名稱。 如果以登入的使用者之外的使用者身分執行處理程序，就需要這個選項。 處理序擁有者會列在 [Windows 工作管理員] 的 [處理程序] 索引標籤上的 [使用者名稱] 欄。 |
   | [/crosssession](../profiling/crosssession.md) | 在其他登入工作階段啟用處理序程式碼剖析。 如果 ASP.NET 應用程式在不同的工作階段中執行，則需要這個選項。 工作階段識別碼會列在 [Windows 工作管理員] 的 [處理程序] 索引標籤上的 [工作階段識別碼] 欄。 **/crosssession** 可縮寫成 **/CS**。 |
   | [/waitstart](../profiling/waitstart.md) [**：** `Interval` ] | 指定在分析工具傳回錯誤之前，等候它初始化的秒數。 如果未指定 `Interval`，分析工具會無限期等候。 根據預設，**/start** 會立即傳回。 |
   | [/wincounter](../profiling/wincounter.md) **：**`WinCounterPath` | 指定程式碼剖析期間要收集的 Windows 效能計數器。 |
   | [/automark](../profiling/automark.md) **：**`Interval` | 只能搭配 **/wincounter** 使用。 指定 Windows 效能計數器收集事件間隔的毫秒數。 預設值為 500 毫秒。 |
   | [/events](../profiling/events-vsperfcmd.md) **：**`Config` | 指定程式碼剖析期間要收集的 Windows 事件追蹤 (ETW) 事件。 ETW 事件會收集至個別的 (.etl) 檔案。 |

6. 以一般方式啟動 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式。

7. 將分析工具附加至 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序。 輸入：

    **>vsperfcmd**[/attach](../profiling/attach.md) **：**{ `PID`&#124;`ProcName` } [[/targetclr](../profiling/targetclr.md)**：** `Version` ]  

   - 處理序識別碼 `(PID)` 會指定 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序的處理序識別碼或處理序名稱。 您可以在 [Windows 工作管理員] 中檢視所有執行中處理序的處理序 ID。

   - **/targetclr：** `Version` 指定當應用程式載入多個版本的執行時間時，要進行分析的 common language runtime 版本 (CLR) 。

## <a name="control-data-collection"></a>控制資料收集
 當應用程式在執行時，您可以使用 **VSPerfCmd.exe** 選項，藉由開始和停止將資料寫入至分析工具資料檔中的方式，控制資料收集。 控制資料收集可讓您收集特定程式執行 (例如啟動或關閉應用程式) 的資料。

#### <a name="to-start-and-stop-data-collection"></a>開始和停止資料收集

- 下列 **>vsperfcmd** 選項配對會開始和停止資料收集。 請在個別的命令列上指定各個選項。 您可以多次開始和停止資料收集。

    |選項|Description|
    |------------|-----------------|
    |[/globalon/globaloff](../profiling/globalon-and-globaloff.md)|開始 (**/globalon**) 或停止 (**/globaloff**) 所有處理序的資料收集。|
    |[/processon](../profiling/processon-and-processoff.md) **：** `PID` [/processoff](../profiling/processon-and-processoff.md) **：**`PID`|開始 (**/processon**) 或停止 (**/processoff**) `PID` 指定的處理序資料收集。|
    |**/attach：**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**：**{ `PID`&#124;： `ProcName` }]|**/attach** 會開始為處理序識別碼或處理序名稱指定的處理序收集資料。 如果未指定特定進程， **/detach** 會停止指定進程或所有進程的資料收集。|

## <a name="end-the-profiling-session"></a>結束程式碼剖析工作階段
 若要結束分析工作階段，必須從 Web 應用程式 中斷連結分析工具。 您可以重新啟動 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序或呼叫 **VSPerfCmd /detach** 選項，停止從使用取樣方法分析的應用程式中收集資料。 接著呼叫 **VSPerfCmd** [/shutdown](../profiling/shutdown.md) 選項以停止分析工具，並關閉分析資料檔案。 **VSPerfClrEnv /globaloff** 命令會清除程式碼剖析環境變數，但在重新啟動電腦之前不會重設系統組態。

#### <a name="to-end-a-profiling-session"></a>結束程式碼剖析工作階段

1. 執行下列其中一個步驟，以從目標應用程式中斷連結程式碼剖析工具：

   - 鍵入 **VSPerfCmd** [/detach](../profiling/detach.md)

      -或-

   - 關閉 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序。 輸入：

     **IISReset /stop**

2. 關閉程式碼剖析工具。 輸入：

    **VSPerfCmd /shutdown**

3. (選擇性) 清除程式碼剖析環境變數。 輸入：

    **VSPerfCmd /globaloff**

4. 重新啟動電腦。 如有必要，請重新啟動 Internet Information Services (IIS)。 輸入：

    **IISReset /start**

## <a name="see-also"></a>另請參閱
- [分析 ASP.NET web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [.NET 記憶體資料檢視](../profiling/dotnet-memory-data-views.md)
