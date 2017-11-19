---
title: "屬性視窗中的欄位和介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a4dd37d33230be758bd5a5adf6f5e10d5a978800
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="properties-window-fields-and-interfaces"></a>Properties Window Fields and Interfaces
若要判斷哪些資訊會顯示在選取的模型**屬性**視窗根據在 IDE 中具有焦點的視窗。 每個視窗中，並在選取的視窗中，物件可以有推送至全域範圍內容的選取項目內容物件。 該視窗具有焦點時，環境會更新全域範圍內容視窗框架中的值。 當焦點變更時，也會選取範圍內容。  
  
## <a name="tracking-selection-in-the-ide"></a>追蹤在 IDE 中的選取範圍  
 站台，在 IDE 中所擁有的視窗框架有服務呼叫<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>。 下列步驟顯示如何變更中選取項目，使用者將焦點變更為另一個開啟的視窗，或選取不同的專案項目中所造成**方案總管 中**，實作變更中顯示的內容**屬性**視窗。  
  
1.  VSPackage 設置在選取的視窗呼叫所建立的物件<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>有<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>叫用<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>。  
  
2.  選取容器，提供所選取的視窗中，建立它自己<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>物件。 當選取範圍變更，VSPackage 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>通知在環境中，任何接聽程式包括**屬性**變更視窗。 它也提供新的選取範圍相關的階層和項目資訊的存取權。  
  
3.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>並將其傳遞中選取的階層項目`VSHPROPID_BrowseObject`參數填入<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>物件。  
  
4.  物件衍生自[IDispatch 介面](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)就會傳回<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>要求項目，以及環境會包裝到<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>（請參閱下一個步驟）。 如果呼叫失敗，環境會第二個呼叫`IVsHierarchy::GetProperty`，並選取容器<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>階層項目或項目提供。  
  
     您的專案不會建立 VSPackage<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>因為環境提供視窗 VSPackage，實作該 (比方說，**方案總管 中**) 建構<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>代替它。  
  
