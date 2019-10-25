---
title: 使用 Visual Studio Interop 元件 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0db6e0e0d5014f09a84316143af40f410bc1b10
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722107"
---
# <a name="using-visual-studio-interop-assemblies"></a>使用 Visual Studio Interop 組件
Visual Studio interop 元件可讓 managed 應用程式存取提供 Visual Studio 擴充性的 COM 介面。 直接 COM 介面與其 interop 版本之間有一些差異。 例如，Hresult 通常會表示為 int 值，而且需要以與例外狀況相同的方式來處理，而參數（特別是 out 參數）則會以不同的方式處理。

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>處理從 COM 傳回給 Managed 程式碼的 HRESULT
 當您透過 Managed 程式碼呼叫 COM 介面時，請檢查 HRESULT 值，並視需要擲回例外狀況。 <xref:Microsoft.VisualStudio.ErrorHandler> 類別包含會擲回 COM 例外狀況的 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 方法 (視傳遞給它的 HRESULT 值而定)。

 根據預設，<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 只要傳遞的 HRESULT 值小於零就會擲回例外狀況。 如果這類 HRESULT 是可接受值，而且不應該擲回任何例外狀況，則在測試值之後，應該會將其他 HRESULT 的值傳遞給 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>。 如果正在測試的 HRESULT 符合明確傳遞給 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 的任何 HRESULT 值，則不會擲回任何例外狀況。

> [!NOTE]
> <xref:Microsoft.VisualStudio.VSConstants> 類別包含一般 HRESULT 的常數，例如，<xref:Microsoft.VisualStudio.VSConstants.S_OK> 和 <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>，以及 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的 HRESULT，例如 <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> 和 <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>。 <xref:Microsoft.VisualStudio.VSConstants> 也提供 <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> 和 <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> 方法，而這些方法會對應至 COM 中的 SUCCEEDED 和 FAILED 巨集。

 例如，請考慮下列的函式呼叫，其中，<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> 是可接受的傳回值，但任何其他小於零的 HRESULT 都代表發生錯誤。

 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]

 如果有多個可接受的傳回值，則在 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 呼叫中只能將其他 HRESULT 值附加至清單。

 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]

## <a name="returning-hresults-to-com-from-managed-code"></a>透過 Managed 程式碼將 HRESULT 傳回給 COM
 如果未發生例外狀況，則 Managed 程式碼會將 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 傳回給已呼叫它的 COM 函式。 COM Interop 支援透過 Managed 程式碼進行強類型處理的常見例外狀況。 例如，收到無法接受 `null` 引數的方法會擲回 <xref:System.ArgumentNullException>

 如果您不確定會擲回哪個例外狀況，但知道您想要傳回給 COM 的 HRESULT，則可以使用 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> 方法擲回適當的例外狀況。 這甚至適用於非標準錯誤 (例如，<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>)。 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> 會嘗試將傳遞給它的 HRESULT 對應至強類型例外狀況。 如果失敗，則會改為擲回一般 COM 例外狀況。 最後結果是您透過 Managed 程式碼傳遞給 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> 的 HRESULT 會傳回給呼叫它的 COM 函式。

> [!NOTE]
> 例外狀況會危害效能並用來指出異常程式狀況。 經常發生的狀況應該透過內嵌方式處理，而不是擲回例外狀況。

## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown 參數傳遞為 void * * 類型
 在 COM 介面中尋找定義為類型 `void **` 的 [out] 參數，但在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 元件方法原型中定義為 `[``iid_is``]`。

 有時候，COM 介面會產生 `IUnknown` 物件，然後 COM 介面會將它當做類型 `void **`傳遞。 這些介面特別重要，因為如果變數定義為 IDL 中的 [out]，則 `IUnknown` 物件會使用 `AddRef` 方法進行參考計算。 如果未正確處理物件，就會發生記憶體流失。

> [!NOTE]
> COM 介面所建立並在 [out] 變數中傳回的 `IUnknown` 物件，會導致記憶體流失（如果未明確釋放）。

 處理這類物件的 Managed 方法應將 <xref:System.IntPtr> 視為 `IUnknown` 物件的指標，並呼叫 <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> 方法來取得物件。 呼叫端接著應該將傳回值轉換成適當的任何類型。 當不再需要物件時，請呼叫 <xref:System.Runtime.InteropServices.Marshal.Release%2A> 來釋放它。

 以下是呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> 方法和正確處理 `IUnknown` 物件的範例：

