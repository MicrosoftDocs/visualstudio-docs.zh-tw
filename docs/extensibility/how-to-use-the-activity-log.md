---
title: "如何： 使用活動記錄檔 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: a1ddf51d02d9e20f6806f8bc202f8a08166876d6
ms.contentlocale: zh-tw
ms.lasthandoff: 09/26/2017

---
# <a name="how-to-use-the-activity-log"></a>如何： 使用活動記錄檔
Vspackage 可以將訊息寫入活動記錄檔。 這項功能是在零售環境中偵錯 Vspackage 特別有用。  
  
> [!TIP]
>  永遠開啟活動記錄檔。 Visual Studio 就會輪流緩衝區的上次一百個項目，以及具有一般的設定資訊的前十個項目。  
  
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
  
     這個程式碼取得<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>服務，並將它轉換成<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>介面。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A>寫入資訊到使用目前文化特性內容的活動記錄檔項目。  
  
2.  載入 VSPackage 時 （通常時叫用命令，或在開啟的視窗），將文字寫入活動記錄檔。  
  
### <a name="to-examine-the-activity-log"></a>若要檢查活動記錄檔  
  
1.  尋找 Visual Studio 資料的子資料夾中的活動記錄： *%appdata%*\Microsoft\VisualStudio\15.0\ActivityLog.XML...  
  
2.  使用任何文字編輯器中開啟活動記錄檔。 以下是典型的項目：  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>穩固程式設計  
 因為活動記錄檔的服務，此活動記錄是 VSPackage 建構函式中無法使用。  
  
 您應該取得活動記錄檔之前寫入。 不要快取或儲存供日後使用的活動記錄檔。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [疑難排解 Vspackage](../extensibility/troubleshooting-vspackages.md)   
 [VSPackage](../extensibility/internals/vspackages.md)

