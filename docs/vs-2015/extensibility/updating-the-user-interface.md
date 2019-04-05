---
title: 更新使用者介面 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
caps.latest.revision: 42
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9285e08a9ace015937f8be594153fb3c1d037d6b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58944420"
---
# <a name="updating-the-user-interface"></a>更新使用者介面
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

實作的命令之後，您可以新增程式碼以更新使用者介面與您的新命令的狀態。  
  
 在典型的 Win32 應用程式中，會持續輪詢命令集，使用者可以檢視它們時，您可以調整個別命令的狀態。 不過，因為[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]shell 可以託管無限的數量的 Vspackage，廣泛的輪詢，可能會降低回應能力，尤其在 managed 程式碼與 COM 之間的 interop 組件輪詢  
  
### <a name="to-update-the-ui"></a>若要更新 UI  
  
1.  請執行下列其中一個步驟：  
  
    -   呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 方法。  
  
         <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>介面可從此<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>服務，如下所示。  
  
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
  
         如果參數<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>為非零 (`TRUE`)，然後更新在同步且立即執行。 我們建議您傳遞零 (`FALSE`) 針對此參數，以協助維護良好的效能。 如果您想要避免快取，套用`DontCache`旗標，當您建立在.vsct 檔案中的命令。 不過，請小心使用此旗標，或可能會降低效能。 如需有關命令旗標的詳細資訊，請參閱[Command Flag 元素](../extensibility/command-flag-element.md)文件。  
  
    -   在裝載 ActiveX 控制項視窗中使用就地啟用模型的 Vspackage，可能更方便使用<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A>方法。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>方法中的<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>介面並<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A>方法中的<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>介面的功能相同。 同時會導致環境，以重新查詢所有命令的狀態。 一般而言，更新會不會立即執行。 相反地，更新會延遲到閒置的時間。 殼層會快取的命令狀態，以協助維護良好的效能。 如果您想要避免快取，套用`DontCache`旗標，當您建立在.vsct 檔案中的命令。 不過，在因為可能會降低效能，請小心使用此旗標。  
  
         請注意，您可以取得<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>介面，藉由呼叫`QueryInterface`方法<xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager>物件，或藉由取得從介面<xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager>服務。  
  
## <a name="see-also"></a>另請參閱  
 [Vspackage 如何新增使用者介面項目](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [實作](../extensibility/internals/command-implementation.md)
