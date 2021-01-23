---
title: ProcessOn 和 ProcessOff | Microsoft Docs
description: 瞭解 VSPerfCmd.exe ProcessOff 和 ProcessOn 子命令如何在命令列分析會話中，針對指定的進程暫停和繼續程式碼剖析。
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ae4b5e95636894ddc2d0c4799308afb057145747
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719444"
---
# <a name="processon-and-processoff"></a>ProcessOn 和 ProcessOff
VSPerfCmd.exe 的 **ProcessOff** 和 **ProcessOn** 子命令會暫停和繼續分析命令列分析工作階段中指定的處理序。 **ProcessOff** 會停止分析處理序，**ProcessOn** 則開始分析處理序。

 在大部分的情況下，您可以將 **ProcessOn** 或 **ProcessOff** 指定為 VSPerfCmd.exe 命令列的唯一選項，但它們也可以和 **GlobalOn**、**GlobalOff**、**ThreadOn** 及 **ThreadOff** 子命令合併使用。

 **ProcessOn** 和 **ProcessOff** 子命令可與 **GlobalOn** 和 **GlobalOff** 子命令互動，控制命令列分析工作階段中所有處理序的資料收集，與 **ThreadOn** 和 **ThreadOff** 子命令互動，控制指定執行緒的資料收集。

 **ProcessOff** 和 **ProcessOn** 子命令也會影響分析工具 API 函式操控的處理序開始/停止計數。

- **ProcessOff** 可立即將處理序開始/停止計數設定為 0，並因此會暫停分析。

- **ProcessOn** 可立即將處理序開始/停止計數設定為 1，並因此會繼續分析。

  如需詳細資訊，請參閱 [分析工具 api](../profiling/profiling-tools-apis.md)。

## <a name="syntax"></a>語法

```cmd
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]

```

#### <a name="parameters"></a>參數
 `PID` 開始或停止處理序的整數識別碼。 處理序識別碼會列在 Windows 工作管理員的 [ **流程** ] 索引標籤上。

## <a name="required-subcommands"></a>必要的子命令
 無

## <a name="valid-subcommands"></a>有效的子命令
 您可以在也包含下列子命令的命令列上指定 **ProcessOn** 和 **ProcessOff**。

 **開始：** `Method` 初始化命令列分析會話，並設定指定的分析方法。

 **啟動：** `AppName` 啟動指定的應用程式，並開始使用取樣方法進行程式碼剖析。

 **附加：** `PID` 開始分析指定的進程。

 **GlobalOff**&#124;**GlobalOn** 在命令列分析工作階段中，停止或開始分析所有處理序。

 {**ThreadOff**&#124;**>threadon**}**:**`TID` 只) ，停止或啟動指定之執行緒 (檢測方法的程式碼剖析。

## <a name="example"></a>範例
 在此範例中，**ProcessOff** 子命令是用來收集應用程式啟動的分析資料。

```cmd
; Initialize the profiler.
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp
; Start the instrumented application.
; Stop profiling the process after startup.
VSPerfCmd.exe /ProcessOff:12345
; Shut down the target application.
; Close the profiler.
VSPerfCmd /Shutdown

```

## <a name="see-also"></a>另請參閱
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [分析 ASP.NET web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [分析服務](../profiling/command-line-profiling-of-services.md)
