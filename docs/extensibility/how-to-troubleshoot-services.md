---
title: "How to: 服務進行疑難排解 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "服務疑難排解"
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# How to: 服務進行疑難排解
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

有幾個常見的問題，當您嘗試將取得的服務時，可能會發生:  
  
-   服務未向 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
-   服務要求的介面型別，而不是由服務類型。  
  
-   無法決定位置 VSPackage 服務要求。  
  
-   使用錯誤的服務提供者。  
  
 如果所要求的服務無法取得，呼叫 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 會傳回 null。 您應該一律測試為 null 之後要求的服務:  
  
```c#  
IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog; if (log == null) return;  
```  
  
### 疑難排解服務問題  
  
1.  檢查系統登錄，以查看是否已正確註冊服務。 如需詳細資訊，請參閱[註冊服務](../misc/registering-services.md)。  
  
     下列.reg 檔案片段顯示如何可能登錄 SVsTextManager 服務:  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}] @="{F5E7E720-1401-11d1-883B-0000F87579D2}" "Name"="SVsTextManager"  
    ```  
  
     在上述範例中，版本號碼是版 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], 、 12.0 或 14.0，例如 {F5E7E71D\-1401\-11d1\-883B\-0000F87579D2} 的索引鍵是 SVsTextManager，服務的服務識別碼 \(SID\)，且預設值 {F5E7E720\-1401\-11d1\-883B\-0000F87579D2} 封裝文字管理員 VSPackage，提供服務的 GUID。  
  
2.  當您呼叫 GetService 時，請使用服務型別和介面類型。 要求的服務時 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ，<xref:Microsoft.VisualStudio.Shell.Package> 擷取類型的 GUID。 如果下列條件存在，將無法找到服務:  
  
    1.  介面型別給 GetService，而不是服務類型。  
  
    2.  GUID 不明確指派給介面。 因此，系統會建立物件所需的預設 GUID。  
  
3.  請確定已設置 VSPackage 服務要求。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 之後建構該項目，以及呼叫之前，站台 VSPackage <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>。  
  
     如果您需要服務 VSPackage 建構函式中的程式碼，請將它移至 Initialize 方法。  
  
4.  請務必使用正確的服務提供者。  
  
     並非所有的服務提供者是相同的。 服務提供者， [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 傳遞至工具視窗與傳遞到 VSPackage。 工具視窗服務提供者知道 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, ，但不知道 <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>。 您可以呼叫 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 取得工具視窗內的 VSPackage 服務提供者。  
  
     如果工具視窗裝載使用者控制項或任何其他控制項容器，容器會設置在 Windows 元件模型，將無法存取任何 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 服務。 您可以呼叫 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 取得 VSPackage 服務提供者從控制項容器中的。  
  
## 請參閱  
 [可用服務清單](../extensibility/internals/list-of-available-services.md)   
 [使用並提供服務](../extensibility/using-and-providing-services.md)   
 [服務的基本資訊](../extensibility/internals/service-essentials.md)