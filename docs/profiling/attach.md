---
title: Attach | Microsoft Docs
description: 使用 VSPerfCmd.exe 的附加選項，開始分析處理序識別碼 (PID) 所指定的執行中進程。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0098ec24047e6e16efd27c6aec26943671743bb4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901100"
---
# <a name="attach"></a>Attach
*VSPerfCmd.exe* **Attach** 選項會開始進行處理序識別碼 (PID) 所指定之執行中處理序的樣本分析。

 若要使用 **Attach** 選項，您必須在 Start 選項中指定 **Sample** 選項。

> [!NOTE]
> 如果指定 **Start** 選項和 **Crosssession** 選項，則任何 **VSPerfCmd /Attach** 或 **VSPerfCmd /Detach** 呼叫也必須指定 **Crosssession**。

## <a name="syntax"></a>語法

```cmd
VSPerfCmd.exe /Attach:ProcessID [Options]
```

#### <a name="parameters"></a>參數
 `ProcessID` 執行中處理序的處理序識別碼 (PID)。 執行中處理序的 PID 會列在 Windows 工作管理員的 [處理序] 索引標籤上。

## <a name="valid-options"></a>有效選項
 在單一命令列上，下列 **VSPerfCmd** 選項可以與 **Attach** 選項一起使用。

 **Crosssession** 在登入工作階段以外的工作階段中，啟用分析應用程式。 如果指定 **Start** 選項和 **Crosssession** 選項，則為必要項目。

 **開始：** `Method` 初始化命令列分析工具會話，並設定指定的分析方法。

 **TargetCLR** 指定要在分析工作階段中載入多個版本時分析的 .NET Framework Common Language Runtime (CLR) 版本。 預設會分析第一個載入的版本。

 **GlobalOn GlobalOff** 繼續 (**GlobalOn**) 或暫停 (**GlobalOff**) 分析，但未結束分析工作階段。

 **ProcessOn：** `PID`**ProcessOff：** `PID`繼續 (**ProcessOn**) 或暫停指定進程的 (**ProcessOff**) 程式碼剖析。

## <a name="interval-options"></a>間隔選項
 下列其中一個取樣間隔選項可以指定於 Attach 命令列上。 預設取樣間隔為 10,000,000 個處理器時脈週期。

 **Timer**[**：** `Cycles` ]**PF**[**：** `Events` ]**Sys**[<strong>：</strong>Events]**Counter**[**：** `Name` ， `Reload` ， `FriendlyName` ] 指定取樣間隔的數目和類型。

- **Timer** - 每 `Cycles` 個處理器時脈週期取樣一次。 如果未指定 `Cycles`，會使用 10,000,000 個週期。

- **PF** - 每 `Events` 個分頁錯誤取樣一次。 如果未指定 `Events`，則會使用 10 個分頁錯誤。

- **Sys** - 對作業系統每呼叫 `Events` 次取樣一次。 如果未指定 `Events`，則會使用 10 次系統呼叫。

- **Counter** - `Name` 所指定的 CPU 效能計數器每 `Reload` 個數目就取樣一次。 選擇性，`FriendlyName` 可以指定要作為分析工具報表中資料行標題的字串。

## <a name="example"></a>範例
 此範例示範如何附加至處理序識別碼為 12345 的執行中應用程式執行個體。

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Attach:12345
```

## <a name="see-also"></a>另請參閱
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [分析 ASP.NET web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [分析服務](../profiling/command-line-profiling-of-services.md)
