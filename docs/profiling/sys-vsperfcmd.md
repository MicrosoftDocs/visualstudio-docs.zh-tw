---
title: Sys (VSPerfCmd) | Microsoft Docs
description: 瞭解 VSPerfCmd.exe Sys 選項如何設定取樣至系統呼叫事件的分析事件。
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 66815265544afdee263490ed5eec92301911e3cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868162"
---
# <a name="sys-vsperfcmd"></a>Sys (VSPerfCmd)
*VSPerfCmd.exe* **Sys** 選項會設定對系統呼叫事件取樣的分析事件 (從已分析應用程式到作業系統的函式呼叫)，並選擇性變更取樣間隔中的系統呼叫數目 (預設值為 10)。

 **Sys** 只能用於也包含 **Launch** 或 **Attach** 選項的命令列。

 預設會將分析工具取樣事件設定為處理器時脈週期，並將取樣間隔設定為 10,000,000。 **Timer**、**PF**、**Sys** 和 **Counter** 選項可讓您設定取樣事件和取樣間隔。 **GC** 選項會在每個配置和記憶體回收事件發生時，收集 .NET 記憶體資料。 您只能在命令列上指定上述其中一個選項。

 取樣事件和取樣間隔只能在包含 **Launch** 或 **Attach** 選項的第一個命令列中設定。

## <a name="syntax"></a>語法

```cmd
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]
```

#### <a name="parameters"></a>參數
 `Events` 指定取樣間隔中系統呼叫事件數目的整數值。 如果未指定 `Events`，間隔會設定為 10。

## <a name="required-options"></a>必要選項
 **Sys** 需要下列其中一個選項。

 **啟動：** `AppName` 啟動分析工具和指定的應用程式 `AppName` 。

 **附加：** `PID` 將分析工具附加至所指定的進程 `PID` 。

## <a name="invalid-options"></a>無效的選項
 下列選項無法在與 **Sys** 相同的命令列上指定。

 **PF**[**：** `Events` ] 將取樣事件設定為分頁錯誤，並且選擇性地將取樣間隔設定為 `Events` 。 預設的 PF 間隔為 10。

 **Timer**[**：** `Cycles` ] 將取樣事件設定為處理器頻率週期，並選擇性地將取樣間隔設定為 `Cycles` 。 預設 Timer 間隔為 10,000,000。

 **計數器：** `Name`[ `,Reload` [ `,FriendlyName` ]] 將取樣事件設定為所指定的 CPU 效能計數器 `Name` ，並將取樣間隔設定為 `Reload` 。

 **GC**[**:**{**Allocation**&#124;**Lifetime**}] 收集 .NET 記憶體資料。 根據預設 (**配置**) ，資料會在每個記憶體配置事件收集。 指定 **Lifetime** 參數時，也會在每個垃圾收集事件上收集資料。

## <a name="example"></a>範例
 此範例示範如何將分析工具取樣事件設定為系統呼叫，以及如何將取樣間隔設定為每個樣本 20 次呼叫。

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20
```

## <a name="see-also"></a>另請參閱
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [分析 ASP.NET web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [分析服務](../profiling/command-line-profiling-of-services.md)
