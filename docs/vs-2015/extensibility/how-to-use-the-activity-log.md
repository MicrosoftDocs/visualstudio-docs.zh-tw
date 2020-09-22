---
title: 如何：使用活動記錄 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d450e02d23159f186fd85bf1b687a2fb2c18e82a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839145"
---
# <a name="how-to-use-the-activity-log"></a>如何︰使用活動記錄
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vspackage 可以將訊息寫入至活動記錄。 這項功能特別適用于在零售環境中進行 Vspackage 的偵錯工具。  
  
> [!TIP]
> 活動記錄一律會開啟。 Visual Studio 會保留最後100專案的滾動緩衝區以及具有一般設定資訊的前10個專案。  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>將專案寫入活動記錄檔  
  
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
  
### <a name="to-examine-the-activity-log"></a>檢查活動記錄  
  
1. 在子資料夾中尋找 Visual Studio 資料的活動記錄： *% AppData%* \Microsoft\VisualStudio\14.0\ActivityLog.XML。  
  
2. 使用任何文字編輯器開啟活動記錄。 以下是典型的專案：  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>穩固程式設計  
 因為活動記錄是一項服務，所以活動記錄在 VSPackage 的函式中無法使用。  
  
 在寫入活動記錄之前，您應該先取得活動記錄。 請勿快取或儲存活動記錄檔以供日後使用。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [針對 Vspackage 進行疑難排解](../extensibility/troubleshooting-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)
