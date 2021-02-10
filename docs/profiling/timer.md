---
title: Timer | Microsoft Docs
description: 瞭解 VSPerfCmd.exe 計時器選項如何設定取樣為處理器頻率週期的分析事件。
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3aeffc3be3fee5d3460ddea340d8c4a216829e08
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963155"
---
# <a name="timer"></a>計時器
*VSPerfCmd.exe* **Timer** 選項會將取樣的分析事件設定為處理器時脈週期，並且選擇性變更取樣間隔中預設為 10,000,000 的週期數目。 在 1GH (1 GHz) 處理器上，10,000,000 個時脈週期約為每秒 100 個樣本。 可指定的最小週期數目為 50,000。

 **Timer** 只能在您使用取樣分析方法時使用，並且只能在同時包含 **Launch** 或 **Attach** 選項的命令列中使用。

 預設會將分析工具取樣事件設定為處理器時脈週期，並將取樣間隔設定為 10,000,000。 **Timer**、**PF**、**Sys** 和 **Counter** 選項可讓您設定取樣事件和取樣間隔。 **GC** 選項會在每個配置和記憶體回收事件發生時，收集 .NET 記憶體資料。 您只能在命令列上指定上述其中一個選項。

 取樣事件和取樣間隔只能在包含 **Launch** 或 **Attach** 選項的第一個命令列中設定。

## <a name="syntax"></a>語法

```cmd
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /Timer[:Cycles] [Options]
```

#### <a name="parameters"></a>參數
 `Cycles` 指定取樣間隔中處理器時脈週期數目的整數值。 如果未指定 `Cycles`，間隔會設定為 10,000,000。 指定值時不包含逗號。

## <a name="required-options"></a>必要選項
 **Timer** 只能在包含下列其中一個選項的命令列上指定。

 **啟動：** `AppName` 啟動分析工具和指定的應用程式 `AppName` 。

 **附加：** `PID` 將分析工具附加至處理序識別碼 () 所指定的進程 `PID` 。

## <a name="invalid-options"></a>無效的選項
 下列選項無法在與 **Timer** 相同的命令列上指定。

 **PF**[**：** `Events` ] 將取樣事件設定為分頁錯誤，並且選擇性地將取樣間隔設定為 `Events` 。 預設的 PF 間隔為 10。

 **Sys**[**：** `Events` ] 將取樣事件設定為作業系統呼叫，並選擇性地將取樣間隔設定為 `Events` 。 預設的 Sys 間隔為 10。

 **Counter**[**：** `Name,Reload,FriendlyName` ] 將取樣事件設定為所指定的 CPU 效能計數器 `Name` ，並將取樣間隔設定為 `Reload` 。

 **GC**[**:**{**Allocation**&#124;**Lifetime**}] 收集 .NET 記憶體資料。 根據預設 (**配置**) ，資料會在每個記憶體配置事件收集。 指定 **Lifetime** 參數時，也會在每個垃圾收集事件上收集資料。

## <a name="example"></a>範例
 此範例示範如何將分析工具取樣間隔設定為 1,000,000 個處理器週期。

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000
```

## <a name="see-also"></a>另請參閱
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [分析 ASP.NET web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [分析服務](../profiling/command-line-profiling-of-services.md)
