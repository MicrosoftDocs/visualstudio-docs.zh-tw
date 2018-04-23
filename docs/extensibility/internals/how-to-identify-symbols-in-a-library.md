---
title: 如何： 識別文件庫中的符號 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 310ba421120101ce545888bcf4c069ca454cf086
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-identify-symbols-in-a-library"></a>如何： 識別文件庫中的符號
符號瀏覽工具中顯示符號的階層式的檢視。 符號代表命名空間、 物件、 類別、 類別成員和其他語言項目。  
  
 可以使用符號程式庫所傳遞的瀏覽資訊來識別階層中的每個符號[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件管理員，透過下列介面：  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 在階層中符號的位置區分的符號。 它可讓符號瀏覽工具來瀏覽至特定的符號。 符號的唯一、 完整路徑位置來決定。 在路徑中的每個項目是一個節點。 路徑的最上層節點的開頭和結尾是特定的符號。 例如，如果 M1 方法是 C1 類別的成員，而且 C1 N1 命名空間中，M1 方法的完整路徑是 N1。C1。M1。 此路徑包含三個節點： N1、 C1、 和 M1。  
  
 瀏覽資訊可讓[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件管理員來尋找、 選取並保留在階層中選取符號。 它可讓巡覽到另一個瀏覽工具。 同時使用**物件瀏覽器**瀏覽中的符號[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]專案中，您可以以滑鼠右鍵按一下的方法，並開始**呼叫瀏覽器**工具以顯示方法的呼叫歷程圖中。  
  
 兩種形式說明符號位置。 標準格式根據符號的完整路徑。 它表示符號的階層中唯一的位置。 它是獨立的符號瀏覽工具。 若要取得的標準格式的資訊，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件管理員呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>方法。 簡報表單描述的特定符號瀏覽工具內符號的位置。 符號的位置是相對於 hierarchicy 中的其他符號位置。 指定的符號可能有數個展示檔路徑，但只有一個正式路徑。 例如，如果 C1 類別繼承自 C2 類別，這兩個類別位於 N1 命名空間，**物件瀏覽器**會顯示下列階層樹狀結構：  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 C2 類別，在此範例中，正式路徑為 N1 + C2。 C2 的展示檔路徑包含 C1 和 「 基底和介面 」 節點： N1 + C1 + 「 基底和介面"+ C2。  
  
 若要取得簡報表單資訊物件管理員呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>方法。  
  
## <a name="identifying-a-symbol-in-the-hierarchy"></a>識別階層中的符號  
  
#### <a name="to-obtain-canonical-and-presentation-forms-information"></a>若要取得標準簡報 form 資訊和  
  
1.  實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> 方法。  
  
     物件管理員呼叫此方法來取得標準的符號路徑中包含的節點清單。  
  
    ```vb  
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer  
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)  
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)  
        Return 0  
    End Function  
    ```  
  
    ```csharp  
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)  
    {  
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =  
            new CallBrowserEnumNavInfoNodes(m_strMethod);  
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);  
        return 0;  
    }  
  
    ```  
  
2.  實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> 方法。  
  
     物件管理員呼叫此方法來取得符號的簡報路徑中包含的節點清單。  
  
## <a name="see-also"></a>另請參閱  
 [支援的符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [如何： 註冊物件管理員與程式庫](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [如何︰將程式庫提供的符號清單公開至物件管理員](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)