---
title: 使用 Visual Studio Interop 元件 |Microsoft Docs
description: 瞭解 Visual Studio interop 元件如何讓 managed 應用程式存取提供 Visual Studio 擴充性的 COM 介面。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1764cc735ca836feada2ad6f794f2bc8520fef41
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941693"
---
# <a name="using-visual-studio-interop-assemblies"></a>使用 Visual Studio Interop 組件
Visual Studio interop 元件可讓 managed 應用程式存取提供 Visual Studio 擴充性的 COM 介面。 直接 COM 介面與其 interop 版本之間有一些差異。 例如，Hresult 通常會表示為 int 值，而且需要以與例外狀況相同的方式來處理，而參數 (特別是參數) 的處理方式不同。

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>處理從 COM 傳回給 Managed 程式碼的 HRESULT
 當您透過 Managed 程式碼呼叫 COM 介面時，請檢查 HRESULT 值，並視需要擲回例外狀況。 <xref:Microsoft.VisualStudio.ErrorHandler> 類別包含會擲回 COM 例外狀況的 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 方法 (視傳遞給它的 HRESULT 值而定)。

 根據預設，<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 只要傳遞的 HRESULT 值小於零就會擲回例外狀況。 如果這類 HRESULT 是可接受值，而且不應該擲回任何例外狀況，則在測試值之後，應該會將其他 HRESULT 的值傳遞給 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>。 如果正在測試的 HRESULT 符合明確傳遞給 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 的任何 HRESULT 值，則不會擲回任何例外狀況。

> [!NOTE]
> <xref:Microsoft.VisualStudio.VSConstants>類別包含一般 hresult 的常數，例如 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 和 <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> ，以及 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hresult，例如 <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> 和 <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> 。 <xref:Microsoft.VisualStudio.VSConstants> 也提供 <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> 和 <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> 方法，而這些方法會對應至 COM 中的 SUCCEEDED 和 FAILED 巨集。

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

## <a name="iunknown-parameters-passed-as-type-void"></a>以 void * * 類型傳遞的 IUnknown 參數
 在 COM 介面中尋找定義為類型的 [out] 參數 `void **` ，但是定義為 `[``iid_is``]` [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 元件方法原型中的參數。

 有時候，COM 介面 `IUnknown` 會產生物件，然後 com 介面會將它傳遞為型別 `void **` 。 這些介面特別重要，因為如果變數定義為 IDL 中的 [out]，則 `IUnknown` 會使用方法來計算物件的參考計數 `AddRef` 。 如果物件未正確處理，就會發生記憶體流失。

> [!NOTE]
> `IUnknown`COM 介面所建立，並在 [out] 變數中傳回的物件，如果未明確釋放，則會造成記憶體流失。

 處理這類物件的 Managed 方法應該視為 <xref:System.IntPtr> 物件的指標 `IUnknown` ，然後呼叫 <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> 方法來取得物件。 接著，呼叫端應該將傳回值轉換成適當的任何類型。 當不再需要物件時，呼叫以釋出該物件 <xref:System.Runtime.InteropServices.Marshal.Release%2A> 。

 以下是呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> 方法並正確處理物件的範例 `IUnknown` ：

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
> 已知下列方法會將 `IUnknown` 物件指標傳遞為類型 <xref:System.IntPtr> 。 如本節所述進行處理。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>選擇性的 [out] 參數
 在 COM 介面中尋找定義為 [out] 資料類型 (、等等) 的參數， `int` `object` 但在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 元件方法原型中定義為相同資料類型的陣列。

 某些 COM 介面（例如）會將 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> [out] 參數視為選擇性。 如果不需要物件，這些 COM 介面會將指標傳回 `null` 為該參數的值，而不是建立 [out] 物件。 這是原廠設定。 針對這些介面， `null` 指標會假設為 VSPackage 正確行為的一部分，而且不會傳回任何錯誤。

 因為 CLR 不允許將 [out] 參數的值設為 `null` ，所以在 managed 程式碼中無法直接使用這些介面的部分設計行為。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]受影響之介面的 interop 元件方法會藉由將相關的參數定義為數組來解決此問題，因為 CLR 允許傳遞 `null` 陣列。

 當沒有任何要傳回的專案時，這些方法的 Managed 執行應該會將 `null` 陣列放入參數中。 否則，請建立正確型別的單一元素陣列，並將傳回值放在陣列中。

 使用選擇性的 [out] 參數從介面接收資訊的 Managed 方法會以陣列形式接收參數。 只需要檢查陣列的第一個元素值。 如果不是，則會 `null` 將第一個元素視為原始參數。

## <a name="passing-constants-in-pointer-parameters"></a>在指標參數中傳遞常數
 在 COM 介面中尋找定義為 [in] 指標的參數，但在 <xref:System.IntPtr> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 元件方法原型中定義為類型。

 當 COM 介面傳遞特殊值（例如0、-1 或-2）而非物件指標時，就會發生類似的問題。 與不同 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 的是，CLR 不允許將常數轉換成物件。 相反地， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 元件會將參數定義為 <xref:System.IntPtr> 型別。

 這些方法的 Managed 執行應該會利用這個事實： <xref:System.IntPtr> 類別同時具有和函 `int` 式 `void *` ，以視 <xref:System.IntPtr> 需要從物件或整數常數建立。

 接收 <xref:System.IntPtr> 此型別之參數的 Managed 方法應該使用 <xref:System.IntPtr> 型別轉換運算子來處理結果。 首先，將轉換成 <xref:System.IntPtr> `int` ，並針對相關的整數常數進行測試。 如果沒有相符的值，請將它轉換成所需類型的物件，並繼續進行。

 如需這項的範例，請參閱 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> 。

## <a name="ole-return-values-passed-as-out-parameters"></a>以 [out] 參數傳遞的 OLE 傳回值
 `retval`在 COM 介面中尋找有傳回值的方法，但在 `int` [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 元件方法原型中有傳回值和其他的 [out] 陣列參數。 請注意，這些方法需要特殊處理，因為 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 元件方法原型具有比 COM 介面方法更多的參數。

 許多處理 OLE 活動的 COM 介面都會將 OLE 狀態的相關資訊傳送回介面傳回值中所儲存的呼叫程式 `retval` 。 相對應的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 元件方法會將資訊傳回給儲存在 [out] 陣列參數中的呼叫程式，而不是使用傳回值。

 這些方法的 Managed 執行應該建立與 [out] 參數相同類型的單一元素陣列，並將它放在參數中。 陣列元素的值應該與適當的 COM 相同 `retval` 。

 呼叫此型別之介面的 Managed 方法應該從 [out] 陣列提取第一個元素。 您可以將這個元素視為 `retval` 來自對應 COM 介面的傳回值。

## <a name="see-also"></a>另請參閱
- [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)
