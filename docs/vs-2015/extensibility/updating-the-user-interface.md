---
title: 更新消費者介面 |Microsoft Docs
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
ms.openlocfilehash: db5be965119d1564f2a4bf8a15892af7142663e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186350"
---
# <a name="updating-the-user-interface"></a>更新使用者介面
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在您執行命令之後，您可以新增程式碼，以使用新命令的狀態來更新使用者介面。  
  
 在一般的 Win32 應用程式中，可以持續輪詢命令集，並在使用者加以查看時調整個別命令的狀態。 不過，因為 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] shell 可以裝載不限數目的 vspackage，所以大量輪詢可能會降低回應性，特別是在 managed 程式碼與 COM 之間的交互操作元件之間進行輪詢。  
  
### <a name="to-update-the-ui"></a>更新 UI  
  
1. 請執行下列其中一個步驟：  
  
    - 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 方法。  
  
         您 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 可以從服務取得介面 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> ，如下所示。  
  
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
  
         如果的參數 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 為非零 (`TRUE`) ，則會同步且立即執行更新。 建議您 `FALSE` 為此參數傳遞零 () ，以協助維持良好的效能。 如果您想要避免快取，請在 `DontCache` 您于 .vsct 檔案中建立命令時套用旗標。 不過，請小心使用旗標，否則效能可能會降低。 如需命令旗標的詳細資訊，請參閱 [命令旗標元素](../extensibility/command-flag-element.md) 檔集。  
  
    - 在使用視窗中的就地啟動模型來裝載 ActiveX 控制項的 Vspackage 中，使用方法可能會比較方便 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> 。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>介面中的方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> 介面中的方法在 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> 功能上相同。 這兩者都會使環境重新查詢所有命令的狀態。 通常不會立即執行更新。 相反地，更新會延遲到閒置時間為止。 Shell 會快取命令狀態，以協助維持良好的效能。 如果您想要避免快取，請在 `DontCache` 您于 .vsct 檔案中建立命令時套用旗標。 不過，請小心使用旗標，因為效能可能會降低。  
  
         請注意，您可以 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> `QueryInterface` 在物件上呼叫方法， <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> 或從服務取得介面，以取得介面 <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> 。  
  
## <a name="see-also"></a>另請參閱  
 [Vspackage 如何新增消費者介面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [實作](../extensibility/internals/command-implementation.md)
