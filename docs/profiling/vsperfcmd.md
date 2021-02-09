---
title: VSPerfCmd | Microsoft Docs
description: 瞭解如何使用 VSPerfCmd.exe 工具來啟動和停止效能資料收集。 同時瞭解各種 >vsperfcmd 工具選項。
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- performance tools, VSPerfCmd tool
- command-line tools, VSPerfCmd tool
- command line, tools
- profiling tools,VSPerfCmd
- VSPerfCmd tool
ms.assetid: 778bc105-7643-46c4-a338-f3620e31125a
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a501a3f815d48630afe1a849e91c1fdb52c979fa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911446"
---
# <a name="vsperfcmd"></a>VSPerfCmd
*VSPerfCmd.exe* 工具的用途是啟動及停止效能資料收集。 其使用下列語法：

```cmd
VSPerfCmd [/U] [/options]
```

 下表說明 *VSPerfCmd.exe* 工具選項。

|選項|Description|
|------------|-----------------|
|**U**|以 Unicode 撰寫重新導向的主控台輸出。 務必優先指定此選項。|
|[開始](../profiling/start.md) **：**`mode`|以指定的模式啟動分析服務。|
|[輸出](../profiling/output.md) **：**`filename`|指定輸出檔名稱。 只能與 **Start** 搭配使用。|
|[CrossSession&#124;CS](../profiling/crosssession.md)|允許在 Windows 工作階段中進行分析。 只能與 **Start**、**Attach** 或 **Launch** 搭配使用。|
|[使用者](../profiling/user-vsperfcmd.md) **：**[ `domain\` ]`username`|允許指定的帳戶存取分析工具服務。 只能與 **Start** 搭配使用。|
|[WaitStart](../profiling/waitstart.md)[**：** `n` ]|等候資料收集記錄器初始化。 如有指定 `n`，**VSPerfCmd** 最多會等候 `n` 秒。 若未指定 `n`，**VSPerfCmd** 會無限期等候。 這減輕了 **VSPerfCmd** 在批次程序中的使用。|
|[計數器](../profiling/counter.md) **：**`cfg`|使用樣本分析方法時，會指定要用作取樣間隔的 CPU 計數器及事件數。 您可以只取樣一個計數器值。<br /><br /> 使用檢測分析方法時，會指定在每個檢測點要收集的 CPU 計數器。 只能搭配 **Start：** `Trace` 、 **Attach** 或 **啟動** 使用。|
|[QueryCounters](../profiling/querycounters.md)|顯示目前電腦的有效 CPU 計數器清單。|
|[WinCounter](../profiling/wincounter.md) **：** *path*|指定要加入設定檔標記資料的 Windows 效能計數器事件。 只能與 **Start** 搭配使用。|
|[AutoMark](../profiling/automark.md) **：** *n*|指定 Windows 效能計數器資料收集事件之間的時間間隔 (毫秒)。 搭配 **WinCounter** 使用。|
|[事件](../profiling/events-vsperfcmd.md) **：**`option`|控制指定的 Windows 事件追蹤 (ETW) 事件集合。 ETW 資料會收集到不是分析資料 (.*vsp*) 檔案的 .*itl* 檔案中。|
|[狀態](../profiling/status.md)|顯示分析工具的狀態、目前分析的處理序資訊以及有權控制分析工具的帳戶。|
|[Shutdown](../profiling/shutdown.md)[**：** `n` ]|關閉分析資料檔案並關閉分析工具。|
|[GlobalOn](../profiling/globalon-and-globaloff.md)|在對 **VSPerfCmdGlobalOff** 進行呼叫後恢復資料收集。|
|[GlobalOff](../profiling/globalon-and-globaloff.md)|停止所有資料收集，但不結束分析工作階段。|
|[ProcessOn](../profiling/processon-and-processoff.md) **：**`pid`|在對 **VSPerfCmdProcessOff** 的呼叫暫停分析後，恢復指定處理序的資料收集。|
|[ProcessOff](../profiling/processon-and-processoff.md) **：**`pid`|停止指定處理序的資料收集。|
|[>threadon 和 ThreadOff](../profiling/threadon-and-threadoff.md) **：** *tid*|在對 **VSPerfCmdThreadOff** 的呼叫暫停分析後，恢復指定處理序的分析。 請只在使用檢測方法進行分析時使用 **ThreadOn**。|
|[>threadon 和 ThreadOff](../profiling/threadon-and-threadoff.md) **：** *tid*|暫停指定執行緒的分析。 請只在使用檢測方法進行分析時使用 **ThreadOff**。|
|[Mark](../profiling/mark.md) **：** _MarkNum_[**，**_MarkText_**]**|在分析資料檔案中插入標記，以及選擇性文字。|

## <a name="sample-method-options"></a>取樣方法選項
 只有在使用取樣分析方法時，才能使用下列選項。

|選項|Description|
|------------|-----------------|
|[啟動](../profiling/launch.md) **：** *可執行檔*|啟動指定的應用程式並開始分析。|
|[Args](../profiling/args.md) **：** *引數*|指定要傳遞給啟動應用程式的命令列引數。|
|[主控台](../profiling/console.md)|在新的命令提示字元視窗啟動指定的命令。|
|[Attach](../profiling/attach.md) **：** *PID*[**，**_pid_]|開始分析指定的處理序。 處理序可依處理序識別碼或處理序名稱識別。|
|[Detach](../profiling/detach.md)[**:**_PID_[,_PID_]]|停止分析指定的處理序。 處理序可依處理序識別碼或處理序名稱識別。 如果未指定任何處理序，所有處理序的分析都會停止。|
|[GC](../profiling/gc-vsperfcmd.md)[**:**{**Allocation**`&#124;`**Lifetime**}]|收集 .NET 記憶體配置和物件存留期資料。 只能搭配 **VSPerfCmdLaunch** 選項使用。|

### <a name="sample-interval-options"></a>取樣間隔選項
 下列選項會指定取樣間隔的類型和持續時間。 預設為 **Timer**。 您也可以使用 **Counter** 選項，將 CPU 計數器指定為間隔。 這些選項只能搭配 **Launch** 或分析工作階段的第一個 **Attach** 指定。

|選項|Description|
|------------|-----------------|
|[PF](../profiling/pf.md)[**:**_n_]|在遇到每第 n 個分頁錯誤時取樣 (預設=10)。|
|[Sys](../profiling/sys-vsperfcmd.md)[**:**_n_]|在遇到每第 n 個系統呼叫時取樣 (預設=10)。|
|[Timer](../profiling/timer.md)[**:**_n_]|在遇到每第 n 個處理器週期時取樣 (預設=10000000)。|

## <a name="service-component-and-kernel-mode-device-options"></a>服務元件和核心模式裝置選項
 下列 Admin 選項支援分析服務元件或核心模式裝置驅動程式。 Admin 選項會設定分析權限及控制分析的服務或裝置驅動程式。

 Admin 選項必須在使用系統管理認證執行的命令提示字元執行。

|選項|Description|
|------------|-----------------|
|**Admin： Security**， \<**ALLOW&#124;DENY**> ， *right*[ *right*]， \<*User*&#124;*Group*>|允許或拒絕指定的使用者或群組存取分析服務。<br /><br /> `Right` 可以是：<br /><br /> CrossSession - 將服務存取權提供給使用者，以進行交叉工作階段分析。<br /><br /> SampleProfiling - 將驅動程式存取權提供給使用者，以進行取樣分析。 也可用來在追蹤分析期間存取核心轉換資訊。<br /><br /> FullAccess - 將 CrossSession 和 SampleProfiling 存取權都提供給使用者。|
|**Admin:Security, List**|列出分析服務的目前狀態，並列出使用者權限。|
|**管理員：**\<*Service*&#124;*Driver*>\<**START**&#124;**STOP**&#124;**INSTALL**&#124;**UNINSTALL**>|啟動、停止、安裝或解除安裝分析服務元件 (service) 或核心模式裝置驅動程式 (driver)。|
|**管理員：** \<*Service*&#124;*Driver*>**自動啟動**\<**ON**&#124;**OFF**>|啟用或停用在重新開機後自動啟動分析服務 (service) 或核心模式裝置驅動程式 (driver)。|

## <a name="vsperfcmd-driver"></a>VSPerfCmd /Driver
 **VSPerfCmd /Driver** 選項現已淘汰。 請針對這個功能用 **VsPerfCmd Admin** 選項。

## <a name="see-also"></a>另請參閱
- [VSInstr](../profiling/vsinstr.md)
- [VSPerfMon](../profiling/vsperfmon.md)
- [VSPerfReport](../profiling/vsperfreport.md)
