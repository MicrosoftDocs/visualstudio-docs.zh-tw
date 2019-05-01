---
title: 屬性 Window Fields and Interfaces |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1bf74bb93901cbd1637efd22690b8b1ba52f6b97
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425739"
---
# <a name="properties-window-fields-and-interfaces"></a>Properties Window Fields and Interfaces
若要判斷哪些資訊會顯示在選取的模型**屬性**視窗根據在 IDE 中具有焦點的視窗。 每個視窗中，然後選取視窗內的物件可以有其推送至全域範圍內容的選取項目內容物件。 該視窗具有焦點時，環境會更新全域選取範圍內容視窗框架的值。 當焦點變更時，因此會選取範圍內容。

## <a name="tracking-selection-in-the-ide"></a>追蹤在 IDE 中的選取範圍
 視窗框架或 IDE 中，所擁有的網站有一個稱為服務<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>。 下列步驟示範如何變更在 [選取項目，使用者將焦點變更為另一個開啟的視窗，或選取不同的專案項目中所造成**方案總管] 中**，實作變更中顯示的內容**屬性**視窗。

1. VSPackage 是 value 中選取的視窗呼叫所建立的物件<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>能夠<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>叫用<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>。

2. 選取容器，所選取的視窗中，提供建立它自己<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>物件。 當選取範圍的 VSPackage 會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>通知任何接聽程式，在環境中，包括**屬性**視窗中，變更。 它也提供新的選取範圍相關的階層] 和 [項目資訊的存取權。

3. 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>並將其傳遞中選取的階層項目`VSHPROPID_BrowseObject`參數會填入<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>物件。

4. 物件衍生自[IDispatch 介面](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)會傳回[__VSHPROPID。VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>)要求的項目，且環境會包裝到<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>（請參閱下一個步驟）。 如果呼叫失敗，環境會第二個呼叫`IVsHierarchy::GetProperty`，並選取容器[__VSHPROPID。VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>)的階層項目或項目提供。

    VSPackage 不會建立的專案<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>因為環境提供視窗 VSPackage 實作它 (例如**方案總管 中**) 建構<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>代替它。

5. 環境叫用的方法<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>若要取得根據物件`IDispatch`介面，以填入**屬性**視窗。

   中的值時**屬性** 視窗變更時，實作 Vspackage`IVsTrackSelectionEx::OnElementValueChangeEx`和`IVsTrackSelectionEx::OnSelectionChangeEx`來報告變更的項目值。 環境再叫用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>或是<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>保持中顯示的資訊**屬性**視窗同步處理的屬性值。 如需詳細資訊，請參閱 <<c0> [ 更新 [屬性] 視窗中的屬性值](#updating-property-values-in-the-properties-window)。

   除了選取不同的專案項目**方案總管 中**顯示該項目的相關的屬性，您也可以選擇從使用下拉式清單上可用的表單或文件視窗內的不同物件**屬性**視窗。 如需詳細資訊，請參閱 <<c0> [ 屬性視窗的物件清單](../../extensibility/internals/properties-window-object-list.md)。

   您可以變更資訊會顯示在的方式**屬性**成類別目錄，從依字母順序排列的視窗方格，如果有的話，則您也可以上適當的按鈕，即可開啟所選物件的屬性頁**屬性**視窗。 如需詳細資訊，請參閱 <<c0> [ 屬性視窗的按鈕](../../extensibility/internals/properties-window-buttons.md)並[屬性頁](../../extensibility/internals/property-pages.md)。

   最後，底部**屬性** 視窗也包含在選取的欄位的說明**屬性**視窗方格。 如需詳細資訊，請參閱 <<c0> [ 從 [屬性] 視窗取得欄位描述](#getting-field-descriptions-from-the-properties-window)。

## <a name="updating-property-values-in-the-properties-window"></a> 在 [屬性] 視窗中更新屬性值
有兩種方法可以讓 [屬性]  視窗與屬性值變更同步。 第一種方法是呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 介面，此介面可存取基本視窗化功能 (包括存取和建立環境所提供的工具和文件視窗)。 下列步驟說明這項同步處理程序。

### <a name="updating-property-values-using-ivsuishell"></a>使用 IVsUIShell 更新屬性值

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>使用 IVsUIShell 介面更新屬性值

1. 隨時呼叫 VSPackage、專案或編輯器建立或列舉工具或文件視窗時所需的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (透過 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 服務)。

2. 實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A>保持**屬性**視窗與專案的屬性變更同步 (或所瀏覽的任何其他所選物件**屬性**視窗) 而不需要實作<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>以及引發<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A>事件。

3. 實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A>，分別建立和停用用戶端階層事件通知，而不需要階層實作 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>。

### <a name="updating-property-values-using-iconnection"></a>使用 IConnection 更新屬性值
 第二種讓 [屬性]  視窗與屬性值變更同步的方法是在可連接物件上實作 `IConnection` ，表示輸出介面是否存在。 如果您想要當地語系化屬性名稱，請從 <xref:System.ComponentModel.ICustomTypeDescriptor> 衍生您的物件。 <xref:System.ComponentModel.ICustomTypeDescriptor> 實作可以修改它所傳回的屬性描述元，以及變更屬性的名稱。 若要當地語系化描述，請建立衍生自 <xref:System.ComponentModel.DescriptionAttribute> 的屬性，並覆寫 [描述] 屬性。

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>實作 IConnection 介面的考量

1. `IConnection` 可使用 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> 介面來存取列舉值子物件。 它也可存取所有連接點子物件，而所有連接點子物件都實作 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 介面。

2. 所有瀏覽物件都負責實作 <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> 事件。 [屬性]  視窗將建議透過 `IConnection`所設定的事件。

3. 連接點可控制其 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> 實作中所允許的連線數目 (一個或多個)。 僅允許一個介面的連接點可以從 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> 方法傳回 <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>。

4. 用戶端可以呼叫 `IConnection` 介面，以使用 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> 介面來存取列舉值子物件。 之後可以呼叫 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> 介面來列舉每個輸出介面識別碼 (IID) 的連接點。

5. 也可以呼叫 `IConnection`，以使用 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 介面來存取每個輸出 IID 的連接點子物件。 透過 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 介面，用戶端可使用可連接物件和用戶端自己的同步處理來啟動或終止諮詢迴圈。用戶端也可以呼叫 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 介面以使用 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> 介面來取得列舉值物件，以列舉它所知道的連線。

## <a name="getting-field-descriptions-from-the-properties-window"></a> 從 [屬性] 視窗中取得欄位描述
在 [屬性]  視窗底部的描述區域會顯示選取的屬性欄位相關資訊。 這項功能預設為開啟。 如果想要隱藏描述欄位，請以滑鼠右鍵按一下 [屬性]  視窗，然後按一下 [描述] 。 這樣也會移除功能表視窗之 [描述]  標題旁的核取記號。 只要依照相同的步驟切換 [描述]  ，就可以再次顯示欄位。

 描述欄位中的資訊出自 <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>。 每個方法、介面、coclass 等在類型程式庫中都可以有未當地語系化的 `helpstring` 屬性。 **屬性**視窗中擷取的字串<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>。

### <a name="to-specify-localized-help-strings"></a>指定當地語系化的說明字串

1. 請將 `helpstringdll` 屬性加入類型程式庫 (`typelib`) 的 library 陳述式。

   > [!NOTE]
   > 如果類型程式庫位於物件程式庫 (.olb) 檔案中，這個步驟就是選擇性的。

2. 為字串指定 `helpstringcontext` 屬性。 您也可以指定 `helpstring` 屬性。

    這些屬性與 `helpfile` 和 `helpcontext` 屬性不同，它們位在說明主題的實際 .chm 檔案中。

   若要擷取描述資訊，以顯示反白顯示的屬性名稱，**屬性**視窗呼叫<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A>已選取的屬性，指定想要`lcid`屬性輸出字串。 對內，<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> 會尋找 `helpstringdll` 屬性中指定的 .dll 檔案，並以指定的內容和 `lcid` 屬性呼叫 .dll 檔案的 `DLLGetDocumentation`。

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

 取得屬性的當地語系化名稱和說明的另一個方式，是實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>。 如需實作這個方法的詳細資訊，請參閱 [Properties Window Fields and Interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md)。

## <a name="see-also"></a>另請參閱

- [擴充屬性](../../extensibility/internals/extending-properties.md)