5.  環境會叫用的方法<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>取得根據物件`IDispatch`介面，以填入**屬性**視窗。  
  
 中的值時**屬性**視窗已變更，而 Vspackage 實作`IVsTrackSelectionEx::OnElementValueChangeEx`和`IVsTrackSelectionEx::OnSelectionChangeEx`來報告變更的項目值。 環境再叫用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>或<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>保留中顯示的資訊**屬性**視窗同步處理的屬性值。 如需詳細資訊，請參閱[屬性 視窗中更新屬性值](#updating-property-values-in-the-properties-window)。  
  
 除了選取不同的專案項目中**方案總管 中**若要顯示的項目與相關的屬性，您也可以選擇使用下拉式清單上可用的表單或文件視窗中的不同物件**屬性**視窗。 如需詳細資訊，請參閱[屬性視窗物件清單](../../extensibility/internals/properties-window-object-list.md)。  
  
 您可以變更中顯示資訊的方式**屬性**中依字母順序排列的視窗方格，成類別目錄，而且，如果有的話，則您也可以上的適當按鈕，即可開啟所選物件的屬性頁**屬性**視窗。 如需詳細資訊，請參閱[屬性視窗按鈕](../../extensibility/internals/properties-window-buttons.md)和[屬性頁](../../extensibility/internals/property-pages.md)。  
  
 最後，底部**屬性**視窗也會包含在選取的欄位描述**屬性**視窗方格。 如需詳細資訊，請參閱[從 [屬性] 視窗取得欄位描述](#getting-field-descriptions-from-the-properties-window)。  
  
## <a name="updating-property-values-in-the-properties-window"></a>在 [屬性] 視窗中更新屬性值
有兩種方法可以讓 [屬性]  視窗與屬性值變更同步。 第一個方法是呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>介面，可提供基本視窗化功能，包括存取和建立的工具和文件的 windows 環境所提供的存取。 下列步驟說明這項同步處理程序。  
  
### <a name="updating-property-values-using-ivsuishell"></a>使用 IVsUIShell 更新屬性值  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>使用 IVsUIShell 介面更新屬性值  
  
1.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>(透過<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>服務) 任何一次該 Vspackage、 專案或編輯器需要建立或列舉工具或文件視窗。  
  
2.  實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A>保留**屬性**視窗與專案的屬性變更同步 (或任何其他選取的物件所瀏覽的**屬性**視窗) 而不需要實作<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>和引發<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A>事件。  
  
3.  實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A>建立，並停用，分別用戶端通知的階層架構事件，而不需要階層實作<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>。  
  
### <a name="updating-property-values-using-iconnection"></a>使用 IConnection 更新屬性值  
 第二種讓 [屬性]  視窗與屬性值變更同步的方法是在可連接物件上實作 `IConnection` ，表示輸出介面是否存在。 如果您想要當地語系化屬性名稱，衍生您的物件從<xref:System.ComponentModel.ICustomTypeDescriptor>。 <xref:System.ComponentModel.ICustomTypeDescriptor>實作可以修改它所傳回的屬性描述元，並變更屬性的名稱。 若要當地語系化的描述，建立衍生自屬性<xref:System.ComponentModel.DescriptionAttribute>並覆寫描述屬性。  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>實作 IConnection 介面的考量  
  
1.  `IConnection`提供使用列舉值子物件的存取權<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>介面。 它也提供存取所有連接點子物件，它會實作的每個<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>介面。  
  
2.  瀏覽的任何物件都負責實作<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink>事件。 [屬性]  視窗將建議透過 `IConnection`所設定的事件。  
  
3.  連接點可讓您控制連線數目 （一或多個） 中所允許的其實作<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>。 僅允許一個介面的連接點可以傳回<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>從<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>方法。  
  
4.  用戶端可以呼叫`IConnection`介面，以取得使用列舉值子物件的存取權<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>介面。 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>介面便可以呼叫來列舉每個輸出介面識別碼 (IID) 的連接點。  
  
5.  `IConnection`也可以呼叫以取得存取權連接點子物件與<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>每個輸出 IID 的介面。 透過<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>介面，用戶端啟動或終止諮詢迴圈使用可連接物件和用戶端自己的同步處理。用戶端也可以呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>介面，以取得列舉值物件與<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections>介面，以列舉它所知道的連線。  
  
## <a name="getting-field-descriptions-from-the-properties-window"></a>從 [屬性] 視窗中取得欄位描述
在 [屬性]  視窗底部的描述區域會顯示選取的屬性欄位相關資訊。 這項功能預設為開啟。 如果想要隱藏描述欄位，請以滑鼠右鍵按一下 [屬性]  視窗，然後按一下 [描述] 。 這樣也會移除功能表視窗之 [描述]  標題旁的核取記號。 只要依照相同的步驟切換 [描述]  ，就可以再次顯示欄位。  
  
 描述欄位中的資訊來自<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>。 每個方法、介面、coclass 等在類型程式庫中都可以有未當地語系化的 `helpstring` 屬性。 **屬性**視窗擷取從字串<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>。  
  
### <a name="to-specify-localized-help-strings"></a>指定當地語系化的說明字串  
  
1.  請將 `helpstringdll` 屬性加入類型程式庫 (`typelib`) 的 library 陳述式。  
  
    > [!NOTE]
    >  如果類型程式庫位於物件程式庫 (.olb) 檔案中，這個步驟就是選擇性的。  
  
2.  為字串指定 `helpstringcontext` 屬性。 您也可以指定 `helpstring` 屬性。  
  
     這些屬性與 `helpfile` 和 `helpcontext` 屬性不同，它們位在說明主題的實際 .chm 檔案中。  
  
 若要擷取描述資訊以顯示反白顯示的屬性名稱，**屬性**視窗呼叫<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A>已選取的屬性，指定想要`lcid`屬性輸出字串。 就內部而言，<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2>尋找.dll 檔案中指定`helpstringdll`屬性和呼叫`DLLGetDocumentation`.dll 檔案與指定的內容和`lcid`屬性。  
  
 `DLLGetDocumentation` 的特徵標記和實作是：  
  
```cpp  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
 `DLLGetDocumentation` 函式必須是 .def 檔案中為 DLL 定義的匯出。  
  
 對內建立的 .olb 檔案，其實是個 DLL。 這個 DLL 包含一項資源、類型程式庫 (.tlb) 檔案，以及匯出的函式 `DLLGetDocumentation`。  
  
 如果是 .olb 檔案， `helpstringdll` 屬性即是選擇性的，因為它是包含了 .tlb 檔案本身的同一個檔案。  
  
 若要取得在 [描述]  窗格中顯示的字串，您至少要在類型程式庫中指定 `helpstring` 屬性。 如果希望當地語系化這些字串，您必須指定 `helpstringdll` (選擇性) 屬性和 `helpstringcontext` (必要) 屬性並實作 `DLLGetDocumentation`。  
  
 透過 idl 的 `helpstringcontext` 屬性和 `DLLGetDocumentation`取得當地語系化資訊時，不必實作其他介面。  
  
 取得當地語系化的名稱和屬性描述的另一種是藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>。 如需實作此方法的詳細資訊，請參閱[屬性視窗中的欄位和介面](../../extensibility/internals/properties-window-fields-and-interfaces.md)。  

## <a name="see-also"></a>另請參閱  
 [擴充屬性](../../extensibility/internals/extending-properties.md)