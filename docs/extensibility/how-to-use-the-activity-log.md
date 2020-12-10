---
title: 如何：使用活動記錄 |Microsoft Docs
description: Vspackage 可以將訊息寫入至活動記錄。 瞭解如何使用活動記錄檔，在零售環境中進行 Vspackage 的偵錯工具。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2796b8537c0f94c02c91fddc73f6d913ba1b0c4c
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993571"
---
# <a name="how-to-use-the-activity-log"></a>如何：使用活動記錄
Vspackage 可以將訊息寫入至活動記錄。 這項功能特別適用于在零售環境中進行 Vspackage 的偵錯工具。

> [!TIP]
> 活動記錄一律會開啟。 Visual Studio 保留最後100專案的滾動緩衝區，以及前10個專案（具有一般設定資訊）。

## <a name="to-write-an-entry-to-the-activity-log"></a>將專案寫入活動記錄檔

1. 在 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 方法或任何其他方法（VSPackage 的函式除外）中插入此程式碼：

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     此程式碼 <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> 會取得服務，並將其轉換為 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> 介面。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> 使用目前的文化特性內容，將資訊專案寫入活動記錄中。

2. 載入 VSPackage 時 (通常是在叫用命令或) 開啟視窗時，會將文字寫入至活動記錄。

## <a name="to-examine-the-activity-log"></a>檢查活動記錄

1. 使用 [/log](../ide/reference/log-devenv-exe.md) 命令列參數執行 Visual Studio，以在會話期間將 ActivityLog.xml 寫入磁片。

2. 關閉 Visual Studio 之後，請在子資料夾中尋找 Visual Studio 資料的活動記錄：

   <em> *% AppData%</em>\Microsoft\VisualStudio \\ \<version>\ActivityLog.xml*。

3. 使用任何文字編輯器開啟活動記錄。 以下是典型的專案：

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>穩固程式設計

因為活動記錄是一項服務，所以活動記錄在 VSPackage 的函式中無法使用。

在寫入活動記錄之前，您應該先取得活動記錄。 請勿快取或儲存活動記錄檔以供日後使用。

## <a name="see-also"></a>另請參閱

- [/Log ( # A0) ](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [針對 VSPackage 進行疑難排解](../extensibility/troubleshooting-vspackages.md)
- [VSPackages](../extensibility/internals/vspackages.md)
