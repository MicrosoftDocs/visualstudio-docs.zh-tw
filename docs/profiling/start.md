---
title: Start | Microsoft Docs
description: 瞭解啟動選項是將分析工具初始化為指定之程式碼剖析方法的 VSPerfCmd.exe 選項。
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 98c1fa8a5d95b9819c6b988282fe9fcdb6259bd5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960054"
---
# <a name="start"></a>開始
**Start** 選項是一個 *VSPerfCmd.exe* 選項，可將分析工具初始化為指定的程式碼剖析方法。

## <a name="syntax"></a>語法

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>參數
 `Method` 必須是下列其中一個關鍵字：

- **TRACE** - 指定檢測方法。

- **SAMPLE** - 指定取樣方法。

- **COVERAGE** - 指定程式碼涵蓋範圍。

- **CONCURRENCY** - 指定資源爭用方法。

## <a name="required-options"></a>必要選項
 在命令列上指定 **Start** 時，務必要指定 **Output** 選項。

 **輸出：** `filename` 指定輸出檔名稱。

## <a name="exclusive-options"></a>專屬選項
 在命令列上，下列選項只能和 **Start** 選項一起使用。

 **CrossSession**&#124;**CS** 啟用跨處理序分析。 支援 **CrossSession** 和 **CS** 這兩個選項名稱。

 **使用者：**[ `domain\` ] `username` 可讓用戶端從指定的帳號存取監視器。

 **WinCounter:** `Path` [**Automark**:`n`] **WinCounter** 可指定 Windows 效能計數器，作為標記包含在分析資料檔案中。 **AutoMark** 以毫秒指定資料檔案之間的收集間隔。

## <a name="invalid-options"></a>無效的選項
 在命令列上，下列選項無法和 **Start** 選項一起使用。

 **Status** **Status** 適用於已分析的那些處理序。 其會列出處理序和執行緒，以及其目前的分析狀態 (開啟/關閉)。 例如，如果已停止處理序，**Status** 並不會在報表中指出這點。 **Status** 會顯示該處理序是否已進行程式碼剖析。

 **Shutdown**[**：** `Timeout` ] 關閉分析工具。

## <a name="example"></a>範例
 下列範例示範如何使用 *VSPerfCmd.exe* **Start** 選項來初始化分析工具。

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>另請參閱
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [分析獨立應用程式](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [分析 ASP.NET web 應用程式](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [分析服務](../profiling/command-line-profiling-of-services.md)
