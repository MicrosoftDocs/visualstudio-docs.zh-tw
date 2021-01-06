---
title: 屬性視窗欄位和介面 |Microsoft Docs
description: 根據焦點在 Visual Studio IDE 中的視窗，深入瞭解決定要在屬性視窗中顯示哪些資訊的選項。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 21bc3a7f1d46a1afe579a67afa09097fd04458ff
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875761"
---
# <a name="properties-window-fields-and-interfaces"></a>Properties Window Fields and Interfaces
用來決定要在 [ **屬性** ] 視窗中顯示哪些資訊的模型是根據焦點在 IDE 中的視窗。 在選取的視窗內，每個視窗和物件都可以將其選取內容物件推送至全域選取內容。 當視窗具有焦點時，環境會以視窗框架中的值來更新全域選取內容。 當焦點變更時，就會進行選取內容。

## <a name="tracking-selection-in-the-ide"></a>在 IDE 中追蹤選取專案
 IDE 所擁有的視窗框架或網站有一個稱為的服務 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> 。 下列步驟顯示如何將焦點變更為另一個開啟的視窗，或在 **方案總管** 中選取不同的專案專案，以變更 [ **屬性** ] 視窗中顯示的內容。

1. 由您的 VSPackage 所建立的物件，該物件位於所選視窗呼叫中，並 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> 具有 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> invoke <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> 。

2. 選取的視窗所提供的選取專案容器會建立自己的 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 物件。 當選取範圍變更時，VSPackage 會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 以在環境中通知任何接聽程式，包括 **屬性** 視窗在內的變更。 它也可讓您存取與新選項相關的階層和專案資訊。

3. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 並傳遞給它。參數中選取的階層專案會 `VSHPROPID_BrowseObject` 填入 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 物件。

4. 針對 __VSHPROPID，會傳回衍生自 [IDispatch 介面](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) 的物件 [。VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) 要求的專案，且環境會將其包裝到 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (，請參閱) 的下列步驟。 如果呼叫失敗，則環境會進行第二個呼叫 `IVsHierarchy::GetProperty` ，並將選取容器 __VSHPROPID 傳遞給它 [。](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) 階層專案或專案所提供的 VSHPROPID_SelContainer。

    您的專案 VSPackage 不會建立， <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 因為環境提供的視窗 VSPackage 會執行它 (例如， **方案總管**) <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 代表它的結構。

