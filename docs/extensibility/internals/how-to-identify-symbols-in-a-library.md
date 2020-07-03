---
title: 如何：識別程式庫中的符號 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd091f003909110c696c2e42ad80d6c6ea4859d2
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905401"
---
# <a name="how-to-identify-symbols-in-a-library"></a>如何：識別程式庫中的符號
符號流覽工具會顯示符號的階層式視圖。 符號代表命名空間、物件、類別、類別成員和其他語言元素。

 階層中的每個符號都可以透過下列介面，由符號連結庫傳遞至物件管理員的導覽資訊來識別 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ：

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.

 階層中符號的位置會區分符號。 它允許符號流覽工具流覽至特定的符號。 符號的唯一、完整路徑會決定位置。 路徑中的每個元素都是一個節點。 路徑會從最上層節點開始，並以特定符號結尾。 例如，如果 M1 方法是 C1 類別的成員，而 C1 是在 N1 命名空間中，則 M1 方法的完整路徑為 N1。C1.M1. 此路徑包含三個節點： N1、C1 和 M1。

 導覽資訊可讓 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 物件管理員尋找、選取並繼續選取階層中的符號。 它可以從一個流覽工具流覽到另一個。 使用**物件瀏覽器**流覽專案中的符號時 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] ，您可以用滑鼠右鍵按一下方法，然後啟動**呼叫瀏覽器**工具，在呼叫圖表中顯示方法。

 兩個表單會描述項號位置。 標準格式是以符號的完整路徑為基礎。 它代表階層中符號的唯一位置。 它與符號流覽工具無關。 為了取得標準格式資訊， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 物件管理員會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> 方法。 展示形式會描述項號在特定符號流覽工具內的位置。 符號的位置相對於階層中其他符號的位置。 指定的符號可能有數個呈現路徑，但只能有一個標準路徑。 例如，如果 C1 類別是繼承自 C2 類別，而且這兩個類別都在 N1 命名空間中，則**物件瀏覽器**會顯示下列階層式樹狀結構：

```
N1
    C1
        Bases and Interfaces
            C2
    C2
        Bases and Interfaces
. . . . . . . . . . .

```

 C2 類別的標準路徑（在此範例中為 N1 + C2）。 C2 的呈現路徑包含 C1 和「基底和介面」節點： N1 + C1 + 「基底和介面」 + C2。

 為了取得簡報表單資訊，物件管理員會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> 方法。

## <a name="to-obtain-canonical-and-presentation-forms-information"></a>取得標準和簡報形式資訊

1. 實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> 方法。

     物件管理員會呼叫這個方法，以取得符號的標準路徑中包含的節點清單。

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

2. 實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> 方法。

     物件管理員會呼叫這個方法，以取得符號呈現路徑中包含的節點清單。

## <a name="see-also"></a>另請參閱
- [支援符號流覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [如何：使用物件管理員註冊程式庫](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [如何：將程式庫提供的符號清單公開至物件管理員](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
