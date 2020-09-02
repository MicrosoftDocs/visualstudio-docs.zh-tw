---
title: 提供自訂屬性視窗 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- property browsers, providing
- Properties window, providing your own
ms.assetid: 408dcdef-8ef9-4644-97d2-f311cd35824f
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: a244463832ff5620efa74a2c7fd20d6d47d79e76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62810694"
---
# <a name="providing-a-custom-properties-window"></a>提供自訂屬性視窗
您可以為指定的專案系統提供自己的**屬性**視窗，而不是擴充**Properties** [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 整合式開發環境 (IDE) 所提供的 [屬性] 視窗。 最常見的情況是當您自行執行放置於視窗框架中的物件時。  
  
 如果您未執行視窗框架中的物件，但仍可透過其他方式存取該物件，則有數種方式可以存取 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 此介面，如本頁最後一個程式中所列。  
  
### <a name="to-provide-your-properties-window"></a>若要提供您的屬性視窗  
  
1. 定義表示 **屬性** 視窗執行的 GUID。  
  
2. 在您的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 執行中，使用服務將 [ <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> **屬性** ] 視窗 proffer 為 Visual Studio 環境的服務。  
  
### <a name="to-call-your-properties-window"></a>呼叫您的屬性視窗  
  
1. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> 方法。  
  
2. `QueryService` 若為， <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> 則會 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 傳遞至 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> 方法。  
  
3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>從 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> 服務取得。  
  
4. <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>第一個參數設定為 `SEID_PropertyBrowserSID` (取自 <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> 列舉) ，第三個參數的呼叫， `varValue` 代表代表您**屬性**視窗之 GUID 的字串形式。 只有在第一次建立 [ **屬性** ] 視窗文件視窗時，才進行此呼叫一次。 在呼叫之後，這個 [ **屬性** ] 視窗會與您的視窗框架相關聯。  
  
### <a name="to-obtain-the-window-frame-object-when-you-are-not-the-implementer"></a>當您不是實施者時，取得視窗框架物件  
  
- 您可以 `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> 從將 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 參數 `propid` 設定為的服務 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> 。  
  
- 您可以透過 SVsMonitorSelection 服務呼叫來取得活動文件視窗 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> 。 將參數設定 `elementid` 為 `SEID_WindowFrame` ，取自 <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> 列舉。  
  
## <a name="see-also"></a>另請參閱  
 [擴充屬性](../extensibility/internals/extending-properties.md)   
 [Properties Window Fields and Interfaces](../extensibility/internals/properties-window-fields-and-interfaces.md)