5. 環境會叫用的方法 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> ，以根據 `IDispatch` 要在 [ **屬性** ] 視窗中填入的介面來取得物件。

   當 [ **屬性** ] 視窗中的值變更時，vspackage 會執行 `IVsTrackSelectionEx::OnElementValueChangeEx` ，並將 `IVsTrackSelectionEx::OnSelectionChangeEx` 變更回報給元素值。 然後環境會叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> 用或，讓 [ **屬性** ] 視窗中顯示的資訊與屬性值同步。 如需詳細資訊，請參閱在 [屬性視窗中更新屬性值](#updating-property-values-in-the-properties-window)。

   除了在 **方案總管** 中選取不同的專案專案，以顯示與該專案相關的屬性之外，您也可以使用 [ **屬性** ] 視窗上提供的下拉式清單，從表單或文件視窗中選擇不同的物件。 如需詳細資訊，請參閱 [屬性視窗物件清單](../../extensibility/internals/properties-window-object-list.md)。

   您可以將 [ **屬性** ] 視窗方格中的資訊顯示方式從字母順序變更為類別，如果有的話，您也可以按一下 [ **屬性** ] 視窗上的適當按鈕，開啟所選物件的屬性頁。 如需詳細資訊，請參閱 [屬性視窗按鈕](../../extensibility/internals/properties-window-buttons.md) 和 [屬性頁](../../extensibility/internals/property-pages.md)。

   最後，[ **屬性** ] 視窗的底部也包含 [ **屬性** ] 視窗方格中所選取之欄位的描述。 如需詳細資訊，請參閱 [從屬性視窗取得欄位描述](#getting-field-descriptions-from-the-properties-window)。

## <a name="updating-property-values-in-the-properties-window"></a><a name="updating-property-values-in-the-properties-window"></a> 更新屬性視窗中的屬性值
有兩種方法可以讓 [屬性]  視窗與屬性值變更同步。 第一種方法是呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 介面，此介面可存取基本視窗化功能 (包括存取和建立環境所提供的工具和文件視窗)。 下列步驟說明這項同步處理程序。

### <a name="updating-property-values-using-ivsuishell"></a>使用 IVsUIShell 更新屬性值

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>使用 IVsUIShell 介面更新屬性值

1. 隨時呼叫 VSPackage、專案或編輯器建立或列舉工具或文件視窗時所需的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (透過 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 服務)。

2. [執行] <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> 可讓 [屬性] 視窗與專案 (的屬性變更或 [**屬性**] 視窗所流覽的任何其他選取物件保持同步，) 不會執行 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> 和引發 <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> 事件。

3. 實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A>，分別建立和停用用戶端階層事件通知，而不需要階層實作 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>。

### <a name="updating-property-values-using-iconnection"></a>使用 IConnection 更新屬性值
 第二種讓 [屬性]  視窗與屬性值變更同步的方法是在可連接物件上實作 `IConnection` ，表示輸出介面是否存在。 如果您想要當地語系化屬性名稱，請從 <xref:System.ComponentModel.ICustomTypeDescriptor> 衍生您的物件。 <xref:System.ComponentModel.ICustomTypeDescriptor> 實作可以修改它所傳回的屬性描述元，以及變更屬性的名稱。 若要當地語系化描述，請建立衍生自 <xref:System.ComponentModel.DescriptionAttribute> 的屬性，並覆寫 [描述] 屬性。

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>實作 IConnection 介面的考量

1. `IConnection` 可使用 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> 介面來存取列舉值子物件。 它也可存取所有連接點子物件，而所有連接點子物件都實作 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 介面。

2. 所有瀏覽物件都負責實作 <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> 事件。 [屬性]  視窗將建議透過 `IConnection`所設定的事件。

3. 連接點可控制其 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> 實作中所允許的連線數目 (一個或多個)。 僅允許一個介面的連接點可以從 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> 方法傳回 <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>。

4. 用戶端可以呼叫 `IConnection` 介面，以使用 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> 介面來存取列舉值子物件。 之後可以呼叫 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> 介面來列舉每個輸出介面識別碼 (IID) 的連接點。

5. 也可以呼叫 `IConnection`，以使用 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 介面來存取每個輸出 IID 的連接點子物件。 透過 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 介面，用戶端會使用可連線物件和用戶端自己的同步處理來啟動或終止諮詢迴圈。用戶端也可以呼叫 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 介面，取得具有介面的列舉值物件， <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> 以列舉其知道的連接。

## <a name="getting-field-descriptions-from-the-properties-window"></a><a name="getting-field-descriptions-from-the-properties-window"></a> 從 [屬性] 視窗中取得欄位描述
在 [屬性]  視窗底部的描述區域會顯示選取的屬性欄位相關資訊。 這項功能預設為開啟。 如果想要隱藏描述欄位，請以滑鼠右鍵按一下 [屬性]  視窗，然後按一下 [描述] 。 這樣也會移除功能表視窗之 [描述]  標題旁的核取記號。 只要依照相同的步驟切換 [描述]  ，就可以再次顯示欄位。

 描述欄位中的資訊出自 <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>。 每個方法、介面、coclass 等在類型程式庫中都可以有未當地語系化的 `helpstring` 屬性。 [ **屬性** ] 視窗會從抓取字串 <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A> 。

### <a name="to-specify-localized-help-strings"></a>指定當地語系化的說明字串

1. 請將 `helpstringdll` 屬性加入類型程式庫 (`typelib`) 的 library 陳述式。

   > [!NOTE]
   > 如果類型程式庫位於物件程式庫 (.olb) 檔案中，這個步驟就是選擇性的。

2. 為字串指定 `helpstringcontext` 屬性。 您也可以指定 `helpstring` 屬性。

    這些屬性與 `helpfile` 和 `helpcontext` 屬性不同，它們位在說明主題的實際 .chm 檔案中。

   為了抓取醒目提示的屬性名稱所顯示的描述資訊，[ **屬性** ] 視窗 <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> 會呼叫已選取的屬性，並指定輸出字串的所需 `lcid` 屬性。 對內，<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> 會尋找 `helpstringdll` 屬性中指定的 .dll 檔案，並以指定的內容和 `lcid` 屬性呼叫 .dll 檔案的 `DLLGetDocumentation`。

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

## <a name="see-also"></a>請參閱

- [擴充屬性](../../extensibility/internals/extending-properties.md)
