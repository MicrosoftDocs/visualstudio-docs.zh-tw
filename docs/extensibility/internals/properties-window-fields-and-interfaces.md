---
title: 屬性視窗欄位和介面 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9529708c781e7fdb04c3b4c5ee143b7605857e84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706154"
---
# <a name="properties-window-fields-and-interfaces"></a>Properties Window Fields and Interfaces
用於確定 **「屬性」** 視窗中顯示的資訊的模型基於 IDE 中具有焦點的視窗。 每個視窗和所選視窗中的物件都可以將其選擇上下文物件推送到全域選擇上下文。 當視窗具有焦點時,環境會使用視窗框架中的值更新全域選擇上下文。 當焦點更改時,選擇上下文也是如此。

## <a name="tracking-selection-in-the-ide"></a>IDE 的追蹤選擇
 由 IDE 擁有的視窗框架或網站具有<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>名為的服務。 以下步驟展示如何實現由於使用者將焦點更改為另一個打開的視窗或**解決方案資源管理器**中選擇其他項目項而導致的所選內容的更改,以更改 **「屬性」** 視窗中顯示的內容。

1. 由 VSPackage 建立的物件,該物件位於選取視窗呼<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>叫 中,以<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection><xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>呼叫 。

2. 所選視窗提供的選擇容器將創建其自己的<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>物件。 當選擇更改時,VSPackage<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>會呼叫該更改通知環境中的任何偵聽器(包括 **"屬性"** 視窗)。 它還提供對與新選擇相關的層次結構和項信息的訪問。

3. 調用<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>並傳遞參數`VSHPROPID_BrowseObject`中的 選定層次結構項<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>填充 物件。

4. 從[IDispatch 介面](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)派生的物件返回[__VSHPROPID。VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>)請求的項目,環境將其包裝成<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>( 請參閱以下步驟)。 如果呼叫失敗,環境將發出第二個調用`IVsHierarchy::GetProperty`,將其傳遞給選擇容器[__VSHPROPID。VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>)層次結構項或項供應。

    專案 VSPackage<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>不會建立 ,因為實現它的環境提供的視窗 VSPackage(例如,<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>**解決方案資源管理員**) 會代表它建構。

