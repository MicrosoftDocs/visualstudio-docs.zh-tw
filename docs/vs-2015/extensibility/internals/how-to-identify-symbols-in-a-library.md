---
title: HOW TO：識別文件庫中的符號 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5dcdbd6d9f9f24b094d62289b0b058edde8c156b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945750"
---
# <a name="how-to-identify-symbols-in-a-library"></a>HOW TO：識別程式庫中的符號
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

符號瀏覽工具顯示符號的階層式的檢視。 符號代表命名空間、 物件、 類別、 類別成員和其他語言項目。  
  
 每個階層中的符號，可識別的符號程式庫所傳遞的瀏覽資訊[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]物件管理員，透過下列介面：  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 在階層中符號位置區分的符號。 它可讓瀏覽至特定符號的符號瀏覽工具。 唯一、 完整的路徑，該符號會決定位置。 在路徑中的每個項目是一個節點。 路徑的最上層節點的開頭和結尾的特定符號。 例如，如果 M1 方法 C1 類別的成員，而且 C1 是 N1 命名空間中，M1 方法的完整路徑會是 N1。C1。M1。 此路徑包含三個節點：N1，C1 和 M1。  
  
 瀏覽資訊可讓[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]物件管理員，以找出、 選取並持續在階層中選取的符號。 它可讓從一種瀏覽工具巡覽到另一個。 在使用時**物件瀏覽器**瀏覽中的符號[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]專案中，您可以以滑鼠右鍵按一下方法，並開始**呼叫瀏覽器**工具以顯示方法的呼叫歷程圖中。  
  
 兩種形式會描述符號位置。 標準的格式根據符號的完整路徑。 它代表的符號之階層中唯一的位置。 它是獨立的符號瀏覽工具。 若要取得標準格式的資訊，[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]物件管理員呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>方法。 呈現表單描述特定符號瀏覽工具內符號的位置。 符號的位置會相對於 hierarchicy 中其他符號的位置。 指定的符號可能會有數個展示檔路徑，但只有一個正式路徑。 例如，如果 C1 類別繼承自 C2 類別，而這兩個類別是在 N1 的命名空間**物件瀏覽器**會顯示下列階層樹狀結構：  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 C2 類別，在此範例中，正式路徑為 N1 + C2。 C2 的展示檔路徑包含 C1 和 「 基底和介面 「 節點：N1 + C1 + 「 基底和介面 」 + C2。  
  
 若要取得呈現表單資訊物件管理員呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>方法。  
  
## <a name="identifying-a-symbol-in-the-hierarchy"></a>識別階層中的符號  
  
#### <a name="to-obtain-canonical-and-presentation-forms-information"></a>若要取得標準，並展示形成的資訊  
  
1.  實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> 方法。  
  
     物件管理員會呼叫此方法來取得標準的符號路徑中包含的節點清單。  
  
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
  
     物件管理員會呼叫這個方法，以取得符號的簡報路徑中包含的節點清單。  
  
## <a name="see-also"></a>另請參閱  
 [支援符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [如何：使用物件管理員註冊程式庫](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [如何：公開 （expose) 程式庫提供對物件管理員中的符號的清單](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
