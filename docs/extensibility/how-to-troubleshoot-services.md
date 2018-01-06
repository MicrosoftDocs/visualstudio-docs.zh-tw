---
title: "如何： 疑難排解服務 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 71ac3cda8e3df935ab743fed7aa94a5152c152a5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-troubleshoot-services"></a>如何： 疑難排解服務問題
有幾個常見的問題，當您嘗試取得服務可能會發生：  
  
-   服務未向[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
-   服務要求的介面型別，而不是由服務類型。  
  
-   服務要求 VSPackage 未已設置。  
  
-   使用錯誤的服務提供者。  
  
 如果所要求的服務無法取得，呼叫<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>會傳回 null。 要求服務之後，您應該一律測試 null 值：  
  
```csharp  
IVsActivityLog log =   
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
### <a name="to-troubleshoot-a-service"></a>若要疑難排解服務  
  
1.  檢查系統登錄，以查看是否已正確註冊服務。 如需詳細資訊，請參閱[How to： 提供服務](../extensibility/how-to-provide-a-service.md)。  
  
     下列.reg 檔案片段顯示可能會如何登錄 SVsTextManager 服務：  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
    @="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
    "Name"="SVsTextManager"  
    ```  
  
     在上述範例中，版本號碼是版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，例如 12.0 或 14.0，機碼 {F5E7E71D-1401-11d1-883B-0000F87579D2} 是 SVsTextManager 服務預設值 {的服務識別元 (SID)F5E7E720-1401-11d1-883B-0000F87579D2} 是封裝之文字管理員 VSPackage，提供服務的 GUID。  
  
2.  使用的服務類型，而不是介面類型，當您呼叫 GetService。 要求的服務時[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，<xref:Microsoft.VisualStudio.Shell.Package>擷取類型的 GUID。 如果存在下列條件，則不會找到服務：  
  
    1.  介面型別會傳遞給 GetService，而不是服務類型。  
  
    2.  GUID 不明確指派給介面。 因此，系統會建立物件所需的預設 GUID。  
  
3.  請確定已設置 VSPackage 服務要求。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]之後它建構，以及呼叫之前，站台 VSPackage <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>。  
  
     如果您需要服務 VSPackage 建構函式中的程式碼，請將它移至初始化方法。  
  
4.  請務必使用正確的服務提供者。  
  
     並非所有的服務提供者是相同的。 服務提供者，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]傳遞至工具視窗不同就會傳遞至 VSPackage。 工具視窗服務提供者知道<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>，但不知道<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>。 您可以呼叫<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>取得 VSPackage 的服務提供者，從工具視窗中。  
  
     如果工具視窗裝載使用者控制項或任何其他控制項容器，容器會設置在 Windows 元件模型，而且沒有任何存取權[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]服務。 您可以呼叫<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>取得 VSPackage 服務提供者從控制項容器中的。  
  
## <a name="see-also"></a>請參閱  
 [可用服務清單](../extensibility/internals/list-of-available-services.md)   
 [使用並提供服務](../extensibility/using-and-providing-services.md)   
 [服務的基本資訊](../extensibility/internals/service-essentials.md)