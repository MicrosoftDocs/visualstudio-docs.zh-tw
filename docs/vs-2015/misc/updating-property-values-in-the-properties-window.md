---
title: 更新屬性值，在 [屬性] 視窗 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Properties window, updating property values
- property values, updating in Properties window
ms.assetid: 9358e8c3-b9d2-4fd4-aaab-cf48d1526db4
caps.latest.revision: 9
manager: douge
ms.openlocfilehash: 0272ba348e29fb1a2a118a0ff4b0989a2aa1683f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489230"
---
# <a name="updating-property-values-in-the-properties-window"></a>更新屬性視窗中的屬性值
有兩種方法可以讓 [屬性]  視窗與屬性值變更同步。 第一個是呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>介面，可提供存取基本視窗化功能，包括存取和建立環境所提供的工具和文件視窗。 下列步驟說明這項同步處理程序。  
  
## <a name="updating-property-values-using-ivsuishell"></a>使用 IVsUIShell 更新屬性值  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>使用 IVsUIShell 介面更新屬性值  
  
1.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>(透過<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>服務) 時該 Vspackage、 專案或編輯器需要建立或列舉工具或文件視窗。  
  
2.  實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A>保持**屬性**視窗與專案的屬性變更同步 (或所瀏覽的任何其他所選物件**屬性**視窗) 而不需要實作<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>以及引發<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A>事件。  
  
3.  實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A>並<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A>來建立和停用，分別用戶端事件通知的階層而不需要階層實作<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>。  
  
## <a name="updating-property-values-using-iconnection"></a>使用 IConnection 更新屬性值  
 第二種讓 [屬性]  視窗與屬性值變更同步的方法是在可連接物件上實作 `IConnection` ，表示輸出介面是否存在。 如果您想要當地語系化屬性名稱，衍生您的物件，從<xref:System.ComponentModel.ICustomTypeDescriptor>。 <xref:System.ComponentModel.ICustomTypeDescriptor>實作可以修改它所傳回的屬性描述項，並變更屬性的名稱。 若要當地語系化的描述，請建立衍生自屬性<xref:System.ComponentModel.DescriptionAttribute>並覆寫描述屬性。  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>實作 IConnection 介面的考量  
  
1.  `IConnection` 提供列舉值子物件使用的存取權<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>介面。 它也提供對所有連接點子物件，存取每個實作<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>介面。  
  
2.  所有瀏覽物件負責實作<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink>事件。 [屬性]  視窗將建議透過 `IConnection`所設定的事件。  
  
3.  連接點可讓您控制多少個連線 （一或多個） 它可讓在實作<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>。 僅允許一個介面的連接點可以傳回<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>從<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>方法。  
  
4.  用戶端可以呼叫`IConnection`介面，以取得使用列舉值子物件的存取權<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>介面。 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>介面便可以呼叫來列舉每個輸出介面識別碼 (IID) 的連接點。  
  
5.  `IConnection` 也可以取得存取權連接點子物件使用呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>每個輸出 IID 的介面。 透過<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>介面，用戶端啟動或終止諮詢迴圈使用可連接物件與用戶端自己的同步處理。用戶端也可以呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>介面，以取得列舉值物件與<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections>介面，以列舉它所知道的連接。  
  
## <a name="see-also"></a>另請參閱  
 [宣告屬性視窗選取範圍追蹤](../misc/announcing-property-window-selection-tracking.md)   
 [擴充屬性](../extensibility/internals/extending-properties.md)