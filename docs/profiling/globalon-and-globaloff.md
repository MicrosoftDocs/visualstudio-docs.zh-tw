---
title: GlobalOn 和 GlobalOff | Microsoft Docs
description: 請參閱 VSPerfCmd.exe 中的 GlobalOn 和 GlobalOff 選項。 這些選項會暫停和繼續分析命令列分析會話中的進程和執行緒。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b0ed68-d19e-473e-9af3-252c11d82bcf
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: eaeac096c6bdff77368508bd34276d66530fa739
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801338"
---
# <a name="globalon-and-globaloff"></a>GlobalOn 和 GlobalOff
*VSPerfCmd.exe* **GlobalOff** 和 **GlobalOn** 選項可暫停和繼續對命令列分析工作階段中的所有處理序和執行緒進行分析。

 您可以在 *VSPerfCmd.exe* 命令列中僅指定 **GlobalOn** 和 **GlobalOff** 選項，也可以將它們納入同時還包含 **Start**、**Launch** 或 **Attach** 選項的命令列中。

 **GlobalOn** 和 **GlobalOff** 也能夠結合 **ProcessOn**、**ProcessOff**、**ThreadOn** 及 **ThreadOff** 選項一起使用。

 **GlobalOn** 和 **GlobalOff** 選項能與控制指定處理序資料集合的 **ProcessOn** 和 **ProcessOff** 選項互動，以及與控制指定執行緒資料集合的 **ThreadOn** 和 **ThreadOff** 選項互動。

 **GlobalOff** 和 **GlobalOn** 選項也會影響由分析工具的 API 函式操作的全域開始/停止計數。

- **GlobalOff** 可立即將全域啟動/停止計數設定為 0，並因此會暫停分析。

- **GlobalOn** 可立即將全域啟動/停止計數設定為 1，並因此會繼續分析。

  如需詳細資訊，請參閱[分析工具 API](../profiling/profiling-tools-apis.md)。

## <a name="syntax"></a>語法

```cmd
VSPerfCmd.exe /{GlobalOff|GlobalOn}

VSPerfCmd.exe /Start:Method /{GlobalOff|GlobalOn} [Options]

VSPerfCmd.exe {Launch:AppName|Attach:PID} /{GlobalOff|GlobalOn}[Options]
```

#### <a name="parameters"></a>參數
 None

## <a name="valid-options"></a>有效選項
 您可以在也包含下列選項的命令列上指定 **GlobalOn** 和 **GlobalOff**。

 **開始：** `Method` 初始化命令列分析工具會話，並設定指定的分析方法。

 **啟動：** `AppName` 啟動指定的應用程式，並開始使用取樣方法進行程式碼剖析。

 **附加：** `PID` 開始分析指定的進程。

 {**ProcessOff**&#124;**ProcessOn**}**:**`PID` 停止或啟動指定進程的程式碼剖析。

 {**ThreadOff**&#124;**>threadon**}**:**`TID` 只)  (檢測方法，停止或啟動指定進程的程式碼剖析。

## <a name="example"></a>範例
 在此範例中，可使用 **GlobalOff** 和 **GlobalOn** 選項，避免收集應用程式啟動和關閉的分析資料。

```cmd
; Initialize the profiler with profiling stopped.
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp /GlobalOff
; Start an instrumented application and wait for it to warm up.
; Start profiling.
VSPerfCmd.exe /GlobalOn
; Exercise the application functionality that you want to profile.
; Stop profiling.
VSPerfCmd.exe /GlobalOff
; Shut down the target application.
; Close the profiler.
VSPerfCmd /Shutdown

```

## <a name="see-also"></a>另請參閱
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [分析 ASP.NET web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [分析服務](../profiling/command-line-profiling-of-services.md)
