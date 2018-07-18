---
title: 如何： 使用活動記錄檔 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6200c5e71054c6132d9239769d354bfd32703fb0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127094"
---
# <a name="how-to-use-the-activity-log"></a>如何： 使用活動記錄檔
Vspackage 可以將訊息寫入活動記錄檔。 這項功能是在零售環境中偵錯 Vspackage 特別有用。  
  
> [!TIP]
>  永遠開啟活動記錄檔。 Visual Studio 就會輪流緩衝區的最近 100 個項目，以及具有一般的設定資訊的前 10 個項目。  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>若要將項目寫入活動記錄檔  
  
1.  插入這個程式碼的<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法或任何其他方法的 VSPackage 建構函式除外：  
  
    ```csharp  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     這個程式碼取得<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>服務，並將它轉換成<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>介面。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> 寫入資訊到使用目前文化特性內容的活動記錄檔項目。  
  
2.  載入 VSPackage 時 （通常時叫用命令，或在開啟的視窗），將文字寫入活動記錄檔。  
  
### <a name="to-examine-the-activity-log"></a>若要檢查活動記錄檔  
  
1.  執行使用 Visual Studio [/記錄檔](../ide/reference/log-devenv-exe.md)ActivityLog.xml 寫入磁碟，在您的工作階段期間的命令列參數。

2.  在關閉之後 Visual Studio，尋找活動記錄檔中的子資料夾 Visual Studio 資料： *%appdata%* \Microsoft\VisualStudio\15.0\ActivityLog.xml。  
  
3.  使用任何文字編輯器中開啟活動記錄檔。 以下是典型的項目：  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>穩固程式設計  
 因為活動記錄檔的服務，此活動記錄是 VSPackage 建構函式中無法使用。  
  
 您應該取得活動記錄檔之前寫入。 不要快取或儲存供日後使用的活動記錄檔。  
  
## <a name="see-also"></a>另請參閱
 [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [疑難排解 Vspackage](../extensibility/troubleshooting-vspackages.md)   
 [VSPackage](../extensibility/internals/vspackages.md)
