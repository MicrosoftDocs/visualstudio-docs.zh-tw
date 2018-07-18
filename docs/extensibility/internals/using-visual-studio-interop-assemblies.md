---
title: 使用 Visual Studio Interop 組件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ca0ff9a75d72bc723b767a43f12123094a520644
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31146815"
---
# <a name="using-visual-studio-interop-assemblies"></a>使用 Visual Studio Interop 組件
Visual Studio interop 組件可讓受管理的應用程式存取 COM 介面，提供 Visual Studio 擴充性。 有一些直線的 COM 介面和其 interop 的版本之間的差異。 例如，Hresult 通常會表示為 int 值需要處理的例外狀況，以相同的方式和參數 (特別是 out 參數） 的處理方式不同。  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>處理從 COM 傳回給 Managed 程式碼的 HRESULT  
 當您透過 Managed 程式碼呼叫 COM 介面時，請檢查 HRESULT 值，並視需要擲回例外狀況。 <xref:Microsoft.VisualStudio.ErrorHandler>類別包含<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>方法，這個方法會擲回 COM 例外狀況的 HRESULT 值而定，傳遞給它。  
  
 根據預設，<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>傳遞的值小於零的 HRESULT 時擲回例外狀況。 在這類 Hresult 是可接受的值，應該擲回任何例外狀況的情況下，其他 hresult 值應該傳遞至<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>測試值之後。 如果正在測試的 HRESULT 符合明確傳遞至任何 HRESULT 值<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>，擲回任何例外狀況。  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants>類別包含常數的常見的 HRESULT，比方說，<xref:Microsoft.VisualStudio.VSConstants.S_OK>和<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>，和[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]HRESULT，比方說，<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>和<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>。 <xref:Microsoft.VisualStudio.VSConstants> 也提供<xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A>和<xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>方法，其對應至在 COM 中的 SUCCEEDED 和 FAILED 巨集  
  
 例如，請考慮下列函式呼叫，其中<xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>是可接受的傳回值，但任何其他 HRESULT 小於零代表發生錯誤。  
  
 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]  
  
 如果有多個可接受的傳回值，其他 HRESULT 值只附加到清單中的呼叫<xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>。  
  
 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>透過 Managed 程式碼將 HRESULT 傳回給 COM  
 如果沒有發生例外狀況，管理程式碼傳回<xref:Microsoft.VisualStudio.VSConstants.S_OK>至呼叫它的 COM 函式。 COM Interop 支援透過 Managed 程式碼進行強類型處理的常見例外狀況。 例如，收到無法接受方法`null`引數會擲回<xref:System.ArgumentNullException>。  
  
 如果您不確定哪個例外狀況擲回，但您知道 HRESULT 您想要傳回至 COM，您可以使用<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>方法會擲回適當的例外狀況。 這甚至適用於非標準的錯誤，例如<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>。 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> 嘗試的 HRESULT 對應傳送給強類型例外狀況。 如果失敗，則會改為擲回一般 COM 例外狀況。 最終的結果會是 HRESULT 您傳遞至<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>從 managed 程式碼會傳回給呼叫它的 COM 函式。  
  
> [!NOTE]
>  例外狀況會危害效能並用來指出異常程式狀況。 經常發生的狀況應該透過內嵌方式處理，而不是擲回例外狀況。  
  
## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown 參數傳遞為類型 void * *  
 [Out] 參數定義為類型尋找`void **`COM 介面，但會定義成`[``iid_is``]`中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]interop 組件方法的原型。  
  
 某些情況下，會產生 COM 介面`IUnknown`物件和 COM 介面然後將它當做傳遞類型`void **`。 這些介面是特別重要因為如果變數定義為 IDL 中 [out] 則`IUnknown`物件是以參考計數`AddRef`方法。 如果物件未正確處理，就會發生記憶體流失。  
  
