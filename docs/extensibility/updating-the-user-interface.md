---
title: "更新使用者介面 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "更新的使用者介面"
  - "更新 UI 的命令"
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
caps.latest.revision: 41
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 41
---
# 更新使用者介面
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

執行命令後，您可以加入程式碼以更新使用者介面與您的新命令的狀態。  
  
 典型的 Win32 應用程式中的命令集可用於連續輪詢，使用者可以檢視它們時，您可以調整個別命令的狀態。 不過，因為 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 殼層可以裝載無限的數量的 Vspackage，廣泛輪詢可能會降低回應性，特別輪詢多個 managed 程式碼與 COM interop 組件  
  
### 若要更新 UI  
  
1.  請執行下列其中一個步驟：  
  
    -   呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 方法。  
  
         <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 介面可以取自 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 服務，如下所示。  
  
        ```c#  
        void UpdateUI(Microsoft.VisualStudio.Shell.ServiceProvider sp)  
        {  
            IVsUIShell vsShell = (IVsUIShell)sp.GetService(typeof(IVsUIShell));  
            if (vsShell != null)  
            {  
                int hr = vsShell.UpdateCommandUI(0);  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);  
            }  
        }  
  
        ```  
  
         如果參數 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 為非零 \(`TRUE`\)，然後執行更新，以同步方式以及立即。 我們建議您傳遞零 \(`FALSE`\) 這個參數可協助您維護良好的效能。 如果您想要避免快取，套用 `DontCache` 旗標，當您建立.vsct 檔案中的命令。 不過，請小心使用此旗標，或可能會降低效能。 如需命令旗標的詳細資訊，請參閱 [命令旗標的項目](../extensibility/command-flag-element.md) 文件。  
  
    -   在使用就地啟動模型，在視窗中裝載 ActiveX 控制項的 Vspackage，可能會更方便使用 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> 方法。<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 方法中的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 介面和 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> 方法中的 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> 介面的功能相同。 兩者會造成重新查詢所有命令的狀態的環境。 一般而言，更新是不會立即執行。 相反地，更新會延遲到閒置時。 殼層會快取命令狀態可協助您維護良好的效能。 如果您想要避免快取，套用 `DontCache` 旗標，當您建立.vsct 檔案中的命令。 不過，在因為可能會降低效能，請小心使用此旗標。  
  
         請注意，您可以取得 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> 介面呼叫 `QueryInterface` 方法 <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> 物件，或藉由取得從介面 <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> 服務。  
  
## 請參閱  
 [VSPackages 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [實作](../extensibility/internals/command-implementation.md)