```
MyClass myclass;
Object object;
IntPtr pObj;
Guid iid = Typeof(MyClass).Guid;
int hr = windowFrame.QueryViewInterface(ref iid, out pObj);
if (NativeMethods.Succeeded(hr))
{
    try
    {
        object = Marshal.GetObjectForIUnknown(pObj);
        myclass = object;
    }
    finally
    {
        Marshal.Release(pObj);
    }
}
else
{
    // error calling QueryViewInterface
}
```

> [!NOTE]
> 已知下列方法會將 `IUnknown` 物件指標當做類型 <xref:System.IntPtr>傳遞。 如本節所述來處理它們。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>選擇性 [out] 參數
 在 COM 介面中尋找定義為 [out] 資料類型（`int`、`object`等等）的參數，但在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 元件方法原型中，會定義為相同資料類型的陣列。

 某些 COM 介面，例如 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>，會將 [out] 參數視為選擇性。 如果不需要物件，這些 COM 介面會傳回 `null` 指標做為該參數的值，而不是建立 [out] 物件。 這是依設計的結果。 針對這些介面，`null` 指標會被假設為 VSPackage 的正確行為的一部分，而且不會傳回任何錯誤。

 因為 CLR 不允許 `null`[out] 參數的值，所以在 managed 程式碼中無法直接使用這些介面之設計行為的一部分。 受影響介面的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 元件方法會將相關的參數定義為數組，藉此解決此問題，因為 CLR 允許傳遞 `null` 陣列。

 當沒有任何要傳回的內容時，這些方法的 Managed 執行應該會將 `null` 陣列放入參數中。 否則，請建立一個正確類型的單一元素陣列，並將傳回值放在陣列中。

 從具有選擇性 [out] 參數的介面接收資訊的 Managed 方法，會接收參數做為陣列。 只要檢查陣列第一個元素的值。 如果不是 `null`，請將第一個元素視為原始參數。

## <a name="passing-constants-in-pointer-parameters"></a>在指標參數中傳遞常數
 尋找在 COM 介面中定義為 [in] 指標的參數，但在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 元件方法原型中定義為 <xref:System.IntPtr> 類型。

 當 COM 介面傳遞特殊值（例如0、-1 或-2，而不是物件指標）時，就會發生類似的問題。 不同于 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]，CLR 不允許將常數轉換成物件。 相反地，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 元件會將參數定義為 <xref:System.IntPtr> 類型。

 這些方法的 Managed 執行應該可以利用 <xref:System.IntPtr> 類別同時具有 `int` 和 `void *` 的函式，以視情況從物件或整數常數建立 <xref:System.IntPtr>。

 接收此類型 <xref:System.IntPtr> 參數的 Managed 方法應該使用 <xref:System.IntPtr> 類型轉換運算子來處理結果。 先將 <xref:System.IntPtr> 轉換為 `int`，並針對相關的整數常數進行測試。 如果沒有符合的值，請將它轉換成所需類型的物件，並繼續。

 如需這種情況的範例，請參閱 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>。

## <a name="ole-return-values-passed-as-out-parameters"></a>當做 [out] 參數傳遞的 OLE 傳回值
 在 COM 介面中尋找具有 `retval` 傳回值的方法，但在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 元件方法原型中具有 `int` 傳回值和額外的 [out] 陣列參數。 請注意，這些方法需要特殊處理，因為 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 元件方法原型除了 COM 介面方法之外，還有一個參數。

 處理 OLE 活動的許多 COM 介面都會將 OLE 狀態的相關資訊傳送回呼叫端程式，並儲存在介面的 `retval` 傳回值中。 對應的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 元件方法會將資訊傳回給儲存在 [out] 陣列參數中的呼叫程式，而不是使用傳回值。

 這些方法的 Managed 執行應該會建立與 [out] 參數相同類型的單一元素陣列，並將它放在參數中。 Array 元素的值應該與適當的 COM `retval`相同。

 呼叫這個型別的介面的 Managed 方法應從 [out] 陣列提取第一個元素。 這個元素可以視為來自對應 COM 介面的 `retval` 傳回值。

## <a name="see-also"></a>請參閱
- [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)