5. 環境調用<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>的方法 ,以獲取`IDispatch`有關基於 介面獲取物件以填充**屬性**視窗的方法。

   更改 **「屬性」** 視窗中的值時,VS`IVsTrackSelectionEx::OnElementValueChangeEx``IVsTrackSelectionEx::OnSelectionChangeEx`包實現 並 報告對元素值的更改。 然後,環境調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>或<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>保持**屬性**視窗中顯示的資訊與屬性值同步。 關於詳細資訊,請參閱[在屬性視窗中更新屬性值](#updating-property-values-in-the-properties-window)。

   除了在**解決方案資源管理器**中選擇其他專案項以顯示與該專案相關的屬性外,您還可以使用 **「屬性」** 視窗中的下拉清單從窗體或文件視窗中選擇其他物件。 有關詳細資訊,請參閱[屬性視窗物件清單](../../extensibility/internals/properties-window-object-list.md)。

   您可以將「**屬性」** 視窗格線中的資訊顯示方式從字母順序更改為分類,如果可用,還可以透過按下 **「屬性」** 視窗中的相應按鈕為選定物件打開屬性頁。 關於詳細資訊,請參閱[屬性視窗按鈕](../../extensibility/internals/properties-window-buttons.md)與[屬性頁](../../extensibility/internals/property-pages.md)。

   最後,「**屬性」** 視窗的底部還包含「**屬性」** 視窗格格中選擇的欄位的說明。 關於詳細資訊,請參閱[從屬性視窗取得欄位說明](#getting-field-descriptions-from-the-properties-window)。

## <a name="updating-property-values-in-the-properties-window"></a><a name="updating-property-values-in-the-properties-window"></a>更新屬性視窗中的屬性值
有兩種方法可以讓 [屬性] **** 視窗與屬性值變更同步。 第一種方法是呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 介面，此介面可存取基本視窗化功能 (包括存取和建立環境所提供的工具和文件視窗)。 下列步驟說明這項同步處理程序。

### <a name="updating-property-values-using-ivsuishell"></a>使用 IVsUIShell 更新屬性值

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>使用 IVsUIShell 介面更新屬性值

1. 隨時呼叫 VSPackage、專案或編輯器建立或列舉工具或文件視窗時所需的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (透過 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 服務)。

2. 實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A>使**屬性**視窗與專案的屬性更改(或**屬性**視窗正在瀏覽的任何其他選定物件)<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>保持同步,<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A>而無需實現和觸發 事件。

3. 實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A>，分別建立和停用用戶端階層事件通知，而不需要階層實作 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>。

### <a name="updating-property-values-using-iconnection"></a>使用 IConnection 更新屬性值
 第二種讓 [屬性] **** 視窗與屬性值變更同步的方法是在可連接物件上實作 `IConnection` ，表示輸出介面是否存在。 如果您想要當地語系化屬性名稱，請從 <xref:System.ComponentModel.ICustomTypeDescriptor> 衍生您的物件。 <xref:System.ComponentModel.ICustomTypeDescriptor> 實作可以修改它所傳回的屬性描述元，以及變更屬性的名稱。 若要當地語系化描述，請建立衍生自 <xref:System.ComponentModel.DescriptionAttribute> 的屬性，並覆寫 [描述] 屬性。

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>實作 IConnection 介面的考量

1. `IConnection` 可使用 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> 介面來存取列舉值子物件。 它也可存取所有連接點子物件，而所有連接點子物件都實作 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 介面。

2. 所有瀏覽物件都負責實作 <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> 事件。 [屬性] **** 視窗將建議透過 `IConnection`所設定的事件。

3. 連接點可控制其 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> 實作中所允許的連線數目 (一個或多個)。 僅允許一個介面的連接點可以從 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> 方法傳回 <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>。

4. 用戶端可以呼叫 `IConnection` 介面，以使用 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> 介面來存取列舉值子物件。 之後可以呼叫 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> 介面來列舉每個輸出介面識別碼 (IID) 的連接點。

5. 也可以呼叫 `IConnection`，以使用 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 介面來存取每個輸出 IID 的連接點子物件。 通過<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>介面,用戶端啟動或終止具有可連接物件和用戶端自身同步的諮詢迴圈。用戶端還可以調用<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>介面以獲取具有介面<xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections>的 枚舉器物件,以枚舉它知道的連接。

## <a name="getting-field-descriptions-from-the-properties-window"></a><a name="getting-field-descriptions-from-the-properties-window"></a>從屬性視窗抓取欄位描述
在 [屬性] **** 視窗底部的描述區域會顯示選取的屬性欄位相關資訊。 這項功能預設為開啟。 如果想要隱藏描述欄位，請以滑鼠右鍵按一下 [屬性] **** 視窗，然後按一下 [描述] ****。 這樣也會移除功能表視窗之 [描述] **** 標題旁的核取記號。 只要依照相同的步驟切換 [描述] **** ，就可以再次顯示欄位。

 描述欄位中的資訊出自 <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>。 每個方法、介面、coclass 等在類型程式庫中都可以有未當地語系化的 `helpstring` 屬性。 屬性**視窗**從 檢索<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>字串 。

### <a name="to-specify-localized-help-strings"></a>指定當地語系化的說明字串

1. 請將 `helpstringdll` 屬性加入類型程式庫 (`typelib`) 的 library 陳述式。

   > [!NOTE]
   > 如果類型程式庫位於物件程式庫 (.olb) 檔案中，這個步驟就是選擇性的。

2. 為字串指定 `helpstringcontext` 屬性。 您也可以指定 `helpstring` 屬性。

    這些屬性與 `helpfile` 和 `helpcontext` 屬性不同，它們位在說明主題的實際 .chm 檔案中。

   若要檢索要為突出顯示的屬性名稱顯示的說明資訊,「**屬性」** 視窗將呼<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A>叫選取的屬性,指定輸出字串的所需`lcid`屬性。 對內，<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> 會尋找 `helpstringdll` 屬性中指定的 .dll 檔案，並以指定的內容和 `lcid` 屬性呼叫 .dll 檔案的 `DLLGetDocumentation`。

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

 若要取得在 [描述] **** 窗格中顯示的字串，您至少要在類型程式庫中指定 `helpstring` 屬性。 如果希望當地語系化這些字串，您必須指定 `helpstringdll` (選擇性) 屬性和 `helpstringcontext` (必要) 屬性並實作 `DLLGetDocumentation`。

 透過 idl 的 `helpstringcontext` 屬性和 `DLLGetDocumentation`取得當地語系化資訊時，不必實作其他介面。

 取得屬性的當地語系化名稱和說明的另一個方式，是實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>。 如需實作這個方法的詳細資訊，請參閱 [Properties Window Fields and Interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md)。

## <a name="see-also"></a>另請參閱

- [擴充屬性](../../extensibility/internals/extending-properties.md)