> [!NOTE]
>  `IUnknown` COM 介面所建立及傳回的 [out] 變數中的物件會導致記憶體流失，如果沒有明確釋出。  
  
 處理這類物件的 managed 的方法應該將<xref:System.IntPtr>為指標`IUnknown`物件，然後呼叫<xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A>方法，以取得物件。 呼叫端應該然後傳回值轉換為任何類型的適用。 當不再需要物件時，呼叫<xref:System.Runtime.InteropServices.Marshal.Release%2A>釋放它。  
  
 下列是範例呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>方法和處理`IUnknown`正確物件：  
  
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
>  下列方法來傳遞已知`IUnknown`做為類型的物件指標<xref:System.IntPtr>。 本章節中所述，請處理它們。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
## <a name="optional-out-parameters"></a>[Out] 參數的選擇性  
 尋找定義為 [out] 參數的資料類型 (`int`，`object`等等) 在 COM 介面，但會定義為在相同的資料類型的陣列[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]interop 組件方法的原型。  
  
 某些 COM 介面，例如<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>，將 [out] 參數為選擇性。 如果物件不是必要的這些 COM 介面傳回`null`指標做為該參數，而不是建立 [out] 物件的值。 這是依設計的結果。 這些介面，如`null`指標就會被一部分的 VSPackage，正確的行為，而不會傳回錯誤。  
  
 因為 CLR 不允許的值為 [out] 參數`null`，這些介面的設計的行為部分不是直接使用 managed 程式碼中。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Interop 組件之受影響的介面的方法藉由定義相關的參數為陣列，因為 CLR 允許傳遞的暫時解決此問題`null`陣列。  
  
 這些方法的 managed 的實作應放置`null`至參數時沒有任何要傳回的陣列。 否則，會建立正確類型的單一元素陣列並將傳回的值放入陣列中。  
  
 管理從介面與選擇性 [out] 接收資訊的方法參數方式收到參數陣列。 只要檢查陣列的第一個元素的值。 如果不是`null`，將第一個項目，就好像原始參數。  
  
## <a name="passing-constants-in-pointer-parameters"></a>傳遞常數指標參數  
 尋找的參數定義為 [in] COM 介面的指標，但定義為<xref:System.IntPtr>輸入[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]interop 組件方法的原型。  
  
 當 COM 介面至特殊的值，例如 0、-1 或-2，而不是物件指標時，就會發生類似的問題。 不同於[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]，CLR 不允許轉換為物件的常數。 相反地， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 組件定義做為參數<xref:System.IntPtr>型別。  
  
 這些方法的 managed 的實作應該利用事實<xref:System.IntPtr>類別同時具有`int`和`void *`建構函式來建立<xref:System.IntPtr>從物件或整數常數，適當地。  
  
 管理方法接收<xref:System.IntPtr>應該使用這個型別參數的<xref:System.IntPtr>類型轉換運算子，以處理結果。 第一次轉換<xref:System.IntPtr>至`int`與測試相關的整數常數。 如果沒有任何值相符時，將它轉換成所需的類型的物件，並繼續。  
  
 這個範例，請參閱<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>。  
  
## <a name="ole-return-values-passed-as-out-parameters"></a>OLE 傳回值傳遞做為 [out] 參數  
 尋找具有方法`retval`傳回值會在 COM 介面，但有`int`傳回值，以及有額外的 [out] 中的陣列參數[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]interop 組件方法的原型。 應該很清楚這些方法需要特殊處理，因為[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]interop 組件方法原型有一個比 COM 介面方法的多個參數。  
  
 許多 OLE 活動處理的 COM 介面將 OLE 狀態的相關資訊傳送回呼叫端程式儲存在`retval`傳回值的介面。 而不是使用傳回的值，對應[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]interop 組件的方法將資訊傳送回呼叫端程式儲存在 [out] 陣列參數。  
  
 這些方法的 managed 的實作應該建立 [out] 參數具有相同類型的單一項目陣列，並將它放在參數中。 陣列元素的值應該是適當的 COM 與相同`retval`。  
  
 呼叫此類型的介面的 managed 的方法應該提取從 [out] 陣列的第一個項目。 可以處理這個項目，就好像`retval`從對應的 COM 介面傳回值。  
  
## <a name="see-also"></a>另請參閱  
 [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)