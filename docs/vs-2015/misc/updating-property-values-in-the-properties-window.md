---
title: 更新屬性值，在 [屬性] 視窗 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 8db48e1f746afa8f8f219935555815587ce5823c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49290481"
---
# <a name="updating-property-values-in-the-properties-window"></a>更新屬性視窗中的屬性值
有兩種方法可以讓 [屬性]  視窗與屬性值變更同步。 第一種方法是呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 介面，此介面可存取基本視窗化功能 (包括存取和建立環境所提供的工具和文件視窗)。 下列步驟說明這項同步處理程序。  
  
## <a name="updating-property-values-using-ivsuishell"></a>使用 IVsUIShell 更新屬性值  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>使用 IVsUIShell 介面更新屬性值  
  
1.  隨時呼叫 VSPackage、專案或編輯器建立或列舉工具或文件視窗時所需的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (透過 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 服務)。  
  
2.  實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A>保持**屬性**視窗與專案的屬性變更同步 (或所瀏覽的任何其他所選物件**屬性**視窗) 而不需要實作<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>以及引發<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A>事件。  
  
3.  實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A>，分別建立和停用用戶端階層事件通知，而不需要階層實作 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>。  
  
## <a name="updating-property-values-using-iconnection"></a>使用 IConnection 更新屬性值  
 第二種讓 [屬性]  視窗與屬性值變更同步的方法是在可連接物件上實作 `IConnection` ，表示輸出介面是否存在。 如果您想要當地語系化屬性名稱，請從 <xref:System.ComponentModel.ICustomTypeDescriptor> 衍生您的物件。 <xref:System.ComponentModel.ICustomTypeDescriptor> 實作可以修改它所傳回的屬性描述元，以及變更屬性的名稱。 若要當地語系化描述，請建立衍生自 <xref:System.ComponentModel.DescriptionAttribute> 的屬性，並覆寫 [描述] 屬性。  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>實作 IConnection 介面的考量  
  
1.  `IConnection` 可使用 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> 介面來存取列舉值子物件。 它也可存取所有連接點子物件，而所有連接點子物件都實作 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 介面。  
  
2.  所有瀏覽物件都負責實作 <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> 事件。 [屬性]  視窗將建議透過 `IConnection`所設定的事件。  
  
3.  連接點可控制其 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> 實作中所允許的連線數目 (一個或多個)。 僅允許一個介面的連接點可以從 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> 方法傳回 <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>。  
  
4.  用戶端可以呼叫 `IConnection` 介面，以使用 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> 介面來存取列舉值子物件。 之後可以呼叫 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> 介面來列舉每個輸出介面識別碼 (IID) 的連接點。  
  
5.  也可以呼叫 `IConnection`，以使用 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 介面來存取每個輸出 IID 的連接點子物件。 透過 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 介面，用戶端可使用可連接物件和用戶端自己的同步處理來啟動或終止諮詢迴圈。用戶端也可以呼叫 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 介面以使用 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> 介面來取得列舉值物件，以列舉它所知道的連線。  
  
## <a name="see-also"></a>另請參閱  
 [宣告屬性視窗選取範圍追蹤](../misc/announcing-property-window-selection-tracking.md)   
 [擴充屬性](../extensibility/internals/extending-properties.md)