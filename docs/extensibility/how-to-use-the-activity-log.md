---
title: 如何:使用活動日誌 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64986be303370cf8c9048612ff3d44e82e96805a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710586"
---
# <a name="how-to-use-the-activity-log"></a>如何:使用活動紀錄
VS包可以將消息寫入活動日誌。 此功能對於在零售環境中調試 VSPackages 特別有用。

> [!TIP]
> 活動日誌始終處於打開狀態。 Visual Studio 保留最近 100 個條目的前 10 個條目的滾動緩衝區以及前 10 個條目,這些條目具有常規配置資訊。

## <a name="to-write-an-entry-to-the-activity-log"></a>將項目寫入活動紀錄

1. 在<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法或任何其他方法中插入此代碼,但 VSPackage 建構函數除外:

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     此代碼獲取<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>服務並將其轉換為<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>介面。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A>使用當前文化上下文將資訊條目寫入活動日誌。

2. 載入 VSPackage 時(通常在呼叫命令或打開視窗時),文本將寫入活動日誌。

## <a name="to-examine-the-activity-log"></a>檢查活動記錄

1. 使用[/Log](../ide/reference/log-devenv-exe.md)命令列開關運行 Visual Studio,在工作階段期間將 ActivityLog.xml 寫入磁碟。

2. 關閉 Visual Studio 後,在可視化工作室數據的子資料夾中尋找活動日誌:

   <em> *%AppData%</em>[微軟]VisualStudio\\\<版本>_活動日誌.xml*。

3. 使用任何文字編輯器開啟活動日誌。 下面是一個典型的條目:

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>穩固程式設計

由於活動日誌是服務,因此在 VSPackage 構造函數中,活動日誌不可用。

您應該在寫入活動日誌之前獲取活動日誌。 不要緩存或保存活動日誌以供將來使用。

## <a name="see-also"></a>另請參閱

- [/日誌 (devenv.exe)](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [針對 VSPackage 進行疑難排解](../extensibility/troubleshooting-vspackages.md)
- [VSPackage](../extensibility/internals/vspackages.md)
