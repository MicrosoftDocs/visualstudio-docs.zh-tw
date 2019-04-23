---
title: 使用 Interop 組件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
caps.latest.revision: 34
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 303947c2299601e68ae830b13e6b6753c5e0dd79
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60067920"
---
# <a name="using-visual-studio-interop-assemblies"></a>使用 Visual Studio Interop 組件
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio interop 組件可讓受管理的應用程式存取 COM 介面，提供 Visual Studio 擴充性。 有一些直接的 COM 介面和其 interop 版本之間的差異。 比方說，Hresult 通常統稱為 int 值，和需要處理例外狀況，以相同的方式和參數 (尤其是 out 參數） 的處理方式不同。

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>處理從 COM 傳回給 Managed 程式碼的 HRESULT
 當您透過 Managed 程式碼呼叫 COM 介面時，請檢查 HRESULT 值，並視需要擲回例外狀況。 <xref:Microsoft.VisualStudio.ErrorHandler> 類別包含會擲回 COM 例外狀況的 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 方法 (視傳遞給它的 HRESULT 值而定)。

 根據預設，<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 只要傳遞的 HRESULT 值小於零就會擲回例外狀況。 如果這類 HRESULT 是可接受值，而且不應該擲回任何例外狀況，則在測試值之後，應該會將其他 HRESULT 的值傳遞給 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>。 如果正在測試的 HRESULT 符合明確傳遞給 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 的任何 HRESULT 值，則不會擲回任何例外狀況。

> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants>類別包含常數常見 hresults，例如<xref:Microsoft.VisualStudio.VSConstants.S_OK>並<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>，和[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]HRESULT，比方說，<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>和<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>。 <xref:Microsoft.VisualStudio.VSConstants> 也提供 <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> 和 <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> 方法，而這些方法會對應至 COM 中的 SUCCEEDED 和 FAILED 巨集。

 例如，請考慮下列的函式呼叫，其中，<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> 是可接受的傳回值，但任何其他小於零的 HRESULT 都代表發生錯誤。

 [!code-csharp[VSSDKHRESULTInformation#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]

 如果有多個可接受的傳回值，則在 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 呼叫中只能將其他 HRESULT 值附加至清單。

 [!code-csharp[VSSDKHRESULTInformation#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]

## <a name="returning-hresults-to-com-from-managed-code"></a>透過 Managed 程式碼將 HRESULT 傳回給 COM
 如果未發生例外狀況，則 Managed 程式碼會將 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 傳回給已呼叫它的 COM 函式。 COM Interop 支援透過 Managed 程式碼進行強類型處理的常見例外狀況。 例如，收到無法接受 `null` 引數的方法會擲回 <xref:System.ArgumentNullException>

 如果您不確定會擲回哪個例外狀況，但知道您想要傳回給 COM 的 HRESULT，則可以使用 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> 方法擲回適當的例外狀況。 這甚至適用於非標準錯誤 (例如，<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>)。 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> 會嘗試將傳遞給它的 HRESULT 對應至強類型例外狀況。 如果失敗，則會改為擲回一般 COM 例外狀況。 最後結果是您透過 Managed 程式碼傳遞給 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> 的 HRESULT 會傳回給呼叫它的 COM 函式。

> [!NOTE]
>  例外狀況會危害效能並用來指出異常程式狀況。 經常發生的狀況應該透過內嵌方式處理，而不是擲回例外狀況。

## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown 參數傳遞做為類型 void * *
 [Out] 定義為類型的參數尋找`void **`COM 介面，但會定義成`[``iid_is``]`在[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]interop 組件的方法原型。

 某些情況下，會產生 COM 介面`IUnknown`物件，並在 COM 介面然後將它傳遞做為類型`void **`。 這些介面是特別重要因為如果變數定義為 [out] 中的 IDL 中，則`IUnknown`物件是使用參考計數`AddRef`方法。 如果物件未正確地處理，就會發生記憶體流失。

> [!NOTE]
>  `IUnknown`未明確地釋放時建立的 COM 介面，並在 [out] 的變數中傳回的物件會造成記憶體流失。

 處理這類物件的 managed 的方法應該視為<xref:System.IntPtr>為指標`IUnknown`物件，然後呼叫<xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A>方法，以取得物件。 呼叫端應該再將傳回值轉換成任何類型的適用。 當不再需要物件時，呼叫<xref:System.Runtime.InteropServices.Marshal.Release%2A>釋放它。

 以下是呼叫的範例<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>方法，並處理`IUnknown`正確物件：

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
>  下列方法將已知`IUnknown`做為類型的物件指標<xref:System.IntPtr>。 在本節中所述，請處理它們。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>[Out] 參數的選擇性
 尋找定義為 [out] 參數資料類型 (`int`，`object`等等) 在 COM 介面，但定義為在相同的資料類型的陣列[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]interop 組件的方法原型。

 某些 COM 介面，例如<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>，將 [out] 參數為選擇性。 如果物件不是必要的這些 COM 介面傳回`null`指標做為該參數，而不是建立 [out] 物件的值。 這是依設計的結果。 這些介面，如`null`指標會假設為一部分的 VSPackage，正確的行為，並會傳回任何錯誤。

 因為 CLR 不允許的值是 [out] 參數`null`，部分這些介面的設計的行為不是 managed 程式碼中直接提供。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Interop 組件之受影響的介面的方法能解決問題，藉由定義為陣列的相關參數，因為 CLR 允許的傳遞`null`陣列。

 這些方法的 managed 的實作應該放置`null`至參數時沒有任何要傳回的陣列。 否則，建立正確型別的其中一個項目陣列，而且陣列中放入的傳回值。

 管理從介面的選擇性 [out] 接收資訊的方法參數會接收參數做為陣列。 只要檢查陣列的第一個元素的值。 如果不是`null`，如同它是原始的參數，將第一個項目。

## <a name="passing-constants-in-pointer-parameters"></a>傳遞常數指標參數
 參數定義為 [in] 中的 COM 介面指標，但為定義看起來<xref:System.IntPtr>輸入[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]interop 組件的方法原型。

 當 COM 介面傳遞特殊的值，例如 0、-1 或 – 2，而不是物件指標時，就會發生類似的問題。 不同於[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]，CLR 不允許轉型為物件的常數。 相反地， [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interop 組件會定義為參數<xref:System.IntPtr>型別。

 這些方法的 managed 的實作應該利用事實<xref:System.IntPtr>類別同時具有`int`和`void *`建構函式來建立<xref:System.IntPtr>從物件或整數常數，以適當的。

 管理接收的方法<xref:System.IntPtr>此類型的參數應該使用<xref:System.IntPtr>型別轉換運算子，來處理結果。 第一次轉換<xref:System.IntPtr>至`int`及測試對相關的整數常數。 如果沒有任何值相符時，將它轉換成所需型別物件，並繼續。

 這個範例，請參閱<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>。

## <a name="ole-return-values-passed-as-out-parameters"></a>OLE 會傳回值傳遞做為 [out] 參數
 尋找具有方法`retval`傳回的值，在 COM 介面，但有`int`傳回值和額外的 [out] 中的陣列參數[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]interop 組件的方法原型。 應該很清楚這些方法需要特殊處理，因為[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]interop 組件方法原型有一個比 COM 介面方法的參數。

 許多 OLE 活動處理的 COM 介面將 OLE 狀態的相關資訊傳送回呼叫端程式儲存在`retval`介面的傳回值。 而不是使用傳回的值，對應[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]interop 組件的方法將資訊傳送回給呼叫程式中的 [out] 儲存陣列參數。

 這些方法的 managed 的實作應該建立以 [out] 參數相同類型的單一元素陣列，並將它放在參數中。 陣列元素的值應該是適當的 COM 與相同`retval`。

 呼叫此類型的介面的 managed 的方法應該提取從 [out] 陣列的第一個項目。 這個項目可以視為，就好像`retval`自對應的 COM 介面傳回的值。

## <a name="see-also"></a>另請參閱
 [與 Unmanaged 程式碼互通](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
