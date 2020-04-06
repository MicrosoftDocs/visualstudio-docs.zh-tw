---
title: 使用視覺化工作室互動元件 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5926b2cce217565c889c7ef2eeef877691101ed6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704138"
---
# <a name="using-visual-studio-interop-assemblies"></a>使用 Visual Studio Interop 組件
可視化工作室互通程式集允許託管應用程式訪問提供可視化工作室可擴充性的 COM 介面。 直 COM 介面與其互通版本之間存在一些差異。 例如,HRESULT 通常表示為 int 值,需要以與異常相同的方式處理,並且參數(尤其是出參數)的處理方式不同。

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>處理從 COM 傳回給 Managed 程式碼的 HRESULT
 當您透過 Managed 程式碼呼叫 COM 介面時，請檢查 HRESULT 值，並視需要擲回例外狀況。 <xref:Microsoft.VisualStudio.ErrorHandler> 類別包含會擲回 COM 例外狀況的 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 方法 (視傳遞給它的 HRESULT 值而定)。

 根據預設，<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 只要傳遞的 HRESULT 值小於零就會擲回例外狀況。 如果這類 HRESULT 是可接受值，而且不應該擲回任何例外狀況，則在測試值之後，應該會將其他 HRESULT 的值傳遞給 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>。 如果正在測試的 HRESULT 符合明確傳遞給 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 的任何 HRESULT 值，則不會擲回任何例外狀況。

> [!NOTE]
> <xref:Microsoft.VisualStudio.VSConstants>類別<xref:Microsoft.VisualStudio.VSConstants.S_OK>包含公共 H 結果的常量,例如<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]與 H<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA><xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>結果, 與 。 <xref:Microsoft.VisualStudio.VSConstants> 也提供 <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> 和 <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> 方法，而這些方法會對應至 COM 中的 SUCCEEDED 和 FAILED 巨集。

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

## <a name="iunknown-parameters-passed-as-type-void"></a>I 未知參數傳遞為類型無效*
 尋找在 COM 介面中定義為類型`void **`的 [out]`[``iid_is``]`[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]參數,但在內部程式集方法原型中定義為類型。

 有時,COM 介面產生`IUnknown`物件 ,然後 COM 介面`void **`將其傳遞為類型 。 這些介面尤其重要,因為如果變數在 IDL 中定義為`IUnknown`[out],`AddRef`則使用方法對物件進行引用計數。 如果物件處理不正確,則會發生內存洩漏。

> [!NOTE]
> 由`IUnknown`COM 介面建立並在 [out] 變數中傳回的物件如果未顯式釋放,則會導致記憶體洩漏。

 處理此類物件的託管方法應視為<xref:System.IntPtr>指向`IUnknown`物件的指標,並調用<xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A>方法以獲取該物件。 然後,調用方應將返回值轉換為任何合適的類型。 當不再需要該物件時,調用<xref:System.Runtime.InteropServices.Marshal.Release%2A>以釋放它。

 下面是呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>該方法並正確`IUnknown`處理 物件的範例:

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
> 已知以下方法將物件指標傳遞`IUnknown`為類型<xref:System.IntPtr>。 如本節所述處理它們。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>選擇選擇 [出] 參數
 在 COM 介面中尋找定義為 [out]`int`資料`object`類型 (、 等[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) 的參數,但在內部程式集方法原型中定義為相同數據類型的陣列。

 某些 COM<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>介面( 如 )將 [out] 參數視為可選參數。 如果不需要物件,這些 COM`null`介面將指標作為該參數的值返回,而不是創建 [out] 物件。 這是原廠設定。 對於這些介面,`null`指標被假定為 VSPackage 正確行為的一部分,並且不會返回任何錯誤。

 由於 CLR 不允許 [out]`null`參數的值是 ,這些介面的設計行為的一部分不能直接在託管代碼中可用。 受影響[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]介面的互操作程式集方法通過將相關參數定義為陣列來解決此問題,因為CLR允許`null`傳遞陣列。

 當沒有返回時,這些方法的託管實現`null`應將數組放入參數中。 否則,創建正確類型的單元素陣列,並將返回值放在陣列中。

 從具有可選 [out] 參數的介面接收資訊的託管方法將參數作為陣列接收。 只需檢查陣列的第一個元素的值。 如果不是`null`,則將第一個元素視為原始參數。

## <a name="passing-constants-in-pointer-parameters"></a>在指標參數中傳遞常量
 在 COM 介面中尋找定義為 [in] 指標,但在內部操作程式集方法原型中<xref:System.IntPtr>定義為[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]類型的 參數。

 當 COM 介面傳遞特殊值(如 0、-1 或 -2)而不是物件指標時,也會出現類似的問題。 與[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]不同,CLR不允許將常量轉換為物件。 相反,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]互通程式集會定義為類型<xref:System.IntPtr>。

 這些方法的託管<xref:System.IntPtr>實現應利用類具有和`int``void *`建構函數這一事實,以便根據需要從物件或整數常<xref:System.IntPtr>量 創建 。

 接收<xref:System.IntPtr>此類型參數的託管方法應使用<xref:System.IntPtr>類型轉換運算符來處理結果。 首先將<xref:System.IntPtr>轉換`int`為 ,並針對相關的整數常量進行測試。 如果沒有值匹配,請將其轉換為所需類型的物件並繼續。

 有關此範例,請參閱<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>。

## <a name="ole-return-values-passed-as-out-parameters"></a>為 [out] 參數傳遞的 OLE 傳回值
 尋找在 COM`retval`介面中具有傳回`int`[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]值但 具有傳回值並在內部分聲程式集方法原型中具有附加 [out] 陣列參數的方法。 應該清楚的是,這些方法需要特殊處理,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]因為內部程式集方法原型比 COM 介面方法多一個參數。

 處理 OLE 活動的許多 COM 介面將有關 OLE 狀態`retval`的資訊發送回儲存在介面返回值中的調用程式。 相應的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]內部程式集方法不使用返回值,而是將資訊發送回存儲在 [out] 陣列參數中的調用程式。

 這些方法的託管實現應創建與 [out] 參數類型相同的單元素陣列,並將其放入參數中。 陣列元素的值應與相應的`retval`COM 相同。

 呼叫此類型介面的託管方法應從 [out] 陣列中提取第一個元素。 可以將此元素視為來自相應 COM`retval`介面的返回值。

## <a name="see-also"></a>另請參閱
- [與非託管代碼互通](/dotnet/framework/interop/index)
