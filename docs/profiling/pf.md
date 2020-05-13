---
title: PF | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 07ec6d636ec087386fdc9462ae09db55400957a9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778410"
---
# <a name="pf"></a>PF
*VSPerfCmd.exe 的 * **PF** 選項會將取樣的分析事件設定為分頁錯誤，並且選擇性地變更取樣間隔的分頁錯誤數目，預設值為 10。

> [!NOTE]
> **PF** 不能在 64 位元系統上使用。

**PF** 只能用於也包含 [啟動]**** 或 [連結]**** 選項的命令列。

 預設會將取樣事件設定為未暫止處理器時脈週期，並將取樣間隔設定為 10,000,000。 [計時器]****、[PF]****、[Sys]**** 和 [計數器]**** 選項可讓您設定取樣事件和取樣間隔。 **GC** 選項會在每個配置和記憶體回收事件發生時，收集 .NET 記憶體資料。 您只能在命令列上指定上述其中一個選項。

 取樣事件和取樣間隔只能在包含 [啟動]**** 或 [附加]**** 選項的第一個命令列中設定。

## <a name="syntax"></a>語法

```cmd
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]
```

#### <a name="parameters"></a>參數
 `Events` 指定取樣間隔中分頁錯誤事件數目的整數值。 如果未指定 `Events`，間隔會設定為 10。

## <a name="required-options"></a>必要選項
 **PF** 只能在包含下列其中一個選項的命令列上指定。

 **啟動：**`AppName`啟動探測器和 AppName 指定的應用程式。

 **附加：**`PID`將探測器附加到 AppName 指定的進程。

## <a name="invalid-options"></a>無效的選項
 下列選項無法在與 **PF** 相同的命令列上指定。

 **計時器**[**：**`Cycles`] 將採樣事件設置為處理器時鐘週期，並選擇性地將`Cycles`取樣間隔設置為 。 預設 Timer 間隔為 10,000,000。

 **Sys**=**：**`Events`* 將採樣事件設置為從設定檔的應用程式到作業系統內核 （syscalls） 的調用，並可以選擇將取樣間隔`Events`設置為 。 預設的 Sys 間隔為 10。

 **計數器：** `Name` `,Reload`[`,FriendlyName`] 將採樣事件設置為 指定的`Name`CPU 效能計數器，並將取樣間隔設置為`Reload`。

 **GC**[**:**{**Allocation**&#124;**Lifetime**}] 收集 .NET 記憶體資料。 預設情況下（**分配**），資料在每個記憶體分配事件時收集。 指定**存留期**參數時，還會在每個垃圾回收事件中收集資料。

## <a name="example"></a>範例
 此範例示範如何將分析取樣事件設定為分頁錯誤，並將取樣間隔設定為 20 個分頁錯誤。

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /PF:20
```

## <a name="see-also"></a>另請參閱
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [設定檔ASP.NET Web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [分析服務](../profiling/command-line-profiling-of-services.md)
