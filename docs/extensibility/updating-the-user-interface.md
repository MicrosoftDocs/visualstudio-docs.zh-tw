---
title: 正在更新使用者介面 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6b3bc8c4b87aefe62cbd27e64fc426ddb7abf96e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139152"
---
# <a name="updating-the-user-interface"></a>更新使用者介面
實作命令之後，您可以加入程式碼以更新使用者介面與您的新命令的狀態。  
  
 在典型的 Win32 應用程式中，會持續輪詢命令集，可以調整個別命令的狀態，使用者可以檢視它們。 不過，因為[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]殼層可以裝載無限的數量的 Vspackage，廣泛輪詢可能會降低回應性，特別輪詢多個 managed 程式碼與 COM 之間的 interop 組件  
  
### <a name="to-update-the-ui"></a>更新 UI  
  
1.  請執行下列其中一個步驟：  
  
    -   呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 方法。  
  
         <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>介面可以取自<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>服務，如下所示。  
  
        ```csharp  
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
  
         如果參數<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>為非零 (`TRUE`)，然後執行以同步和立即更新。 我們建議您將傳遞為零 (`FALSE`) 為此參數可協助您維護良好的效能。 如果您想要避免快取，套用`DontCache`旗標，當您建立.vsct 檔中的命令。 不過，請小心使用此旗標，或可能會降低效能。 如需命令旗標的詳細資訊，請參閱[命令旗標的項目](../extensibility/command-flag-element.md)文件。  
  
    -   在 Vspackage 中裝載在視窗中使用就地啟用模型的 ActiveX 控制項，可能會更方便使用<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A>方法。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>方法中的<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>介面和<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A>方法中的<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>介面都是相同的功能。 同時會造成重新查詢所有命令的狀態的環境。 一般而言，更新不立即執行。 相反地，更新會延遲到閒置時間。 殼層會快取命令狀態，可協助您維護良好的效能。 如果您想要避免快取，套用`DontCache`旗標，當您建立.vsct 檔中的命令。 不過，在因為可能會降低效能，請小心使用旗標。  
  
         請注意，您可以取得<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>介面，藉由呼叫`QueryInterface`方法<xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager>物件，或藉由取得從介面<xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager>服務。  
  
## <a name="see-also"></a>另請參閱  
 [Vspackage 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [實作](../extensibility/internals/command-implementation.md)