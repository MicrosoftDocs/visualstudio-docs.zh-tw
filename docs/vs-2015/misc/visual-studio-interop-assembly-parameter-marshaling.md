---
title: Visual Studio Interop 元件參數封送處理 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- troubleshooting Visual Studio SDK interop assemblies
- interop assemblies, parameter marshaling
- interop assemblies, troubleshooting
ms.assetid: 89123eae-0fef-46d5-bd36-3d2a166b14e3
caps.latest.revision: 24
manager: jillfra
ms.openlocfilehash: ac95c40b356c542da323a3ea3744827087f2d840
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686917"
---
# <a name="visual-studio-interop-assembly-parameter-marshaling"></a>Visual Studio Interop 組件參數封送處理
以 managed 程式碼撰寫的 Vspackage 可能必須呼叫或由非受控 COM 程式碼呼叫。 通常，interop 封送處理器會自動轉換或封送處理方法引數。 不過，有時候引數無法以直接的方式轉換。 在這些情況下，interop 元件方法原型參數會用來盡可能地比對 COM 函數參數。 如需詳細資訊，請參閱 [Interop 封送處理](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)。  
  
## <a name="general-suggestions"></a>一般建議  
  
##### <a name="read-the-reference-documentation"></a>閱讀參考檔  
 偵測互通性問題的有效方法，是閱讀每個方法的參考檔。  
  
 每個方法的參考檔包含三個相關章節：  
  
- COM 函式 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] 原型。  
  
- Interop 元件方法原型。  
  
- COM 參數的清單和每個參數的簡短描述。  
  
##### <a name="look-for-differences-between-the-two-prototypes"></a>尋找兩個原型之間的差異  
 大部分的互通性問題衍生自 COM 介面中特定類型的定義與 interop 元件中相同型別的定義之間的不相符 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 例如，請考慮在 `null` [out] 參數中傳遞值的功能差異。 您必須尋找兩個原型之間的差異，並考慮它們對傳遞資料的後果。  
  
##### <a name="read-the-parameter-definitions"></a>讀取參數定義  
 讀取參數定義。 相較于 common language runtime (CLR) 與在單一參數中混合不同類型的資料有關，COM 較不嚴格。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]COM 介面充分利用此彈性。 任何可以傳遞或要求非標準值或資料類型的參數（例如指標參數中的常數值），都應該如檔中所述。  
  
### <a name="iunknown-objects-passed-as-type-void"></a>以 void * * 類型傳遞的 IUnknown 物件  
 在 COM 介面中尋找定義為類型的 [out] 參數 `void **` ，但是定義為 `[``iid_is``]` [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interop 元件方法原型中的參數。  
  
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
  
### <a name="optional-out-parameters"></a>選擇性的 [out] 參數  
 在 COM 介面中尋找定義為 [out] 資料類型 (、等等) 的參數， `int` `object` 但在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interop 元件方法原型中定義為相同資料類型的陣列。  
  
 某些 COM 介面（例如）會將 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> [out] 參數視為選擇性。 如果不需要物件，這些 COM 介面會將指標傳回 `null` 為該參數的值，而不是建立 [out] 物件。 這是原廠設定。 針對這些介面， `null` 指標會假設為 VSPackage 正確行為的一部分，而且不會傳回任何錯誤。  
  
 因為 CLR 不允許將 [out] 參數的值設為 `null` ，所以在 managed 程式碼中無法直接使用這些介面的部分設計行為。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]受影響之介面的 interop 元件方法會藉由將相關的參數定義為數組來解決此問題，因為 CLR 允許傳遞 `null` 陣列。  
  
 當沒有任何要傳回的專案時，這些方法的 Managed 執行應該會將 `null` 陣列放入參數中。 否則，請建立正確型別的單一元素陣列，並將傳回值放在陣列中。  
  
 使用選擇性的 [out] 參數從介面接收資訊的 Managed 方法會以陣列形式接收參數。 只需要檢查陣列的第一個元素值。 如果不是，則會 `null` 將第一個元素視為原始參數。  
  
### <a name="passing-constants-in-pointer-parameters"></a>在指標參數中傳遞常數  
 在 COM 介面中尋找定義為 [in] 指標的參數，但在 <xref:System.IntPtr> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interop 元件方法原型中定義為類型。  
  
 當 COM 介面傳遞特殊值（例如0、-1 或-2）而非物件指標時，就會發生類似的問題。 與不同 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] 的是，CLR 不允許將常數轉換成物件。 相反地， [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interop 元件會將參數定義為 <xref:System.IntPtr> 型別。  
  
 這些方法的 Managed 執行應該會利用這個事實： <xref:System.IntPtr> 類別同時具有和函 `int` 式 `void *` ，以視 <xref:System.IntPtr> 需要從物件或整數常數建立。  
  
 接收 <xref:System.IntPtr> 此型別之參數的 Managed 方法應該使用 <xref:System.IntPtr> 型別轉換運算子來處理結果。 首先，將轉換成 <xref:System.IntPtr> `int` ，並針對相關的整數常數進行測試。 如果沒有相符的值，請將它轉換成所需類型的物件，並繼續進行。  
  
 如需這項的範例，請參閱 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> 。  
  
### <a name="ole-return-values-passed-as-out-parameters"></a>以 [out] 參數傳遞的 OLE 傳回值  
 `retval`在 COM 介面中尋找有傳回值的方法，但在 `int` [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interop 元件方法原型中有傳回值和其他的 [out] 陣列參數。 請注意，這些方法需要特殊處理，因為 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interop 元件方法原型具有比 COM 介面方法更多的參數。  
  
 許多處理 OLE 活動的 COM 介面都會將 OLE 狀態的相關資訊傳送回介面傳回值中所儲存的呼叫程式 `retval` 。 相對應的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interop 元件方法會將資訊傳回給儲存在 [out] 陣列參數中的呼叫程式，而不是使用傳回值。  
  
 這些方法的 Managed 執行應該建立與 [out] 參數相同類型的單一元素陣列，並將它放在參數中。 陣列元素的值應該與適當的 COM 相同 `retval` 。  
  
 呼叫此型別之介面的 Managed 方法應該從 [out] 陣列提取第一個元素。 您可以將這個元素視為 `retval` 來自對應 COM 介面的傳回值。  
  
## <a name="see-also"></a>另請參閱  
 [Interop 封送處理](https://msdn.microsoft.com/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [Interop 封送處理](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [疑難排解互通性](https://msdn.microsoft.com/library/b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37)   
 [Managed VSPackages](../misc/managed-vspackages.md)