---
title: 如何:識別庫中的符號 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1fe920fabd05a875b336467fbba16e4229fa9613
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708008"
---
# <a name="how-to-identify-symbols-in-a-library"></a>如何:識別庫中的符號
符號流覽工具顯示符號的分層檢視。 符號表示命名空間、物件、類、類成員和其他語言元素。

 層次結構中的每個符號都可以透過符號庫傳遞到[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件管理員的導航資訊通過以下介面進行標識:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.

 符號在層次結構中的位置區分符號。 它允許符號流覽工具導航到特定符號。 符號的唯一、完全限定的路徑決定了位置。 路徑中的每個元素都是一個節點。 路徑從頂級節點開始,以特定符號結束。 例如,如果 M1 方法是 C1 類的成員,而 C1 位於 N1 命名空間中,則 M1 方法的完整路徑為 N1。C1.M1. 此路徑包含三個節點:N1、C1 和 M1。

 導航資訊允許[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件管理器在層次結構中尋找、選擇和保留所選符號。 它允許從一個瀏覽工具導航到另一個流覽工具。 使用**物件瀏覽器**瀏覽專案中的[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]符號時 ,可以右鍵單擊方法並啟動 **「調用瀏覽器」** 工具以在調用圖中顯示該方法。

 兩個表單描述符號位置。 規範形式基於符號的完全限定路徑。 它表示符號在層次結構中的唯一位置。 它與符號流覽工具無關。 要獲取規範形式資訊,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件管理器調<xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>用 方法。 簡報文件檔描述符號在特定符號流覽工具中的位置。 符號的位置相對於層次結構中其他符號的位置。 給定的符號可能有多個表示路徑,但只有一個規範路徑。 例如,如果 C1 類是從 C2 類繼承的,並且兩個類都在 N1 命名空間中,**則物件瀏覽器**將顯示以下分層樹:

```
N1
    C1
        Bases and Interfaces
            C2
    C2
        Bases and Interfaces
. . . . . . . . . . .

```

 在此示例中,C2 類的規範路徑為 N1 + C2。 C2 的表示路徑包括 C1 和「基礎和介面」節點:N1 + C1 = 「基礎和介面」 = C2。

 要獲取表示表單資訊,物件管理器調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>方法。

## <a name="to-obtain-canonical-and-presentation-forms-information"></a>取得規格及展示表單資訊

1. 實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> 方法。

     物件管理員調用此方法以獲取符號規範路徑中包含的節點清單。

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

     物件管理員調用此方法以獲取符號的表示路徑中包含的節點清單。

## <a name="see-also"></a>另請參閱
- [支援符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [如何:向物件管理員註冊庫](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [如何:向物件管理員公開函式庫提供的符號清單](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
