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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62810694"
---
# <a name="providing-a-custom-properties-window"></a>提供自訂屬性視窗
可提供您自己**屬性**視窗中指定的專案系統，而不是擴充**屬性**所提供的視窗[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]整合式的開發環境 (IDE)。 最常遇到的案例是當您自行實作設置在視窗框架的物件。  
  
 萬一您不會實作設置在視窗框架的物件，但仍然可以存取它的其他方式，有數種方式來存取<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>介面如下所示在此頁面上的最後一個程序。  
  
### <a name="to-provide-your-properties-window"></a>若要提供您的 [屬性] 視窗  
  
1. 定義 GUID，代表您**屬性**window 實作。  
  
2. 在您<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>實作中，使用<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>服務以 proffer 您**屬性**為 Visual Studio 環境的服務視窗。  
  
### <a name="to-call-your-properties-window"></a>若要呼叫您的 [屬性] 視窗  
  
1. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> 方法。  
  
2. `QueryService` 針對<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>從<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>傳入<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A>方法。  
  
3. 取得<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>從<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>服務。  
  
4. 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>第一個參數設定為`SEID_PropertyBrowserSID`(取自<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>列舉型別)，並使用第三個參數， `varValue`，代表字串格式的 GUID，代表您**屬性**視窗。 在第一個建立進行這個呼叫一次您**屬性**視窗文件視窗。 在呼叫之後這**屬性**視窗是視窗框架與相關聯。  
  
### <a name="to-obtain-the-window-frame-object-when-you-are-not-the-implementer"></a>您不是實作器時，取得視窗框架物件  
  
- 您可以`QueryService`for<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>服務<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>搭配參數`propid`設定為<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>。  
  
- 您可以藉由呼叫來取得作用中的文件視窗<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A>透過 SVsMonitorSelection 服務。 設定參數`elementid`要`SEID_WindowFrame`，摘錄自<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>列舉型別。  
  
## <a name="see-also"></a>另請參閱  
 [擴充屬性](../extensibility/internals/extending-properties.md)   
 [屬性視窗中的欄位和介面](../extensibility/internals/properties-window-fields-and-interfaces.md)