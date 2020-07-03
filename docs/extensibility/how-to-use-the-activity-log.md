---
title: 如何：使用活動記錄 |Microsoft Docs
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
ms.openlocfilehash: 824feee64f928dc837a379aeb539daaa5ba0d1db
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905577"
---
# <a name="how-to-use-the-activity-log"></a>如何：使用活動記錄
Vspackage 可以將訊息寫入至活動記錄。 這項功能特別適用于在零售環境中進行 Vspackage 的偵錯工具。

> [!TIP]
> 活動記錄一律會開啟。 Visual Studio 會保留最後100專案的輪流緩衝區，以及具有一般設定資訊的前10個專案。

## <a name="to-write-an-entry-to-the-activity-log"></a>若要將專案寫入活動記錄

1. 在 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 方法或任何其他方法（VSPackage 的函式除外）中插入此程式碼：

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     這段程式碼 <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> 會取得服務，並將它轉換成 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> 介面。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A>使用目前的文化內容，將資訊專案寫入活動記錄中。

2. 載入 VSPackage 時（通常是在叫用命令或開啟視窗時），會將文字寫入至活動記錄檔。

## <a name="to-examine-the-activity-log"></a>檢查活動記錄

1. 使用[/log](../ide/reference/log-devenv-exe.md)命令列參數執行 Visual Studio，以在會話期間將 ActivityLog.xml 寫入磁片。

2. 關閉 Visual Studio 之後，請在子資料夾中尋找 Visual Studio 資料的活動記錄檔：

   <em> *% AppData%</em>\Microsoft\VisualStudio \\ \<version>\ActivityLog.xml*。

3. 使用任何文字編輯器開啟活動記錄檔。 以下是典型的專案：

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>穩固程式設計

由於活動記錄是一項服務，因此無法在 VSPackage 的函式中使用活動記錄。

在寫入活動記錄之前，您應該先取得它。 不要快取或儲存活動記錄以供未來使用。

## <a name="see-also"></a>另請參閱

- [/Log （devenv.exe）](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [針對 VSPackage 進行疑難排解](../extensibility/troubleshooting-vspackages.md)
- [VSPackage](../extensibility/internals/vspackages.md)
