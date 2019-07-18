---
title: Visual Studio Interop 組件參數封送處理 |Microsoft Docs
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686917"
---
# <a name="visual-studio-interop-assembly-parameter-marshaling"></a>Visual Studio Interop 組件參數封送處理
Vspackage 以 managed 程式碼撰寫，可能必須呼叫或 unmanaged 的 COM 程式碼所呼叫。 一般而言，方法引數轉換，或由封送處理，會自動 interop 封送處理器。 不過，有時候引數無法轉換以直接的方式。 在這些情況下，interop 組件方法的原型參數來儘可能密集地符合 COM 函式參數。 如需詳細資訊，請參閱 < [Interop 封送處理](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)。  
  
## <a name="general-suggestions"></a>一般建議  
  
##### <a name="read-the-reference-documentation"></a>閱讀參考文件  
 偵測到互通性問題的有效方法是閱讀每個方法的參考文件。  
  
 每個方法的參考文件包含三個相關的區段：  
  
- [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] COM 函式原型。  
  
- Interop 組件的方法原型。  
  
- COM 參數清單和每個的簡短描述。  
  
##### <a name="look-for-differences-between-the-two-prototypes"></a>尋找兩個原型之間的差異  
 大部分的互通性問題是衍生自 COM 介面中的特定類型的定義中相同類型的定義之間的不符[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]interop 組件。 例如，請考慮在能夠傳遞的差異`null`以 [out] 參數的值。 您必須尋找兩個原型之間的差異，並考慮他們所傳遞之資料的後果。  
  
##### <a name="read-the-parameter-definitions"></a>讀取的參數定義  
 讀取的參數定義。 COM 是比有關混合使用不同類型的單一參數中的資料的 common language runtime (CLR) 較不嚴格。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] COM 介面充分善用此彈性。 任何可以傳送或需要非標準的值或類型的資料，例如中指標參數的常值的參數應該因此描述文件中。  
  
### <a name="iunknown-objects-passed-as-type-void"></a>IUnknown 物件傳遞為類型 void * *  
 [Out] 定義為類型的參數尋找`void **`COM 介面，但會定義成`[``iid_is``]`在[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]interop 組件的方法原型。  
  
 某些情況下，會產生 COM 介面`IUnknown`物件，並在 COM 介面然後將它傳遞做為類型`void **`。 這些介面是特別重要因為如果變數定義為 [out] 中的 IDL 中，則`IUnknown`物件是使用參考計數`AddRef`方法。 如果物件未正確地處理，就會發生記憶體流失。  
  
> [!NOTE]
> `IUnknown`未明確地釋放時建立的 COM 介面，並在 [out] 的變數中傳回的物件會造成記憶體流失。  
  
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
> 下列方法將已知`IUnknown`做為類型的物件指標<xref:System.IntPtr>。 在本節中所述，請處理它們。  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
### <a name="optional-out-parameters"></a>[Out] 參數的選擇性  
 尋找定義為 [out] 參數資料類型 (`int`，`object`等等) 在 COM 介面，但定義為在相同的資料類型的陣列[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]interop 組件的方法原型。  
  
 某些 COM 介面，例如<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>，將 [out] 參數為選擇性。 如果物件不是必要的這些 COM 介面傳回`null`指標做為該參數，而不是建立 [out] 物件的值。 這是依設計的結果。 這些介面，如`null`指標會假設為一部分的 VSPackage，正確的行為，並會傳回任何錯誤。  
  
 因為 CLR 不允許的值是 [out] 參數`null`，部分這些介面的設計的行為不是 managed 程式碼中直接提供。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Interop 組件之受影響的介面的方法能解決問題，藉由定義為陣列的相關參數，因為 CLR 允許的傳遞`null`陣列。  
  
 這些方法的 managed 的實作應該放置`null`至參數時沒有任何要傳回的陣列。 否則，建立正確型別的其中一個項目陣列，而且陣列中放入的傳回值。  
  
 管理從介面的選擇性 [out] 接收資訊的方法參數會接收參數做為陣列。 只要檢查陣列的第一個元素的值。 如果不是`null`，如同它是原始的參數，將第一個項目。  
  
### <a name="passing-constants-in-pointer-parameters"></a>傳遞常數指標參數  
 參數定義為 [in] 中的 COM 介面指標，但為定義看起來<xref:System.IntPtr>輸入[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]interop 組件的方法原型。  
  
 當 COM 介面傳遞特殊的值，例如 0、-1 或 – 2，而不是物件指標時，就會發生類似的問題。 不同於[!INCLUDE[vcprvc](../includes/vcprvc-md.md)]，CLR 不允許轉型為物件的常數。 相反地， [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interop 組件會定義為參數<xref:System.IntPtr>型別。  
  
 這些方法的 managed 的實作應該利用事實<xref:System.IntPtr>類別同時具有`int`和`void *`建構函式來建立<xref:System.IntPtr>從物件或整數常數，以適當的。  
  
 管理接收的方法<xref:System.IntPtr>此類型的參數應該使用<xref:System.IntPtr>型別轉換運算子，來處理結果。 第一次轉換<xref:System.IntPtr>至`int`及測試對相關的整數常數。 如果沒有任何值相符時，將它轉換成所需型別物件，並繼續。  
  
 這個範例，請參閱<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>。  
  
### <a name="ole-return-values-passed-as-out-parameters"></a>OLE 會傳回值傳遞做為 [out] 參數  
 尋找具有方法`retval`傳回的值，在 COM 介面，但有`int`傳回值和額外的 [out] 中的陣列參數[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]interop 組件的方法原型。 應該很清楚這些方法需要特殊處理，因為[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]interop 組件方法原型有一個比 COM 介面方法的參數。  
  
 許多 OLE 活動處理的 COM 介面將 OLE 狀態的相關資訊傳送回呼叫端程式儲存在`retval`介面的傳回值。 而不是使用傳回的值，對應[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]interop 組件的方法將資訊傳送回給呼叫程式中的 [out] 儲存陣列參數。  
  
 這些方法的 managed 的實作應該建立以 [out] 參數相同類型的單一元素陣列，並將它放在參數中。 陣列元素的值應該是適當的 COM 與相同`retval`。  
  
 呼叫此類型的介面的 managed 的方法應該提取從 [out] 陣列的第一個項目。 這個項目可以視為，就好像`retval`自對應的 COM 介面傳回的值。  
  
## <a name="see-also"></a>另請參閱  
 [Interop 封送處理](https://msdn.microsoft.com/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [Interop 封送處理](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [互通性的疑難排解](https://msdn.microsoft.com/library/b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37)   
 [Managed VSPackages](../misc/managed-vspackages.md)